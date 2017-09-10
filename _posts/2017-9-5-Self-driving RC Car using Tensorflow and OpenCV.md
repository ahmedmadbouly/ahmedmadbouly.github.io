---
layout: post
categories: [Artificial Intelligence, OpenCV , Tensorflow]
title: Self-driving RC Car using Tensorflow and OpenCV
---

<p align='center'> <img src = '{{site.baseurl}}/assets/img/car.jpg'/> </p>


If there's one topic that gets a lot of attention lately in the media, the public policy sphere, and in general health and wellness discussions, it is how to make the **<font color="red">roadways safer</font>** According to the **Centers for Disease Control**, fatalities from traffic incidents happen on an annual basis upwards of 33,000 people. Many of these accidents are preventable, and an alarming number of them are a result of distracted driving.
<p align='center'> <img src = '{{site.baseurl}}/assets/img/car01.png'> </p>


## Why Self-Driving Cars?
> <b>Safety</b>

> <b>Convenience</b>

> <b>Efficiency</b>

> <b>Affordability</b>

## * Software Simulation

#### 1 - Finding Lane Lines
<p align='center'> <img src = '{{site.baseurl}}/assets/img/car1.gif'> </p>

[Code](https://github.com/ahmedmadbouly/amd/blob/master/solution1.ipynb)

#### 2 - Advanced Lane Finding
<p align='center'> <img src = '{{site.baseurl}}/assets/img/car2.gif'> </p>

[Code](https://github.com/ahmedmadbouly/amd/blob/master/model.py)

#### 3 - Behavioral Cloning
<p align='center'> <img src = '{{site.baseurl}}/assets/img/car3.gif'> </p>

[Code](https://github.com/ahmedmadbouly/amd/blob/master/load_data.py)

#### 4 - Vehicle Detection
<p align='center'> <img src = '{{site.baseurl}}/assets/img/car4.gif'> </p>

[Code](https://github.com/ahmedmadbouly/amd/blob/master/solution.ipynb)


# Project

### Step 1: Components We Need

<ul>
	<li>RC Car Chassis</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/1.png'> </p>
	<li>Raspberry Pi 3 Board</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/2.png'> </p>
	<li>Raspberry Pi 3 Case (optional)</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/3.jpg'> </p>
	<li>Heat Sinks x 2</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/4.jpg'> </p>
	<li>Micro SDHC Card</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/5.jpg'> </p>
	<li>L298N Motor Driver</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/6.jpg'> </p>
	<li>Battery Pack</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/7.jpg'> </p>
	<li>Jumper Wires x 16</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/8.jpg'> </p>
	<li>HDMI Cable (optional)</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/9.jpeg'> </p>
	<li>HDMI Monitor (optional)</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/10.jpg'> </p>
	<li>Resistors</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/11.png'> </p>
	<li>Pi Camera Module</li>
	<p align='center'> <img src = '{{site.baseurl}}/assets/img/component/12.jpg'> </p>
</ul>

### Step 2: Connecting

<p align='center'> <img src = '{{site.baseurl}}/assets/img/connecting/1.jpg ' width="600" height="600"> </p>
<p align='center' > <img src = '{{site.baseurl}}/assets/img/connecting/2.jpg' width="600" height="600"> </p>
<p align='center'> <img src = '{{site.baseurl}}/assets/img/connecting/3.jpg'> </p>
<p align='center'> <img src = '{{site.baseurl}}/assets/img/connecting/4.jpg'> </p>
<p align='center'> <img src = '{{site.baseurl}}/assets/img/connecting/5.jpg'> </p>
<p align='center'> <img src = '{{site.baseurl}}/assets/img/connecting/6.JPG ' width="600" height="600"> </p>
<p align='center'> <img src = '{{site.baseurl}}/assets/img/connecting/7.JPG ' width="600" height="600"> </p>
<p align='center'> <img src = '{{site.baseurl}}/assets/img/connecting/8.JPG ' width="600" height="600"> </p>
<p align='center'> <img src = '{{site.baseurl}}/assets/img/connecting/9.JPG ' width="600" height="600"> </p>

### Step 3: Wiring Pi and Components
<p align='center'> <img src = '{{site.baseurl}}/assets/img/wiring.jpg'> </p>


### Step 4: Software Required
<ul>
	<li>Raspbian Wheezy (This is the Linux OS flavor)</li>
	<li>TensorFlow</li>
	<li>OpenCV</li>
	<li>RPi.GPIO (control GPIO)</li>
	<li>Remot3.it (For controlling the device from anywhere) </li>
	<li>Socket.io</li>
	<li>Express.js (nodejs For developing web apps)</li>
</ul>

### Step 5: Installing dependencies from PiP

#### install opencv

> sudo add-apt-repository ppa:orangain/opencv

> sudo apt-get update

> sudo apt-get install python-opencv

#### install tensorflow

> sudo apt-get update

> sudo apt-get install python-pip python-dev

> wget https://github.com/samjabrahams/tensorflow-on-raspberry-pi/releases/download/v0.12.1/tensorflow-0.12.1-cp27-none-linux_armv7l.whl

> sudo pip install tensorflow-0.12.1-cp27-none-linux_armv7l.whl

> sudo pip install mock

> sudo pip2 install tensorflow-0.12.1-cp27-none-linux_armv7l.whl

#### install the python RPi.GPIO library

> sudo apt-get install python-rpi.gpio

#### instal nodejs

> sudo apt-get install nodejs

> sudo apt-get install npm

#### install socket.io

> npm install socket.io express johnny-five

#### install remot3.it

> sudo apt-get install weavedconnectd


```javascript

var args = process.argv.slice(2);
var express = require('express');
var app = express();
var http = require('http').Server(app);
var io = require('socket.io')(http);
var bodyParser = require('body-parser');

app.use(bodyParser.json());       


if (args.indexOf("noArduino") == -1) {
  var five = require("johnny-five")
    , board, servo;
  
  var arduinoServos = {};
  var throttleTimeout;
  var accelerationServo = {
    pin: 9,
    range: [0, 180], 
    type: "standard",   
    startAt: 90,          
    center: false
  };
  var steeringServo = {
    pin: 10, 
    range: [40, 100], 
    type: "standard", 
    startAt: 75, 
    center: true, 
  };
}


stringValues = {
  //throttle
  'forward': 65,
  'reverse': 105,
  'stop': 90,
  'throttleTime': 500,
  //steering
  'left': 40,
  'right': 100,
  'neutral': 75,
};

serverStatus = {
  hasArduino: false,
  hasCamera: false,
  currentAI: 'none',
};

// Start server
http.listen(80, function(){
  console.log('Starting server, listening on *:80');
});

app.use(express.static(__dirname + '/public'));

app.get('/', function (req, res) {
  res.sendfile(__dirname + '/index.html');
});

// allow commands to be send via http call - GET only accepts command
app.get('/command/', function (req, res) {
  processRobotCommand (req.query.command);
  res.send('command: ' + req.query.command);
  
  // Eventually replace with json so commands can be sent back
  res.json({ 'state': serverStatus.currentAI });
});
// POST can look for timestamp(ms), command, and status
app.post('/command/', function (req, res) {
  processRobotCommand (req.body.command);
  
  updateRobotStatus (req.body.status);
});

io.on('connection', function (socket) {
  console.log('A user has connected ');
  socket.emit('robot status', { data: 'server connected' });
  
  // Robot commands
  socket.on('robot command', function (data) {
    processRobotCommand (data.data);
  });
  
  // Status update - gets forwarded to the webpage
  socket.on('robot update', function (data) {
    var updatedData = data.data;
    updateRobotStatus (updatedData);
  });
});

// Interprets and acts on a given command (expects strings split by "-")
function processRobotCommand (command) {
  var parsedCommand = command.split("-");
  console.log('----- Command: -----');
  console.log(parsedCommand);
  
  if (serverStatus.hasArduino) {
    // commands to johnny five
    // A bit convoluted here: commands are split between '-', with an arbitrary order for each section
    if (parsedCommand[0] == 'manual') {
      if (parsedCommand[1] == 'throttle') {
        if (parsedCommand.length < 4) {
          parsedCommand[3] = stringValues['throttleTime'];
        }
        if (parsedCommand[2] in stringValues) {
          accelChange(stringValues[parsedCommand[2]], parsedCommand[3]);
        }
        else {
          accelChange(parseInt(parsedCommand[2]), parsedCommand[3]);
        }
      }
      else if (parsedCommand[1] == 'turn') {
        if (parsedCommand[2] in stringValues) {
          steerChange(stringValues[parsedCommand[2]]);
        }
        else {
          steerChange(parseInt(parsedCommand[2]));
        }
      }
    }
    // AI commands - to be forwarded to opencv
    else if (parsedCommand[0] == 'face') {
      console.log('facing');
      if (parsedCommand[1] == 'begin') {
        serverStatus.currentAI = 'face';
      }
      else {
        serverStatus.currentAI = 'none';
      }
    }
    else if (parsedCommand[0] == 'red') {
      if (parsedCommand[1] == 'begin') {
        serverStatus.currentAI = 'red';
      }
      else {
        serverStatus.currentAI = 'none';
      }
    }
    else {    // parsedCommand[0] = 'stop'
      steerChange(stringValues['neutral']);
      accelChange(stringValues['stop']);
    }
  }
}

// Broadcasts an update to the robot status
function updateRobotStatus (updatedData) {
  updatedData['Time'] = new Date();
  updatedData['Arduino Attached'] = serverStatus.hasArduino;
  
  socket.broadcast.emit('robot status', { 'data': updatedData });
}

// ----- Johnny Five -----
// These should only be called or accessed if "noArduino" is not an option

function steerChange (value) {
  arduinoServos.steering.to(value);
  
  board.repl.inject({
    s: arduinoServos
  });
}

function accelChange (value, accelFor) {
  // Throttle has an automatic timeout so car doesn't run into things
  if (accelFor) {
    if (throttleTimeout) {
      clearTimeout(throttleTimeout);
    }
    throttleTimeout = setTimeout(function(){accelChange(stringValues['stop'])}, accelFor);
  }
  
  arduinoServos.acceleration.to(value);
  
  board.repl.inject({
    s: arduinoServos
  });
}

if (args.indexOf("noArduino") == -1) {
  board = new five.Board();

  board.on("ready", function() {
    arduinoServos = {
      acceleration: new five.Servo(accelerationServo),
      steering: new five.Servo(steeringServo)
    };
    acceleration = arduinoServos.acceleration;
    steering = arduinoServos.steering;
   
    // Inject the `servo` hardware into
    // the Repl instance's context;
    // allows direct command line access
    board.repl.inject({
      s: arduinoServos
    });
    
    serverStatus.hasArduino = true;
  });
}

```

whole project is on [this Github repo](https://github.com/ahmedmadbouly/amd)



#### Thanks for reading !
