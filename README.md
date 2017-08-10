## Deploy Facebooks' React VR `TourSample` to Heroku in 5 minutes or less

Step by step instructions for deploying [react-vr/tree/master/Examples/TourSample](https://github.com/facebook/react-vr/tree/master/Examples/TourSample) to Heroku.

## Demo
[https://serene-retreat-76943.herokuapp.com/index.html](https://serene-retreat-76943.herokuapp.com/index.html)

## Shout-outs to:
1) [Facebook](https://github.com/facebook) for their VR framework [React VR](https://github.com/facebook/react-vr).

2) [zivile777](https://github.com/zivile777) for her example use of [React VR](https://github.com/facebook/react-vr) with [react-vr-paris-tour](https://github.com/zivile777/react-vr-paris-tour).

3) [ltfschoen](https://github.com/ltfschoen) for his example use of [React VR](https://github.com/facebook/react-vr) with [PolkadotConsensusVR](https://github.com/ltfschoen/PolkadotConsensusVR).


## The following steps require:
    * Node.js version 6.0.0 or higher
    * npm (>= v3.0.0) package manager

## Condensed Steps

1) In the terminal, from your working directory(example: ~/projects), copy/paste these commands, hit Enter:
```
npm install -g react-vr-cli \
&& git clone https://github.com/facebook/react-vr.git \
&& cd react-vr/Examples \
&& react-vr init TourSampleTest \
&& cd TourSampleTest \
&& rm -rf static_assets \
&& cp -r ../TourSample/static_assets static_assets \
&& cp ../TourSample/{InfoButton.js,LoadingSpinner.js,NavButton.js,Tooltip.js,index.vr.js} . \
&& sed -i '' 's/TourSample/TourSampleTest/g' index.vr.js \
&& npm run bundle \
&& cp -r ./static_assets vr/build/static_assets \
&& cp vr/index.html vr/build
```

2) Modify vr/build/index.html (NOT vr/index.html)
  * Replace `'<script src="./build/client.bundle?platform=vr"></script>'` with `'<script src="./client.bundle.js?platform=vr"></script>'`
  * Replace `'./build/index.bundle?platform=vr&dev=false',` with `'./index.bundle.js?platform=vr',`
  * Modify `document.body` with the following for all static assets:
    ```
    document.body,
    {}, 
    ['./static_assets/Three-Cocktails.jpg', 
     './static_assets/Three-Cocktails.webm', 
     './static_assets/beer-cheers.jpg', 
     './static_assets/cafe.wav', 
     './static_assets/chalkboard-menu.jpg', 
     './static_assets/chester_icon.png', 
     './static_assets/circle_ramp.png', 
     './static_assets/info_icon.png',
     
     './static_assets/License.html', 
     './static_assets/menu-click.wav', 
     './static_assets/old-fashioned.jpg', 
     './static_assets/react_logo.png', 
     './static_assets/switch-flip.wav',
     './static_assets/the-chester--v112351.prefilter.jpg',
     './static_assets/the-chester--v112355.prefilter.jpg',
     './static_assets/the-chester--v112362.prefilter.jpg',
     './static_assets/the-chester--v112371.prefilter.jpg',
     './static_assets/the-chester--v112379.prefilter.jpg',
     './static_assets/the-chester--v112392.prefilter.jpg',
     './static_assets/the-chester--v112393.prefilter.jpg',
     './static_assets/the-chester--v112399.prefilter.jpg',
     './static_assets/tourOfTheChester.json',
     './static_assets/whiskey-sour.jpg'
     ]
     ```

3) ```echo "<?php header( 'Location: /index.html' ) ; ?>" > vr/build/index.php```
4) ```cd vr/build```
5) ```heroku login```
6) ```git init && git add . && git commit -m "my first commit"```
7) ```heroku create && git push heroku master```
8) visit [https://url-generated-from-previous-step.herokuapp.com](http://localhost)

## Detailed Step by Step Directions
1) Install the React VR CLI – a command-line tool

```npm install -g react-vr-cli```

2) Clone the React VR repo
```git clone https://github.com/facebook/react-vr.git```

3) Change working directory to `Examples`

```cd react-vr/Examples/```

4) Initialize a new React VR project

```react-vr init TourSampleTest```

5) Change working directory to new project and remove `static_assets` folder

```cd TourSampleTest && rm -rf static_assets/```

6) Copy `static_assets` folder from example project

```cp -r ../TourSample/static_assets static_assets```

7) Copy `js` files from example project

```cp ../TourSample/{InfoButton.js,LoadingSpinner.js,NavButton.js,Tooltip.js,index.vr.js} .```

8) Replace `TourSample` with `TourSampleTest`

```sed -i '' 's/TourSample/TourSampleTest/g' index.vr.js```

9) Build the project

```npm run bundle```

10) Copy static_assets into the build

```cp -r ./static_assets vr/build/static_assets```

11) Copy index.html into the build

```cp vr/index.html vr/build```

12) Modify vr/build/index.html (NOT vr/index.html)
  * Replace `'<script src="./build/client.bundle?platform=vr"></script>'` with `'<script src="./client.bundle.js?platform=vr"></script>'`
  * Replace `'./build/index.bundle?platform=vr&dev=false',` with `'./index.bundle.js?platform=vr',`
  * Modify `document.body` with the following for all static assets:
    ```
    document.body,
    {}, 
    ['./static_assets/Three-Cocktails.jpg', 
     './static_assets/Three-Cocktails.webm', 
     './static_assets/beer-cheers.jpg', 
     './static_assets/cafe.wav', 
     './static_assets/chalkboard-menu.jpg', 
     './static_assets/chester_icon.png', 
     './static_assets/circle_ramp.png', 
     './static_assets/info_icon.png',
     
     './static_assets/License.html', 
     './static_assets/menu-click.wav', 
     './static_assets/old-fashioned.jpg', 
     './static_assets/react_logo.png', 
     './static_assets/switch-flip.wav',
     './static_assets/the-chester--v112351.prefilter.jpg',
     './static_assets/the-chester--v112355.prefilter.jpg',
     './static_assets/the-chester--v112362.prefilter.jpg',
     './static_assets/the-chester--v112371.prefilter.jpg',
     './static_assets/the-chester--v112379.prefilter.jpg',
     './static_assets/the-chester--v112392.prefilter.jpg',
     './static_assets/the-chester--v112393.prefilter.jpg',
     './static_assets/the-chester--v112399.prefilter.jpg',
     './static_assets/tourOfTheChester.json',
     './static_assets/whiskey-sour.jpg'
     ]
     ```

13) Create `index.php` file to trick Heroku

```echo "<?php header( 'Location: /index.html' ) ; ?>" > vr/build/index.php```

14) Change working directory to build

```cd vr/build```

15) Login to Heroku

```heroku login```

16) Initialize for Heroku

```git init && git add . && git commit -m "my first commit"```

17) Create a new Heroku project

```heroku create```

18) Deploy build to Heroku

```git push heroku master```

19) visit [https://url-generated-from-previous-step.herokuapp.com](http://localhost)
