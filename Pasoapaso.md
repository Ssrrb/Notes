
---

## ✅ STEP 1: Set Up ClearML Server (Locally)

We'll use **Docker Compose** to run the ClearML Server locally.

### A. Create a directory:

```bash
mkdir clearml-server && cd clearml-server
```

### B. Download `docker-compose.yml` for ClearML Server:

```bash
curl -O https://raw.githubusercontent.com/allegroai/clearml-server/master/docker/docker-compose.yml
```



### C. Start ClearML Server:

```bash
docker-compose up -d
```

- Dashboard: [http://localhost:8080](http://localhost:8080)
- API Server: `http://localhost:8008`
- File Server: `http://localhost:8081`

---

## ✅ STEP 2: Set Up ClearML Agent

ClearML Agent is what runs your training jobs and reports to the server.

### A. Install ClearML & Agent (en el servidor local):

```bash
pip install clearml clearml-agent
```

### B. Configure ClearML:

```bash
clearml-init
```

It will ask for:

- ClearML Server API: `http://localhost:8008`
- Files Server: `http://localhost:8081`
- Web Server: `http://localhost:8080`

It will then store this in `~/.clearml.conf`

### C. Start ClearML Agent:

```bash
clearml-agent daemon --queue default
```

This will run a worker listening on the default queue.

---

## ✅ STEP 3: Set Up Jenkins in Docker (with Docker socket access)

### A. Create a Jenkins Docker Compose:

```bash
mkdir jenkins && cd jenkins
```

Create `docker-compose.yml`:

```yaml
version: '3.8'

services:
  jenkins:
    image: jenkins/jenkins:lts
    container_name: jenkins
    ports:
      - "8082:8080"
      - "50000:50000"
    volumes:
      - jenkins_home:/var/jenkins_home
      - /var/run/docker.sock:/var/run/docker.sock

volumes:
  jenkins_home:
```

### B. Start Jenkins:

```bash
docker-compose up -d
```

- Jenkins UI: [http://localhost:8082](http://localhost:8082)

On first login:

```bash
docker exec -it jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

---

## ✅ STEP 4: Install Jenkins Plugins (via UI)

Login to Jenkins and install:

- **Docker Pipeline**
- **Git**
- **GitLab Plugin** (optional if you want GitLab trigger)
- **Pipeline**

---

## ✅ STEP 5: Create a Jenkins Pipeline Job

Create a new **Pipeline** project and add a `Jenkinsfile` like:

```groovy
pipeline {
  agent {
    docker {
      image 'python:3.10'
    }
  }
  stages {
    stage('Install ClearML') {
      steps {
        sh 'pip install clearml clearml-agent'
      }
    }
    stage('Trigger ClearML Task') {
      steps {
        sh '''
        clearml-agent run \
          --project "MyProject" \
          --name "Experiment from Jenkins" \
          --script train.py \
          --queue default
        '''
      }
    }
  }
}
```

---

## ✅ Final Notes

- ✅ Jenkins uses Docker to isolate builds
- ✅ Jenkins calls `clearml-agent run`, which triggers a task on your **ClearML Agent**
- ✅ Agent runs jobs and logs them to **ClearML Server**
- ✅ Everything is local and works offline

---

Do you want:

- An example `train.py`?
- To add GitLab Webhook to trigger Jenkins on commit?
- To run multiple ClearML tasks (like grid search) automatically from Jenkins?

Let me know and I’ll walk you through it!