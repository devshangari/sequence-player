sequence-player
===============

Image sequence player

This script is built to work with an array of images. It simply picks the source of one image, 
and replaces it with the one currently being used and its speed depends on the FPS set by the user. 
The rendering loop is controlled using requestAnimationFrame if it is available otherwise it uses timeout. 

It takes the following options for initialization
```javascript

  var options = {
		currentIndex: 0,                    // Start frame for the sequence
		elementSelector: "#playerImage",    // Selector for the html image element
		images: images,                     // Array of image objects
		fps: 24                             // Frame rate for animation
	},
  sequencePlayer = new ImageSequencePlayer(options); // Initialize the sequence player with the above options
  sequencePlayer.start(); // Start playing the animation sequence

```


Using the provided image preloader 

```javascript
  /**
   *  This script assumes the image name is of the following format: img/frames/frame-%4d.png
   *  where `img/frames` is the folder prefix, `frame-` is the name, `%4d` here is a 4-digit numeric value
   *  You can change this to a n-digit by modifying the zeroFill value
   */
  var file = {
      prefix: "img/override",   // folder path to image
      name: "override-",        // Image name prefix
      extension: ".png",        // Image extension
      startIndex: 1,            // Image frame start number - eg frame-0001.png
      endIndex: 15,             // Image frame end number
      zeroFill: 4               // ZeroFill modifier
  },
  options = {
      onComplete: onPreloadComplete, // Callback for preload complete
      onSuccess: onPreloadSuccess,   // Callback for preload success
      onError: onPreloadError,       // Callback for preload error
      file: file                     // Files data object  
  },
  preloader = new Preloader(options);// Initialize the preloader
  preloader.preload();               // Begin preloading the images
```
    
