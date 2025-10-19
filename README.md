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
