# 🚀 Despliegue local de sitio web estático con Minikube y Kubernetes

Este repositorio contiene un sitio web estático personalizado y los manifiestos necesarios para desplegarlo localmente usando Minikube y Kubernetes. El contenido del sitio se monta desde un volumen persistente.

## ✅ Requisitos

Antes de comenzar, asegurate de tener instalado lo siguiente:

- **Minikube**
- **Docker** (si usás `--driver=docker`)
- **Kubectl**
- **Git**

> 💡 Recomendación: usar Minikube 1.24.x o superior y Docker 20.x o superior.

---

## 🛠️ Pasos para ejecutar el entorno

### 1. Fork y clonación del repositorio

- Realicé un **fork** del repositorio original: [ewojjowe/static-website](https://github.com/ewojjowe/static-website)
- Cloné el repositorio forkeado en mi máquina:

```bash
git clone https://github.com/tu_usuario/static-website.git

2. Iniciar Minikube con volumen montado

minikube start --mount --mount-string="C:/Users/ruta_a/static-website:/mnt/web"
Esto monta el sitio web local en el path /mnt/web dentro del contenedor.

3. Aplicar los manifiestos de Kubernetes
Los manifiestos se encuentran en la carpeta K8s/Manifiestos_K8s, divididos por tipo:

cd "C:/Users/ruta_a/Manifiestos_K8s"

cd deployment
kubectl apply -f .

cd ../service
kubectl apply -f .

cd ../volume
kubectl apply -f .

4. Verificar el estado del pod

kubectl get pods
El pod debe estar en estado Running con READY 1/1.

5. Acceder al sitio

minikube service static-site-service
Esto abre el navegador con la URL del sitio web desplegado.

Eso es todo!
