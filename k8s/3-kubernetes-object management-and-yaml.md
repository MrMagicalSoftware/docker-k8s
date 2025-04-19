# k8s object Manageemnt and yaml manifests


![Screenshot 2025-04-16 alle 21 29 37](https://github.com/user-attachments/assets/84c2d42c-cc7e-4bc2-a1fc-ab1ab5f568a2)
![Screenshot 2025-04-16 alle 21 33 04](https://github.com/user-attachments/assets/4ce37aad-b77e-4eea-a7bc-8d50c18cef68)
![Screenshot 2025-04-16 alle 21 33 47](https://github.com/user-attachments/assets/742ee5e0-2bae-4880-860c-ebdde5c40d57)



La gestione degli oggetti in Kubernetes (K8s) è un aspetto fondamentale per il funzionamento e l'amministrazione delle applicazioni containerizzate. Kubernetes utilizza vari tipi di oggetti per rappresentare e gestire le risorse nel cluster. 

### Tipi di Oggetti Kubernetes

1. **Pod**: L'unità base di esecuzione in Kubernetes. Un pod può contenere uno o più container che condividono lo stesso spazio di rete e storage.

2. **Service**: Un oggetto che definisce un modo per accedere a uno o più pod. I servizi possono essere di tipo `ClusterIP`, `NodePort`, `LoadBalancer`, ecc.

3. **Deployment**: Un oggetto che gestisce la creazione e l'aggiornamento dei pod. I deployment garantiscono che il numero desiderato di repliche di un'applicazione sia in esecuzione.

4. **ReplicaSet**: Assicura che un numero specifico di repliche di un pod siano in esecuzione in un dato momento. I deployment utilizzano ReplicaSet per gestire i pod.

5. **StatefulSet**: Simile ai deployment, ma progettato per gestire applicazioni con stato, come database, che richiedono identificatori unici e persistenza.

6. **DaemonSet**: Assicura che un'istanza di un pod sia eseguita su ogni nodo del cluster o su un sottoinsieme di nodi.

7. **Job e CronJob**: Oggetti utilizzati per eseguire attività batch. Un Job esegue un pod fino al completamento, mentre un CronJob esegue un Job a intervalli regolari.

8. **ConfigMap e Secret**: Utilizzati per gestire la configurazione delle applicazioni. ConfigMap memorizza dati non sensibili, mentre Secret è progettato per dati sensibili come password e chiavi API.

### Gestione degli Oggetti Kubernetes

#### Creazione e Aggiornamento

- **YAML/JSON**: Gli oggetti Kubernetes sono generalmente definiti in file YAML o JSON. Puoi creare o aggiornare oggetti utilizzando il comando `kubectl apply`:

  ```bash
  kubectl apply -f file.yaml
  ```

- **kubectl create**: Puoi anche creare oggetti direttamente dalla riga di comando:

  ```bash
  kubectl create deployment nome-deployment --image=nome-immagine
  ```

#### Visualizzazione

- **kubectl get**: Per visualizzare gli oggetti nel cluster, puoi utilizzare:

  ```bash
  kubectl get pods
  kubectl get services
  kubectl get deployments
  ```

- **kubectl describe**: Per ottenere informazioni dettagliate su un oggetto specifico:

  ```bash
  kubectl describe pod nome-del-pod
  ```

#### Aggiornamento e Scalabilità

- **Aggiornamento**: Puoi aggiornare un deployment modificando il file YAML e rieseguendo `kubectl apply`, oppure utilizzando il comando `kubectl set image` per aggiornare l'immagine di un container.

- **Scalabilità**: Puoi scalare un deployment modificando il numero di repliche:

  ```bash
  kubectl scale deployment nome-deployment --replicas=3
  ```

#### Eliminazione

- **kubectl delete**: Per eliminare oggetti, puoi utilizzare:

  ```bash
  kubectl delete pod nome-del-pod
  kubectl delete service nome-del-service
  ```

### Monitoraggio e Logging

- **kubectl logs**: Per visualizzare i log di un pod:

  ```bash
  kubectl logs nome-del-pod
  ```

- **kubectl top**: Per monitorare l'utilizzo delle risorse:

  ```bash
  kubectl top pods
  ```

### Conclusione

La gestione degli oggetti in Kubernetes è essenziale per garantire che le applicazioni siano eseguite in modo efficiente e scalabile. Utilizzando i comandi `kubectl` e definendo correttamente gli oggetti nel tuo cluster, puoi gestire facilmente le tue applicazioni containerizzate. La comprensione di questi concetti ti aiuterà a sfruttare al meglio le potenzialità di Kubernetes.



![Screenshot 2025-04-16 alle 21 40 56](https://github.com/user-attachments/assets/a207bd8f-d711-48ae-80ac-0e11a0d12658)


![Screenshot 2025-04-16 alle 21 42 30](https://github.com/user-attachments/assets/d82d7d21-209b-40bb-95cb-3b20770d7e7b)




![Screenshot 2025-04-16 alle 21 44 53](https://github.com/user-attachments/assets/baf4b6fe-a0ab-48c7-8c7f-c1d1af9062f4)


I manifest file in Kubernetes sono file di configurazione che definiscono gli oggetti Kubernetes e le loro proprietà. Questi file sono generalmente scritti in formato YAML o JSON e vengono utilizzati per creare, aggiornare e gestire le risorse nel cluster Kubernetes. I manifest file sono fondamentali per l'infrastruttura come codice (IaC), poiché consentono di versionare e gestire la configurazione delle applicazioni in modo sistematico.

I manifest file sono uno strumento potente per gestire le risorse in Kubernetes. Ti permettono di definire in modo chiaro e ripetibile le configurazioni delle tue applicazioni e di gestire l'infrastruttura in modo efficiente. Utilizzando i manifest file, puoi implementare pratiche di DevOps e Continuous Integration/Continuous Deployment (CI/CD) nel tuo flusso di lavoro.


### Struttura di un Manifest File

Un manifest file tipico in Kubernetes ha una struttura che include le seguenti sezioni:

1. **apiVersion**: Specifica la versione dell'API Kubernetes da utilizzare per l'oggetto.
2. **kind**: Indica il tipo di oggetto Kubernetes (ad esempio, Pod, Deployment, Service, ecc.).
3. **metadata**: Contiene informazioni di identificazione come il nome, il namespace e le etichette.
4. **spec**: Definisce le specifiche dell'oggetto, come i container, le porte, le risorse, ecc.

### Esempi di Manifest File

#### 1. Manifest di un Pod

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: my-app
spec:
  containers:
  - name: my-container
    image: nginx:latest
    ports:
    - containerPort: 80
```

#### 2. Manifest di un Deployment

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
      - name: my-container
        image: nginx:latest
        ports:
        - containerPort: 80
```

#### 3. Manifest di un Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  type: NodePort
  selector:
    app: my-app
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30001
```

#### 4. Manifest di un ConfigMap

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: my-config
data:
  key1: value1
  key2: value2
```

#### 5. Manifest di un Secret

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: my-secret
type: Opaque
data:
  username: dXNlcm5hbWU=  # "username" in base64
  password: cGFzc3dvcmQ=  # "password" in base64
```

### Applicare i Manifest File

Per applicare un manifest file e creare o aggiornare le risorse nel cluster, utilizza il comando `kubectl apply`:

```bash
kubectl apply -f nome-del-file.yaml
```

### Visualizzare e Gestire le Risorse

Dopo aver applicato i manifest file, puoi visualizzare le risorse create utilizzando i seguenti comandi:

- Per visualizzare i pod:

  ```bash
  kubectl get pods
  ```

- Per visualizzare i deployment:

  ```bash
  kubectl get deployments
  ```

- Per visualizzare i servizi:

  ```bash
  kubectl get services
  ```



_________________________________



# ESERCITAZIONE

<img width="1482" alt="Screenshot 2025-04-19 alle 10 10 28" src="https://github.com/user-attachments/assets/a192aee9-6c1d-42a7-b853-a8cc027feb88" />



```
kubectl create -f nginx-pod.yaml
```

Vedremo che ha creato un nuovo pod :

```
kubectl get pods
kubectl describe pod nginx-pod
```

Proseguiamo la nostra esercitazione e creami un file di configurazione service











<img width="1488" alt="Screenshot 2025-04-19 alle 10 21 43" src="https://github.com/user-attachments/assets/c307d83d-639f-40a7-9f36-7b461b8a1c7c" />

<img width="1486" alt="Screenshot 2025-04-19 alle 10 22 13" src="https://github.com/user-attachments/assets/9121ed19-eb1d-4aad-a100-74c70c1b2b65" />


```
kubectl create -f nginx-svc.yaml
kubectl get services
```

<img width="1461" alt="Screenshot 2025-04-19 alle 10 26 50" src="https://github.com/user-attachments/assets/1faffa52-f1d9-4744-89cd-9360b3782720" />


__________________________________



## Hands-On Generating Kubernetes Manifests with kubectl

I manifesti sono file di configurazione in formato YAML o JSON che definiscono le risorse da creare e gestire nel cluster.

### Spiegazione

1. **Cosa sono i manifesti Kubernetes?**
   - I manifesti sono file che descrivono le risorse Kubernetes, come Pod, Service, Deployment, ConfigMap, ecc. Questi file contengono tutte le informazioni necessarie per creare e gestire le risorse nel cluster.

2. **Utilizzo di `kubectl` per generare manifesti:**
   - `kubectl` offre comandi per generare manifesti a partire da risorse esistenti o per creare nuovi manifesti da zero.

### Esempi

1. **Generare un manifesto per un Pod:**
   Puoi generare un manifesto per un Pod utilizzando il comando `kubectl run`. Ad esempio:
   ```bash
   kubectl run my-pod --image=nginx --dry-run=client -o yaml
   ```
   Questo comando crea un manifesto YAML per un Pod chiamato `my-pod` che utilizza l'immagine `nginx`, senza effettivamente creare il Pod (`--dry-run=client`).

2. **Generare un manifesto per un Deployment:**
   Puoi generare un manifesto per un Deployment con il comando `kubectl create deployment`. Ad esempio:
   ```bash
   kubectl create deployment my-deployment --image=nginx --dry-run=client -o yaml
   ```
   Questo comando genera un manifesto YAML per un Deployment chiamato `my-deployment`.

3. **Generare un manifesto per un Service:**
   Puoi generare un manifesto per un Service utilizzando il comando `kubectl expose`. Ad esempio:
   ```bash
   kubectl expose deployment my-deployment --port=80 --target-port=80 --type=LoadBalancer --dry-run=client -o yaml
   ```
   Questo comando crea un manifesto YAML per un Service che espone il Deployment `my-deployment`.

4. **Modificare un manifesto esistente:**
   Se hai già un manifesto YAML e desideri modificarlo, puoi utilizzare `kubectl edit`. Ad esempio:
   ```bash
   kubectl edit deployment my-deployment
   ```
   Questo comando apre il manifesto del Deployment in un editor di testo, consentendoti di apportare modifiche.

5. **Salvare un manifesto esistente:**
   Puoi anche esportare un manifesto esistente in un file YAML utilizzando il comando `kubectl get`. Ad esempio:
   ```bash
   kubectl get deployment my-deployment -o yaml > my-deployment.yaml
   ```
   Questo comando salva il manifesto del Deployment `my-deployment` in un file chiamato `my-deployment.yaml`.

6. **Creare un ConfigMap:**
   Puoi generare un ConfigMap utilizzando il comando `kubectl create configmap`. Ad esempio:
   ```bash
   kubectl create configmap my-config --from-literal=key1=value1 --dry-run=client -o yaml
   ```
   Questo comando genera un manifesto YAML per un ConfigMap chiamato `my-config` con una chiave `key1` e valore `value1`.


________________

## Comando kubectl apply


`kubectl apply` è un comando fondamentale nell'interfaccia a riga di comando di Kubernetes (`kubectl`) che consente di applicare configurazioni a risorse nel cluster Kubernetes. Questo comando è utilizzato per creare o aggiornare risorse in base a un manifesto YAML o JSON fornito.

### Funzionamento di `kubectl apply`

1. **Creazione e Aggiornamento:**
   - Quando utilizzi `kubectl apply`, Kubernetes confronta lo stato attuale della risorsa nel cluster con la configurazione specificata nel manifesto. Se la risorsa non esiste, `kubectl apply` la crea. Se esiste già, `kubectl apply` aggiorna la risorsa per riflettere le modifiche nel manifesto.

2. **Gestione dello Stato Desiderato:**
   - `kubectl apply` è progettato per gestire lo stato desiderato delle risorse. Puoi modificare il manifesto e rieseguire il comando per applicare le modifiche, e Kubernetes si occuperà di aggiornare solo le parti necessarie della risorsa.

3. **Strategia di Merge:**
   - Quando si applicano modifiche, `kubectl apply` utilizza una strategia di merge per unire le modifiche nel manifesto con lo stato attuale della risorsa. Questo è particolarmente utile per le risorse che possono avere più campi o configurazioni.

### Sintassi

La sintassi di base per utilizzare `kubectl apply` è la seguente:

```bash
kubectl apply -f <file.yaml>
```

Dove `<file.yaml>` è il percorso del file di configurazione che contiene il manifesto della risorsa.

### Esempi

1. **Creare una risorsa:**
   Supponiamo di avere un file chiamato `deployment.yaml` che definisce un Deployment. Puoi creare il Deployment eseguendo:
   ```bash
   kubectl apply -f deployment.yaml
   ```

2. **Aggiornare una risorsa esistente:**
   Se successivamente modifichi `deployment.yaml` (ad esempio, cambiando l'immagine del container) e riesegui il comando:
   ```bash
   kubectl apply -f deployment.yaml
   ```
   Kubernetes aggiornerà il Deployment esistente per riflettere le modifiche.

3. **Applicare più file:**
   Puoi anche applicare più file contemporaneamente. Ad esempio, se hai più manifesti in una directory, puoi eseguire:
   ```bash
   kubectl apply -f ./manifests/
   ```
   Questo applicherà tutti i file YAML nella directory `manifests`.

4. **Applicare risorse da stdin:**
   Puoi anche applicare risorse direttamente da stdin. Ad esempio:
   ```bash
   echo "apiVersion: v1\nkind: Pod\nmetadata:\n  name: my-pod\nspec:\n  containers:\n  - name: nginx\n    image: nginx" | kubectl apply -f -
   ```

### Vantaggi di `kubectl apply`

- **Idempotenza:** Puoi eseguire `kubectl apply` più volte senza preoccuparti di creare duplicati o di causare errori, poiché il comando gestisce automaticamente le differenze tra lo stato attuale e quello desiderato.
- **Facilità di gestione:** È facile tenere traccia delle modifiche apportate alle risorse, poiché puoi semplicemente modificare il file di configurazione e rieseguire il comando.
- **Supporto per il controllo delle versioni:** Puoi utilizzare strumenti di controllo delle versioni (come Git) per gestire i tuoi file di configurazione, facilitando la collaborazione e il tracciamento delle modifiche.









