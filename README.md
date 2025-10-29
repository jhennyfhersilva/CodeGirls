# Code Girls
Evolução e entregas
    
# Aulas de Projetos
# Aula 3 - Gerenciando Instâncias EC2 na AWS

# Criação e uso de imagens AMI

Uma Amazon Machine Image (AMI) é um modelo pré-configurado que serve como a unidade básica para criar instâncias do servidor virtual no Amazon Elastic Compute Cloud (EC2). Ela contém todo o software necessário, como um sistema operacional, aplicações e configurações, para iniciar e executar instâncias na nuvem da Amazon Web Services (AWS). 

**Criação:** As AMIs podem ser criadas a partir de isntâncias em execução ou paradas.

**AMIs públicas ou privadas:** AWS fornece uma variedade de AMIs públicas que podem ser usadas, ou você pode criar e usar suas próprias

**Personalização:** é possível personalizar (software, configurar definições) e criar uma AMI a partir dela

**Iniciar instâncias:** para executar ec2, seleciona uma ami, a ami fornece as informações necessárias para iniciar a instância, como volume e permissões

**Tipos de AMI:** amazon linux, windows entre outros, escolha a ami com base nos requisitos de aplicação e do sistema.

![image.png](attachment:ac6e73b3-af10-4d51-ae49-6cc72647c942:image.png)

# Snapshots EBS

- Snapshots de Amazon EBS são **cópias incrementais e pontuais (para um determinado momento) dos dados em volumes do Amazon EBS, salvos no Amazon S3 para fins de backup, recuperação de desastres e migração de dados**. Eles capturam o estado completo de um volume em um instante e podem ser usados para criar novos volumes, restaurar dados ou servir como base para migrar dados entre diferentes regiões e contas da AWS.

<aside>
⁉️

Os snapshots podem ser guardados no S3

</aside>

- É um serviço de backup dos volumes do EBS em um determinado momento
    - É possível configurar a frequência com que os snapshots são tirados
- Faz parte do **IAAS**
- Para fins de recuperção de desastres, os instantâneos do EBS podem ser armazenados em uma região remota
- Os valores dos snapshots depende da região

**AMI**
Faz o backup de um servidor inteiro, incluindo todos os volumes

**Snapshot**
Faz uma cópia pontual de um determinado volume

![image.png](attachment:8ddfec2a-0420-4f47-8c0c-c87e1bd78299:image.png)

# Projeto - Desafio Instâncias EC2

![image.png](attachment:bed602dc-001e-43cd-898f-a357bb7cc14d:image.png)

S3 → Lambda function

EC2 → EBS

## Projeto com EC2

Imagine que terá 2 EBS, em um EBS (nuvem) uma pessoa irá colocar os arquivos

EC2 lê o arquivo, processa e envia para outro EBS

→ Se alimenta de um banco de dados RDS

 e terá uma automação para que envie para outro EBS

![image.png](attachment:a841cc13-a86c-4553-aae3-7c3d96d8b323:image.png)

→ Adicionar flow ediction deixa a imagem interessante

## Projeto com S3

Toda vez que um ator madan um arquivo  pro S3 por meio de linha de comando

S3 envia arquivo pro lambda processar e manda para o dynamo (automatização de rotinas)

![image.png](attachment:dfcae799-1a22-48e9-a89a-c293f02f65f5:image.png)

## Exemplos de desenhos

![image.png](attachment:be467c98-4fd9-4da8-8faf-41575ff2e794:image.png)

# Aula 4 - Explorando Workflows automatizados com AWS Step Functions

# Documentos auxiliares

https://aws.amazon.com/pt/step-functions/

# Conhecendo o AWS Step Functions

- Construtor visual para criar fluxos de trabalho
- O AWS Step Functions **é um serviço visual sem servidor da AWS que orquestra fluxos de trabalho distribuídos, permitindo a criação de aplicativos complexos conectando diferentes serviços da AWS**
- Utiliza um console gráfico para definir e visualizar etapas, gerenciando automaticamente a execução, o tratamento de erros e os retentativas para garantir a confiabilidade do aplicativo.
- Usado para automatizar processos, orquestrar microsserviços, criar pipelines de dados e aprendizado de máquina, e integrar diversas funções e serviços em uma arquitetura escalável
- Facilita a coordenação de aplicativos e microserviços
- Ao criar um fluxo, pode ter os recursos criados ou não, para começar a trabalhar

