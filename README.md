# react-reflux

some experiments

## Lab

### Simple counter

http://jsbin.com/yicetu/edit?html,js,output

```javascript
var number = 1;

var actions = Reflux.createActions([
    "updateNumber"
  ]);
  
var store = Reflux.createStore({
  listenables: [actions],
  
  onUpdateNumber: function() {
    number = number + 1;
    this.trigger({
      n: number
    })
  },
  
  getInitialState: function() {
    return {
      n: number
    }
  }

});

var App = React.createClass({
  mixins: [Reflux.connect(store)],
  render: function() {
    return <button onClick={actions.updateNumber}>{this.state.n}</button>
  }
})

React.render(<App/>, document.body);
```
