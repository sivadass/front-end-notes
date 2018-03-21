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
