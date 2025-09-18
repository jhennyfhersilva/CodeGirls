# CodeGirls
##Evolução do aprendizado e entregas##

# O que são instâncias EC2

**EC2 →** Amazon Elastic Compute Cloud (Computação Elástica na Nuvem da Amazon), um serviço da Amazon Web Services (AWS) que fornece servidores virtuais escaláveis e sob demanda, chamados de instâncias, para que desenvolvedores e empresas possam executar aplicações sem a necessidade de comprar e gerenciar hardware físico. 

Composta por: CPU, Memória, Disco, Rede, Sitema operacional

- Tipo de recuso IAAS, infraestrutura como serviço
    - Responsabilidade pelos aplicativos, dados e conexões (gerência do recurso)
- Escolher EC2 visando eficiência, escalabilidade e economia, dependendo da aplicação que será realizada
- O EC2 nos fornece capacidade de computação na cloud da AWS
- Pode definir segurança básica utilizando firewall icnorporada do AWS
- Cada instância oferece diferentes recursos de computação
- **Famílias de instâncias EC2**

### Propósito das instâncias EC2
- Verificar o valor da instância pelo AWS pricing calculator
    https://aws.amazon.com/pt/aws-cost-management/aws-pricing-calculator/
    https://aws.amazon.com/pt/ec2/
    → Selecionar region → serviço (EC2) → tipo de locação → número de hosts → sistema operacional → carga de trabalho → número de instâncias (qtd de máquinas) → família de instância → cpu, memória e performance de rede
    
    **Outras opções:** sob demanda, estâncias spot, instâncias reservadas padrão e instâncias reservadas conversíveis
    
### Convenção do nome

- Dentro da AWS há um módulo para contratar e configurar o EC2

# Otimização de recursos

- Otimização → poupar custos
1. Desligar instâncias não utilizadas
    - Não utilização durante a noite ou finais de semana → desligamento automático
2. Remover recursos ociosos ou não utilizados
3. Escalar recursos
    - Scale de recursos para processar os workloads em determinados momentos
    - Aumentar ou diminuir de forma manual ou automática

      ⁉️
    **workloads** é usado para se referir às demandas computacionais específicas impostas a uma aplicação, serviço ou recurso em um ambiente virtualizado
    
       
    - **Vertical:** acrescentar ou diminuir a capacidade de um recurso em mesmo nó e geralmenta está relacionado ao poder computacional (CPU, memória, rede, storage etc.)
    - **Horizontal:** aumentar o número de recursos (ex: adicionar disco rídico, adicionando instâncias, etc.)

### Outras opções de otimização

**Sob demanda** → são compradas a uma taxa fixa por hora e são recomendadas para aplicativos com cargas de trabalhos irregulares de curto prazo que não podem ser interrompidas

→ Bastante utilizadas para testes ou desenvolvimento

**Reservadas** → são mais baratas, mas precisa pagar o ano inteiro de uso, mesmo sem o uso

# Amazon EBS

- Amazon EBS Amazon Elastic Block Store é um serviço de armazenamento em blocos de alta performance da **Amazon Web Services** que fornece volumes de armazenamento persistente e escaláveis para serem usados com instâncias do Amazon EC2 Elastic Compute Cloud. Semelhante a um disco rígido físico, o EBS permite que você anexe esses volumes a instâncias, crie sistemas de arquivos, execute bancos de dados e armazene dados persistentes que permanecem mesmo quando a instância é desativada.
- Capacidade de expansão de forma rápida
- Parecido com um HD externo
- Amazon EBS garante 99,999% de disponibilidade para seus volumes


# Amazon S3

- O Amazon S3 (Simple Storage Service) **é um serviço de armazenamento de objetos que permite guardar e recuperar qualquer quantidade de dados na internet de forma escalável, segura e com alto desempenho**. Ele é usado para data lakes, aplicativos nativos da nuvem, aplicativos móveis, sites e dados de IoT, oferecendo classes de armazenamento e recursos de gerenciamento de custos e acesso para atender a diversos requisitos de negócios e conformidade.
- Permite o arquivamento de dados de longa duração, o gerenciamento de ativos de mídia e o armazenamento seguro de logs

