https://code.tutsplus.com/using-celery-with-django-for-background-task-processing--cms-28732t
python -m venv env
pip install Django
django-admin startproject quick_publisher
cd quick_publisher 
python manage.py startapp main
python manage.py startapp publish
python manage.py runserver
python manage.py makemigrations 
python manage.py migrate 
pip install Celery
pip install redis
https://redis.com/blog/redis-on-windows-10/

celery -A quick_publisher.celery worker --loglevel=debug --concurrency=4

pip install django-celery-beat

celery -A quick_publisher flower
flower -A quick_publisher.celery --port=5555