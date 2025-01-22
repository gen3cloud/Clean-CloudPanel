# ⚡ Servidor CloudPanel Comprometido? Limpeza e Fortalecimento de Defesa! ⚡

🛡️ **Recentemente, servidores utilizando o CloudPanel como sistema de gerenciamento foram alvo de uma série de ataques** que exploraram vulnerabilidades de **zero-day** em versões anteriores à **V2.5.0**. Esses ataques resultaram em sérios comprometimentos, incluindo:

- ⚠️ Transformação de servidores em **botnets** para ataques **DDoS**.
- ⚠️ **Roubo de dados sensíveis**, como arquivos `.env` e `db.sq3`.
- ⚠️ **Escalonamento de privilégios**, permitindo o controle total do servidor.
- ⚠️ **Instalação de malwares**, desfiguração de sites e uso do servidor para **atividades ilegais**, como envio de **spam** e hospedagem de conteúdo malicioso.

🚀 **Boa notícia**: Já foi lançado um **patch** para corrigir essas falhas! Agora, é essencial que todos os usuários do CloudPanel atualizem para a versão mais recente **imediatamente**. ✅

---

## 🔧 **O que você encontrará aqui:**

Este repositório oferece um guia completo para:

- ❌ **Limpar servidores infectados**.
- ⬆ **Atualizar o CloudPanel para a versão mais recente**.

🔹 **Aviso Importante**: Embora o script fornecido tenha sido desenvolvido com base em análises de sistemas infectados, é fundamental lembrar que ele pode não ser uma solução única para todos os casos. ⚠️❤ **Recomenda-se realizar uma verificação minuciosa do sistema após a execução**.

🌐 **Precisa de mais segurança?** A [WPShield](https://wpshield.com.br) pode ajudar a proteger seu servidor contra ameaças como essas!

---

## **Explicação do Script de Limpeza:**

### **Função `install_freshclam()`**:
Verifica se o **freshclam** (ferramenta para atualizar as definições de vírus do ClamAV) está instalado. Caso contrário, o script realiza a instalação automaticamente.

### **Função `run_scan()`**:
Pergunta ao usuário se ele deseja executar uma varredura completa no sistema em busca de malwares. Se o usuário concordar, o script executa o **clamscan** com a opção recursiva (`-r /`), escaneando todos os arquivos do sistema. O resultado da varredura é armazenado na variável `scan_result`.

### **Função `delete_infected_files()`**:
Caso a varredura encontre arquivos infectados, o script lista esses arquivos e pede confirmação ao usuário. O usuário pode optar por deletá-los digitando 'y' ou 'Y'. Se confirmado, os arquivos são removidos do sistema.

### **Função `delete_user()`**:
Lista todos os usuários do sistema e verifica a presença de um usuário malicioso conhecido como **"dotsh"**. Se encontrado, o script solicita que o usuário forneça o nome do usuário a ser deletado, excluindo-o após confirmação.

### **Função `remove_attacker_public_key()`**:
O script verifica todos os usuários no sistema, procurando arquivos **authorized_keys** (usados para chaves SSH autorizadas). Se uma chave pública maliciosa (ex: `admin@test.com`) for encontrada, ela será removida. O processo continua até todos os usuários serem verificados.

### **Função `remove_bad_files()`**:
O script procura e remove arquivos maliciosos específicos, como **isbdd**, **ispdd** e **dotnet.x86**, do diretório **/tmp/**, caso existam.

### **Função `run_clp_update()`**:
Executa o comando `clp-update`, atualizando o CloudPanel para a versão mais recente, garantindo a correção de vulnerabilidades conhecidas.

### **Função `remove_cron_jobs()`**:
Busca e remove cron jobs maliciosos que referenciem o diretório **/tmp** para o usuário **clp**, eliminando possíveis agendamentos prejudiciais configurados pelos atacantes.

---

## **Objetivo do Script:**

Este script foi desenvolvido para:

- **Limpar servidores infectados**.
- **Atualizar o CloudPanel** para a versão mais recente.
- **Remover ameaças**, como arquivos maliciosos, usuários comprometidos, chaves SSH de atacantes e cron jobs maliciosos.

Executar este script é uma ótima medida para melhorar a segurança do servidor contra ameaças já conhecidas. No entanto, para manter seu servidor seguro, é fundamental realizar **monitoramento contínuo** e **atualizações periódicas**.
