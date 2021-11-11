# log-my-ass

simple nodejs logger

# Get start

```
npm install log-my-ass
```

## Init

```js
const Logger = require('log-my-ass');
const log = new Logger(
  {
    info: {
      console_output: true,
      file_write: true,
      file_path: './path/to/info.log',
    },
    error: {
      console_output: true,
      file_write: true,
      file_path: './path/to/error.log',
    },
    access: {
      console_output: true,
      file_write: true,
      file_path: './path/to/acceess.log',
    },
  },
  'Start'
);

// OR:

// firstly add configuration:
config = {
  info: {
    console_output: true,
    file_write: true,
    file_path: './path/to/info.log',
  },
  error: {
    console_output: true,
    file_write: true,
    file_path: './path/to/error.log',
  },
  access: {
    console_output: true,
    file_write: true,
    file_path: './path/to/acceess.log',
  },
};

// and init
const Logger = require('log-my-ass');
const log = new Logger(config, 'Start');
```

## Usage

```js
// log classified as a "info" log
log.info('Hello world!');

try {
  some.code.with.error();
} catch (err) {
  log.error(err);
  // err it's error string or object
}
// log classified as a "error" log

log.error(err, "it's error message");
// log classified as a "error" and "info" log

// => it's equivalent
log.error(err);
log.info("it's error message");
```

## Log expressjs req and res

Add this in your main `index.js` file

It log classified as a "access" log

```js
app.use((req, res, next) => {
  log.access(req, res);
  next();
});
```

# Log message syntax

Example of output:

```
[04-11-2021 21:20:12] [Start] Message
```

- First scopes `[04-11-2021 21:20:12]` it's date and time in `es-CL` locales
- `[Start]` it's prefix. Declared in logger init
- `Message` it's log text, string or obj of error without `\n` symbols

# Configuration

```json
{
  "info": {
    "console_output": true,
    "file_write": true,
    "file_path": "./path/to/info.log"
  },
  "error": {
    "console_output": true,
    "file_write": true,
    "file_path": "./path/to/error.log"
  },
  "access": {
    "console_output": true,
    "file_write": true,
    "file_path": "./path/to/acceess.log"
  }
}
```
