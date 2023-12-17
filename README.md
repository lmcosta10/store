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
7) 