
# Tutorial de criação da instância EC2

O deploy da api pode ser feita em duas instâncias EC2 da AWS. Uma para a api e uma para o banco de dados.

**Segue os passos para a criação das instâncias:**

No site da [AWS](console.aws.amazon.com/console), 
* clique em [Todos os serviços](console.aws.amazon.com/console/services);
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/1awstodososservicos.png)

* na categoria **Computação** clique em [EC2](console.aws.amazon.com/ec2);
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/2awsecs.png)

* clique em **Executar instância**;
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/3awsexecutarinstancia.png)

* clique em **Adicionar mais tags**, nesse projeto utilizaremos três tags:
        
        1. Chave: Name. Valor: node-api. Tipos de Recurso: Instâncias e Volumes;
        2. Chave: CostCenter. Valor: test. Tipos de Recurso: Instâncias e Volumes;
        3. Chave: Project. Valor: test. Tipos de Recurso: Instâncias e Volumes.
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/4awstags.png)

* selecione a imagem de aplicação e de sistema operacional. Para a api utilizaremos a **Amazon Linux** e para o banco de dados o **Ubuntu**, ambos com as configurações padrão e o tipo de instância padrão;
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/5awsimagens.png)

* em Par de chaves (login), clique em **Criar novo par de chaves**:
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/6awspardechaves.png)

    * Nome do par de chaves: node-api-key;
    * Tipo de par de chaves: RSA;
    * Formato de arquivo de chave privada: .pem;
    * clique em **Criar par de chaves**.
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/7awsapikey.png)

* faça o download da chave e selecione a chave criada;

* em **Configurações de rede**, marque as opções **Permitir tráfego HTTPS da Internet** e **Permitir Tráfego HTTP da Internet** e clique em **Editar**;
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/8awsseguranca.png)

    * Nome do grupo de segurança - obrigatório: node-api-security.
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/9awsseguranca2.png)

* em **Regras do grupo de segurança de entrada** clique em **Adicionar regra de grupo de segurança**:
    * Tipo: TCP personalizado;
    * Tipo de origem: Qualquer lugar;
    * Intervalo de portas: 3000 para a API e 5432 para o banco de dados.
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/9awsseguranca5.png)

* em **Configurar armazenamento** e **Detalhes avançados** mantenha como padrão pré-definido.

* clique em **Executar instância**.
![](https://github.com/rafael-arashiro/ANOUT_OUT24_D03_AWS/blob/main/ec2_images/10awsexecutar.png)