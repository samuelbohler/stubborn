## Stubborn

### Install
```sh
npm install stubborn
```

### Example
```js
var Stubborn = require('stubborn');

var options = {
  maxAttempts: 5,
  delay: 1000
};

var stubborn = new Stubborn(task, options, callback);

stubborn.on('attemptError', onAttemptError);

stubborn.run();

function task(callback) {
  if (Math.random() > 0.2) {
    callback('Task error');
  } else {
    callback(null, 'Task result');
  }
}

function callback(err, result) {
  if (err) {
    console.error(err);
    return;
  }
  console.log(result);
}

function onAttemptError(err) {
  console.error(err);
}

```

## Methods
 * ```run``` starts specified task, call it only once
 * ```cancel``` stops retries

## Events
 * ```run```
 * ```onAttemptError```
 * ```schedule```
