

# Esercitazione Docker file


Passo 1 :
Creare la struttura del progetto

```
mkdir hello-docker
cd hello-docker
```
Passo 2 :
Creare l'applicazione Node.js:
Crea un file chiamato app.js con il seguente contenuto:

```
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => {
    res.send('Hello, World!');
});

app.listen(port, () => {
    console.log(`App listening at http://localhost:${port}`);
});


Passo 3:
Creare un file package.json:
Crea un file chiamato package.json con il seguente contenuto:
```


```
{
  "name": "hello-docker",
  "version": "1.0.0",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "^4.17.1"
  }
}
```
Passo 4:

Installare le dipendenze:
Esegui il seguente comando per installare Express:
```
npm install
```


Creare un Dockerfile:


```
# Usa un'immagine base di Node.js
FROM node:14

# Imposta la cartella di lavoro
WORKDIR /usr/src/app

# Copia il file package.json e installa le dipendenze
COPY package*.json ./
RUN npm install

# Copia il resto dell'applicazione
COPY . .

# Espone la porta su cui l'app ascolta
EXPOSE 3000

# Comando per avviare l'app
CMD ["npm", "start"]
```


Costruire l'immagine Docker:
```
docker build -t hello-docker .
```


Eseguire il container:
Esegui il container con il seguente comando:
bash

```
docker run -p 3000:3000 hello-docker
```

Testare l'applicazione:
Apri il tuo browser e vai su http://localhost:3000. Dovresti vedere il messaggio "Hello, World!".




