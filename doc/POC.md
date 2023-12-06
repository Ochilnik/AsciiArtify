POC.md

# Демо-інструкція

Щоб продемонструвати, що система ArgoCD працює, ми розгорнемо просте застосунок "Hello World".
![Application on Kubernetes](625258.cast) 

### Створіть репозиторій Git для застосунку.
Bash
*git init hello-world*

Додайте в репозиторій файл Dockerfile, який буде описувати образ контейнера для застосунку.
Фрагмент коду
*FROM nginx:latest*

*COPY index.html /usr/share/nginx/html/*

### Додайте в репозиторій файл index.html, який буде містити сторінку з текстом "Hello World".
*HTML*
*<!DOCTYPE html>*
*<html lang="en">*
*<head>*
 * <meta charset="UTF-8">*
*  <title>Hello World</title>*
*</head>*
*<body>*
*  <h1>Hello World!</h1>*
*</body>*
*</html>*

### Створіть нову ветку у репозиторії і додайте в неї зміни.
Bash
*git checkout -b main*
*git add .*
*git commit -m "Add Hello World application"*

### Відправте зміни в репозиторій.
Bash
*git push origin main*

### У графічному інтерфейсі ArgoCD створіть нову синхронізацію.
У списку синхронізацій натисніть кнопку "Add".
Введіть назву синхронізації "hello-world".
У полі "Repository" введіть URL-адресу репозиторію.
У полі "Revision" виберіть ветку "main".
Натисніть кнопку "Create".
ArgoCD автоматично синхронізує репозиторій і розгорне застосунок на Kubernetes.

Перейдіть за адресою http://localhost:8080/hello-world, щоб перевірити, чи працює застосунок.

Якщо ви побачите сторінку з текстом "Hello World", значить система ArgoCD працює коректно.

Висновок

В цьому документі ми розглянули покрокову інструкцію з розгортання GitOps-системи на варіанті K3D Kubernetes. За допомогою цієї інструкції ви можете швидко і легко розгорнути систему ArgoCD, яка дозволить вам використовувати Git для управління Kubernetes-кластером.