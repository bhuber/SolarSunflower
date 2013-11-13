# Solar Sunflower: A #TechCamp and CodeforPhilly.org Project

About
-----------
Solar Sunflower is a citywide sensor network, designed to be open source, extensible, and accessible. 

It is constructed out of [Arduino-compatible electronics](http://jeelabs.com/products/jeenode), [Raspberry Pi computers](http://www.raspberrypi.org/), and open source software.

The current focus of the project is on wireless monitoring of green stormwater infrastructure. The prototypes collect environmental data with analog sensors (soil moisture, temperature, light) embedded in the green stormwater infrastructure system (e.g., a school's rain garden). This data is sent wirelessly to a Raspberry Pi onsite, which packages the data and uploads it to a server in the cloud.

After receiving the data, the server frames it in educational and decision-making contexts. In the decision-making context, city planners and officials are presented with data that will provide snapshots of the current state of stormwater infrastructure (data on water saturation, flow between sensors, etc.) and enable them to make real, tangible decisions about infrastructure.

In the educational context, students and teachers are provided with data from the water sensors as a means of enhancing the educational experience. Young students can see visual representations of data collected in a way that is easy to understand. Older students can access the data as exported csv files, allowing them to perform simple statistical and analytical operations. And older students are able to access exposed APIs to develop web applications.

Still further engagement with students can take the form of allowing them to create and decorate the housings for the sensors and electronics or even assemble kits.

Installation
-----------

To initialize:
`rake db:create`
`rake db:migrate`
`rake db:seed`

You might also want to POST some data points using the`curl` request below.

login with user@example.com/changeme

Usage
-----------

To POST soil moisture data to the database, execute this `curl` request:

curl -v -H "Content-Type: application/json" -X POST -d '{"type":"soilmoisture", "data":{"collection_point_id":1,"collection_time":"2013-03-08 08:58AM","deptha":1,"depthb":1.2,"depthc":1.9}}' 'http://localhost:3000/dc/'

Each soil moisture data bundle belongs to a `collection point`, which belongs to a `site`. You can navigate through this heirarchy from the the home page.

Each `site` has a page that displayes `collection points` and `soilmoisture` data bundles. Add `.json` to the `site` URL get request to return a JSON object representation of that site's data, i.e. `http://localhost:3000/sites/1.json`

This can be used to generate graphs and visualizations.
