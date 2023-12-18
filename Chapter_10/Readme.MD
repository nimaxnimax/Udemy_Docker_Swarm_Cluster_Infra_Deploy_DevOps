How to Run PHP Container Using Data Volume?


To run a PHP container with a simple "Hello, World!" example using a data volume for the container and expose port 80, you can follow these steps:

1. **Create a Directory for PHP Files:**
   Create a directory on your host machine where you'll store your PHP files. For example, let's create a directory named `php-app`:

   ```bash
   mkdir php-app
   ```

2. **Create index.php:**
   Inside the `php-app` directory, create a file named `index.php` with the following content:

   ```php
   <?php
   echo "Hello, World!";
   ?>
   ```

3. **Run PHP Container:**
   Run a PHP container, mounting the `php-app` directory as a data volume and exposing port 80:

   ```bash
   docker run -d -p 80:80 -v $(pwd)/php-app:/var/www/html --name my_php_container php:apache
   ```

   - `-d`: Run the container in the background (detached mode).
   - `-p 80:80`: Map port 80 on the host to port 80 in the container.
   - `-v $(pwd)/php-app:/var/www/html`: Mount the `php-app` directory as a data volume at `/var/www/html` in the container.
   - `--name my_php_container`: Assign a name to the container (replace "my_php_container" with your preferred name).
   - `php:apache`: Use the official PHP image with Apache.

4. **Access PHP Application:**
   Open a web browser or use a tool like curl to access the PHP application at `http://localhost`. If you specified a different container name or used a remote host, replace `localhost` with the appropriate hostname or IP address.

   ```bash
   curl http://localhost
   ```

   You should see "Hello, World!" displayed.

5. **Stop and Remove the Container (Optional):**
   If you want to stop and remove the PHP container when you're done:

   ```bash
   docker stop my_php_container
   docker rm my_php_container
   ```

   Replace "my_php_container" with the actual name you used when running the container.

This example uses the official PHP image with Apache and mounts the `php-app` directory as a data volume, allowing changes in the host's `php-app` directory to be reflected inside the container. 

