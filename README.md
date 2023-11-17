# WME EntryPoint
GreasyFork script for Waze Map Editor

EntryPoint class necessary for creating an entryExitPoint in code.

Instantiate the class and pass the object with geoJSON data in the constructor then add the `Point` object to the `entryExitPoints` array.

## Example

```javascript
// We need it to update object
let WazeActionUpdateObject = require('Waze/Action/UpdateObject')
  
// Get selected POI
let poi = W.selectionManager.getSelectedDataModelObjects()[0]

// Create entry point object
let point = {
  point: { type: 'Point', coordinates: [0, 0] },
  entry: true,
  exit: false,
  primary: false,
  name: ''
}

// Create instance of the entryPoint
let entry = new entryPoint({point: W.userscripts.toGeoJSONGeometry(point)})

// Update some POI
W.model.actionManager.add(new WazeActionUpdateObject(poi, { entryExitPoints: [entry] }))


// If you use OpenLayers point you can convert it, and assign to object
let OLPoint = new OpenLayers.Geometry.Point(lon, lat).transform('EPSG:4326', 'EPSG:900913')
point.point = W.userscripts.toGeoJSONGeometry(OLPoint)
```

## Links
Author homepage: http://anton.shevchuk.name/  
Script homepage: https://github.com/AntonShevchuk/wme-entrypoint
