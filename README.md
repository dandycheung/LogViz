LOGVIZ
===================

## Description
View the geolocation, status code, operating system and full request of IP addresses visiting visiting NGINX using tooltips on an SVG map

- Upload and processes multiple Nginx Log files and generate multiple maps at a time

- Backend: Flask for routing, processing logs, and python geoip2/maxmindDB for geolocation 

- Frontend: React for UI, d3 for generating svg maps

- There is a separate repo for running LogViz in seperate flask containers: https://www.github.com/seanquinn781/LogViz-Docker

![](logviz.gif)

## Installation

LogViz can be installed and ran a few different ways, using docker, using docker-compose, or by running the flask app with Python

# Docker Installation

from root of github repo:

```
docker build -t logviz_service .
```

run the container
```
docker run -p 5000:80 -t logviz_service
```

# Docker-compose installation
```
docker-compose up
```

# Python3 installation

1. Install python3 venv

```
sudo apt-get install python3-venv
```

2. Create virtual enviroment

```
cd LogViz
python3 -m venv LogViz
```

3. Activate virtual environment:
```
source LogViz/bin/activate
```

4. Install python requirements in the environment:  
```
pip3 install -r --user requirements.txt
deactivate
```

5. Run the app

in dev mode with flask:

```
cd app && python3 main.py
```

Go to http://127.0.0.1:5000


USAGE
==========================

1. Upload Log Files:

Download the Nginx access Log Files from your web server and unzip (or uncomment the unzip function in LogViz/app.py)

2. Upload multiple files to uploader at http://127.0.0.1:5000

8. click 'GENERATE MAP' and you will be routed to your maps

9. For more information about users OS, IP, request type etc, hover over datapoints on the SVG map


## Gunicorn/ Systemd service

See documentation and scripts in /app/gunicorn_config

