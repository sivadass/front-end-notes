# Arrays and Objects

### Convert array of objects into array of properties
```
let users = [
  {id: 0, name: "John", age: 25},
  {id: 1, name: "Stephen", age: 21},
  {id: 2, name: "Robin", age: 32}
];
let userIDs = users.map((user) => {
  return user.id;
});
console.log(userIDs); //[0, 1, 2];
```

### Filter array of objects by key value
