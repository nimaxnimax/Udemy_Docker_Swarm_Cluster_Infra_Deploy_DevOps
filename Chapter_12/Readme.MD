How to Run Commands in Running Container in Docker?


Here's an example to execute commands in a container:

1. **Run an Nginx Container:**
   First, run an Nginx container in the background:

   ```bash
   docker run -d -p 80:80 --name my_nginx nginx
   ```

   This command starts an Nginx container in detached mode with the name "my_nginx."

2. **Run Commands:**
   Use `docker exec` to run commands inside the Nginx container.

   - To create an empty file named `test.txt` using the `touch` command:

     ```bash
     docker exec -it my_nginx sh -c 'touch /usr/share/nginx/html/test.txt'
     ```

   - To list the files in the Nginx container's HTML directory using the `ls` command:

     ```bash
     docker exec -it my_nginx sh -c 'ls /usr/share/nginx/html'
     ```

   - To view the contents of the `test.txt` file using the `cat` command:

     ```bash
     docker exec -it my_nginx sh -c 'cat /usr/share/nginx/html/test.txt'
     ```

3. **Cleanup (Optional):**
   If you no longer need the containers, you can stop and remove them:

   ```bash
   docker stop my_nginx
   docker rm my_nginx
   ```

