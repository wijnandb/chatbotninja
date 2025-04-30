# Chatbotninja

Custom chatbots. Chat with your own data.

## Installation

You can setup a virtual environment and install dependencies in a single command with:

```bash
uv sync
```

This will create your virtual environment in the `.venv` directory of your project root.

## Set up database

Create a database named `chatbotninja`.

```
createdb chatbotninja
```

Create database migrations:

```
uv run manage.py makemigrations
```

Create database tables:

```
uv run manage.py migrate
```

## Running server

```bash
uv run manage.py runserver
```

## Building front-end

To build JavaScript and CSS files, first install npm packages:

```bash
npm install
```

Then build (and watch for changes locally):

```bash
npm run dev-watch
```

## Running Celery

Celery can be used to run background tasks.

Celery requires [Redis](https://redis.io/) as a message broker, so make sure
it is installed and running.

You can run it using:

```bash
celery -A chatbotninja worker -l INFO --pool=solo
```

Or with celery beat (for scheduled tasks):

```bash
celery -A chatbotninja worker -l INFO -B --pool=solo
```

Note: Using the `solo` pool is recommended for development but not for production.

## Updating translations

```bash
uv run manage.py makemessages --all --ignore node_modules --ignore .venv
uv run manage.py makemessages -d djangojs --all --ignore node_modules --ignore .venv
uv run manage.py compilemessages --ignore .venv
```

## Installing Git commit hooks

To install the Git commit hooks run the following:

```shell
$ uv run pre-commit install --install-hooks
```

Once these are installed they will be run on every commit.

For more information see the [docs](https://docs.saaspegasus.com/code-structure.html#code-formatting).

## Running Tests

To run tests:

```bash
uv run manage.py test
```

Or to test a specific app/module:

```bash
uv run manage.py test apps.utils.tests.test_slugs
```

On Linux-based systems you can watch for changes using the following:

```bash
find . -name '*.py' | entr uv run manage.py test apps.utils.tests.test_slugs
```
