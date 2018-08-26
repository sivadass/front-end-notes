### Connecting the Provider
```
import React from "react";
import ReactDOM from "react-dom";
import { BrowserRouter as Router, Route, Switch } from "react-router-dom";
import { createStore, applyMiddleware } from "redux";
import { Provider } from "react-redux";
import thunk from "redux-thunk";
import { createLogger } from "redux-logger";

import reducer from "./reducers";
import { loadState, saveState } from "./utils/local-storage";

const middleware = [thunk];
if (process.env.NODE_ENV !== "production") {
  middleware.push(createLogger());
}

const persistedState = loadState();
const store = createStore(
  reducer,
  persistedState,
  applyMiddleware(...middleware)
);

store.subscribe(() => {
  saveState(store.getState());
});

const App = props => {
  return(
    <Provider store={store}>
      <Router>
        <div className="container">
          <Header />
          <Switch>
            <Route exact path="/" component={Home} />
            <Route path="/products" component={Products} />
          </Switch>
          <Footer />
        </div>
      </Router>
    </Provider>
  )
}

ReactDOM.render(<App />, document.getElementById("root"));
```

### Create Actions
```
export const DO_SOME_ACTION = "DO_SOME_ACTION";

export const doSomeAction = data => ({
  type: DO_SOME_ACTION,
  payload: data
});
```

### Create Reducers
```
import { combineReducers } from "redux";
import { DO_SOME_ACTION } from "../actions";

const initialState = {
  isLoggedIn: false
};

const someUserData = (state = initialState, action) => {
  if (action.type === DO_SOME_ACTION) {
    return Object.assign({}, state, {
      isLoggedIn: action.payload
    });
  }
  return state;
};

const rootReducer = combineReducers({
  someUserData
});

export default rootReducer;
```

### Connecting the component
```
import { connect } from "react-redux";
import { withRouter } from "react-router-dom";
import { bindActionCreators } from "redux";
import PropTypes from "prop-types";
import { someAction } from "../actions/"; // Import actions here

class MyComponent extends React.Component{
...
}

const mapStateToProps = ({ someUserData }) => ({
  someUserData
});

function mapDispatchToProps(dispatch) {
  return bindActionCreators({ someAction }, dispatch);
}

BudgetStep.ProtoTypes = {
  someUserData: PropTypes.object,
  someAction: PropTypes.func
};

export default withRouter(
  connect(
    mapStateToProps,
    mapDispatchToProps
  )(MyComponent)
);
```