### Caso de uso

![image.png](attachment:64853c8b-3bab-498e-96fb-33cb43512032:image.png)

# Benefícios e Projeto Modelo no AWS Step Functions

- Acessar Step Functions

<aside>
❓
# AWS Cloudformation

- Serviço que facilita a modelagem e a configuração de recursos na AWS
- Permite criar modelos e descrevem os recursos necessários, como instâncias EC2 ou banco de dados RDS, automatizando provisionamento e configuração
- Elimina a necessidade de configurar recursos manualmente, permitindo focar no desenvolvimento e gestão de aplicativos

# Benefícios do AWS Cloudformation e formatos para criação de modelos

- Ajuda a automatizar o processo de criação, configuração e gerenciamento de recursos da AWS
    - Implantação rápida confiável e repetida
- Possível criar modelos padrão de pilhas de infraestrutura que podem ser usados para criar cópias idênticas
- Ajuda a reduzir custos permitindo que os clientes usem modelos de infraestrutura existentes e os reutilizem em vários ambientes
- Ajuda a garantir que todos os recursos da AWS sejam configurados com segurança usando políticas e regras de segurança

![image.png](attachment:a1af9115-2d9f-4d83-b3e8-6049497cf470:image.png)

- Suporta JSON e AML como formatos para o modelo (templates)

# Acessando o AWS Cloudformation para criar uma Stack e a diferença entre o Terraform

- Acessar AWS Cloudformation
- Acessar infraestructure composer
    - Pode criar ou utilizar um template já pronto de forma visual ou por código

![image.png](attachment:919ba116-0a5f-4362-a620-e545b130c48f:image.png)
Funciona muito parecido com o **Power Automate**

</aside>

- Pode escolher um modelo automatizado
    - O modelo consta a documentação com detalhes do flow
- **Step Functions de exemplo:** Mapa distribuído para processar arquivos no S3
- Há a visualização em design visual e, também, em código para alteração
- Colocar algum flow para executar

# Realizado validações no AWS Step Functions

- Ao adicionar um novo step, você deve definir as configurações e parâmetros
- Objetos que não foram criados antes da execução para serem aneados no fluxo de trabalho, são criados após a execução
    - **Exemplo**: dentro do S3 foi criado arquivo csv que antes do fluxo não existiam
- CloudWatch deixa visível os logs de execução do fluxo de trabalho

# Criando e Executando Lambda no AWS Step Functions

- Criar novo fluxo do zero
    - Configurações da máquina
        - Padrão
- Adicionar Lambda function
    - Criar uma function do 0 ou anexar uma já criada

# Aula 3 - Implementando sua Primeira Stack com AWS CloudFormation

# Documentos auxiliares

https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/gettingstarted.walkthrough.html

# O que é o AWS Cloudformation

- AWS CloudFormation **é um serviço da AWS que permite modelar e provisionar infraestrutura na nuvem de forma automatizada, segura e repetível**
- Utiliza arquivos de modelo (em formatos como JSON ou YAML) para descrever todos os recursos da AWS necessários para uma aplicação, como instâncias EC2, bancos de dados e balanceadores de carga
    - Esses recursos são gerenciados como uma única unidade, chamada pilha (stack)
- Processo que auxilia na automação de criação de recursos na AWS
- Podemos usar templates quantas vezes quisermos e pagamentos apenas pelas stacks criadas (conjunto de recursos)

![image.png](attachment:f6376a69-865f-472d-8129-3168d75e725a:image.png)

## Exemplo de template

![image.png](attachment:f8e7276e-5418-40fb-8c91-fa899faa0862:image.png)

# Criando Stacks no AWS CloudFormation

- Acessar CloudFormation
- Criar stack
    - Se quiser, a partir de template
    - Ele disponibiliza a url do template
    - Também é possível pegar os templates do repositório do Github
- Possível utilizar por meio do VS

# Criando stacks de firewall no CloudFormation

- Criar stack com recurso importado (upload)
    - Apache file

![image.png](attachment:f970d2ae-d34e-41ef-af9b-d241d02fd856:image.png)

# Tarefas automatizadas com Amazon S3 e Lambda

## Entendendo o Amazon S3

