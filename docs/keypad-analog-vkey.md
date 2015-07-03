<!--remove-start-->

# Keypad - VKEY

<!--remove-end-->






##### Breadboard for "Keypad - VKEY"



![docs/breadboard/keypad-analog-vkey.png](breadboard/keypad-analog-vkey.png)<br>

&nbsp;




Run with:
```bash
node eg/keypad-analog-vkey.js
```


```javascript
var exec = require("child_process").exec;
var argv = require("minimist")(process.argv.slice(2), { default: { show: 1 } });
var five = require("../");
var board = new five.Board();

board.on("ready", function() {
  // Sparkfun's VKey Voltage Keypad
  var keypad;

  if (argv.show === 1) {
    keypad = new five.Keypad({
      controller: "VKEY",
      pin: "A0",
    });
  }

  if (argv.show === 2) {
    keypad = new five.Keypad({
      controller: "VKEY",
      pin: "A0",
      keys: [
        ["!", "@", "#"],
        ["$", "%", "^"],
        ["&", "-", "+"],
        ["<", ">", "?"],
      ]
    });
  }

  if (argv.show === 3) {
    keypad = new five.Keypad({
      controller: "VKEY",
      pin: "A0",
      keys: ["!", "@", "#", "$", "%", "^", "&", "-", "+", "<", ">", "?"]
    });
  }

  ["change", "press", "hold", "release"].forEach(function(eventType) {
    keypad.on(eventType, function(data) {
      console.log("Event: %s, Target: %s", eventType, data.which);
    });
  });
});



```








&nbsp;

<!--remove-start-->

## License
Copyright (c) 2012, 2013, 2014 Rick Waldron <waldron.rick@gmail.com>
Licensed under the MIT license.
Copyright (c) 2014, 2015 The Johnny-Five Contributors
Licensed under the MIT license.

<!--remove-end-->