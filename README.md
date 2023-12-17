This repository is based on this youtube tutorial: https://youtu.be/rHux0gMZ3Eg?si=O7HlqrsMnJ7sOkLl

Step by step:
1) (In vscode terminal in project folder) pipenv install django
2) pipenv shell
2) django-admin startproject projectname .
3) python manage.py runserver (portnumber)
(Stop server)
4) pipenv --venv -> copy output -> Command Palette -> search "python interpreter" -> Create interpreter path -> paste and append "\Scripts\python.exe" -> relaunch terminal
5) Command Palette -> search "Open Workspace Settings (JSON)". This will create a .vscode folder
6) In .vscode/settings.json: "python.pythonPath": "path-to-interpreter". Change \ to / if on Windows
7) python manage.py runserver [portnumber]
If you get invalid syntax, open a new terminal window
8) (New terminal window) python manage.py startapp appname
9) In projectfolder/settings.py -> INSTALLED_APPS -> add 'appname'
10) In projectfolder/views.py:
	```python
	from django.http import HttpResponse
	
	def say_hello(request):
		return HttpResponse()
	```
11) Create urls.py in app folder
12) In this file, write:
	```python
	from django.urls import path
	from . import views

	urlpatterns = [
		path('hello/', views.say_hello)
	]
	```
13) In projectfolder/urls.py
	```python
	from django.urls import path, include

	urlpatterns = [
		...
		path('appname/', include('appname.urls'))
	]
	```