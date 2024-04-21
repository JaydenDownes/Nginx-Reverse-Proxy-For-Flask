# Flask App with Nginx Reverse Proxy Docker Setup

This documentation provides an example and instructions on how to use and edit a Flask app with Nginx reverse proxy Docker setup. 
<img align="right" width="400" src="https://res.cloudinary.com/practicaldev/image/fetch/s--dc_gXynR--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://ishankhare.com/media/images/nginx-reverse-proxy.png" alt="The image illustrates a Nginx reverse proxy setup (Khare, 2022). https://dev.to/ishankhare07/nginx-as-reverse-proxy-for-a-flask-app-using-docker-3ajg">
> [!IMPORTANT]
> This setup is intended for development and testing purposes only. It is not suitable for production environments. By using this setup, you acknowledge and accept that your use is at your own risk, and the developers are not liable for any damages or consequences arising from its use.

<br>

#### Why Use This Setup:

* Isolation: Docker containers package each component (Flask app, Nginx server, dependencies) separately, ensuring they run in isolation for easier management and deployment.
* Scalability: Nginx acts as a reverse proxy, enabling horizontal scaling of the application by adding more Flask containers behind it to handle increased traffic.
* Simplicity: Docker Compose allows easy management of multiple containers with a single configuration file, simplifying the start, stop, and rebuild processes.
* Consistency: Docker ensures consistency across development, testing, and production environments, reducing compatibility issues during deployment.

#### Common Applications:

* Web Development: Ideal for developing and testing Flask-based web applications locally.
* Microservices Architecture: Suitable for building microservices-based architectures, with each Flask app representing a microservice.
* CI/CD Pipelines: Easily integrates into CI/CD workflows for automated build, test, and deployment processes.
* Prototyping and POC: Enables quick prototyping and validation of ideas, allowing developers to focus on application logic without infrastructure concerns.
* Overall, this setup provides a convenient and flexible environment for web application development, testing, and deployment.
<br>

## Prerequisites

- Docker installed on your machine ([Install Docker](https://docs.docker.com/get-docker/))
<br>

## Usage

#### 1. Clone the Repository

```bash
git clone https://github.com/JaydenDownes/Nginx-Reverse-Proxy-For-Flask
cd Nginx-Reverse-Proxy-For-Flask
```

#### 2. Run the Application

```bash
docker-compose up --build
```

This command will build and start the Docker containers for the Flask app and Nginx.

#### 3. Access the Application

- Open your web browser and go to `http://localhost` to access the Flask app.
- You can also access the app using the IP address of your machine or the hostname configured in your hosts file (e.g., `http://device01`).

#### 4. Edit the Application

- To make changes to the Flask app, edit the `app.py` file.
- To customize the Nginx configuration, edit the `nginx.conf` file.
- After making changes, rebuild and restart the Docker containers:

```bash
docker compose down
```
Run in background (Daemon):
```bash
docker compose up --build -d
```
Run in Terminal:
```bash
docker compose up --build
```
<br>

## Directory Structure

```
drive-backend/
│
├── app.py
├── Dockerfile
├── Dockerfile.nginx
├── nginx.conf
├── requirements.txt
└── docker-compose.yml
```

- `app.py`: Flask application code.
- `Dockerfile`: Dockerfile for the Flask app.
- `Dockerfile.nginx`: Dockerfile for Nginx.
- `nginx.conf`: Nginx configuration file.
- `requirements.txt`: Python dependencies for the Flask app.
- `docker-compose.yml`: Docker Compose configuration file.
<br>

## Configuration

#### Flask App

- The Flask app runs on port 5000 inside the Docker container.
- To edit the Flask app, modify the `app.py` file.

#### Nginx

- Nginx acts as a reverse proxy and listens on port 80.
- The `nginx.conf` file contains the Nginx configuration.
- Edit this file to customize Nginx settings, such as server_name or location directives.

#### Docker

- Docker Compose is used to manage the Docker containers.
- The `docker-compose.yml` file defines the services and their configurations.
- You can customize ports, volumes, and other settings in this file.
<br>

## Troubleshooting

- If you encounter any issues, check the logs of the Docker containers using `docker-compose logs`.
- Verify network connectivity, firewall settings, and DNS resolution if you're unable to access the application.
