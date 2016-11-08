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
story.process('*', (req, state) => {
   // business logic
  return {};
});

/**
 * @param {Object} req
 * @param {Object} state - current state
 */
story.process('HOGE', (req, state) => {
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
    story.process ->
    story.disposeAll ->
    story.dispose ->
view
```
