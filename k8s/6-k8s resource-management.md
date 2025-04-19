# Kubernetes resource Management


<img width="1432" alt="Screenshot 2025-04-19 alle 14 10 33" src="https://github.com/user-attachments/assets/72c6ec24-7fe1-4231-b501-ef9a6eaa4e14" />

<img width="1342" alt="Screenshot 2025-04-19 alle 14 11 07" src="https://github.com/user-attachments/assets/f520a362-9223-43d5-bd2e-0e44dc445a68" />


<img width="923" alt="Screenshot 2025-04-19 alle 14 26 22" src="https://github.com/user-attachments/assets/e8ddd2c9-85ee-450e-87d4-0a718e8bb5dd" />


In Kubernetes, le **labels** e i **selectors** sono concetti fondamentali utilizzati per organizzare, gestire e selezionare risorse nel cluster. Questi strumenti consentono di raggruppare e filtrare le risorse in modo efficiente, facilitando la gestione delle applicazioni e delle loro configurazioni.

### Labels

#### Cosa sono le Labels?

Le **labels** sono coppie chiave-valore associate a risorse Kubernetes (come Pod, Service, Deployment, ReplicaSet, ecc.). Le labels forniscono un modo per identificare e categorizzare le risorse in base a criteri specifici.

#### Caratteristiche delle Labels:

1. **Flessibilità:** Le labels possono essere utilizzate per qualsiasi scopo, come identificare l'ambiente (sviluppo, test, produzione), il team responsabile, la versione dell'applicazione, ecc.
  
2. **Multi-Valore:** Una risorsa può avere più labels, consentendo di categorizzarla in diversi modi.

3. **Non Uniche:** Le labels non devono essere uniche. Più risorse possono avere la stessa label.

#### Esempio di Labels:

Ecco un esempio di come definire le labels in un manifesto YAML per un Pod:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  labels:
    app: my-app
    environment: production
    version: v1
spec:
  containers:
  - name: nginx
    image: nginx
```

In questo esempio, il Pod `my-pod` ha tre labels: `app`, `environment` e `version`.

### Selectors

#### Cosa sono i Selectors?

I **selectors** sono utilizzati per filtrare e selezionare risorse in base alle labels. I selectors consentono di specificare criteri per identificare un insieme di risorse che corrispondono a determinate labels.

#### Tipi di Selectors:

1. **Equality-based Selectors:** Permettono di selezionare risorse in base all'uguaglianza delle labels. Ad esempio, `app=my-app` selezionerà tutte le risorse con la label `app` impostata su `my-app`.

2. **Set-based Selectors:** Permettono di selezionare risorse in base a un insieme di valori. Ad esempio, `environment in (production, staging)` selezionerà tutte le risorse con la label `environment` impostata su `production` o `staging`.

#### Esempio di Selectors:

I selectors sono comunemente utilizzati nei manifesti di risorse come i Service e i Deployment. Ecco un esempio di un Service che utilizza un selector per selezionare i Pod:

```yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
    environment: production
  ports:
    - port: 80
      targetPort: 80
```

In questo esempio, il Service `my-service` utilizza un selector per selezionare tutti i Pod che hanno le labels `app=my-app` e `environment=production`. Il Service inoltrerà il traffico a questi Pod.

### Vantaggi di Labels e Selectors

1. **Organizzazione:** Le labels consentono di organizzare le risorse in modo logico, facilitando la gestione delle applicazioni.

2. **Selezione Dinamica:** I selectors consentono di selezionare dinamicamente le risorse in base a criteri specifici, rendendo più facile il bilanciamento del carico, la gestione delle versioni e l'implementazione di strategie di rollout.

3. **Flessibilità:** Puoi modificare le labels delle risorse senza dover cambiare la configurazione delle applicazioni, consentendo una gestione più agile delle risorse.

<img width="1441" alt="Screenshot 2025-04-19 alle 14 30 50" src="https://github.com/user-attachments/assets/930b32c5-5804-47db-997d-541a5624d522" />

<img width="1427" alt="Screenshot 2025-04-19 alle 14 31 55" src="https://github.com/user-attachments/assets/a6ccf105-0781-4567-8ba4-676e8a9f50ba" />

<img width="1436" alt="Screenshot 2025-04-19 alle 14 33 46" src="https://github.com/user-attachments/assets/b3f18a6f-b4ee-4c9f-810a-0a847cd0b1d0" />






