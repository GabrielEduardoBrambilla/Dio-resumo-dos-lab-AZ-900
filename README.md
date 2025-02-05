# Dio-resumo-dos-lab-AZ-900
Resumo do lab Criando máquinas Virtuais na Azure. Formação AZ-900 

## Modelos de nuvem

- Nuvem publica
- Nuvem privada
- Nuvem Hibrida

# **CapEx**

Servidor local

Despesas de capital

# **OpEx**

Servidor em nuvem

Despesas operacionais

Modelo baseado por consumo

## **Azure Arc**

O Azure Arc é um conjunto de tecnologias que ajuda a gerenciar seu ambiente de nuvem. O Azure Arc pode ajudar a gerenciar o seu ambiente de nuvem, seja uma nuvem pública exclusivamente no Azure, uma nuvem privada em seu datacenter, uma configuração híbrida ou até mesmo um ambiente de várias nuvens em execução em vários provedores de nuvem ao mesmo tempo.

# **Beneficios da nuvem**

- Alta disponibilidade
- SLA - Service level agreement
    - Acordo entre provedor de serviços e consumidor para nivelamento de expectativas, sobre os serviços oferecidos.
    - Possui um downtime acordado em contrato, de quanto tempo esse serviço pode ficar fora do ar, caso o serviço exceda esse tempo de downtime a microsoft te disponibiliza credito
- Dimensionamento vertical
    - Refere-se a possibilidade de aumentar a capacidade computacional de uma maquina controtada em especifico
- Dimensionamento horizontal
    - O famoso escalonamento horizontal o qual permite que novas maquinas ou containers virtuais sejam adiconados automaticamente (ou manualmente, quem faz manualmente?), para suprir um pico de demanda na aplicação. Do mesmo modo como novas maquinas são adicionadas elas são eliminadas assim que percebido a queda de demanda da aplicação.
- Escalabilidade
    - Capacidade de ajustar recursos para atender a demanda, do produto. Gastando somente o que é utilizado devida a politica de pagar por consumo dentro da Azure
- Elasticidade
    - 
- Confiabilidade
    - Devido ao design descentralizado, a nuvem naturalmente dá suporte a uma infraestrutura confiável e resiliente. Com um design descentralizado, a nuvem permite que você tenha recursos implantados em várias regiões do mundo. Com essa escala global, mesmo que ocorra um evento catastrófico em uma região, as outras regiões ainda estarão em funcionamento. Você pode criar aplicativos para aproveitar automaticamente essa confiabilidade maior. Em alguns casos, o próprio ambiente de nuvem mudará automaticamente para uma região diferente, sem que você precise realizar nenhuma ação. Você entenderá melhor como o Azure aproveita a escala global para oferecer confiabilidade mais adiante nesta série.
- Previsibilidade
    - Refere-se tanto a desempenho quanto a custos, devido as ferramentas oferecidas para calculo de custos e SLA o qual nivela uma expectativa de desempenho esperado.
- Custos
    - A previsibilidade de custos se refere a capaciadde de prever seus gastos com a nuvem. Podendo ser feito o acompanhamento e monitoria de usos e gastos em tempo real de recursos, possibilitando um melhor planejamento de uso e implantação de recursos.
    - TCO é uma das ferramentas de calculadora de possiveis gastos com a nuvem
- Pares de Região
- Grupos de Recursos
- Assinaturas
- Grupos de Gerenciamento
- Azure Containers
    
    Containers are a virtualization environment. Much like running multiple virtual machines on a single physical host, you can run multiple containers on a single physical or virtual host. Unlike virtual machines, you don't manage the operating system for a container. Virtual machines appear to be an instance of an operating system that you can connect to and manage. Containers are lightweight and designed to be created, scaled out, and stopped dynamically. It's possible to create and deploy virtual machines as application demand increases, but containers are a lighter weight, more agile method. Containers are designed to allow you to respond to changes on demand. With containers, you can quickly restart if there's a crash or hardware interruption. One of the most popular container engines is Docker, and Azure supports Docker.
    

![image.png](attachment:cbce4ab8-ec4d-4ed6-92f9-3ad6741d413f:image.png)

- Azure Functions
    
    Eventdriven, serverless compute option
    
    Using Azure Functions is ideal when you're only concerned about the code running your service and not about the underlying platform or infrastructure. Functions are commonly used when you need to perform work in response to an event (often via a REST request), timer, or message from another Azure service, and when that work can be completed quickly, within seconds or less
    
    Azure only charges you for the CPU time used while your function runs.
    
    az vm create --resource-group "learn-fb16e193-7865-47ef-8cfc-683fcd7a1fc9"  --name my-vm   --public-ip-sku Standard   --image Ubuntu2204   --admin-username azureuser   --generate-ssh-keys
    
    az vm extension set --resource-group "learn-fb16e193-7865-47ef-8cfc-683fcd7a1fc9"  --vm-name my-vm  --name customScript  --publisher Microsoft.Azure.Extensions  --version 2.1  --settings '{"fileUris":["https://raw.githubusercontent.com/MicrosoftDocs/mslearn-welcome-to-azure/master/configure-nginx.sh"]}'  --protected-settings '{"commandToExecute": "./configure-nginx.sh"}'
    
    IPADDRESS="$(az vm list-ip-addresses --resource-group "learn-fb16e193-7865-47ef-8cfc-683fcd7a1fc9" --name my-vm --query "[].virtualMachine.network.publicIpAddresses[*].ipAddress" --output tsv)”
    

