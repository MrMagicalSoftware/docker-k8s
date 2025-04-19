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













