A fork of PHP Google Map API Class 
==================================

The original source: [http://code.google.com/p/php-google-map-api/](http://code.google.com/p/php-google-map-api/). If you don't know what this Class is about, then you are in the wrong place. You should visit [php-google-map-api](http://code.google.com/p/php-google-map-api/) to get up to speed. 

About
-----

On a recent [project](http://culturedays.ca/en/celebration-schedule/by-region/british-columbia/map) we were using the PHP Google Map API Class. Very nice, very helpful. 

In any case, we needed some extra features. So, we added them (to the v3.0 class only!), and here's the code, which will hopefully help others. We will tell the maintainers of this project about these mods in the hope the changes can just be incorporated to the main project, but until then, here it is. 

What was added
--------------

* Locale support: Ability to specify what language of the Google Map API you would like
* Support for setting up your MarkerClusterer cluster icons via the API.
* Compatibility with infoOnClick, which we added to the MarkerClusterer JS Library (You will need our modified code for the MarkerClusterer if you would like to use that feature. See  [http://github.com/plank/MarkerClusterer/](http://github.com/plank/MarkerClusterer/) for more info. )

Usage
-----

Pretty straight-forward. See the original [php-google-map-api](http://code.google.com/p/php-google-map-api/) for all docs, examples and whatnot. 

### re: Language ###


To specify the Language, once you have a Map Object, just do

    //For french
    $MAP_OBJECT->locale = "fr"
    
Before you start outputting any code.

Check [here](http://code.google.com/apis/maps/faq.html#languagesupport) for a full list of locales

### re: MarkerClusterer Icons ###

    $MAP_OBJECT->setClusterImageOptions(array(
        'imagePath' => 'http://www.example.com/my/icons/m',
        'imageExtension' => 'png
    ));

This will lead MarkerClusterer using images like http://www.example.com/my/icons/m1.png, http://www.example.com/my/icons/m2.png and so forth for each of your styles. If you don't use setClusterImageOptions, it will use the defaults setup in your markerclusterer.js

### re: MarkerClusterer - Info On Click ###

Added 2 new parameters to GoogleMapAPI::setClusterOptions()

Info On Click: Whether we show the InfoWindow Content for all the markers in the cluster on click.

    $infoOnClick: defaults to false. If you set this to "true" (yes, use a string - it gets output in JS)

Info On Click Zoom: So, once you zoomed in @ this level or closer, it will overide zoomOnClick and instead display an infowindow with the info from all the markers.

    $infoOnClickZoom: The zoom threshold that infoOnClick will trigger if its turned on. 

Always worth just looking at the code, there's comments for all the changes that have been made. 

m.
