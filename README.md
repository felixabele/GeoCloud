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


Examples
========
Checkout: 
 - /germany/...
 - /iberia/...
 - /italy/...
 - /france/ ...

And for a usecase: 
http://www.felix-abele.de/map/example
