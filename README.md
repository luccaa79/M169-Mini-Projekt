# M169-Mini-Projekt

```bash
$projektPfad = "C:\Users\luca.vatrella\OneDrive - RMD Informatik GmbH\Luca\2. Lehrjahr\S4\GBSSG\M169\mein-web-projekt"
New-Item -ItemType Directory -Path $projektPfad -Force
Set-Location -Path $projektPfad
```

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
    <p>Projektort: OneDrive / M169</p>
</body>
</html>

"@ | Out-File -FilePath "html\index.html" -Encoding utf8
```

```bash
docker build -t mein-webserver .
```

```bash
docker run -d --name mein-web-container --user root -p 8080:80 -v "${PWD}\html:/usr/share/nginx/html:ro" -v "${PWD}\logs:/var/log/nginx" mein-webserver
```
