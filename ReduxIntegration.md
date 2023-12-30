 # Redux Basic Cheatsheet
## Installation
To install Redux in your React project, run the following command:
npm install redux react-redux
## Setting up the Store
1. Import createStore from Redux:
   
```javascript
   import { createStore } from 'redux';
 ```  
2. Create a reducer function that will handle state changes:
   
```javascript
   const reducer = (state = initialState, action) => {
     switch (action.type) {
       case 'ACTION_TYPE':
         return { ...state, property: action.payload };
       default:
         return state;
     }
   };
  ``` 
3. Create the store using the createStore function and pass in the reducer:
   
```javascript
   const store = createStore(reducer);
  ``` 
4. Wrap your app with the Provider component from react-redux and pass in the store:
   
```javascript
   import { Provider } from 'react-redux';

   ReactDOM.render(
     <Provider store={store}>
       <App />
     </Provider>,
     document.getElementById('root')
   );
 ```  
## Connecting Components to the Store
1. Import connect from react-redux:
   
```javascript
   import { connect } from 'react-redux';
```   
2. Define a mapStateToProps function that will map the state to props:
   
```javascript
   const mapStateToProps = (state) => {
     return {
       property: state.property,
     };
   };
 ```  
3. Define a mapDispatchToProps function that will map actions to props:
   
```javascript
   const mapDispatchToProps = (dispatch) => {
     return {
       action: (payload) => dispatch({ type: 'ACTION_TYPE', payload }),
     };
   };
 ```  
4. Connect your component to the store using the connect function and pass in the mapStateToProps and mapDispatchToProps functions:
   
```javascript
   export default connect(mapStateToProps, mapDispatchToProps)(MyComponent);
```   
5. Access the state and actions as props in your component:
   
```javascript
   const MyComponent = ({ property, action }) => {
     return (
       <div>
         <p>{property}</p>
         <button onClick={() => action('new value')}>Update Property</button>
       </div>
     );
   };
```   
## Accessing the Store Directly
If you need to access the store directly, you can import it from your Redux module:
```javascript
import store from './redux/store';
```
console.log(store.getState());
store.dispatch({ type: 'ACTION_TYPE', payload: 'new value' });
