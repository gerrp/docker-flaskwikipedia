# Kubernetes con Helm y Actions
### Despliegue de infraestructura de kubernetes utilizando helm                                                                             
                                      
## Vagrant                                                                
Utilicé **vagrant** para la creación de la máquina virtual, en el **bootstrap.sh** instalé las siguientes dependencias necesarias:                                                 

**Docker**                                                                                                                       
                                                                                                                                                
**Kubectl**                                                                                                                   

**Minikube** 

**Helm** 

**ArgoCD** (GitOps)

Levantamos la máquina e instalamos las dependencias con ``` vagrant up 
                                           ```

Nos conectamos con ``` vagrant ssh
                                           ```
## Docker
Utilicé una aplicación web flask de wikipedia como base                       

## Github Actions
El workflow se activa con cualquier cambio dentro del directorio /docker, cumple los siguientes pasos:                                 
**Hadolint** (verifica las mejores prácticas del Dockerfile) -> **Build** -> **Trivy** (busca vulnerabilidades en la imagen creada) -> **Push a dockerhub**  

## Kubernetes
Implementé 3 recursos:                                      

**Namespace** (aislación de infraestructura)                              

**Deployment** (despliegue de aplicación)                                                 

**Nodeport** (red)

## Helm
Empaqueté los recursos anteriormente mencionados con distintas variables ( para la visualización o modificación de las mismas -> helm/chart/**values.yaml** )
                                                                                                            
Para la implementación vamos a necesitar tener levantado un **cluster** de **kubernetes**, utilizamos ``` minikube start ```

Instalamos el paquete de helm situandonos en **/helm** y utilizando ``` helm install wiki-helm ./chart ```

## Adicional - ArgoCD
Como paso adicional podemos hacer referencia a la infraestructura de **helm** subida en este repositorio por medio de **ArgoCD** (GitOps)
