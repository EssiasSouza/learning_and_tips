### TIPS

To deactivate PowerShall terminal command suggestions
```
Set-PSReadLineOption -PredictionSource None
```

Set-PSReadLineOption -PredictionSource History
```
Set-PSReadLineOption -PredictionSource None
```

Extra: If you wanna keep, but remove "ghost" mode (inline gray text)
```
Set-PSReadLineOption -PredictionViewStyle ListView
```

### ATALHOS

Abrir command palet:
CTRL+SHIF+P para abrir 

Criar projeto flutter
flutter: new project

## RODAR NO WSL

- 1 - Abrir o VSCode
- 2 - Clicar em More abaixo do `Getting start with Coontainer Tools`
- 3 - Clicar em `Get started with WSL`
- 4 - Clicar no botão `Open the menu`
- 5 - Clicar em Conect to WSL
- 6 - Clicar em Go back
- 7 - Clicar em Open folder (O caminho já vai aparecer como /home/user)

## REMOTE SSH

### ✅ O que você precisa:

1. **VS Code instalado na sua máquina local**
2. **Extensão Remote - SSH instalada**
3. **Acesso SSH ao computador remoto** (com IP ou hostname, usuário e senha ou chave privada)

---

### 🔧 Como configurar:

#### 1. Instalar a extensão "Remote - SSH"

No VS Code:

* Vá para o menu lateral de extensões (ícone de quadrado com 4 blocos)
* Pesquise por `Remote - SSH`
* Clique em **Instalar**

#### 2. Abrir o VS Code com acesso ao servidor remoto:

* Pressione `Ctrl+Shift+P` e digite: `Remote-SSH: Connect to Host...`
* Adicione o host remoto, por exemplo:

  ```
  essias@192.168.0.100
  ```

  ou com nome DNS:

  ```
  essias@meuserver.dyndns.org
  ```

#### 3. (Opcional) Editar o arquivo de configuração SSH:

Você pode editar manualmente o arquivo `~/.ssh/config` para adicionar o servidor:

```ssh
Host meu-servidor
    HostName 192.168.0.100
    User essias
    Port 22
```

Depois, basta se conectar com:

```
Remote-SSH: Connect to Host... → meu-servidor
```

---

### 🧠 O que acontece por trás:

O VS Code instala automaticamente um pequeno **server headless** no host remoto. Esse server permite que você edite, rode e depure o código como se estivesse localmente — com suporte a terminal, linting, Git, depuração, etc.

---

### ✅ Funciona com:

* **Linux remoto → Windows ou Linux local**
* **Raspberry Pi**
* **WSL (usando `Remote - WSL`)**
* **Containers (`Remote - Containers`)**
* **Máquinas virtuais em nuvem (AWS, Azure, etc.)**


# ERRORS
.../venv/Scripts/Activate.ps1"
& : File C:\Users\essias.souza\OneDrive - Corpay\DEV\DEV-PROD\Automible\venv\Scripts\Activate.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies  
at https:/go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:3

- To check:
```
Get-ExecutionPolicy -List
```
- To solve:
```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```