# Modelo de responsabilidade compartilhada

## IaaS

Infraestrutura as a service

Resposabilidades da Microsoft:

- Host Fisico
- Rede Fisica
- Datacenter Fisico

## PaaS

Plataforma as a service

Resposabilidades da Microsoft:

- + Sistema Operaciona

Responsabilidade compartilhada

- Controles de rede
- Aplicativos
- Infraestrutura de identidade e diretório

## SaaS

Software as a service

Resposabilidades da Microsoft:

- + Controles de rede
- + Aplicativos

Responsabilidade compartilhada

- + Infraestrutura de identidade e diretório

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/26de6d8c-6953-4249-b0c7-f3371bc0adf0/775f9b7c-bce3-4fc2-b86d-05713264c17e/image.png)

## Iaas

O IaaS (infraestrutura como serviço) é a categoria mais flexível de serviços de nuvem, pois oferece o máximo de controle sobre os recursos de nuvem. Em um modelo de IaaS, o provedor de nuvem é responsável por manter o hardware, a conectividade de rede (com a Internet) e a segurança física. Você é responsável por todo o resto: instalação, configuração e manutenção do sistema operacional; configuração de rede; configuração de banco de dados e armazenamento e assim por diante. Com o IaaS, basicamente o hardware é alugado em um datacenter de nuvem, mas cabe a você decidir o que fazer com ele.

## Paas

O PaaS (Plataforma como serviço) é um meio termo entre alugar espaço em um datacenter (infraestrutura como serviço) e pagar uma solução completa e implantada (software como serviço). Em um ambiente de PaaS, o provedor de nuvem mantém a infraestrutura física, a segurança física e a conexão com a Internet. Ele também mantém os sistemas operacionais, o middleware, as ferramentas de desenvolvimento e os serviços de business intelligence que compõem uma solução de nuvem. Em um cenário de PaaS, você não precisa se preocupar com o licenciamento nem com a aplicação de patch em sistemas operacionais e bancos de dados.

Pense no PaaS como o uso de um computador conectado ao domínio: o departamento de TI mantém o dispositivo com atualizações, patches e renovações regulares.

Dependendo da configuração, você ou o provedor de nuvem pode ser responsável pelas configurações de rede e a conectividade no ambiente de nuvem, a segurança da rede e do aplicativo e a infraestrutura de diretório.

## SaaS

O modelo de responsabilidade compartilhada se aplica a todos os tipos de serviço de nuvem. O SaaS é o modelo que coloca a maior responsabilidade sobre o provedor de nuvem e a menor responsabilidade com o usuário. Em um ambiente de SaaS, você é responsável pelos dados que coloca no sistema, pelos dispositivos que permite que se conectem ao sistema e pelos usuários que têm acesso. Quase todo o resto é responsabilidade do provedor de nuvem. O provedor de nuvem é responsável pela segurança física dos datacenters, pela energia, pela conectividade de rede e pelo desenvolvimento e aplicação de patch dos aplicativos.

## Componentes de arquitetura

Regiões e pares de regiões 

Não são todos os recursos que estao disponiveis em todas as regiões

As regiões tem no minimo 3 datacenter, com uma comunicação muito rapida, disaster recovery

Baixa latencia 

## Região Par

É a região para qual o backup de desaster recovery ficar configurada, se houver um problema da região brasileira ficar indisponivel a região par referente a região brasileira é a regia central sul norte americana

## Região Soberana

São regiões de serviço para governos e estados basicamente

A China possui uma região soberana a qual é operada pela 21Vianet não diretamente pela microsoft 

## Conta e assinaturas

Uma conta pode ter varias assinaturas, mas uma assinatura vai estar relacionada somente a uma conta por conta do billing que deve ser gerado, deve sempre haver somente um unico responsavel por aquele pagamento

- Area de trabalho remota no Azure
- AKS, Azure Kubernetes Service
- Aplicativo Serviços
- Conteiner e instancias
- Maquinas Virtuais

Maquinas Virtuais temos acesso a tudo, menos ao hardware em si, mas ainda assim podemos configurar quantidade de processadores e recursos na maquina

Dimensionamento de Recursos

Conjuntos de disponibilidade 

- Dominio de atualização
- Dominio de falha

Container 

Não precisa de um sistema operacional completo

Instancias de Container

Serviço no modelo PaaS, o qual permite a execução de containers sem a necessidade de criação de um VM na azure, vai pro contianer direto

