# chat

An example Chat app built with molten.


## First-time setup

Run `./scripts/bootstrap` in a terminal.  This will install
`pip-tools` and sync the dependencies for the first time.

To run the app, you'll need to have [postgres] running.  Create a
database called `chat` and another called
`chat_tests` and grant the `postgres` user
access to both.  Finally, run `alembic upgrade head` to migrate the
database.


## Running the development server

Run `./scripts/runserver`.


## Running the interactive interpreter

Run `./scripts/interpreter`.


## Dependency management

Dependencies are managed via [pip-tools].

### Adding a dependency

To add a dependency, edit `requirements.in` (or `requirements-dev.in`
for dev dependencies) and add your dependency then run `pip-compile
requirements.in`.

### Syncing dependencies

Run `pip-sync requirements.txt requirements-dev.txt`.


## Migrations

Migrations are managed using [alembic].

### Generating new migrations

    alembic revision --autogenerate -m 'message'

### Running the migrations

    alembic upgrade head  # to upgrade the local db
    env ENVIRONMENT=test alembic upgrade head  # to upgrade the test db
    env ENVIRONMENT=prod alembic upgrade head  # to upgrade prod


## Testing

Run the tests by invoking `py.test` in the project root.  Make sure you
run any pending migrations beforehand.


[alembic]: http://alembic.zzzcomputing.com/en/latest/
[pip-tools]: https://github.com/jazzband/pip-tools
[postgres]: https://www.postgresql.org/
