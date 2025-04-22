

creare una cartella flask-docker-example
```
mkdir flask-docker-example
cd progetto-python

```





app.py
```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Ciao dal container Docker con Python!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```



requirements.txt
```
flask
```


Dockerfile
```
# Usa un'immagine base di Python
FROM python:3.11-slim

# Imposta la directory di lavoro nel container
WORKDIR /app

# Copia i file locali nel container
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY app.py .

# Espone la porta dell'app Flask
EXPOSE 5000

# Comando di esecuzione dell'app
CMD ["python", "app.py"]

```

```
docker build -t flask-docker-example .

docker run -d -p 5000:5000 flask-docker-example
```