## Tipos de storage S3
- S3 é um recurso com alta disponibilidade (99,999999999%)
https://aws.amazon.com/pt/s3/storage-classes/

→ Lamba function solicita pegar os dados do arquivo (pelo S3 glacier ou standard) dependendo de quantos dias o dado ficou sem consulta

# Diferença entre os dois storages

A principal diferença é que

**o Amazon S3 é um armazenamento de objetos escalável e durável, ideal para dados não estruturados e backups, enquanto o Amazon EBS é armazenamento em bloco de alto desempenho e baixa latência**

, parecido com um disco rígido, usado para sistemas operacionais, bancos de dados e aplicativos que exigem acesso rápido a dados em uma instância EC2.

**Amazon S3 (Simple Storage Service)**

- **Tipo de Armazenamento:** Armazenamento de objetos.
- **Caso de Uso:** Armazenamento de dados não estruturados (como imagens, vídeos, backups), hospedagem de sites estáticos, e é ideal para grandes volumes de dados com escalabilidade ilimitada.
- **Acesso:** Acessível via web e APIs, com um identificador exclusivo (chave) para cada objeto.
- **Desempenho:** Geralmente mais lento que o EBS, com maior latência.
- **Escalabilidade:** Altamente escalável, com durabilidade excelente.

**Amazon EBS (Elastic Block Store)**

- **Tipo de Armazenamento:** Armazenamento em bloco, onde dados são armazenados em blocos de tamanho fixo.
- **Caso de Uso:** Ideal para anexar a instâncias Amazon EC2, servindo como o disco para um sistema operacional, banco de dados, ou para aplicativos que requerem alto desempenho e baixo latência.
- **Acesso:** Acessível apenas por uma instância EC2 específica na qual está anexado.
- **Desempenho:** Oferece alto desempenho e baixa latência, sendo a melhor opção para cargas de trabalho que exigem acesso rápido e frequente aos dados.
- **Escalabilidade:** Menos escalável que o S3; o tamanho do volume é um limite.

**Spot** → aplicação sob demanda com descontos de até 90%, porém a AWS pode encerrá-la a qualquer momento com um aviso de dois minutos
# Criação e uso de imagens AMI

Uma Amazon Machine Image (AMI) é um modelo pré-configurado que serve como a unidade básica para criar instâncias do servidor virtual no Amazon Elastic Compute Cloud (EC2). Ela contém todo o software necessário, como um sistema operacional, aplicações e configurações, para iniciar e executar instâncias na nuvem da Amazon Web Services (AWS). 

**Criação:** As AMIs podem ser criadas a partir de isntâncias em execução ou paradas.

**AMIs públicas ou privadas:** AWS fornece uma variedade de AMIs públicas que podem ser usadas, ou você pode criar e usar suas próprias

**Personalização:** é possível personalizar (software, configurar definições) e criar uma AMI a partir dela

**Iniciar instâncias:** para executar ec2, seleciona uma ami, a ami fornece as informações necessárias para iniciar a instância, como volume e permissões

**Tipos de AMI:** amazon linux, windows entre outros, escolha a ami com base nos requisitos de aplicação e do sistema.

# Snapshots EBS

- Snapshots de Amazon EBS são **cópias incrementais e pontuais (para um determinado momento) dos dados em volumes do Amazon EBS, salvos no Amazon S3 para fins de backup, recuperação de desastres e migração de dados**. Eles capturam o estado completo de um volume em um instante e podem ser usados para criar novos volumes, restaurar dados ou servir como base para migrar dados entre diferentes regiões e contas da AWS.

⁉️
Os snapshots podem ser guardados no S3

- É um serviço de backup dos volumes do EBS em um determinado momento
    - É possível configurar a frequência com que os snapshots são tirados
- Faz parte do **IAAS**
- Para fins de recuperção de desastres, os instantâneos do EBS podem ser armazenados em uma região remota
- Os valores dos snapshots depende da região

AMI - Faz o backup de um servidor inteiro, incluindo todos os volumes

Snapshot - Faz uma cópia pontual de um determinado volume
