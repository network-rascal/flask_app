# flask_app
working through udemy course - [REST APIs with Flask and Python in 2023](https://www.udemy.com/course/rest-api-flask-and-python/) 

## setup working environment
1. create virtual environment and activate
    ```
    python -m venv .venv
    source .venv/bin/activate
    ```
1. install packages
    ```
    pip install -r requirements.txt
    ```
1. run app locally
    ```
    flask --app app.py run
    ```

## setup docker app
1. install desktop [docker](https://www.docker.com)
1. create docker image
    ```
    docker build -t rest-apis-flask-python .
    ```
1. spin up container leveraging and auto-update - (this will output the container ID)
    ```
    docker run -dp 5001:5000 -w /app -v "$(pwd):/app" rest-apis-flask-python
    ```
1. you can view logs in the docker desktop app

## helpful docker commands
1. list running containers
    ```
    docker ps
    ```
1. stopping containers
    ```
    docker stop <CONTAINER_ID/NAME>
    ```
1. remove container
    ```
    docker rm CONTAINER_ID/NAME
    ```