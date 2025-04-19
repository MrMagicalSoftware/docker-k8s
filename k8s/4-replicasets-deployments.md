# Replica Sets and Deployments


<img width="1455" alt="Screenshot 2025-04-19 alle 11 20 31" src="https://github.com/user-attachments/assets/1a346361-12f1-4ec3-b61d-fae9b10d14d2" />
<img width="1455" alt="Screenshot 2025-04-19 alle 11 24 18" src="https://github.com/user-attachments/assets/aac57419-b21d-4513-a5dc-8fd951ac232b" />
<img width="1408" alt="Screenshot 2025-04-19 alle 11 25 42" src="https://github.com/user-attachments/assets/e4812c1c-26d6-4b0e-8ed8-ca072dfbab32" />








In Kubernetes, i **ReplicaSet** e i **Deployment** sono due risorse fondamentali utilizzate per gestire la scalabilità e la disponibilità delle applicazioni. Sebbene abbiano scopi simili, ci sono differenze chiave tra di loro. Ecco una panoramica di entrambi.

### ReplicaSet

#### Cos'è un ReplicaSet?

Un **ReplicaSet** è una risorsa di Kubernetes che garantisce che un numero specifico di repliche di un Pod siano in esecuzione in un dato momento. Se un Pod fallisce o viene terminato, il ReplicaSet crea automaticamente un nuovo Pod per sostituirlo, mantenendo così il numero desiderato di repliche.

#### Caratteristiche principali:

- **Scalabilità:** Puoi specificare il numero di repliche desiderate, e il ReplicaSet si occuperà di mantenere quel numero.
- **Selezione dei Pod:** Utilizza un selettore di etichette per identificare quali Pod gestire.
- **Semplicità:** È una risorsa più semplice rispetto ai Deployment, ma non offre funzionalità avanzate come il rollout e il rollback.

#### Esempio di un ReplicaSet:

Ecco un esempio di manifesto YAML per un ReplicaSet:

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: my-replicaset
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: nginx
        image: nginx
```

Puoi applicare questo manifesto con:

```bash
kubectl apply -f replicaset.yaml
```

### Deployment

#### Cos'è un Deployment?

Un **Deployment** è una risorsa di Kubernetes che gestisce la creazione e l'aggiornamento di ReplicaSet e, di conseguenza, dei Pod. I Deployment offrono funzionalità avanzate per il controllo delle versioni, il rollout e il rollback delle applicazioni.

#### Caratteristiche principali:

- **Gestione dei ReplicaSet:** Un Deployment crea e gestisce uno o più ReplicaSet, consentendo di aggiornare le applicazioni in modo sicuro.
- **Rollout e Rollback:** Puoi aggiornare un Deployment per modificare l'immagine del container o altre configurazioni, e Kubernetes gestirà il rollout delle nuove versioni. Se qualcosa va storto, puoi facilmente eseguire un rollback alla versione precedente.
- **Strategie di Aggiornamento:** Supporta diverse strategie di aggiornamento, come il rolling update e il recreate.

#### Esempio di un Deployment:

esempio di manifesto YAML per un Deployment:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: nginx
        image: nginx:latest
```

Puoi applicare questo manifesto con:

```bash
kubectl apply -f deployment.yaml
```

### Differenze tra ReplicaSet e Deployment

| Caratteristica         | ReplicaSet                          | Deployment                          |
|------------------------|------------------------------------|-------------------------------------|
| Scopo                  | Mantiene un numero fisso di repliche di Pod | Gestisce ReplicaSet e fornisce funzionalità di rollout e rollback |
| Aggiornamenti          | Non supporta aggiornamenti automatici | Supporta aggiornamenti rolling e rollback |
| Complessità            | Più semplice, ma meno flessibile   | Più complesso, ma offre più funzionalità |
| Utilizzo               | Usato raramente direttamente; di solito tramite Deployment | Usato per gestire applicazioni in produzione |



_______________________________________


# Hands on Creating and Managing ReplicaSets


```
kubectl get pods
kubectl get svc

```

<img width="1471" alt="Screenshot 2025-04-19 alle 11 28 37" src="https://github.com/user-attachments/assets/92ba251c-73a4-4dc7-9559-933997eda528" />


<img width="1484" alt="Screenshot 2025-04-19 alle 11 30 43" src="https://github.com/user-attachments/assets/10f24ba6-4163-490d-8ee6-9b050ac551c6" />



```
kubectl apply -f nginx-rs.yaml
```

<img width="1477" alt="Screenshot 2025-04-19 alle 11 32 38" src="https://github.com/user-attachments/assets/72226784-2b8b-47b7-812f-f2b22e3109a0" />


```
kubectl get rs
```

