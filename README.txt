Building and Running the PostgreSQL with pgvector Docker Container
==================================================================

This README provides instructions on how to build and run the custom PostgreSQL
Docker container with pgvector extension.

Prerequisites:
--------------
- Docker installed on your system
- The Dockerfile in the same directory as this README

Steps:
------

1. Build the Docker image:
   Open a terminal in the directory containing the Dockerfile and run:
   
   docker build -t postgres-pgvector .

   This command builds the Docker image and tags it as "postgres-pgvector:15".

2. Run the Docker container:
   After the image is built, you can run it with the following command:
   
   docker run -d --name postgres-pgvector -p 5432:5432 -e POSTGRES_PASSWORD=postgres postgres-pgvector

   Replace "your_password" with a secure password of your choice.

   This command:
   - Runs the container in detached mode (-d)
   - Names the container "postgres-pgvector"
   - Maps port 5432 from the container to port 5432 on your host
   - Sets the PostgreSQL password to "your_password"

3. Verify the container is running:
   
   docker ps

   You should see your "postgres-pgvector" container in the list.

4. Connect to the PostgreSQL database:
   You can now connect to the database using any PostgreSQL client, using:
   - Host: localhost
   - Port: 5432
   - User: postgres
   - Password: your_password (the one you set in step 2)

   The vector extension should be automatically available in the default database.

5. Stop the container (when you're done):
   
   docker stop postgres-pgvector

6. Remove the container (if you want to delete it):
   
   docker rm postgres-pgvector

Note: The pgvector extension is automatically created in the default database.
If you create new databases, you'll need to manually enable the extension by
running: CREATE EXTENSION vector;
