*This repository is a mirror of the [component](http://component.io) module [yyx990803/workerify](http://github.com/yyx990803/workerify). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/yyx990803-workerify`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
# Workerify

Turn the body of a function into a web worker.

## Usage

``` js
var workerify = require('workerify')

var worker = workerify(function () {
	// think of here as if you are writing in a
	// separate file: you do not have access to
	// anything outside this function's scope.
    self.onmessage = function (e) {
        self.postMessage('pong')
    }
})

worker.onmessage = function (e) {
    console.log(e.data)
}

worker.postMessage('ping') // pong
```