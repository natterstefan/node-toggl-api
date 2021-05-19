# @natterstefan/toggl-api

[Toggl track](https://track.toggl.com/) API for Node.js. Library is based on official Toggl API [documentation](https://github.com/toggl/toggl_api_docs).

## Attention

This is a fork from the [original repository](https://github.com/7eggs/node-toggl-api),
that is not maintained anymore. Toggl is updating the API domain, that is why I
had to fork it and publish it with with a new name - for now. That is because
some of my projects depend on this package. I do not plan to update this project
any further at the moment.

## Installation

    npm install @natterstefan/toggl-api --save

## How to use

```js
var TogglClient = require('@natterstefan/toggl-api');
var toggl = new TogglClient({apiToken: '1971800d4d82861d8f2c1651fea4d212'});

toggl.startTimeEntry({
  description: 'Some cool work',
  billable:    true
}, function(err, timeEntry) {
  // handle error

  // working 10 seconds
  setTimeout(function() {
    toggl.stopTimeEntry(timeEntry.id, function(err) {
      // handle error

      toggl.updateTimeEntry(timeEntry.id, {tags: ['finished']}, function(err) {
        toggl.destroy()
      });
    });
  }, 120000);
});
```

## Documentation

Documentation is available at: [http://7eggs.github.io/node-toggl-api/](http://7eggs.github.io/node-toggl-api/)

## TODO

* TESTS
* Documentation in Markdown format
* Remove custom data validator
