GeoCloud
========

jQuery Plugin to create points on a flat map by their longitudes and latitudes

Plugin-Init
========

    $('#map_cloud').geocloud({
        width: 306,             // hidth of the map
        height: 400,            // height of the map
        map_src: 'italy_s.png', // path to the image-file
    
        // you will get these value together with the map
        geo_settings: {         
            x_corr: 0.81,
            y_corr: 1.10,
            coef: 0.0316
        },
        ref_point: { 
            pixel_point: [149, 208],
            coord: [12.4942486, 41.8905198]
        }                   
    });   

Adding Points to your map
=======
    $('#map_cloud').data('geocloud').drawPoints([
      {title: 'Roma',      size: 24, coord: [12.4942486, 41.8905198]},
      {title: 'Trento',    size: 18, coord: [11.1190591, 46.0667123]},
      {title: 'Palermo',   size: 13, coord: [13.3614059, 38.11564]},
      {title: 'Catanzaro', size: 10, coord: [16.5877572, 38.9105359]},
      {title: 'Genova',    size: 18, coord: [8.93398890, 44.4070624]},
      {title: 'Aosta',     size: 11, coord: [7.313234,   45.7350001]},
      {title: 'Napoli',    size:  9, coord: [14.2525421, 40.8399833]},
      {title: 'Bari',      size: 20, coord: [16.8721133, 41.1259135]},
      {title: 'Venezia',   size: 17, coord: [12.3387844, 45.4343363]},
      {title: 'Milano',    size:  8, coord: [9.1881714,  45.463681]},
      {title: 'Cagliari',  size: 14, coord: [9.10932389, 39.2154086]}
    ],
    
        css: {},      // add further Styles
        attr: {},     // add some attributes as title, class, etc..
    
        // Define Events on your points (event.data.city contains all values from your 
        // point {title, size, coor, etc..} you can add as many as you want to)
        events: {    
            'mouseover': function(event) {},
            'click': function(event) {
                alert(event.data.city.title);
            }          
        }
    });


Available Maps
========
Germany, Spain and Portugal, Italy.
Soon there will be more


Canvas Support and distance between Points / Cities
========
From now on you have two more options for enabling HTML5 Canvas support for additional features:
    
    use_canvas: true,       // best if you use Modernizr.canvas here, checkout: http://modernizr.com/
    canvas_style_opt: {     // Styles for Canvas-Line
        fillStyle: "grey",  // color-Code
        lineWidth: 2}       // Line-width in Pixels

Example:
-------

Define some Cities

    var cities = [
        {title: 'Bordeaux', size: 22, coord: [-0.57918, 44.837789]},
        {title: 'Roanne',   size: 10, coord: [4.072695, 46.034432]},
        {title: 'Limoges',  size: 16, coord: [1.261105, 45.833619]},
        {title: 'Nantes',   size: 20, coord: [-1.553621, 47.218371]},
        {title: 'Paris',    size: 30, coord: [2.3522219, 48.856614]},
        {title: 'Le Havre', size: 10, coord: [0.107929, 49.49437]},
        {title: 'Monaco',   size: 18, coord: [7.42461579, 43.7384176]},
        {title: 'Lyon',     size: 21, coord: [4.835659, 45.764043]},
        {title: 'Toulouse', size: 13, coord: [1.444209, 43.604652]},
        {title: 'Perpignan',size:  8, coord: [2.8958719, 42.698684]}    
    ];

Draw them on your map

    $('#map_cloud').data('geocloud').drawPoints(cities);

Draw a Line between cities by passing the names ..

    $('#map_cloud').data('geocloud').drawLineByNames('Roanne', 'Toulouse');
    $('#map_cloud').data('geocloud').drawLineByNames('Toulouse', 'Paris');
    $('#map_cloud').data('geocloud').drawLineByNames('Paris', 'Nantes');
    $('#map_cloud').data('geocloud').drawLineByNames('Nantes', 'Bordeaux');

.. or Draw the Lines by passing the points with Geo-coordinates. This will return the distance in Km.

    var dist = $('#map_cloud').data('geocloud').drawLine(cities[9], cities[6]);
    alert("Distance between "+ cities[9].title +" and "+ cities[6].title +" is "+ parseInt(dist) +" Km"); // Distance between Perpignan and Monaco is 385 Km

Checkout /france/canvas_distance_calculation.html for the code

Examples
========
Checkout: 
 - /germany/...
 - /iberia/...
 - /italy/...
 - /france/ ...
 - /great_britain/ ...

And for a usecase: 
http://www.felix-abele.de/map/example
