
# Dockerfile Structure

A Dockerfile is a script containing a series of instructions to assemble a Docker image. Each line of a Dockerfile specifies a step in the process of building the image. Here’s a breakdown of commonly used Dockerfile instructions with a sample project example.

Key Dockerfile Instructions
FROM: Defines the base image to use. This is the first instruction in a Dockerfile, as it sets the foundation for the image.

```dockerfile
FROM nginx:alpine
```
Here, we use the lightweight nginx:alpine image as the base for our web server.

WORKDIR: Sets the working directory inside the container. It simplifies file paths for subsequent commands and ensures they’re relative to this directory.

```dockerfile
WORKDIR /usr/share/nginx/html
```
This sets /usr/share/nginx/html as the default directory, where Nginx serves static files.

COPY: Copies files from the host system to the container. This is commonly used to add files like HTML, configuration files, or scripts.

```dockerfile
COPY index.html index.html
```
This command copies the local index.html file to the working directory inside the container.

EXPOSE: Informs Docker that the container will listen on a specified network port at runtime. This does not publish the port but serves as documentation.

```dockerfile
EXPOSE 80
```
Here, we expose port 80, which is the default port for web servers.

CMD: Specifies the command to execute when the container starts. Unlike RUN, which executes commands during the build, CMD runs only when a container based on the image is launched.

```dockerfile
CMD ["nginx", "-g", "daemon off;"]
```
This starts the Nginx server and keeps it running in the foreground to prevent the container from stopping.

Example: Building a Docker Image for a Static Website
Let’s go through an example to create a Docker image that serves a simple HTML page using Nginx.

Project Directory Structure
```plaintext
my-website/
├── Dockerfile
└── index.html
```

Step 1: Create Your HTML File
Create an index.html file with some sample HTML content:

```html
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Simple Web Page</title>
</head>
<body>
    <h1>Hello, Docker!</h1>
    <p>This is a simple HTML page served by Docker and Nginx.</p>
</body>
</html>
```

Step 2: Write the Dockerfile
Create a Dockerfile in the same directory as your index.html file.

```dockerfile
# Step 1: Use the Nginx Alpine image as the base
FROM nginx:alpine

# Step 2: Set the working directory inside the container
WORKDIR /usr/share/nginx/html

# Step 3: Copy the local index.html to the container's HTML directory
COPY index.html index.html

# Step 4: Expose port 80 for the web server
EXPOSE 80

# Step 5: Run Nginx in the foreground
CMD ["nginx", "-g", "daemon off;"]
```

Step 3: Build the Docker Image
In your terminal, navigate to the project directory (my-website/) and run the following command to build the Docker image:

```bash
docker build -t my-static-website .
```
This command tells Docker to build an image named my-static-website based on the instructions in the Dockerfile.

Step 4: Run the Docker Container
After building the image, use the following command to start a container and map it to port 8080 on your host:

```bash
docker run -d -p 8080:80 my-static-website
```
- `-d`: Runs the container in detached mode (in the background).
- `-p 8080:80`: Maps port 80 inside the container to port 8080 on the host machine.

Step 5: Access Your Web Page
Open your web browser and go to http://localhost:8080. You should see the HTML page content: "Hello, Docker!"

Summary of Each Dockerfile Instruction
- `FROM`: Defines the base image, which includes a minimal Linux environment and Nginx.
- `WORKDIR`: Sets the working directory to /usr/share/nginx/html (where Nginx serves files).
- `COPY`: Copies index.html from the host machine to the container’s HTML directory.
- `EXPOSE`: Specifies port 80, so the web server knows where to listen.
- `CMD`: Runs the Nginx server and keeps it active, so the container doesn’t stop immediately.

This Dockerfile creates a simple web server container to serve static HTML, perfect for demonstrating Docker basics. Let me know if you need further customization or have questions!









<br>
<br>
<br>
<br>



**👨‍💻 𝓒𝓻𝓪𝓯𝓽𝓮𝓭 𝓫𝔂**: [Suraj Kumar Choudhary](https://github.com/Surajkumar4-source) | 📩 **𝓕𝓮𝓮𝓵 𝓯𝓻𝓮𝓮 𝓽𝓸 𝓓𝓜 𝓯𝓸𝓻 𝓪𝓷𝔂 𝓱𝓮𝓵𝓹**: [csuraj982@gmail.com](mailto:csuraj982@gmail.com)





<br>
