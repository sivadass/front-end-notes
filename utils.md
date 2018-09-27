# Utitlity Functions

### Random Color Generator

```
function getRandomColor() {
  let letters = '0123456789ABCDEF'
  let color = '#'
  for (let i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)]
  }
  return color;
}
```

### Format Number to Indian Number System
```
let price = 987450000;

let formattedPrice = price.toLocaleString("en-IN", {
    maximumFractionDigits: 3,
    style: 'currency',
    currency: 'INR'
});

console.log(formattedPrice); // ₹ 98,74,50,000.00
```

### Axios Wrapper

```
import axios from "axios";
import { loadState } from "./localStorage";

class Service {
  constructor() {
    let service = axios.create({
      headers: {
        Authorization: "BEARER some token"
      }
    });
    service.interceptors.response.use(this.handleSuccess, this.handleError);
    this.service = service;
  }

  handleSuccess(response) {
    return response;
  }

  handleError = error => {
    switch (error.response.status) {
      case 401:
        this.redirectTo(document, "/");
        break;
      case 404:
        this.redirectTo(document, "/404");
        break;
      default:
        this.redirectTo(document, "/500");
        break;
    }
    return Promise.reject(error);
  };

  redirectTo = (document, path) => {
    document.location = path;
  };

  get(path, callback) {
    return this.service
      .get(path)
      .then(response => callback(response.status, response.data));
  }

  patch(path, payload, callback) {
    return this.service
      .request({
        method: "PATCH",
        url: path,
        responseType: "json",
        data: payload
      })
      .then(response => callback(response.status, response.data));
  }

  post(path, payload, callback) {
    return this.service
      .request({
        method: "POST",
        url: path,
        responseType: "json",
        data: payload
      })
      .then(response => callback(response.status, response.data));
  }
}

export default new Service();
```
