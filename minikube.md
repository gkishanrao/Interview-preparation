# minikube created for deployment into Kubernetes

https://github.com/kubernetes/minikube/releases/tag/v1.36.0

      minikube-windows-amd64.exe

Env: C:\Users\gkish\Minikube


cmd> minikube start –driver=docker   or minikube start –driver=hyperkit

      > minikube status

                  minikube
                  
                  type: Control Plane
                  host: Running
                  kubelet: Running
                  apiserver: Running
                  kubeconfig: Configured
                  >kubectl cluster-info
                  Kubernetes control plane is running at https://127.0.0.1:57480
                  CoreDNS is running at https://127.0.0.1:57480/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

> kubectl get node
          
          NAME       STATUS   ROLES           AGE     VERSION
          minikube   Ready    control-plane   4m29s   v1.33.1


> minikube docker-env
            
            SET DOCKER_TLS_VERIFY=1
            SET DOCKER_HOST=tcp://127.0.0.1:57477
            SET DOCKER_CERT_PATH=C:\Users\gkish\.minikube\certs
            SET MINIKUBE_ACTIVE_DOCKERD=minikube
            REM To point your shell to minikube's docker-daemon, run:
            REM @FOR /f "tokens=*" %i IN ('minikube -p minikube docker-env --shell cmd') DO @%i

C:\Users\xxx> @FOR /f "tokens=*" %i IN ('minikube -p minikube docker-env --shell cmd') DO @%i

>docker images
            
            REPOSITORY                                TAG        IMAGE ID       CREATED         SIZE
            registry.k8s.io/kube-apiserver            v1.33.1    c6ab243b29f8   2 months ago    102MB
            registry.k8s.io/kube-controller-manager   v1.33.1    ef43894fa110   2 months ago    94.6MB
            registry.k8s.io/kube-scheduler            v1.33.1    398c985c0d95   2 months ago    73.4MB
            registry.k8s.io/kube-proxy                v1.33.1    b79c189b052c   2 months ago    97.9MB
            registry.k8s.io/etcd                      3.5.21-0   499038711c08   3 months ago    153MB
            registry.k8s.io/coredns/coredns           v1.12.0    1cf5f116067c   7 months ago    70.1MB
            registry.k8s.io/pause                     3.10       873ed7510279   13 months ago   736kB
            gcr.io/k8s-minikube/storage-provisioner   v5         6e38f40d628d   4 years ago     31.5MB

cmd>docker build -t spring-k8s-demo:1.0 .
          
          
          Verify the created images
          Cmd>docker images
          REPOSITORY                                TAG        IMAGE ID       CREATED          SIZE
          spring-k8s-demo                           1.0        96767569dea1   23 seconds ago   492MB


C:\Users\xxx\Workspace\springboot-ecr-eks-deploy>kubectl create deployment springboot-k8s --image=spring-k8s-demo:1.0 --port=8080

deployment.apps/springboot-k8s created


>kubectl describe  deployment springboot-k8s-demo
          
          >kubectl get pods
          NAME                                  READY   STATUS    RESTARTS       AGE
          springboot-k8s-demo-856955d66-jx9hn   1/1     Running   0              6m27s


C:\Users\gkish\Workspace\springboot-ecr-eks-deploy>kubectl logs springboot-k8s-demo-856955d66-jx9hn

>kubectl get deployment –o wide
        
        NAME                  READY   UP-TO-DATE   AVAILABLE   AGE
        springboot-k8s-demo   1/1     1            1           78m


> kubectl expose deployment springboot-k8s-demo --type=NodePort

service/springboot-k8s-demo exposed

          >minikube service springboot-k8s-demo –url
          http://127.0.0.1:59261

 >minikube dashboard
                
                > kubectl delete service springboot-k8s-demo
                
                >kubectl delete deployment springboot-k8s-demo


> minikube stop
      
      * 1 node stopped

Service Types in Kubernetes
            
            Nodeport
            ClusterIp
            LoadBalancer

# Ingress

minikube addons enable ingress
<img width="1102" height="650" alt="image" src="https://github.com/user-attachments/assets/d10caad8-4e94-4158-93f4-0359ebd08bed" />


<img width="766" height="735" alt="image" src="https://github.com/user-attachments/assets/476cf904-27c1-492d-aa42-338b522bf101" />

<img width="501" height="667" alt="image" src="https://github.com/user-attachments/assets/d1ca7ecb-6730-433a-b56d-8d594778824f" />

