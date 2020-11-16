---
tags: [Code Snippets, React]
title: Example React App Architecture
created: '2020-11-15T05:06:39.047Z'
modified: '2020-11-15T06:34:08.586Z'
---

Example React App Architecture
==============================
App Description
---------------
This is a simple React app example that uses three primary components, App, SearchBar, and FoodList to retrieve a list of foods from an external API based on a search term, and display it in a `<select>` element. 

* App:
  * Renders SearchBar and FoodList
  * State contains array `foods`
  * Contains asynchronous `onSearchSubmit(term)` method to make API call and set state with the call response
* SearchBar:
  * State contains string `term`
  *  Uses onChange to set `term` to input field value
  * Uses `onFormSubmit()` to pass `term` to prop `onSubmit`. `onSubmit` passes `term` to App's `onSearchSubmit()` method
* FoodList:
  * Contains `renderedList` method that maps foods to `<option>` elements within a `<select>` element
  * Foods passed in via `foods` prop

Sequence Diagram
----------------

``` mermaid
sequenceDiagram
participant A as App.js
participant S as SearchBar.js
participant F as FoodList.js
    A->>+S: Render SearchBar.js
    A->>+F: Render FoodList.js
    loop onChange()
      S->>S: update state Term to input val
    end
    S->>+A: Pass Term via onFormSubmit() to onSubmit prop 
    loop onSearchSubmit()
      A->>+A: POST: set state Foods to response
    end
      A->>+F: Pass Foods via foods prop
      loop map response values
        F->>+F:Populate select elements with values
      end
    F->>+A: Return populated form element
            
```
Components
----------
### App
``` javascript
import React from 'react';
import usda from '../api/usda';
import SearchBar from './SearchBar'
import FoodList from './FoodList'

class App extends React.Component {
    state = {
        foods: []
    };

    // Set state to API call results
    onSearchSubmit = async (term) => {
        const response = await usda.post("/foods/search?api_key=Pcx35ak7cgaoo1U22LNf36jywsefUmiQBS0cStLE", {query: term});
        this.setState({ foods: response.data.foods })
    };

    render() {
        return (
            <div className="ui container" style={{ marginTop: "10px" }}>
                <div className="ui segment">
                    // Call onSearchSubmit() to initiate API call with search term passed from SearchBar component
                    <SearchBar onSubmit={this.onSearchSubmit} />
                    <br />
                    // Pass foods from App state via foods prop into FoodList component
                    <FoodList foods={this.state.foods}/>
                </div>
            </div>
        );
    };  
};

export default App;
```
#### Uses an axios setup component (usda):
``` javascript
import axios from 'axios';

export default axios.create ({
    baseURL: 'https://api.nal.usda.gov/fdc/v1'
});
```

### SearchBar
``` javascript
import React from 'react';

class SearchBar extends React.Component {
    state = { term: "" };
    // Call onSubmit() method passed in via onSubmit prop in App, passing in term from state
    onFormSubmit = e => {
      // Stop default form submit behavior (page refresh)
        e.preventDefault();
        this.props.onSubmit(this.state.term);
    };

    render() {
        return (
          // Call onFormSubmit() onSubmit
            <form onSubmit={this.onFormSubmit} className="ui form" id="foodsForm">
                <div className="field">
                    <label htmlFor="foodInput">Enter your search term:</label>
                    <input
                        type="text"
                        id="foodInput"
                        // Set value to state.term
                        value={this.state.term}
                        // On change, update state
                        onChange={e => this.setState({term: e.target.value})}
                    ></input>
                </div>
            </form>
        )
    }
};

export default SearchBar;
```

### FoodList
``` javascript
import React from 'react';

// Map foods as passed in via foods prop in App
const FoodList = ({ foods, onFoodSelect }) => {
    const renderedList = foods.map((food) => {
        let description = food.description;
        // Return truncated value in <option> if str.length > 50
        if (description.length > 50) {
            return <option key={food.fdcId} value={description}>{`${description.slice(0, 46)}...`}</option>
        } else {
            return <option key={food.fdcId} value={description}>{description}</option>
        }
    });
    return (
        <form>
            <label htmlFor="foodList">Choose a result from the USDA food database:</label>
            <br />
            <select name="foodList" id="foodList" form="foodsForm">
                {renderedList}
            </select>
        </form>
    );
};

export default FoodList;
```

