# react-checkbox-list
A bootstrap-style react component for checkbox list

This is just a simple react component that takes a meta data, translates it into a checkbox list and notifies change.
That's all it does.

Listen for changes, get the new value as intuitively as possible:

```html
<CheckboxGroup name="fruit" value={['apple','watermelon']} ref="fruitsGroup" onChange={this.handleChange}>
// further...

this.refs.fruitsGroup.getCheckedValues(); // => whatever's currently checked
```

That's it for the API! See below for a complete example.

## Install

```sh
bower install react-checkbox-group
or
npm install react-checkbox-group
```

Simply require it to use it:

```javascript
var CheckboxGroup = require('react-checkbox-group');
```

## Example

```html
/**
* @jsx React.DOM
*/
var Demo = React.createClass({
  getInitialState: function() {
    return {value: ['apple','watermelon']};
  },

  componentDidMount: function() {
    // Add orange and remove watermelon after 1 second
    setTimeout(function() {
      this.setState({value: ['apple','orange']});
    }.bind(this), 1000);
  },

  render: function() {
    // the checkboxes can be arbitrarily deep. They will always be fetched and
    // attached the `name` attribute correctly. `value` is optional
    return (
      <CheckboxGroup
        name="fruits"
        value={this.state.value}
        ref="fruitsGroup"
        onChange={this.handleChange}
      >
        <div>
          <label>
            <input type="checkbox" value="apple"/>Apple
          </label>
          <label>
            <input type="checkbox" value="orange"/>Orange
          </label>
          <label>
            <input type="checkbox" value="watermelon"/>Watermelon
          </label>
        </div>
      </CheckboxGroup>
    );
  },

  handleChange: function() {
    // will return the currently selected checkbox values as an array, possibly empty
    var selectedFruits = this.refs.fruitsGroup.getCheckedValues();
  }
});

React.renderComponent(<Demo/>, document.body);
```

## License

MIT.
