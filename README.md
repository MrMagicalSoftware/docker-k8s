# docker-k8s




# Installare Docker su Ubuntu Server

```
sudo apt update

```

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y

```

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```


```
sudo apt update
sudo apt install docker-ce -y
```

```
sudo systemctl start docker
sudo systemctl enable docker
```

___________________



# installare portainer su ubuntu server

```
sudo docker volume create portainer_data
```
```
sudo docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts
```



# Portainer: How to Fix “Unable to retrieve image details”

I cannot access container’s console in Portainer. When click Console link, it showed error message “Unable to retrieve image details”.
To fix this, I remove Portainer image and pull again with portainer/portainer-ce:sts image.

Use the following commands to stop then remove the current Portainer. Your other applications/containers will not be removed.


```
sudo docker stop portainer
```

```
sudo docker rm portainer
```

```
sudo docker pull portainer/portainer-ce:sts
```

```
docker run -d -p 9000:9000 -p 9443:9443 --name=portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:sts
```
______________

Docker è un programma per la gestione dei container

![Screenshot 2025-04-17 alle 11 53 53](https://github.com/user-attachments/assets/3ff60ecb-e294-44a7-8bc9-c0e94358c8c5)


```
docker -v

```


```
docker version

```
![Screenshot 2025-04-17 alle 12 08 35](https://github.com/user-attachments/assets/7d190c10-6c35-43e9-b212-4d21b41d1f67)


```
docker ps
```

Il comando `docker ps` è utilizzato per visualizzare i container Docker attualmente in esecuzione sul sistema. Quando esegui questo comando, ottieni un elenco dei container attivi, insieme a informazioni utili su ciascuno di essi. Ecco alcune delle informazioni che puoi vedere:

- **CONTAINER ID**: L'identificatore univoco del container.
- **IMAGE**: L'immagine Docker da cui è stato creato il container.
- **COMMAND**: Il comando che è stato eseguito all'interno del container.
- **CREATED**: Quando è stato creato il container.
- **STATUS**: Lo stato attuale del container (ad esempio, "up" se è in esecuzione).
- **PORTS**: Le porte esposte e il loro mapping tra il container e l'host.
- **NAMES**: Il nome assegnato al container.

Se desideri visualizzare anche i container che non sono in esecuzione (stati "stopped" o "exited"), puoi utilizzare l'opzione `-a` (o `--all`):

```bash
docker ps -a
```

Inoltre, ci sono altre opzioni che puoi utilizzare con `docker ps`, come:

- `-q`: Mostra solo gli ID dei container.
- `--filter`: Filtra i risultati in base a criteri specifici.


# Variabili d'ambiente 


Le Environment Variables (variabili d'ambiente) in Docker sono utilizzate per configurare il comportamento dei container al momento della loro esecuzione. Queste variabili possono essere utilizzate per passare informazioni al container, come configurazioni, credenziali, percorsi di file e altre impostazioni necessarie per l'applicazione in esecuzione all'interno del container.




___________________________________________________


# Principali comandi Docker


| Comando                | Significato                                                                                     |
|-----------------------|------------------------------------------------------------------------------------------------|
| `docker run`          | Crea ed esegue un container da un'immagine specificata.                                       |
| `docker ps`           | Elenca i container in esecuzione.                                                             |
| `docker ps -a`        | Elenca tutti i container, inclusi quelli non in esecuzione.                                   |
| `docker images`       | Mostra tutte le immagini disponibili localmente.                                             |
| `docker rmi`          | Rimuove un'immagine specificata.                                                               |
| `docker rm`           | Rimuove uno o più container.                                                                    |
| `docker exec`         | Esegue un comando all'interno di un container in esecuzione.                                   |
| `docker logs`         | Mostra i log di un container specificato.                                                      |
| `docker build`        | Costruisce un'immagine a partire da un Dockerfile.                                            |
| `docker pull`         | Scarica un'immagine da un registry (es. Docker Hub).                                          |
| `docker push`         | Carica un'immagine in un registry.                                                             |
| `docker network`      | Gestisce le reti Docker.                                                                        |
| `docker volume`       | Gestisce i volumi Docker per la persistenza dei dati.                                          |
| `docker-compose up`    | Avvia i servizi definiti in un file `docker-compose.yml`.                                     |
| `docker-compose down`  | Ferma e rimuove i container, le reti e i volumi definiti in un file `docker-compose.yml`.     |


## Esempio di utilizzo


| Comando                | Significato                                                                                     | Esempio                                                                                     |
|-----------------------|------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| `docker run`          | Crea ed esegue un container da un'immagine specificata.                                       | `docker run -d -p 80:80 nginx` <br> (Esegue un container Nginx in background sulla porta 80) |
| `docker ps`           | Elenca i container in esecuzione.                                                             | `docker ps` <br> (Mostra i container attivi)                                               |
| `docker ps -a`        | Elenca tutti i container, inclusi quelli non in esecuzione.                                   | `docker ps -a` <br> (Mostra tutti i container, attivi e non)                              |
| `docker images`       | Mostra tutte le immagini disponibili localmente.                                             | `docker images` <br> (Elenca tutte le immagini scaricate)                                 |
| `docker rmi`          | Rimuove un'immagine specificata.                                                               | `docker rmi nginx` <br> (Rimuove l'immagine Nginx)                                        |
| `docker rm`           | Rimuove uno o più container.                                                                    | `docker rm my_container` <br> (Rimuove il container chiamato "my_container")              |
| `docker exec`         | Esegue un comando all'interno di un container in esecuzione.                                   | `docker exec -it my_container /bin/bash` <br> (Apre una shell bash nel container "my_container") |
| `docker logs`         | Mostra i log di un container specificato.                                                      | `docker logs my_container` <br> (Mostra i log del container "my_container")               |
| `docker build`        | Costruisce un'immagine a partire da un Dockerfile.                                            | `docker build -t my_image .` <br> (Costruisce un'immagine chiamata "my_image" dalla directory corrente) |
| `docker pull`         | Scarica un'immagine da un registry (es. Docker Hub).                                          | `docker pull ubuntu` <br> (Scarica l'immagine Ubuntu dal Docker Hub)                      |
| `docker push`         | Carica un'immagine in un registry.                                                             | `docker push my_image` <br> (Carica l'immagine "my_image" nel registry configurato)      |
| `docker network`      | Gestisce le reti Docker.                                                                        | `docker network create my_network` <br> (Crea una rete chiamata "my_network")            |
| `docker volume`       | Gestisce i volumi Docker per la persistenza dei dati.                                          | `docker volume create my_volume` <br> (Crea un volume chiamato "my_volume")              |
| `docker-compose up`   | Avvia i servizi definiti in un file `docker-compose.yml`.                                     | `docker-compose up` <br> (Avvia i servizi definiti nel file `docker-compose.yml`)        |
| `docker-compose down` | Ferma e rimuove i container, le reti e i volumi definiti in un file `docker-compose.yml`.     | `docker-compose down` <br> (Ferma e rimuove i servizi definiti nel file `docker-compose.yml`) |

