Il comando kubectl get rs è utilizzato per elencare i ReplicaSet (abbreviato come "rs") presenti nel cluster Kubernetes. I ReplicaSet sono risorse che garantiscono che un numero specifico di repliche di un Pod siano in esecuzione in un dato momento. Utilizzando questo comando, puoi ottenere informazioni sui ReplicaSet attualmente gestiti dal tuo cluster.


    NAME: Il nome del ReplicaSet.
    DESIRED: Il numero di repliche desiderate.
    CURRENT: Il numero attuale di repliche in esecuzione.
    READY: Il numero di repliche pronte per ricevere traffico.
    AGE: Il tempo trascorso dalla creazione del ReplicaSet.


_________________________________________________________________________


![Screenshot 2025-04-19 alle 11 43 50](https://github.com/user-attachments/assets/bc0baea8-1a7d-4ada-a08b-d4739d9eb36d)


![Screenshot 2025-04-19 alle 11 46 43](https://github.com/user-attachments/assets/29e0dbe9-eaeb-44dc-ad8c-c8b6e4338ca1)

![Screenshot 2025-04-19 alle 11 48 50](https://github.com/user-attachments/assets/09b2da04-8758-4f0d-afc7-05d1962bf573)

![Screenshot 2025-04-19 alle 11 49 37](https://github.com/user-attachments/assets/da7d5436-6d7f-4fb8-ae1c-33bbcb6c2990)
![Screenshot 2025-04-19 alle 11 49 55](https://github.com/user-attachments/assets/da3c440e-8d9c-4fcd-a7cd-ba1d0b998955)
![Screenshot 2025-04-19 alle 11 50 20](https://github.com/user-attachments/assets/b0333653-71bd-4286-9d97-ed976c298d68)
![Screenshot 2025-04-19 alle 11 50 40](https://github.com/user-attachments/assets/06ea4274-5c4a-4efa-9f43-bd07c11ecc08)


___________________________________________


# Hands on creating and managing Deployments



Creare e gestire i **Deployment** in Kubernetes è un'attività fondamentale per garantire che le applicazioni siano scalabili, aggiornabili e resilienti. 

### 1. Creazione di un Deployment

#### Passo 1: Creare un Manifesto YAML

creiamo un file YAML per definire un Deployment. utilizziamo un editor di testo per creare un file chiamato `deployment.yaml` con il seguente contenuto:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

In questo esempio, stiamo creando un Deployment chiamato `my-deployment` che esegue 3 repliche di un Pod con un container Nginx.

#### Passo 2: Applicare il Manifesto

Per creare il Deployment nel cluster :

```bash
kubectl apply -f deployment.yaml
```

#### Passo 3: Verificare il Deployment

verificare che il Deployment sia stato creato correttamente :

```bash
kubectl get deployments
```

output simile a questo:

```
NAME            READY   UP-TO-DATE   AVAILABLE   AGE
my-deployment   3/3     3            3           1m
```

### 2. Aggiornare un Deployment

#### Passo 1: Modificare il Manifesto

Supponiamo di voler aggiornare l'immagine del container a una versione specifica. Modifica il file `deployment.yaml` per cambiare l'immagine:

```yaml
      containers:
      - name: nginx
        image: nginx:1.21.0  # Aggiornato a una versione specifica
```

#### Passo 2: Applicare le Modifiche

Eseguire nuovamente il comando `kubectl apply`:

```bash
kubectl apply -f deployment.yaml
```

#### Passo 3: Verificare l'Aggiornamento

controllare lo stato del Deployment e vedere se l'aggiornamento è stato applicato correttamente:

```bash
kubectl rollout status deployment/my-deployment
```

### 3. Rollback di un Deployment

Se l'aggiornamento ha causato problemi, puoi eseguire un rollback al Deployment precedente.

#### Passo 1: Eseguire il Rollback

Per eseguire un rollback, utilizza il comando:

```bash
kubectl rollout undo deployment/my-deployment
```

#### Passo 2: Verificare il Rollback

controlliamo lo stato del Deployment per assicurarti che sia tornato alla versione precedente:

```bash
kubectl get deployments
```

### 4. Scalare un Deployment

Puoi facilmente scalare il numero di repliche di un Deployment.

#### Passo 1: Scalare il Deployment

Per aumentare il numero di repliche a 5, esegui:

```bash
kubectl scale deployment my-deployment --replicas=5
```

#### Passo 2: Verificare il Nuovo Numero di Repliche

Controlla il numero di repliche attive:

```bash
kubectl get deployments
```

### 5. Eliminare un Deployment

Se si desira eliminare il Deployment, puoi farlo con il seguente comando:

```bash
kubectl delete deployment my-deployment
```











______________________________________________
















