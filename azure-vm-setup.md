# (Guia Rápido): Azure VM com Terraform

Este guia detalha os blocos e opções essenciais para provisionar uma infraestrutura básica de Máquina Virtual no Azure.

## 1. Pré-requisitos

* **Azure CLI** instalado e logado (`az login`).
* **Terraform** instalado (v1.0+ recomendado).
* Uma **Subscription** ativa no Azure.

---

## 2. Estrutura do Código

Para criar uma VM, o Terraform precisa de uma hierarquia de recursos. Sem rede, não há VM.

### Bloco de Provedor (Provider)

O primeiro passo é declarar que você usará o Azure.

```hcl
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "~> 3.0"
    }
  }
}

provider "azurerm" {
  features {} # Obrigatório para o Azure
}

```

---

## 3. Definição dos Recursos

Abaixo estão as opções comuns divididas por categorias:

### A. Grupo de Recursos e Rede

Todo recurso no Azure deve pertencer a um grupo.

```hcl
resource "azurerm_resource_group" "rg" {
  name     = "rg-terraform-producao"
  location = "East US" # Ex: Brazil South, West US
}

resource "azurerm_virtual_network" "vnet" {
  name                = "vnet-projeto"
  address_space       = ["10.0.0.0/16"]
  location            = azurerm_resource_group.rg.location
  resource_group_name = azurerm_resource_group.rg.name
}

resource "azurerm_subnet" "subnet" {
  name                 = "internal"
  resource_group_name  = azurerm_resource_group.rg.name
  virtual_network_name = azurerm_virtual_network.vnet.name
  address_prefixes     = ["10.0.2.0/24"]
}

```

### B. Interface de Rede (NIC)

A NIC liga a VM à Subnet.

```hcl
resource "azurerm_network_interface" "nic" {
  name                = "nic-vm-01"
  location            = azurerm_resource_group.rg.location
  resource_group_name = azurerm_resource_group.rg.name

  ip_configuration {
    name                          = "internal"
    subnet_id                     = azurerm_subnet.subnet.id
    private_ip_address_allocation = "Dynamic" # Ou "Static"
    # public_ip_address_id = azurerm_public_ip.pip.id (Opcional)
  }
}

```

### C. A Máquina Virtual (Linux)

Aqui definimos o tamanho e a imagem do SO.

```hcl
resource "azurerm_linux_virtual_machine" "vm" {
  name                = "vm-app-01"
  resource_group_name = azurerm_resource_group.rg.name
  location            = azurerm_resource_group.rg.location
  size                = "Standard_B1s" # Opção barata para testes
  admin_username      = "adminuser"

  network_interface_ids = [
    azurerm_network_interface.nic.id,
  ]

  # Autenticação via SSH
  admin_ssh_key {
    username   = "adminuser"
    public_key = file("~/.ssh/id_rsa.pub")
  }

  # Disco de Sistema Operacional
  os_disk {
    caching              = "ReadWrite"
    storage_account_type = "Standard_LRS" # Opções: Standard_LRS, Premium_LRS
  }

  # Imagem do Marketplace (Ubuntu 22.04)
  source_image_reference {
    publisher = "Canonical"
    offer     = "0001-com-ubuntu-server-jammy"
    sku       = "22_04-lts"
    version   = "latest"
  }
}

```

---

## 4. Tabela de Referência de Opções (Tamanhos e Discos)

| Parâmetro | Opções Comuns | Descrição |
| --- | --- | --- |
| `size` | `Standard_B1s`, `Standard_D2s_v3` | B1s é ideal para labs (1 vCPU, 1GB RAM). |
| `storage_account_type` | `Standard_LRS`, `Premium_LRS` | LRS é o armazenamento localmente redundante (mais barato). |
| `admin_password` | *String* | Use apenas se `disable_password_authentication = false`. |
| `location` | `brazilsouth`, `eastus` | Região geográfica onde os dados residem. |

---

## 5. Comandos para Executar

1. `terraform init`: Instala o plugin do Azure.
2. `terraform plan`: Valida o que será criado.
3. `terraform apply -auto-approve`: Cria a infraestrutura.
4. `terraform destroy`: Remove tudo para evitar cobranças.
