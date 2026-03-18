# Django Local Setup Script

This script resets your local Django environment, installs dependencies, applies migrations, and starts the development server on port 8080.

```bash
#!/bin/bash

# Delete all migration files except __init__.py
find . -path "*/migrations/*.py" -not -name "__init__.py" -delete

# Delete all compiled Python migration files
find . -path "*/migrations/*.pyc" -delete

# Remove database files
rm db.*

# Remove existing virtual environment
rm -rf env/

# Create a new virtual environment
virtualenv -p python3 env

# Activate the virtual environment
source env/bin/activate

# Install Python dependencies
pip install -r requirements.txt

# Apply Django migrations
python manage.py makemigrations
python manage.py migrate

# Start Django development server on port 8080
python manage.py runserver 8080
