
# README - Tienda Perritos 🐶

## Descripción del Proyecto

Tienda Perritos es una aplicación web desarrollada con arquitectura distribuida utilizando:

- Frontend React
- Backend Node.js + Express
- Base de datos MySQL
- Docker
- GitHub
- AWS EC2
- Amazon ECR
- GitHub Actions

El objetivo del proyecto fue desplegar una arquitectura de 3 capas en AWS utilizando contenedores Docker y automatización CI/CD.

## Arquitectura del Proyecto

### Componentes

| Servicio | Tecnología | Tipo |
|---|---|---|
| Frontend | React | Pública |
| Backend | Node.js + Express | Privada |
| Base de Datos | MySQL | Privada |

## Arquitectura AWS

### EC2 utilizadas

| Instancia | Tipo | Acceso |
|---|---|---|
| frontend-tienda | EC2 Pública | Internet |
| backend-tienda | EC2 Privada | Solo Frontend |
| db-tienda | EC2 Privada | Solo Backend |

## Flujo de conexión

Usuario
↓
Frontend React (EC2 Pública)
↓
Backend Node.js (EC2 Privada)
↓
MySQL Database (EC2 Privada)

## Tecnologías utilizadas

### Frontend
- React
- Axios
- Vite

### Backend
- Node.js
- Express
- mysql2
- dotenv
- cors

### Base de Datos
- MySQL 8

### DevOps
- Docker
- Docker Hub / Amazon ECR
- GitHub
- GitHub Actions
- AWS EC2
- AWS VPC

## Configuración AWS

### Creación de VPC

CIDR:
10.0.0.0/16

### Subredes

- subnet-public-front → 10.0.1.0/24
- subnet-private-back → 10.0.2.0/24
- subnet-private-db → 10.0.3.0/24

## Security Groups

### Frontend
- SSH 22
- HTTP 80
- HTTPS 443

### Backend
- SSH 22
- Puerto 3001

### Database
- Puerto 3306

## Configuración GitHub

### Inicializar repositorio

git init

### Agregar archivos

git add .

### Crear commit

git commit -m "Primer commit"

### Conectar repositorio remoto

git remote add origin URL_DEL_REPOSITORIO

### Cambiar rama principal

git branch -M main

### Subir código

git push -u origin main

## Dockerización

### Backend

docker build -t tienda-backend .

docker run -d -p 3001:3001 --name backend tienda-backend

### Frontend

docker build -t tienda-frontend .

docker run -d -p 80:80 --name frontend tienda-frontend

### Base de Datos

docker run -d --name mysql-db -p 3306:3306 -e MYSQL_ROOT_PASSWORD=admin123 mysql:8

## Amazon ECR

### Login

aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin AWS_ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com

### Push imagen

docker push AWS_ACCOUNT_ID.dkr.ecr.us-east-1.amazonaws.com/tienda-backend:latest

## GitHub Actions

### Flujo CI/CD

Push GitHub
↓
GitHub Actions
↓
Build Docker
↓
Push ECR
↓
EC2 descarga nueva imagen
↓
Docker levanta contenedor actualizado

## Variables de Entorno

DB_HOST=10.0.x.x
DB_USER=root
DB_PASSWORD=admin123
DB_NAME=tienda_perritos
DB_PORT=3306

## Resultado Final

 Frontend desplegado en EC2 pública
 Backend desplegado en EC2 privada
 Base de datos MySQL privada
 Arquitectura segura por capas
 Docker funcionando correctamente
 Integración con Amazon ECR
 GitHub Actions automatizado

## Integrantes

- Dangelo Javier Lopez Vera

## Conclusión

El proyecto permitió implementar una arquitectura cloud moderna utilizando herramientas DevOps y servicios AWS.
