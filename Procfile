release: python manage.py migrate
web: gunicorn --bind 0.0.0.0:$PORT --workers 1 --threads 8 --timeout 0 chatbotninja.asgi:application -k uvicorn.workers.UvicornWorker
worker: celery -A chatbotninja worker -l INFO --beat --concurrency 2
