# Lunch Menu Creator

Lunch Menu Creator is a browser-based publication editor for building, editing, printing, and reusing school breakfast and lunch menus. It is delivered as a single HTML application and served by Nginx when deployed with Docker.

## Features

- Four-week meal-cycle editor
- Lunch, breakfast, and custom menu titles
- Configurable dates, pricing, daily choices, and calendar cycles
- Color-coded cycle weeks
- Demo menu population
- Browser autosave with status notifications
- JSON backup download and restore
- Landscape print and PDF layout
- Huron City Schools publication styling

## Docker Deployment

### Requirements

- Docker Engine or Docker Desktop
- Docker Compose v2 (`docker compose`)
- Git, if cloning or updating from GitHub

### Quick Start

Clone the repository and start the application:

```bash
git clone git@github.com:huroncityschools/menu-creator.git
cd menu-creator
docker compose up -d --build
```

Open [http://localhost:8080](http://localhost:8080) in a browser. From another computer, replace `localhost` with the Docker server's hostname or IP address.

### Use a Different Port

The default host port is `8080`. Set `PORT` when starting the container to use another port:

```bash
PORT=80 docker compose up -d --build
```

For HTTPS or a public deployment, place the application behind the district's existing reverse proxy or ingress service and terminate TLS there.

### Check Status and Logs

```bash
docker compose ps
docker compose logs -f lunch-menu-creator
```

The image includes an HTTP health check. A healthy deployment will show the service as running and healthy in `docker compose ps`.

### Update the Application

Pull the latest changes and rebuild the container:

```bash
git pull
docker compose up -d --build
```

### Stop or Remove the Container

Stop the application without removing its container:

```bash
docker compose stop
```

Stop and remove the application container and network:

```bash
docker compose down
```

## Menu Data and Backups

Menu content is stored in the web browser's local storage, not inside the Docker container. Each browser and device therefore has its own saved menu. Rebuilding or replacing the container does not erase browser-saved menus.

Use **Download backup** to save a portable JSON copy before changing computers, clearing browser data, or performing important menu updates. Use **Upload backup** to restore that file in another browser.

Printing and PDF creation are handled by the browser through **Print / PDF**.

## Project Files

- `index.html` - complete Lunch Menu Creator application
- `Dockerfile` - Nginx production image
- `docker-compose.yml` - single-service deployment configuration
- `.dockerignore` - files excluded from the container build context

## Local Use Without Docker

Because the application is a single HTML document, `index.html` can also be opened directly in a modern browser. Docker is recommended for shared access and server deployment.

