# **Desafio DIO: Configurando um Banco de Dados SQL no Microsoft Azure**

Este repositório documenta o processo de criação e configuração de uma instância de Banco de Dados SQL na plataforma Microsoft Azure, como parte do desafio de projeto da [Digital Innovation One (DIO)](https://www.dio.me/). O objetivo é servir como um guia prático e material de consulta, consolidando os conhecimentos adquiridos durante as aulas.

## **Índice**

  - [Visão Geral do Desafio](https://www.google.com/search?q=%23vis%C3%A3o-geral-do-desafio)
  - [Tecnologias Utilizadas](https://www.google.com/search?q=%23tecnologias-utilizadas)
  - [Passo a Passo da Implementação](https://www.google.com/search?q=%23passo-a-passo-da-implementa%C3%A7%C3%A3o)
      - [1. Criação do Recurso no Portal Azure](https://www.google.com/search?q=%231-cria%C3%A7%C3%A3o-do-recurso-no-portal-azure)
      - [2. Configuração do Banco de Dados SQL](https://www.google.com/search?q=%232-configura%C3%A7%C3%A3o-do-banco-de-dados-sql)
      - [3. Definição das Regras de Firewall](https://www.google.com/search?q=%233-defini%C3%A7%C3%A3o-das-regras-de-firewall)
      - [4. Conexão e Validação](https://www.google.com/search?q=%234-conex%C3%A3o-e-valida%C3%A7%C3%A3o)
  - [Dicas e Pontos de Atenção](https://www.google.com/search?q=%23dicas-e-pontos-de-aten%C3%A7%C3%A3o)
  - [Conclusão](https://www.google.com/search?q=%23conclus%C3%A3o)

-----

## **Visão Geral do Desafio**

O desafio consistiu em provisionar, configurar e validar um serviço de banco de dados na nuvem da Microsoft, aplicando os conceitos de computação em nuvem, gerenciamento de recursos e segurança de rede.

## **Tecnologias Utilizadas**

  - **Microsoft Azure:** Plataforma de nuvem utilizada para hospedar e gerenciar o banco de dados.
  - **Azure SQL Database:** Serviço de banco de dados relacional gerenciado (PaaS).
  - **GitHub:** Plataforma para controle de versão e documentação do projeto.
  - **Markdown:** Linguagem de marcação para formatação do `config-db-azure.md`.

## **Passo a Passo da Implementação**

Aqui serão inseridas as suas capturas de tela para ilustrar cada etapa do processo.

### **1. Criação do Recurso no Portal Azure**

A primeira etapa envolveu o login no portal do Azure e a criação de um novo recurso do tipo "Banco de Dados SQL".

*(Me envie a print desta etapa e eu adicionarei aqui)*
`![Descrição da Imagem 1](images/01-criacao-recurso.png)`

### **2. Configuração do Banco de Dados SQL**

Nesta fase, foram definidas as configurações essenciais do banco, como o grupo de recursos, o nome do servidor, a localização, o método de autenticação e o plano de serviço (pricing tier).

*(Me envie a print desta etapa e eu adicionarei aqui)*
`![Descrição da Imagem 2](images/02-configuracao-banco.png)`

### **3. Definição das Regras de Firewall**

Para permitir o acesso externo ao banco de dados, foi necessário configurar as regras de firewall no servidor SQL, liberando o endereço IP da máquina local.

*(Me envie a print desta etapa e eu adicionarei aqui)*
`![Descrição da Imagem 3](images/03-regras-firewall.png)`

### **4. Conexão e Validação**

Com o banco de dados provisionado e o firewall configurado, a etapa final foi conectar a ele utilizando uma ferramenta de gerenciamento (como o Azure Data Studio ou SSMS) para validar a comunicação.

*(Me envie a print desta etapa e eu adicionarei aqui)*
`![Descrição da Imagem 4](images/04-conexao-cliente.png)`

## **Dicas e Pontos de Atenção**

  - **Segurança:** Sempre restrinja o acesso ao banco de dados apenas aos IPs necessários. Evite regras de firewall muito abertas (ex: 0.0.0.0).
  - **Custos:** Fique atento ao plano de serviço (pricing tier) escolhido. Para estudos, os níveis mais básicos ou a camada "Serverless" são geralmente suficientes e mais econômicos.
  - **Grupos de Recursos:** Organize seus serviços em grupos de recursos para facilitar o gerenciamento e a limpeza futura, evitando custos inesperados.

## **Conclusão**

Este desafio prático foi fundamental para solidificar o aprendizado sobre os serviços de banco de dados no Azure. A capacidade de provisionar e configurar recursos na nuvem é uma habilidade essencial para profissionais de tecnologia, e a documentação do processo ajuda a reforçar o conhecimento e a compartilhá-lo com a comunidade.
