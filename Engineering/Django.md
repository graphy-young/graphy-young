Django is high-level [[web]] [[framework]] based on [[Python]] for rapid development and pragmatic design. It follows [[Model-View-Controller]](MVC) architectural pattern. Django is [[open-source]], including [[Object-Relational Mapping]](ORM) system for [[database]] access, a templating engine for defining [[HTML]] templates, and a built-in administrative interface for managing application data. Django also provides tools for handling user authentication, security, and internationalization.

### Developing Django with Docker
Django has official image on [[Docker Hub]], but deprecated in 2016. To develop Django in [[container]] environment, use Python image then install Django via [[pip]].
#### Dockerfile
```
# Use the official Python 3.8 image as the base image
FROM python:3.8

# Set the default value for the 'app_name' argument
ARG app_name=django
ENV APP_NAME $app_name  

# Set the PYTHONUNBUFFERED environment variable to ensure Python prints directly to terminal
ENV PYTHONUNBUFFERED 1

# Set the working directory inside the container to '/django'
WORKDIR /django

# Install Django using pip
RUN pip install Django

# RUN apt-get update && apt-get install -y mariadb-client

# Start a new Django project named as specified in the 'app_name' argument
RUN django-admin startproject $app_name

# Update the 'ALLOWED_HOSTS' setting in the Django project's settings.py file
RUN sed -i "s/ALLOWED_HOSTS = \[\]/ALLOWED_HOSTS = \['*'\]/g" ./${APP_NAME}/${APP_NAME}/settings.py

# Expose port 8000 to allow external access
EXPOSE 8000

# Specify the command to run the Django development server when the container starts
CMD ["sh", "-c", "python ./${APP_NAME}/manage.py runserver 0.0.0.0:8000"]
```