# Rust Rocket REST API

This is a simple REST API built with Rust, using Rocket for the web framework and Diesel for ORM, with SQLite as the database. This API manages "rustaceans," a playful term for users of the Rust programming language.

## Prerequisites

- Rust and Cargo (the Rust build system and package manager)
- SQLite
- Diesel CLI


## Setting Up

1. **Install SQLite:**
   ```bash
   brew install sqlite3
   ```

2. **Install Diesel CLI with SQLite support:**
   ```bash
   cargo install diesel_cli --no-default-features --features sqlite
   ```

3. **Setup Diesel:**
   ```bash
   diesel setup
   diesel migration generate create_rustaceans
   diesel migration run --database-url=database.sqlite
   ```

## Running the API

To start the API server:

```bash
cargo run
```

This will start the Rocket server, and the API will be available at `http://127.0.0.1:8000`.

## API Endpoints

The API supports basic CRUD operations for managing rustaceans. Below are the available endpoints and example commands using `curl` to interact with the API.

### Create a Rustacean

- **POST** `/rustaceans`
  ```bash
  curl 127.0.0.1:8000/rustaceans -X POST -H 'Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==' -d '{"name": "Foo2", "email": "foo2@bar.com"}' -H 'Content-type: application/json'
  ```

### Get Rustaceans

- **GET** `/rustaceans`
  ```bash
  curl 127.0.0.1:8000/rustaceans -H 'Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ=='
  ```
- **GET** `/rustaceans/<id>`
  ```bash
  curl 127.0.0.1:8000/rustaceans/1 -H 'Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ=='
  ```

### Update a Rustacean

- **PUT** `/rustaceans/<id>`
  ```bash
  curl 127.0.0.1:8000/rustaceans/1 -X PUT -H 'Content-type: application/json' -H 'Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==' -d '{"name": "Booz", "email": "fooz@bar.com"}'
  ```

### Delete a Rustacean

- **DELETE** `/rustaceans/<id>`
  ```bash
  curl 127.0.0.1:8000/rustaceans/1 -X DELETE -H 'Content-type: application/json' -H 'Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ=='
  ```
