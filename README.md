# 🐳 M169-Mini-Projekt

## 📂 1. Verzeichnisse erstellen
Zuerst muss man für das Mini-Projekt die benötigten Verzeichnisse erstellen
```bash
$projektPfad = "C:\irgend\ein\Pfad\mein-web-projekt"
New-Item -ItemType Directory -Path $projektPfad -Force
Set-Location -Path $projektPfad
```

## 📝 2. Konfigurationsdateien erstellen
```bash
New-Item -ItemType Directory -Name "logs"
New-Item -ItemType Directory -Name "html"
```

```bash
@"
FROM nginx:latest
EXPOSE 80
"@ | Out-File -FilePath "Dockerfile" -Encoding ascii
```

```bash
@"
<!DOCTYPE html>
<html lang="de">
<head><meta charset="UTF-8"><title>gugus</title></head>
<body>
    <h1>hat alles funktioniert?!</h1>
    <p>nomel en gugus</p>
</body>
</html>

"@ | Out-File -FilePath "html\index.html" -Encoding utf8
```

## 🏗️ 3. Docker Image Build & Deployment
```bash
docker build -t mein-webserver .
```
## 🏃 Container starten
```bash
docker run -d --name mein-web-container --user root -p 8080:80 -v "${PWD}\html:/usr/share/nginx/html:ro" -v "${PWD}\logs:/var/log/nginx" mein-webserver
```
