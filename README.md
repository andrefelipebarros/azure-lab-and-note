# AZURE Lab and Note
Este repositório contém o resumo das lições aprendidas durante o desenvolvimento do lab na DIO.

# Explorando o Ambiente de Laboratório no Microsoft Azure

Este documento serve como um guia completo sobre os recursos, configurações e possibilidades que você encontrará ao criar e gerenciar um laboratório no Azure Lab Services.

## 1\. Visão Geral do Painel do Laboratório

Ao acessar um laboratório específico no portal do Azure, você é recebido por um painel central que oferece uma visão geral e acesso rápido a todas as funcionalidades principais.

Aqui estão os componentes que você verá:

  * **Informações Essenciais:** Detalhes como o grupo de recursos, o plano de laboratório associado e o status atual do laboratório.
  * **Link de Registro:** Um URL exclusivo que você compartilha com os usuários para que eles possam se registrar e acessar suas VMs.
  * **Custo Estimado Máximo:** Uma previsão de custo baseada no número de usuários, nas horas de cota e no tamanho da VM escolhida.

## 2\. Configurações e Gerenciamento do Laboratório

No menu à esquerda, você encontrará todas as opções para configurar, gerenciar e otimizar seu laboratório.

### 2.1. Modelo (Template)

O coração do seu laboratório. O "Modelo" é uma máquina virtual principal onde você instala e configura todo o software, código-fonte, arquivos e configurações que deseja que seus usuários recebam.

  * **Personalização Completa:** Você pode iniciar a VM de modelo a qualquer momento, conectar-se a ela e instalar o que for necessário, desde Visual Studio e Python até softwares de design gráfico ou bancos de dados.
  * **Imagens do Marketplace:** É possível iniciar seu modelo a partir de uma vasta gama de imagens de sistema operacional disponíveis no Azure Marketplace (ex: Windows 10/11, Ubuntu, etc.).
  * **Imagens Personalizadas:** Você também pode usar imagens de VM personalizadas que sua organização já tenha criado.
  * **Publicação:** Após configurar o modelo, você o "publica". Esse processo cria cópias idênticas da VM de modelo para cada usuário do laboratório.

### 2.2. Pool de Máquinas Virtuais

Esta seção mostra o status de todas as VMs dos usuários no laboratório.

  * **Visão Centralizada:** Veja quais usuários se registraram, o status de suas VMs (Parada, Em Execução, Atribuindo) e quantas horas de cota eles usaram.
  * **Ações Individuais:** Você pode iniciar, parar, reimplantar (recriar a partir do modelo) ou redefinir a senha de uma VM de usuário individualmente, o que é útil para suporte técnico.

### 2.3. Usuários

Gerencie quem tem acesso ao seu laboratório.

  * **Adicionar Usuários:** Adicione usuários manualmente por e-mail ou sincronize com um grupo do Microsoft Entra ID (antigo Azure AD) para gerenciamento automatizado.
  * **Cota de Horas:** Defina um número de horas que cada usuário pode usar sua VM. Isso é fundamental para o controle de custos. Você pode adicionar horas adicionais a todos ou a usuários específicos.
  * **Acesso Restrito:** Habilite a opção para que apenas os usuários adicionados à lista possam se registrar no laboratório, garantindo a segurança.

### 2.4. Agendas (Schedules)

Uma das ferramentas mais poderosas para automação e controle de custos.

  * **Eventos Agendados:** Crie eventos que iniciam e param automaticamente as VMs de todos os usuários em horários específicos. Ideal para aulas ou workshops com horários definidos.
  * **Tipos de Eventos:**
      * **Padrão:** Inicia as VMs em um horário e as desliga após um período.
      * **Somente Iniciar:** Apenas liga as VMs no horário agendado.
      * **Somente Parar:** Desliga todas as VMs em um horário específico (útil para o final do dia).
  * **Recorrência:** Configure os eventos para ocorrerem semanalmente, economizando tempo de gerenciamento.

### 2.5. Configurações do Laboratório

Ajustes finos sobre o comportamento do laboratório e a experiência do usuário.

  * **Encerramento Automático:** Configure políticas para desligar VMs automaticamente quando os usuários se desconectam ou quando as VMs estão ociosas por um determinado período. Isso é essencial para evitar custos desnecessários.
      * *Desconectar ao ocioso:* Desliga a VM se o usuário estiver conectado, mas sem atividade.
      * *Desligar quando os usuários se desconectam:* Desliga a VM assim que o usuário fecha a sessão de área de trabalho remota.
  * **Habilitar Conexão via RDP/SSH:** Escolha o protocolo de conexão. Para uma segurança aprimorada, você pode desabilitar o RDP/SSH direto e exigir que os usuários se conectem através do portal do Lab Services.
  * **Rede Avançada (Advanced Networking):** Por padrão, os laboratórios são isolados. Com a rede avançada, você pode conectar seu laboratório a uma rede virtual (VNet) do Azure, permitindo que as VMs do laboratório acessem recursos da sua rede privada, como servidores de arquivos, bancos de dados ou servidores de licença.

## 3\. Aparência e Acessibilidade

Embora o Azure Lab Services seja uma ferramenta técnica, ele oferece opções para melhorar a experiência do usuário.

  * **Tema do Portal do Azure:** Os usuários podem personalizar sua própria experiência no portal do Azure, escolhendo entre temas claros, escuros e de alto contraste, o que melhora a acessibilidade visual.
  * **Integração com o Microsoft Teams:** Você pode adicionar um link direto para o laboratório dentro de um canal do Microsoft Teams, criando um fluxo de trabalho integrado para estudantes e participantes de treinamento.
  * **Acessibilidade da VM:** As configurações de acessibilidade dentro da própria máquina virtual (por exemplo, no Windows ou Ubuntu) são totalmente personalizáveis no modelo. Você pode pré-instalar e pré-configurar lupas, leitores de tela e outras ferramentas de assistência.

## 4\. O que o Usuário Final Vê

A experiência do usuário final é simplificada para focar no acesso à sua máquina virtual.

1.  **Portal do Lab Services:** O usuário acessa um portal web simples (`https://labs.azure.com`).
2.  **Meus Laboratórios:** Ele vê uma lista de todos os laboratórios aos quais tem acesso.
3.  **Controles da VM:** Para cada laboratório, ele tem um "card" com:
      * Um botão para **iniciar/parar** sua VM.
      * Um indicador de status (Parada, Iniciando, Em Execução).
      * Um contador mostrando as **horas de cota restantes**.
      * Um botão para **conectar-se** à VM (que baixa um arquivo RDP/SSH).
      * Uma opção para **redefinir a senha**, se necessário.

Essa interface minimalista garante que mesmo usuários com pouco conhecimento técnico possam usar o ambiente de laboratório sem dificuldades.
