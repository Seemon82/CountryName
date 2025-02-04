# CountryName
Country description of any Continent

Pre-requisites:
1. Install python. Reference:  https://docs.python-guide.org/starting/installation/
2. Install MySQL.  Reference: https://dev.mysql.com/doc/refman/5.5/en/
3. Setup virtual environment:
 # Install virtual environment
sudo pip install virtualenv

# Make a directory
mkdir envs

# Create virtual environment
virtualenv ./envs/

# Activate virtual environment
source envs/bin/activate

4. Clone git repository
git clone "https://github.com/Seemon82/CountryName.git"

 5.Install requirements
 cd CountryName/
pip install -r requirements.txt

6.Load sample data into MySQL
# open mysql bash
mysql -u <mysql-user> -p

# Give the absolute path of the file
mysql> source ~/CountryName/world.sql
mysql> exit;

7.Edit project settings
# open settings file
vim panorbit/settings.py

# Edit Database configurations with your MySQL configurations.
# Search for DATABASES section.
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'world',
        'USER': '<mysql-user>',
        'PASSWORD': '<mysql-password>',
        'HOST': '<mysql-host>',
        'PORT': '<mysql-port>',
    }
}

# Edit email configurations.
# Search for email configurations
EMAIL_USE_TLS = True
EMAIL_HOST = 'smtp.gmail.com'
EMAIL_HOST_USER = '<your-email>'
EMAIL_HOST_PASSWORD = '<your-email-password>'
EMAIL_PORT = 587

# save the file


8. Run the server
   # Make migrations
python manage.py makemigrations
python manage.py migrate

# For search feature we need to index certain tables to the haystack. For that run below command.
python manage.py rebuild_index

# Run the server
python manage.py runserver 0:8001

# your server is up on port 8001



# Try opening http://localhost:8001 in the browser. Now you are good to go.
