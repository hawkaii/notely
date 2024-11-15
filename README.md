# Notely

Notely is a simple, efficient application for writing and managing your notes. Whether for lectures, meetings, or personal thoughts, Notely helps you stay organized and productive.
Features

    Seamless Note Creation: Easily create, edit, and delete notes.
    Categorization: Organize your notes with categories or tags.
    Search Functionality: Quickly find your notes with a robust search feature.
    Cross-Platform Support: Access your notes from any device.
    User-Friendly Interface: Intuitive and clean interface for hassle-free note-taking.

# Technologies Used

    Frontend: React.js
    Backend: Node.js, Express.js
    Database: SQLite hosted on Turso
    Deployment: Google Cloud Run

# Contributing

We welcome contributions! Please fork the repository, create a branch, and submit a pull request. Ensure that your code meets our quality standards.

## Local Development
Make sure you're on Go version 1.20+.

Create a `.env` file in the root of the project with the following contents:

```bash
PORT="8080"
```

Run the server:

```bash
go build -o notely && ./notely
```

*This starts the server in non-database mode.* It will serve a webpage at `http://localhost:8080`. However, you won't be able to interact with the webpage until you connect it to a MySQL database and run the migrations.

## Database Setup

This project uses a MySQL database for persistent storage. You can install MySQL locally for local development, or connect to a remote database.

Add *your* database connection string to your `.env` file. Here's an example:

```bash
DATABASE_URL="username:password@host/dbname?tls=true"
```

Once you have an empty database, you'll need to run migrations to create the schema. Make sure you have [goose](https://github.com/pressly/goose) installed:

```bash
go install github.com/pressly/goose/v3/cmd/goose@latest
```

Then run the migrations:

```bash
./scripts/migrateup.sh
```

Start the server:

```bash
go build -o notely && ./notely
```

Because the `DATABASE_URL` environment variable is set, the server will connect to the database and serve the webpage at `http://localhost:8080`. The page should be fully functional now. You can:

* Create a user (login as that user)
* Save notes
* Logout (To log in again you'll just create a new user)

*The purpose of this project is to just be a simple CRUD app that we can use to practice CI/CD. It's not meant to be a fully functional app.*

