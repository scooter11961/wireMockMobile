
July 2014

wiremock is a java based app that can stand in as a service to respond with expected and controlled output.

ex. To mock out responses from the v1 guidance service for route and traffic information when called from ICE.
This allows me to test how the ETA bar, route ribbon, and traffic overlays work in a controlled way for a specific route.

structure:

mappings/ - files that define a url pattern to match, and what to return as the mock 
ex. mapping-v1-route-officeToArvada.json matches the url pattern "urlPattern": "/guidance/v1/route.*" and then returns the text in "bodyFileName" : "body-v1-route-officeToArvada.json"

__files. - the specific JSON object returned when the URL in the mappings file is requested
ex. "body-v1-route-officeToArvada.json" contains ...{"guidance":{"boundingBox":{"ul":{"lng":-105.081504,"lat":39.80112},"...


to start:
navigate to working directory:
ex. /Users/scotthatch07/src/wiremock

java -jar wiremock-1.46-standalone.jar --port 9999


Note you can also use the jar to capture calls:
ex. java -jar wiremock-1.46-standalone.jar --port 9999 --proxy-all="http://mob-integration.mapquestapi.com" --record-mappings --verbose

more info:
http://wiremock.org/getting-started.html



