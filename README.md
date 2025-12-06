# Renter Easy API – Kubernetes Deployment

![Kubernetes](https://img.shields.io/badge/Kubernetes-1.28-blue?logo=kubernetes)
![NodePort](https://img.shields.io/badge/Service-NodePort-green)
![ClusterIP](https://img.shields.io/badge/Service-ClusterIP-brightgreen)
![ConfigMap](https://img.shields.io/badge/ConfigMap-Enabled-orange)
![Status](https://img.shields.io/badge/Status-Working-success)

Este repositório contém os manifests Kubernetes para subir a aplicação **Renter Easy API** e seu banco de dados MySQL em um cluster Kubernetes.

---

## ✅ Objetivo
- **Pods** para execução dos containers.
- **Services**:
  - **ClusterIP** para comunicação interna entre API e banco.
  - **NodePort** para expor a API externamente.
- **ConfigMap** para gerenciamento de variáveis de configuração.
- **ReplicaSet** objeto que garante que um número específico de réplicas de um Pod esteja sempre em execução
- **Deployment** Camada acima do ReplicaSet que gerencia versionamento

---

## 🏗 Arquitetura
<img width="1536" height="1024" alt="Image" src="https://github.com/user-attachments/assets/9df921b4-57f4-4ee8-8102-e291c1724656" />

---

## 📂 Estrutura do Projeto
```
.
├── app/
│   ├── renter-easy-api-pod.yaml
│   ├── renter-easy-api-svc.yaml
│   └── renter-easy-api-cm.yaml
│   └── renter-easy-api-dp.yaml
└── database/
    ├── db-renter-easy-api-pod.yaml
    ├── db-renter-easy-api-svc.yaml
    └── db-renter-easy-cm.yaml
    └── db-renter-easy-pd.yaml
```

---

## 🔗 Imagens Utilizadas
- **API**: [gordinhodo/renter-easy-api:latest](https://hub.docker.com/r/gordinhodo/renter-easy-api)
- **Banco de Dados**: [mysql:latest](https://hub.docker.com/_/mysql)

---

## 🚀 Como aplicar os manifests
1. Clone este repositório:
  git clone [ https://github.com/seu-usuario/renter-easy-k8s.git](https://github.com/RafaelSilva-si/renter-easy-api-kubernete)
  cd renter-easy-api-kubernete


2. Aplique os ConfigMaps:
  kubectl apply -f app/renter-easy-api-cm.yaml
  kubectl apply -f database/db-renter-easy-cm.yaml

<!-- Não precisa, pois agora rodamos com deployments -->
<!-- 3. Aplique os Pods:
  kubectl apply -f app/renter-easy-api-pod.yaml
  kubectl apply -f database/db-renter-easy-api-pod.yaml -->


4. Aplique os Services:
  kubectl apply -f app/renter-easy-api-svc.yaml
  kubectl apply -f database/db-renter-easy-api-svc.yaml

5. Aplique os Deployments:
  kubectl apply -f app/renter-easy-api-dp.yaml
  kubectl apply -f database/db-renter-easy-api-dp.yaml


---

## ✅ Verificação
- Listar Pods:
  kubectl get pods

- Listar Services:
  kubectl get svc

- Listar versionamento:
  kubectl rollout history deploy [nome-deploy]

- Acessar a API via NodePort:
  http://<IP_DO_NODE>:30000

---

## 🔍 Próximos Passos (Melhorias)
- [X] Migrar Pods para **Deployments** para permitir escalabilidade.
- [ ] Usar **Secrets** para armazenar senhas.
- [ ] Adicionar **PersistentVolumeClaim** para o banco.
- [ ] Configurar **livenessProbe** e **readinessProbe**.

---

### Autor
Rafael Mariano Silva

