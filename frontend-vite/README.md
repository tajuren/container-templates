## Frontend

This folder contains the frontend container template for [Vite](https://vite.dev/). Below is a brief overview of the structure and contents of this folder.

### Structure

- `Dockerfile`: Docker configuration file for building the frontend application and serving it using Nginx.
- `README.md`: This file, containing information about the project.
- `docker-compose.yml`: Docker Compose configuration file for setting up the application stack.
- `docker-compose-traefik.yml`: Docker Compose configuration file for setting up Traefik as a reverse proxy.
- `nginx.conf`: Nginx configuration file.
- `scripts/`: Directory containing utility scripts.
  - `replace_api_prod.sh`: Script to replace API endpoints (`VITE_BACKEND_URL`) for production.

### Setup

To set up the frontend project, follow these steps:

1. Build the Docker image:

```bash
   docker build -t frontend-app .
``` 

For compatibility, you need to use `VITE_BACKEND_URL` environment variable in your source code to access the backend API, which will be automatically replaced in the `replace_api_prod.sh` script later. 

2. Set up Environment Variables (Modify the `.env` file):

```bash
   cp .env.example .env
```

3. Run the application using Docker Compose:

```bash
   docker-compose up
```

Or run the application with Traefik:

```bash
   docker-compose -f docker-compose-traefik.yml up
```