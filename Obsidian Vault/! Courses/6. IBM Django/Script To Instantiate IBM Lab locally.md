```powershell
# 1. Download and extract the IBM lab template
Write-Host "1/4 Downloading and extracting lab template..." -ForegroundColor Cyan
Invoke-WebRequest -Uri "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBM-CD0251EN-SkillsNetwork/labs/m3_django_orm/lab2_template.zip" -OutFile "lab2_template.zip"
Expand-Archive -Path "lab2_template.zip" -DestinationPath "." -Force
Remove-Item "lab2_template.zip"
Set-Location -Path ".\lab2_template"

# 2. Create Virtual Environment & Install Dependencies (VERSION LOCKED)
Write-Host "2/4 Creating Python Virtual Environment and installing packages..." -ForegroundColor Cyan
python -m venv djangoenv
.\djangoenv\Scripts\python.exe -m pip install --upgrade pip -q
# CRITICAL FIX: Locked to Django 4.2 as explicitly requested by the IBM lab instructions
.\djangoenv\Scripts\python.exe -m pip install Django==4.2 psycopg2-binary -q

# 3. Inject the "Ultimate Local Fixes" into Django Settings
Write-Host "3/4 Reconfiguring Django settings for local development..." -ForegroundColor Cyan
$masterSettings = @"

# ==========================================
# MASTER LOCAL OVERRIDES (INJECTED SCRIPT)
# ==========================================
DEBUG = True
ALLOWED_HOSTS = ['*']

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'postgres',
        'USER': 'postgres',
        'PASSWORD': 'postgres', # Assumes default password was set during install
        'HOST': 'localhost',
        'PORT': '5432',
    }
}

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'crud',
]

MIDDLEWARE = [
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
]

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

STATIC_URL = '/static/'
DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'
"@
Add-Content -Path ".\settings.py" -Value $masterSettings

# 4. Migrate and Test
Write-Host "4/4 Applying migrations to local database..." -ForegroundColor Green
.\djangoenv\Scripts\python.exe manage.py makemigrations crud
.\djangoenv\Scripts\python.exe manage.py migrate

Write-Host "=====================================================" -ForegroundColor Magenta
Write-Host "SUCCESS! The lab is fully configured for this PC." -ForegroundColor Magenta
Write-Host "You can now edit models.py and run 'python write.py'" -ForegroundColor Magenta
Write-Host "=====================================================" -ForegroundColor Magenta
```
