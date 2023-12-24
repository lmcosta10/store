This repository is based on this youtube tutorial: https://youtu.be/rHux0gMZ3Eg?si=O7HlqrsMnJ7sOkLl
There is an explained tutorial in html inside the "tutorial" folder

# Step by step:
## Set up
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
## Creating an app
8) (New terminal window) python manage.py startapp appname
9) In projectfolder/settings.py -> INSTALLED_APPS -> add 'appname'
10) In projectfolder/views.py:
	```python
	from django.http import HttpResponse
	
	def say_hello(request):
		return HttpResponse()
	```
## Mapping urls to views
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
## Templates
14) Create templates folder in app folder, and a hello.html file in it
15) In hello.html:
    ```html
	<h1>Hello {{ name }}</h1>
    ```
16) In projectfolder/views.py:
	```python
	def say_hello(request):
		return render(request, 'hello.html', {'name': 'YN'})
	```
17)  Using logic in html:
In hello.html:
	```html
	{% if name %}
	<h1>Hello {{ name }}</h1>
	{% else %}
	<h1>Hello!</h1>
	{% endif %}
	```
## Debug in vscode
18) Click in Run and Debug on your left
19) Click in create a launch launch.json file, and then, in this case, python and then django
20) Add a port in "args" so it doesn't clash with the one in use for the server:
    ```json
    ...
    "runserver",
    "9000"
    ```
21) Now you can debug in Run and Debug, just click on the play button that's followed by Python: Django, and you can use the little bar to take a step forward, step into functions etc
22) Alternatively, you can use F5
## Debug with Django-Debug-Toolbar
