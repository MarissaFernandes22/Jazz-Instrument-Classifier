# Identification of Jazz Instruments

This application is desgined using FastAI and is hosted on a Docker image. 

Run on the browser, the application takes in an image as input and identifies the type of Jazz Instrument it is. The application uses a machine learning FastAI model (RESNET34) to determine the type of instrument it is. The docker instructions were used from 


## Installation

Recommended usage is to build the docker image with name <your_docker_name> yourself, and overwrite the export.pkl at runtime, and provide environment variables and substitute <your_docker_name> with the docker image name you created.

```shell
	docker run -p 80:80 \
		-v ./local/path/to/export.pkl:/app/export.pkl \
		-e TITLE="Chinese Calligraphy Classifier" \
		-e SUBTITLE="Can disambiguate Chinese calligraphy styles like KaiShu, LiShu, XiaoZhuan" 
		<your_docker_name>
```

## Usage


### API
Starlette backend provides a `/classify` endpoint and separate callbacks for GET and POST.

GET requests expect a query param `url` which indicates a URL to an image on the internet which should be classified

Example:
```
GET /classify?url=https%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fen%2Fd%2Fd4%2FMickey_Mouse.png
```

Response:
```
{"predictions":[["mickey",0.9781272411346436],["computer",0.021808452904224396],["animal",6.434295937651768e-05]]}
```

POST requests expect the body to be a Byte array of an image to be classified.


### Webapp
Starlette also serves a simple html/javascript app which can serve as a UI to interact with the backend, and display the prediction of a photo.


	
