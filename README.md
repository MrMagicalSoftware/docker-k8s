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
docker volume create portainer_data
```
```
docker run -d -p 8000:8000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer-ce:lts
```



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











