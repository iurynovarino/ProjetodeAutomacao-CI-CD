# Arquitetura de CI/CD e Infraestrutura Cloud

Este repositório documenta o fluxo de **Integração e Entrega Contínua (CI/CD)** e a infraestrutura em nuvem utilizada no projeto, focada em automação via GitOps e segregação de ambientes.

---

## 🚀 Fluxo de Trabalho

O ciclo de vida da aplicação segue quatro etapas principais:

### 1. Desenvolvimento e Qualidade
* **Envio de Build:** O processo inicia com o push de código pelos desenvolvedores.
* **Aprovação:** Existe um gate manual ou automático de aprovação. Se aprovado, o código segue para a branch de Homologação.
* **Monitoramento:** Engenheiros de DevOps acompanham a execução das pipelines para garantir a integridade do processo.

### 2. Integração Contínua (CI)
* **Pipelines de Build:** Execução automática de testes e empacotamento da aplicação em containers.
* **Azure Container Registry (ACR):** Armazenamento das imagens geradas, separadas por tags de **Hml (Homologação)** e **Prod (Produção)**.

### 3. Entrega Contínua (CD) com GitOps
* **Argo CD:** Atua como o cérebro da implantação, sincronizando o estado do repositório Git diretamente com o cluster.
* **Implantar Release:** Distribuição automatizada dos serviços para os pods do Kubernetes.

### 4. Camada de Rede e Acesso
* **Nginx Ingress-Controller:** Responsável pelo roteamento interno e gerenciamento de tráfego dentro do cluster.
* **Application Gateway:** Funciona como o firewall e balanceador de carga de entrada (WAF).
* **DNS (Public/Private):** Gerenciamento de domínios para acesso externo e interno seguro.

---

## 🛠️ Tecnologias Principais
* **Orquestração:** Kubernetes / Argo CD
* **Cloud:** Azure (ACR, Application Gateway, DNS Zones)
* **Web Server:** Nginx
* **CI Tool:** Azure Pipelines
<br>
<br>
<br>
<br>
<p align="center">
<img src="./images/DevOps.jpg">
</p>