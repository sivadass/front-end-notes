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

### Renaming Object Keys in Arrays

```
let users = [
  {name: "John Doe", mail: "john@acme.com"},
  {name: "Stephen King", mail: "stephen@aol.com"},
  {name: "Robin Sharma", mail: "robin@redux.com"}
];
const keysToRename = { name: 'fullname', mail: 'email' };
const renamer = item => Object.assign(...Object.keys(item).map(k => ({ [keysToRename[k] || k]: item[k] })));
let renamedUsersArray = users.map(renamer);

console.log(renamedUsersArray);
// Output
[
  {fullname: "John Doe", email: "john@acme.com"},
  {fullname: "Stephen King", email: "stephen@aol.com"},
  {fullname: "Robin Sharma", email: "robin@redux.com"}
]
```

### Search and Filter
```
let users = [
  {name: "John Doe", mail: "john@acme.com"},
  {name: "Stephen King", mail: "stephen@aol.com"},
  {name: "Robin Sharma", mail: "robin@redux.com"}
];

let searchTerm = "Ro"
let filteredUsers = users.filter(user => {
  return user.name.indexOf(searchTerm) !== -1;
});

consile.log(filteredUsers);
// Result
[
  {name: "Robin Sharma", mail: "robin@redux.com"}
]
```

### Check whether an Object is Empty
```
let obj = {};
console.log(Object.keys(obj).length); 
//returns 0 if empty or an integer > 0 if non-empty
```

### Filter an array of objects by an array of integers
```
let users = [
  {id: 0, name: "John", age: 25},
  {id: 1, name: "Stephen", age: 21},
  {id: 2, name: "Robin", age: 32},
  {id: 3, name: "Robin", age: 45},
  {id: 4, name: "Robin", age: 80}
];

let userIDsToExclude = [1,4];

let result = users.filter(item => !userIDsToExclude.includes(item.id))

console.log(result);

// Result
[
  {id: 0, name: "John", age: 25},
  {id: 2, name: "Robin", age: 32},
  {id: 3, name: "Robin", age: 45}
]
```
