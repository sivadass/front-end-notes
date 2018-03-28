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
```
let users = [
  {id: 0, name: "John", age: 25},
  {id: 1, name: "Stephen", age: 21},
  {id: 2, name: "Robin", age: 32}
];
let elder = users.filter((user) => {
  return user.age == 32;
});
console.log(elder); //[{id: 2, name: "Robin", age: 32}]
```

### Find index of array item
```
let users = [
  {id: 0, name: "John", age: 25},
  {id: 1, name: "Stephen", age: 21},
  {id: 2, name: "Robin", age: 32}
];
let key = 0; // Let's find an object which has 0 as id
let index = users.findIndex((user => user.id == key));
console.log(index); //0
```

### Convert boolean and number type Key value to string type
```
let users = [
  {name: "John", age: 25, adult: true},
  {name: "Stephen", age: 17, adult: false},
  {name: "Robin", age: 32, adult: true}
];

let usersString = JSON.stringify(users, replacer);

function replacer(key, value) {
  if (typeof value === "boolean" || typeof value === "number") {
    return String(value);
  }
  return value;
}

console.log(usersString);
// [{"name":"John","age":"25","adult":"true"},{"name":"Stephen","age":"17","adult":"false"},{"name":"Robin","age":"32","adult":"true"}]
```