- Serviço de armazenamento em nuvem
- Permite armazenar e acessar dados de forma segura e esclável

### Vantagens do S3

1. Durabilidade → altamente confiável
2. Disponibilidade → garante acesso contínuo
3. Escalabilidade → ajusta automaticamente a capacidade de armazenamento
4. Segurança → oferece criptografia, controle de acesso e monitoramento de atividades

## Entendendo o AWS Lambda

- Serviço de computação serveless que permite executar código em resposta a eventos, sem necessidade de gerenciar servidores
- Upload do código → execução automática
- Execução máxima de 15 minutos

### Vantagens do Lambda

1. Execução sob demanda → somente quando necessário
2. Escalabilidade automática → ajusta capacidade automaticamente com base no numero de eventos
3. Custo eficiente → cobra apenas pelot empo de execuação e pela quantidade de solicitações
4. Integração com outros serviços AWS → funciona como um conector entre diversos serviços AWS

# Upload de Arquivos com processamente e registro no DynamoDB

- **Hands On**
    
    ![image.png](attachment:43583a6e-10c7-46b7-a94a-4527a5869e21:image.png)
    
    ![image.png](attachment:4d523d28-49b8-4368-bab0-6ad81f2a56e3:image.png)
    
- [ ]  Fazer desenho de infraestrutura utilizando o Lambda 1 de novembro de 2025

# Configurando AWS localmente com LocalStack

- Projeto OpenSource
- LocalStack **é um emulador que simula serviços da AWS em sua máquina local**, permitindo que desenvolvedores criem e testem aplicativos na nuvem sem precisar de uma conexão com a nuvem real
- Usa contêineres Docker para rodar serviços como S3, Lambda, DynamoDB, SQS e muitos outros, o que acelera o desenvolvimento, permite testes offline e evita custos durante o ciclo de desenvolvimento
- Permite aos desenvolvedores economizar tempo e custos, especialmente em testes automatizados e em ambientes de integração contínua (CI/CD)

**Serviços suportados:** Lamda, API Gateway, S3, DynamoDB, SNS, SQS, CloudFormation, entre outros

https://docs.localstack.cloud/aws/getting-started/

- Possível acessar pelo Docker desktop
- Possível verificar se foi realizado o download corretamente pelo PowerShell
- Requer o Python instalado para o Local Stack funcionar
- [ ]  Testar funcionalidades de S3 e Lambda pelo Local Stack 1 de novembro de 2025

# Criando recursos

- Dentro do Power Shell
    - Configurar credencias do Local Stack
    - Criar bucket S3 para nota fiscais
    - Criar tabela no DynamoDB com informações das notas fiscais
    - Criar arquivo json (fake) da nota fiscal
        - Pode fazer no VS
    - Enviar arquivo para o S3
        - Remover após realizar o teste de subida do arquivo
    - Criar Lambda Function para processar notas fiscais
    - Configurar o trigger e o evento do Lambda
        - Importante configurar o tipo de arquivo que irá chegar, se terá algum sufixo ou prefixo

# Trabalhando arquivos localmente com LocalStack

- Acessar NoSQL Workbench
    - Adicionar conexão com o DynamoDB
- Fazer upload do arquivo de notas fiscais (teste) dentro do DynamoDB
    - Verificar se o arquivo foi recebido com sucesso
- Verificar logs da Lambda Function

<aside>
❓

Tentar subir um arquivo com erro também é importante para entender se o Lambda está funcionando em sua totalidade

</aside>

- Criar API Gateway para receber requisições para o Lambda executar
    - Atualizar código do Lambda

<aside>
❓

**Postman** é outra ferramenta possível para realizar integração O Postman **é uma plataforma de colaboração para desenvolvimento e testes de APIs que permite aos desenvolvedores criar, compartilhar e testar APIs de forma mais fácil e rápida**

Serve para simplificar o processo de comunicação entre diferentes partes de um sistema, oferecendo uma interface gráfica intuitiva para enviar requisições HTTP, visualizar as respostas e automatizar testes

</aside>

- Acessar Postman e configurar
    - Verificar possibilidades do Postman
    - No caso de uso, o Postman serve para inserir registros ou consultar

# Estudo de caso

![image.png](attachment:ef9f4bd0-e461-4e0e-b871-dc405ed5f728:image.png)

-
