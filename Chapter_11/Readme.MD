How to Build Dockerfile Simple HTML Application Container Using Node JS?


To build a Dockerfile that runs a simple HTML "Hello, World!" application and exposes port 80, follow these steps:

1. **Create an HTML File:**
   Create a simple HTML file named `index.html` with the following content:

   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Hello, World!</title>
   </head>
   <body>
       <h1>Hello, World!</h1>
   </body>
   </html>
   ```

2. **Create a Dockerfile:**
   Create a Dockerfile in the same directory as your HTML file with the following content:

   ```Dockerfile
   # Use an official lightweight Node.js image
   FROM node:14-alpine

   # Set the working directory to /app
   WORKDIR /app

   # Copy index.html file into the container at /app
   COPY index.html /app

   # Expose port 80 to the outside world
   EXPOSE 80

   # Define environment variable
   ENV NAME World

   # Run a simple HTTP server to serve the HTML file
   CMD ["npx", "http-server", "-p", "80"]
   ```

   This Dockerfile uses the Node.js Alpine image, copies index.html file, exposes port 80, and runs the `http-server` command to serve the HTML file.

3. **Build and Run Docker Container:**
   Build the Docker image and run the container:

   ```bash
   docker build -t hello-html .
   docker run -p 80:80 hello-html
   ```

4. **Access HTML Application:**
   Open a web browser or use a tool like curl to access the HTML application at `http://localhost`. If you specified a different container name or used a remote host, replace `localhost` with the appropriate hostname or IP address.

   ```bash
   curl http://localhost
   ```

   You should see "Hello, World!" displayed.

5. **Stop and Remove the Container (Optional):**
   If you want to stop and remove the Docker container when you're done:

   ```bash
   docker stop <container_id_or_name>
   docker rm <container_id_or_name>
   ```

   Replace `<container_id_or_name>` with the actual ID or name of your Docker container.

This example uses a lightweight Node.js image to serve a simple HTML file. 

