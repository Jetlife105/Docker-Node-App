# Assignment #4: Application Containerization

This is a simple Node.js web application designed for learning Docker containerization concepts.

## Application Overview

This application is a basic Express.js web server that:
- Serves a static HTML page at the root (`/`)
- Provides an API status endpoint at `/api/status`
- Includes a health check endpoint at `/health`
- Runs on port 3000 by default (configurable via PORT environment variable)

## What's Included

- **app.js**: Main application server file
- **package.json**: Node.js dependencies and project configuration
- **public/index.html**: Static HTML page that confirms successful containerization
- **public/style.css**: Styling for the web page

## Running Without Docker (for reference only)

If you wanted to run this application directly (not required for assignment):
```bash
npm install
npm start
```

## Your Docker Assignment

**DO NOT MODIFY THE APPLICATION CODE**

Your task is to containerize this existing application using Docker. You need to:

1. Create a `Dockerfile` that properly containerizes this Node.js application
2. Build a Docker image from your Dockerfile
3. Run a container from your image
4. Verify the application works by accessing it in your browser

## Starting the Application

- To build the Docker image, run the command:

```bash
docker build -t docker-node-app .
```

- To run the Docker container on port 3000, run the command:

```bash
docker run -d -p 3000:3000 --name my-node-app docker-node-app
```

- To view running containers:

```bash
docker ps
```

- To stop and restart the container:

```bash
docker stop my-node-app
docker start my-node-app
```

- To remove the container after stopping it:

```bash
docker rm my-node-app
```


## Reflection Question
**Answer the following question in the space below**: How does containerization with Docker differ from using virtual machines, and why might a development team choose Docker containers over VMs for deploying applications like the one you just containerized?

Virtual machines have their own operating systems. Docker containers share the host operating system kernel. That means Docker containers are lighter, faster to start, and more efficient in their use of system resources. One reason development teams may choose to use Docker is that it guaranties that applications will run the same way across different machines without having to manually install all of the dependencies. For this project, I used Docker to create and run a Node.js app on port 3000. Docker makes it easier to bundle the application and its dependencies together, leading to fewer compatibility issues when sharing or deploying applications.

## Application Requirements for Docker

Your Dockerfile should ensure:
- The application has Node.js runtime available
- All application files are copied into the container
- Dependencies are installed (`npm install`)
- Port 3000 is exposed
- The application starts with `npm start`
- The container can be accessed from your host machine

## Verification

When your Docker container is running correctly:
- Navigate to `http://localhost:3000` (or whatever port you mapped)
- You should see a success page confirming containerization worked
- The `/api/status` endpoint should return JSON status information
### Application Screenshot

![Docker Application Running](screenshots/application.png)

### API Status Screenshot

![Docker API Status](screenshots/api-status.png)


## Troubleshooting Tips

- Make sure your port mapping is correct in the `docker run` command
- Check that all files are copied into the container
- Verify Node.js dependencies are installed in the container
- Use `docker logs <container-name>` to see application output

## File Structure Expected
```
docker-assignment/
├── Dockerfile          # You create this
├── app.js              # Provided
├── package.json        # Provided
├── public/             # Provided
│   ├── index.html      # Provided
│   └── style.css       # Provided
└── README.md           # This file
```

Good luck with your Docker containerization!