Aplicativos de Conteiner

Tem o diferencial que pode realizar balanceamento de carga

AKS

Orquestração, principal função do Kubernetes, gerenciar as instancias dos serviços que estão sendo utilizadas

Azure Funcitons 

Execução baseada em eventos, PaaS

# **Describe Azure storage accounts**

- Locally redundant storage (LRS)
- Geo-redundant storage (GRS)
- Read-access geo-redundant storage (RA-GRS)
- Zone-redundant storage (ZRS)
- Geo-zone-redundant storage (GZRS)
- Read-access geo-zone-redundant storage (RA-GZRS)

Blob e Arquivos 

Principais armazenamentos utlizados no Storage account

Pontos de extremidade publicos do serviço de armazenamento

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/26de6d8c-6953-4249-b0c7-f3371bc0adf0/e3443634-f749-4832-9743-fad32544a791/image.png)

Camadas de acesso de armazenamento  

### **Locally redundant storage**

Locally redundant storage (LRS) replicates your data three times within a single data center in the primary region. LRS provides at least 11 nines of durability (99.999999999%) of objects over a given year.

### **Zone-redundant storage**

For Availability Zone-enabled Regions, zone-redundant storage (ZRS) replicates your Azure Storage data synchronously across three Azure availability zones in the primary region. ZRS offers durability for Azure Storage data objects of at least 12 nines (99.9999999999%) over a given year.

### **Geo-redundant storage**

GRS copies your data synchronously three times within a single physical location in the primary region using LRS. It then copies your data asynchronously to a single physical location in the secondary region (the region pair) using LRS. GRS offers durability for Azure Storage data objects of at least 16 nines (99.99999999999999%) over a given year.

Azure Data Box, caracteristica

Migração de dados em larga escala:

- 80TB de dados

## **Azure Storage**

Azure Storage services offer the following benefits for application developers and IT professionals:

- **Durable and highly available**. Redundancy ensures that your data is safe if transient hardware failures occur. You can also opt to replicate data across data centers or geographical regions for additional protection from local catastrophes or natural disasters. Data replicated in this way remains highly available if an unexpected outage occurs.
- **Secure**. All data written to an Azure storage account is encrypted by the service. Azure Storage provides you with fine-grained control over who has access to your data.
- **Scalable**. Azure Storage is designed to be massively scalable to meet the data storage and performance needs of today's applications.
- **Managed**. Azure handles hardware maintenance, updates, and critical issues for you.
- **Accessible**. Data in Azure Storage is accessible from anywhere in the world over HTTP or HTTPS. Microsoft provides client libraries for Azure Storage in a variety of languages, including .NET, Java, Node.js, Python, PHP, Ruby, Go, and others, as well as a mature REST API. Azure Storage supports scripting in Azure PowerShell or Azure CLI. And the Azure portal and Azure Storage Explorer offer easy visual solutions for working with your data.

## Azure blobs

Good for following cenarios 

- Serving images or documentos to a browser
- Storing files for distributed access
- Streaming video and audio
- Backup and restore, disaster recovery and archiving
- Storing data for later analysis

### Storage tiers

- **Hot access tier**: Optimized for storing data that is accessed frequently (for example, images for your website).
- **Cool access tier**: Optimized for data that is infrequently accessed and stored for at least 30 days (for example, invoices for your customers).
- **Cold access tier**: Optimized for storing data that is infrequently accessed and stored for at least 90 days.
- **Archive access tier**: Appropriate for data that is rarely accessed and stored for at least 180 days, with flexible latency requirements (for example, long-term backups).

Considerations 

- Hot, cool, and cold access tiers can be set at the account level. The archive access tier isn't available at the account level.
- Hot, cool, cold, and archive tiers can be set at the blob level, during or after upload.
- Data in the cool and cold access tiers can tolerate slightly lower availability, but still requires high durability, retrieval latency, and throughput characteristics similar to hot data. For cool and cold data, a lower availability service-level agreement (SLA) and higher access costs compared to hot data are acceptable trade-offs for lower storage costs.
- Archive storage stores data offline and offers the lowest storage costs, but also the highest costs to rehydrate and access data.

## **AzCopy**

AzCopy is a command-line utility that you can use to copy blobs or files to or from your storage account. With AzCopy, you can upload files, download files, copy files between storage accounts, and even synchronize files. AzCopy can even be configured to work with other cloud providers to help move files back and forth between clouds.

## Gerenciamento

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/26de6d8c-6953-4249-b0c7-f3371bc0adf0/59746ac0-f143-4490-9f80-ea16a8e96977/image.png)

## **Azure Storage Explorer**

Azure Storage Explorer is a standalone app that provides a graphical interface to manage files and blobs in your Azure Storage Account. It works on Windows, macOS, and Linux operating systems and uses AzCopy on the backend to perform all of the file and blob management tasks. With Storage Explorer, you can upload to Azure, download from Azure, or move between storage accounts.
