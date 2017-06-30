# Project: Mimic Me!


## Overview

In this project, Affectiva will be used to track faces from the camara input and identify facial expressions. These expressions will be tagged with an appropiate emoji next to it. Additionally, a game is implemented in which the player needs to mimic a random emoji displayed on the screen.

## Getting Started

We’ll be using [Affectiva](http://www.affectiva.com/)’s Emotion-as-a-Service API for this project. Visit their [Developer Portal](http://developer.affectiva.com/) and try out some of the sample apps. Affectiva makes it really easy to extract detailed information about faces in an image or video stream. To see what information can be obtainned, check out the [Metrics](http://developer.affectiva.com/metrics/) page.

### Project files

The main files of the project are:

- **mimic.js**: Javascript file with code that connects to the Affectiva API and processes results.
- **index.html**: Dynamic webpage that displays the video feed and results.
- **mimic.css**: Stylesheet file that defines the layout and presentation for HTML elements.
- **serve.py**: A lightweight Python webserver required to serve the webpage over HTTPS, so that we can access the webcam feed.
- **generate-pemfile.sh**: A shell script you’ll need to run once to generate an SSL certificate for the webserver.

### Serving locally over HTTPS

In order to access the webcam stream, modern browsers require you to serve your web app over HTTPS. To run locally, you will need to general an SSL certificate (this is a one-time step):

- Open a terminal or command-prompt, and ensure you are inside the `Mimic-Me/` directory.
- Run the following shell script: `generate-pemfile.sh`

This creates an SSL certificate file named `my-ssl-cert.pem` that is used to serve over https.

Now you can launch the server using:

```
python serve.py
```

_Note: The `serve.py` script uses Python 3._

Alternately, you can put your HTML, JS and CSS files on an online platform (such as [JSFiddle](https://jsfiddle.net/)) and develop your project there.

### Running and implementing the game

Open a web browser and go to: [https://localhost:4443/](https://localhost:4443/)

- Hit the Start button to initiate face tracking. You may have to give permission for the app to access your webcam.
- Hit the Stop button to stop tracking and Reset to reset the detector (in case it becomes stuck or unstable).
_Note: Your browser may notify you that your connection is not secure - that is because the SSL certificate you just created is not signed by an SSL Certificate Authority‎. This is okay, because we are using it only as a workaround to access the webcam. You can suppress the warning or choose "Proceed Anyway" to open the page._


## Tasks

The code sends frames from the webcam to Affectiva’s cloud-based API and fetches the results. Several metrics are being reported, including emotions, expressions and the dominant emoji.

### 1. Display Feature Points

A set of feature points are being tracked constantly with Affectiva's API. These feature points are simple JavaScript objects that store the (x, y) coordinates. `face.featurePoints` is a list of the many points in the face. Simple white points are being drawn on top of these points.


### 2. Show Dominant Emoji

In addition to feature points and metrics that capture facial expressions and emotions, the Affectiva API also reports back what emoji best represents the current emotional state of a face. This is referred to as the _dominant emoji_.

In mimic.js, the `drawEmoji()` function displays this emoji on top of the webcam feed, tracking the user's face:


### 3. Implement Mimic Me!

Finally, the game Mimic Me is implemented. All the emojis are translated to a unicode value with the `toUnicode` function.


## Affectiva Resources

References:

- [Affectiva Developer portal](http://developer.affectiva.com/index.html)
- [Demo](https://jsfiddle.net/affectiva/opyh5e8d/show/) that this project is based on
- Tutorials:
 [Camera stream](https://affectiva.readme.io/docs/analyze-the-camera-stream-3), [video](https://affectiva.readme.io/docs/analyze-a-video-frame-stream-4), [photo](https://affectiva.readme.io/docs/analyze-a-photo-3)


<a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-nd/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a>. Please refer to [Udacity Terms of Service](https://www.udacity.com/legal) for further information.
