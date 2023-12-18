How to Run Nginx Container Sample in Docker and Expose HTTP Port?


To run an Nginx container in Docker and expose the HTTP port, you can use the following steps:

1. **Pull the Nginx Image:**
   If you haven't already, pull the official Nginx image from Docker Hub:

   ```bash
   docker pull nginx
   ```

2. **Run Nginx Container:**
   Run a new Nginx container and expose the default HTTP port (port 80) on the host:

   ```bash
   docker run -d -p 80:80 --name my_nginx nginx
   ```

   - `-d`: Run the container in the background (detached mode).
   - `-p 80:80`: Map port 80 on the host to port 80 in the container.
   - `--name my_nginx`: Assign a name to the container (replace "my_nginx" with your preferred name).
   - `nginx`: The name of the image.

3. **Access Nginx:**
   Open a web browser or use a tool like curl to access Nginx at `http://localhost`. If you specified a different container name or used a remote host, replace `localhost` with the appropriate hostname or IP address.

   ```bash
   curl http://localhost
   ```

   You should see the default Nginx welcome page.

4. **Stop and Remove the Container (Optional):**
   If you want to stop and remove the Nginx container when you're done:

   ```bash
   docker stop my_nginx
   docker rm my_nginx
   ```

   Replace "my_nginx" with the actual name you used when running the container.

