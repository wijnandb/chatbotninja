release: python manage.py migrate
web: gunicorn --bind 0.0.0.0:$PORT --workers 1 --threads 8 --timeout 0 botminds.wsgi:application
worker: celery -A botminds worker -l INFO --beat --concurrency 2
