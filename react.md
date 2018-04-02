# React JS

### Printing State or Props inside component itself

```
<pre>{JSON.stringify(this.state.todos, null, 2)}</pre>
```

### Updating nested state object in React using ID

```
...
constructor(){
  super(props);
  this.state = {
    tasks: [
      {
        id: 1,
        name: "Buy Milk",
        isCompleted: true
      },
      {
        id: 2,
        name: "Take Jimmy to walk",
        isCompleted: false
      }
    ]
  }
}
...
this.setState(prevState => {
   const updatedTasks = prevState.tasks.map(task => {
      return (task.id === 1 ? Object.assign({}, task, {isCompleted: !task.isCompleted}) : task)
   })
   return {tasks: updatedTasks}
})
```

### Bind methods in React Components

```
// 1.Bind in constructor
class A extends React.Component {
  constructor(props) {
    super(props)
    this._eventHandler = this._eventHandler.bind(this)
  }

  _eventHandler() {
    // ...
  }

  render() {
    return <div onClick={this._eventHandler} />
  }
}

// 2.Arrow function in render()
class A extends React.Component {
  _eventHandler() {
    // ...
  }

  render() {
    return <div onClick={()=>{this._eventHandler()}} />
  }
}

// 3. bind in render()
class A extends React.Component {
  _eventHandler() {
    // ...
  }

  render() {
    return <div onClick={this._eventHandler.bind(this)} />
  }
}

// 4. ES2015 arrow function in class fields
class A extends React.Component {
  _eventHandler = () => {
    // ...
  }

  render() {
    return <div onClick={this._eventHandler} />
  }
}

// 5. @autobind decorator
class A extends React.Component {
  @autobind
  _eventHandler() {
    // ...
  }

  render() {
    return <div onClick={this._eventHandler} />
  }
}
```
