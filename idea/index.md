## component
```javascript
dispatch('HOGE', {});
```

## router

```javascript
import {router} from 'euphonium';

router('HOGE', (req) => {
  return {
    test: req.test
  // want to send data
  };
});

// ?
router.pass([
  'HOGE',
  'FUGA'
]);

router('HOGE', (req) => req);
router('FUGA', (req) => req);
router('*', (req) => req);

// redux
export function Action(name) {
  return {
    message: 'HOGE',
    name
  }
}
```

## story
```javascript
import {story} from 'euphonium';

const initailState = {
  userInfo: {
    userId: '0',
    name: 'test'  
  }
};

// initailState is accessed by only this component
story.initState(initailState);

// for logger, etc...
story.beforeAll((req) => {
  return req;
});

story.before('HOGE', (req) => {
  return req;
});

// otherwise
story('*', (req) => {
   // business logic
  return {};
});

story('HOGE', (req) => {
   // business logic
  return {};
});

story.didposeAll((prevState, nowState) => {
  this.send(); // dispatch
  this.done(); // next

  return {};
});

story.dispose(['HOGE', 'AAA'], (prevState, nowState) => {
  return {};
});
```

## effect
```javascript
// think later...

```

## store
```javascript
// singleton
```

## flow
```
view ->
  router ->
    story.beforeAll ->
    story.before ->
    story ->
    story.disposeAll ->
    story.dispose ->
view
```
