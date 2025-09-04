## Guia Rápido: Como Criar uma Máquina Virtual Windows no Portal do Azure

Este guia detalha o passo a passo para a criação de uma máquina virtual (VM) com o sistema operacional Windows utilizando o portal do Azure, com base na documentação oficial da Microsoft.

### Pré-requisitos

  - Uma assinatura do Azure. Caso não possua, é possível criar uma conta gratuita.

### Passo 1: Acessar o Portal do Azure

1.  Abra seu navegador e acesse o [portal do Azure](https://www.google.com/search?q=https://portal.azure.com).
2.  Faça o login com as suas credenciais da Microsoft.

### Passo 2: Iniciar a Criação da Máquina Virtual

1.  Na barra de pesquisa do portal, digite "máquinas virtuais" e selecione **Máquinas virtuais** nos resultados dos serviços.
2.  Na página de Máquinas Virtuais, clique em **+ Criar** e selecione **Máquina virtual do Azure**.

### Passo 3: Configuração dos Detalhes Básicos da VM

Na aba **Básicos**, você precisará preencher as seguintes informações:

  - **Assinatura:** Selecione a sua assinatura do Azure.
  - **Grupo de Recursos:** Um grupo de recursos é um contêiner que mantém recursos relacionados para uma solução do Azure. Clique em **Criar novo** para criar um novo grupo ou selecione um existente.
  - **Nome da máquina virtual:** Insira um nome para a sua VM (ex: `minha-vm-windows`).
  - **Região:** Escolha a região do Azure onde você deseja que sua VM seja hospedada.
  - **Opções de disponibilidade:** Para este guia rápido, você pode manter o padrão: `Nenhuma redundância de infraestrutura necessária`.
  - **Imagem:** Selecione uma imagem do Windows Server. Por exemplo, `Windows Server 2022 Datacenter: Azure Edition - x64 Gen2`.
  - **Tamanho:** Escolha um tamanho para a sua VM com base nos recursos de CPU e RAM necessários. O Azure sugere tamanhos padrão.
  - **Conta de administrador:**
      - **Nome de usuário:** Crie um nome de usuário para a conta de administrador.
      - **Senha:** Defina uma senha forte que atenda aos requisitos de complexidade. Confirme a senha.
  - **Regras de porta de entrada:**
      - **Portas de entrada públicas:** Selecione **Permitir portas selecionadas**.
      - **Selecionar portas de entrada:** Marque as opções **RDP (3389)** para permitir a conexão de área de trabalho remota e, opcionalmente, **HTTP (80)** e/ou **HTTPS (443)** se você planeja hospedar um servidor web.

### Passo 4: Configuração dos Discos

1.  Navegue para a aba **Discos**.
2.  **Tipo de disco do SO:** Você pode manter o padrão `SSD Premium` para um melhor desempenho.
3.  As demais configurações podem ser mantidas como padrão para este guia.

### Passo 5: Configuração de Rede

1.  Prossiga para a aba **Rede**.
2.  O portal do Azure criará automaticamente uma rede virtual, sub-rede e um endereço IP público. Você pode manter as configurações padrão.

### Passo 6: Gerenciamento e Opções Avançadas

1.  Nas abas **Gerenciamento**, **Avançado** e **Marcas**, você pode configurar opções adicionais como monitoramento, extensões e organização de recursos. Para um início rápido, as configurações padrão são suficientes.

### Passo 7: Revisar e Criar

1.  Vá para a aba **Revisar + criar**.
2.  O Azure validará as suas configurações. Após a validação ser bem-sucedida, revise os detalhes da sua máquina virtual.
3.  Clique em **Criar**. O processo de implantação da sua nova VM será iniciado.

### Passo 8: Conectar-se à Máquina Virtual

1.  Após a conclusão da implantação, clique em **Ir para o recurso**.
2.  Na página de visão geral da sua nova VM, clique em **Conectar**.
3.  Selecione a opção **RDP**.
4.  Clique em **Baixar Arquivo RDP**.
5.  Abra o arquivo `.rdp` baixado.
6.  Na janela de Conexão de Área de Trabalho Remota, clique em **Conectar**.
7.  Selecione **Mais opções** e depois **Usar uma conta diferente**.
8.  Insira o nome de usuário (no formato `localhost\seu_nome_de_usuario`) e a senha que você definiu durante a criação da VM.
9.  Você poderá receber um aviso de certificado. Clique em **Sim** para prosseguir com a conexão.

Após esses passos, a área de trabalho da sua nova máquina virtual Windows no Azure será exibida, pronta para uso.
