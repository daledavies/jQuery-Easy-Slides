jQuery Easy Slides v1.1
=======================

Possibly the easiest to use jQuery plugin for making slideshows!

Demo:  http://dev.daledavies.co.uk/easyslides


Purpose
-------

Although there are plenty of features to make this more than just a basic slideshow plugin, the list of features (and options) are not extensive. With jQuery Easy Slides I wanted to make a simple slideshow plugin that is quick and easy to use.

jQuery Easy Slides also has the advantage of being fairly light weight, with both Javascript and CSS weighing in at just under 2.1kb.

Usage
-----

###Preparing Your Images

Before we delve into Javascript and CSS, the first thing you should do is gather and prepare the images for your slideshow. The images you use should be in JPEG format (with .jpg file extension), they should all have the same dimensions and should be named using a number starting from 1.

So for example, if you want a slideshow with 3 images, you should name your files 1.jpg, 2.jpg, 3.jpg.

Then save all your images in the same folder, the relative path to this folder can be supplied to Easy Slides when initiating it using jQuery (see below).
Which Files Do I Need to Use?

To use this plugin you must first include the latest jQuery library on your page, followed by Easy Slides' "jquery.easyslides.min.v1.1.js" file and then Easy Slides' "easySlides.default.min.css" file, also there is a 1px-by-1px PNG image which must be present for captions to have a semi-transparent background colour.

The files required by Easy Slides can be found in the "js", "css" and "img" folders in the Easy Slides archive, copy these 3 folders (or the files contained within) to your workspace. After this we can link to the files from your web page.
Preparing Your HTML & CSS

Include the jQuery library, the Easy Slides JS and CSS files in your web page using something like the following, change any paths to match your own directory structure...

	<script type="text/Javascript" src="js/jquery-1.4.min.js"></script>
	<script type="text/Javascript" src="js/jquery.easyslides.min.v1.1.js"></script>
	<link rel="stylesheet" type="text/css" href="css/easySlides.default.min.css" />

You can then follow this with your own style sheet if you wish to over-ride any of the Easy Slides' default CSS styles.

Next, add one empty DIV element to your html page. Easy Slides will use this to hold your slideshow once it has been initiated.

You should position this DIV container wherever you would like the slideshow to appear on your web page. The container DIV should be given a class of "easy_slides_container", but you can give it any ID you like, so you can easily target it with your own CSS and jQuery.

In the example slideshow at the top of this page (Example 1), I have used the following markup for the container DIV...

	<div id="example_1_container" class="easy_slides_container"></div>

Now it's time to define some CSS styles in your own stylesheet, we'll use these to override the default css provided with the plugin. I recommend at least overriding the follwing to tailor the appearence of your slideshow to the dimensions of images, also you may also wish to set the size and appearence of the captions box...

	#slideshow_container {
		width: WIDTH OF YOUR IMAGES;
		height: HEIGHT OF YOUR IMAGES
	}

	#caption {
		width: WIDTH SET ABOVE;
		height: PREFERRED HEIGHT OF CAPTIONS;
		padding: PREFERRED PADDING;
		color: PREFERRED COLOR;
		font-family: PREFERRED FONT;
		font-size: PREFERRED FONT SIZE
	}
	
Setting Up Easy Slides In jQuery
--------------------------------

In order to get Easy Slides to work it must be initiated using jQuery. You can run Easy Slides with only the basic options using just one line of jQuery, however some of the default options might not suit your requirements.

By default Easy Slides assumes...

    You only have two images (these will be located in the same folder as the web page).
    You have no captions.
    The images do not link anywhere.
    The slideshow will always start on image number 1.
    The transition between images will happen every 6 seconds.

There are a few arguments that can be supplied to Easy Slides, in order to demonstrate the options that are available I have listed them all below, however you can omit any of these if you feel the defaults will suffice.

To initiate the Easy Slides plugin add a block of Javascript like the following into your main JS file (the code below is used in Example 1)...

	// Set up our options for the slideshow...
	var myOptions = {
		noImages: 6, // Number of images
		path: "slideshow_images/", // Relative path with trailing slash.
		captions: { // HTML can be included in the captions.
			1: 'Caption 1',
			2: 'Caption 2',
			3: 'Caption 3',
			4: 'Caption 4',
			5: 'Caption 5',
			6: 'Caption 6'
		},
		links: { // Should the images link anywhere? if no links are required at all then this option can be omitted.
			1:"http://www.google.com",
			2:"http://www.yahoo.com",
			3:"",
			4:"http://www.jquery.com",
			5:"http://www.youtube.com",
			6:""
		},
		linksOpen:'newWindow', // How to open links? sameWindow or newWindow.
		timerInterval: 6500, // 6500 = 6.5 seconds
		randomise: false // Start with random image? true=yes/false=no
	};

	// Initiate the Easy Slides plugin, assigning it to your contaner DIV...
	$('#slideshow_container').easySlides(myOptions);

Examples
--------

###Example No. 1

The first example of Easy Slides in action can be seen at the top of the demo page, to get this to work I used a block of Javascript almost identical to the one shown above (apart from to change the captions). After after unzipping the Easy Slides archive you can find this example in the "Examples/Example 1/" folder.

The following is the css required to create Example 1...

	#example_1_container {
		width:684px;
		height:456px;
	}

	#example_1_container .easy_slides_caption {
		width:674px;
		height:50px;
		padding: 10px 0 0 10px;
	}

###Example No. 2

Small Images, random starting image, no captions, single link. Example 2 illustrates a slightly different usage of Easy Slides. Also this shows that more than one instance of Easy Slides can be run on any page. This example can be found in the "Examples/Example 2/" folder...

The jQuery and options used to create Example 2 can be seen below...

	var myOptions = {
		noImages: 4,
		path: "Examples/Example 2/slideshow_images/",
		links: {
			1:"http://www.jquery.com",
			2:"http://www.jquery.com",
			3:"http://www.jquery.com",
			4:"http://www.jquery.com"
		},
		timerInterval: 2500,
		randomise: true
	};

	// Woo! We have example number 2!
	$('#example_2_container').easySlides(myOptions);

The following css was used to style Example 2...

	#example_2_container {
		width:150px;
		height:103px;
	} 