# Animated and Interactive Maps with Charts and Markers

This apps will help you to present data on web pages without requiring more knowledge about programming. You only need to write your data in JSON format and write your page in markdwon file format than you already have a web page that represents your data on maps and charts.
 
## Features
- Selectable vector map
- Customize vector map styles
- Display charts related with selected area
- Display multi charts with multi chart type
- Display markers based on geolocation with your own marker image
- Visibility setting of markers and map tile
- Display your pages in markdown format
- Display local marker 
- Clickable local marker to show related data


## Prerequested

This software is request the following frameworks:

- NodeJS (v10.20.1)
- Angular 9

## Installation

Go to the project folder and run the following command using your terminal:

```npm install```

Make sure the installation succesful then run the following command to run the application:

```ng serve --open```

For more information please go to [Angular](https://angular.io) offical website.

## Run The Builded Application (Ready to Use)

If you don’t understand how angular works, I provide an application that is ready to use. You can use it easily without having to install NodeJS and Angular first. Go to the `dist/mapLinker` folder and run the `index.html` file using a portable server, for example php-cli. Go to the terminal and run the command:

```php -S localhost: 3000```

Go to your browser and access to the address `http://localhost:3000` to run the application. Make sure you are connected to the internet.

You can also run the application using XAMPP. Make a folder on htdoc, for example with the name ‘mymap’. Move all application files into the mymap folder and then access to the address `http:// localhost/mymap`. Make sure XAMPP is running.

For global installation, you just need to put all the files in the folder into your hosting folder.


 
## File Structure of Builded App

Builded App is in `dist/mapLinker` folder and contain the files below:

```
- index.html
+ assets
  + [countryID]
    - data.json
    - config.json
    - markers.json
    - pages.json
    + markers
      - dot.svg
    + pages
      - mypages.md
- and other js files
```

**DO NOT REMOVE those files!**

## Change HTML Title and Favicon

You can change the HTML Page title by modify the title tag in `index.html`  file.

```
...
<title>[Your App Title]</title>
  <base href="/">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="./assets/dot.ico">
...
```
## Add Custom Color of Area

You can use the custom color of a specific area by adding the attribute in `data.json`.

```
[
    ...
    {     
      ...,
      "color":"green",
      "markers":[],
      "charts":[]
    },
    ..
 ]
```
The color attribute will make the related area colored with green.

## Add Charts Data

Data charts are taken from the data.json file. The data structure in the file is:
```
[
    {
        ...
        "charts":[
            {
                "title":"Column Chart",
                "type":"ColumnChart",
                "columns":["Country", "Value 1", "Value 2"],
                "data":[
                    ["London", 8136000, 678000],
                    ["New York", 8538000, 890200],
                    ["Paris", 2244000,345000],
                    ["Berlin", 3470000, 7891000],
                    ["Kairo", 19500000, 3456999]
                  ]
            },
            ...
      ],
      ...
  },
  ...
]
```
 
You can add data by modifying the chart attributes. The required variables are:
 
**title:**
Title of your charts
 
**type:**
Type of your chart. Charts library is using Google Charts. You can refer to the chart type of the library. You can get the charts gallery here.
 
**columns:**
Column name of data. Column length data and data item must be the same. For example, if column data is `[“Country”, “Value 1”, “Value 2”]` then the each item of data must have 3 items.
 
**data:**
Data content that will present in charts. The structure of each item is `[“label”, value1, value2]`. The label must be string and the value must be integer or double.
 
**DO NOT modify the stateCode and stateName attributes.**

## Add Local Marker

Local marker is the markers that shown only if the area is selected. Modifu the `data.json` file to add your local marker.

```
...
"markers":[
        {
          "lat":-0.7622,
          "lon": 113.0637,
          "src":"./assets/local_marker.svg",
          "text":"local marker",
          "data":{
            "title":"Local Marker Description",
            "content":"./assets/ID/pages/jakarta.md"
          }
        }
]
...
```
Add the above attribute to the item of data.json. If `markers` attribute exist in the object then markers will be shown when the user selects the area. You can get the lat and lon attribute from openstreetmap.org. For example, you get the url below:

```
https://www.openstreetmap.org/search?query=indonesia#map=9/-6.2197/106.9533&layers=H
```

Based on the url, lat value is -6.2197 and lon value is 106.9533. You also can use your own marker image in png or svg and add the text using `text` attribute. If you want to make the marker is clickable, you can add the `data` attributes with the `title` will displayed in the title of dialog and `content` will display in content dialog. The `content` attribute is the url that call your markdown file. Place your markdown file anywhere in assets folder.


## Add Markers Data
 
You can add the markers into the map with your own image marker and title. To add the marker, please modify the markers.json file. Structure of the file is:

```
[
    {
        "lon": 115.8604796,
        "lat":-31.9527121,
        "src":"./assets/markers/dot.svg",
        "text":"",
        "data":{
          "title":"Your dialog title",
          "content":"path/to/yourfile.md"
        }
    },
    {
        "lon":130.30,
        "lat":-24.847,
        "src":"./assets/markers/dot.svg",
        "text":"Your marker text"
    }
]
```
 
**lon:**
Longitude coordinate position. You can get that value from google maps or openstreetmap.
 
**lat:**
Latitude coordinate position.
 
**src:**
Marker image location. Place your marker image in the markers folder. You can use the .svg, .jpg, or .png image.
 
**text:**
Text of your marker.

**data***
Your related marker data. If this attribute exists then you can click the marker image and show the dialog to display related data.

## Change App Title, Style, and Visibility

You can change the title, style, and visibility by modifying the config.json file. The contain of config.json file is:

```
{
    "title":"YOUR APP TITLE",
    "navbarColor":"primary",
    "mapDefault":{
        "fill":"rgba(255, 0, 0, 0.2)",
        "stroke":{
            "color":"white",
            "width":2
        }
    },
    "mapSelected":{
        "fill":"rgba(255, 0, 0, 0.6)",
        "stroke":{
            "color":"green",
            "width":2
        }
    },
    "mapHover":{
        "fill":"rgba(255, 0, 0, 0.6)",
        "stroke":{
            "color":"green",
            "width":2
        }
    },
    "showMapTile":true,
    "showMarkers":true
}
```
 
**title:**
Title of your application. Title will appear in the navigation bar.
 
**navbarColor:**
You can modify the color of the navigation bar. The options of color are: primary, default, warn.
 
**fill:**
Color of vector map. You can use hex color system (“#ccc”) or rgba (redValue, greenValue, blueValue, transparancyValue) color system.
 
**stroke:**
Stroke style vector map.
 
**showMapTile:**
If true, a global map will appear. Set the value false If you want to hide the global map.
 
**showMarkers:**
True value will make the markers appear on the map.

**mapDefault:**
The style for default map vector.

**mapSelected:**
The style for map vector if selected.

**mapHover:**
The style for map vector if the mouse is over the vector.

## Create Page

You can add your own page in markdown format. To create your own page, follow the steps:
1. Modify the pages.json file. Add new object in the array:

  ```
[
    {
        "title":"My Page",
        "src":"./assets/pages/mypage.md"
    }
]
  ```
 
  The code above will get a markdown file that is placed in the assets/pages folder. The title ‘My Page’ will appear in the navigation bar.

  TIPS:

  You can write your markdwon format using online markdown editor like [dilinger](https://dillinger.io/).
 
2. Place your markdown file in folder assets/pages/ or anywhere in assets folder.

