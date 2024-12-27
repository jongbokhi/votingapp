### Voting Application Deployment

This project deploys a multi-component voting application using Kubernetes, consisting of the following services:

#### **Redis**  
- **Image**: `redis:latest`  
- **Port**: `6379`  

#### **Postgres**  
- **Image**: `postgres:9.4`  
- **Port**: `5432`  
- **Environment Variables**:  
  - `POSTGRES_USER=postgres`  
  - `POSTGRES_PASSWORD=postgres`  

#### **Worker**  
- **Image**: `ghcr.io/subicura/voting/worker:latest`  
- **Environment Variables**:  
  - `REDIS_HOST=[redis ip]`  
  - `REDIS_PORT=[redis port]`  
  - `POSTGRES_HOST=[postgres ip]`  
  - `POSTGRES_PORT=[postgres port]`  

#### **Vote**  
- **NodePort**: `31000`  
- **Image**: `ghcr.io/subicura/voting/vote:latest`  
- **Port**: `80`  
- **Environment Variables**:  
  - `REDIS_HOST=[redis ip]`  
  - `REDIS_PORT=[redis port]`  

#### **Result**  
- **NodePort**: `31001`  
- **Image**: `ghcr.io/subicura/voting/result:latest`  
- **Port**: `80`  
- **Environment Variables**:  
  - `POSTGRES_HOST=[postgres ip]`  
  - `POSTGRES_PORT=[postgres port]`  
