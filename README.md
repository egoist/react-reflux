# react-reflux

Just some stupid experiments, with flux your components become extremely simple and readable, less logic related stuffs there. You handle everything in the store, what the component has to do is telling the store what to do, that's it.

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

### Ajax data

What I have to note is that you are supposed to make ajax outside `store`. Details coming soon.

![ajax data](http://i.stack.imgur.com/DodsD.png)
