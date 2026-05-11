# Monitoramento de Kiosks Raspberry Pi 🖥️

Este diretório contém os templates voltados para Raspberry Pi (modelos 3, 4 e 5) configurados como painéis de monitoramento (Kiosk Mode).

## 🛠️ Preparação do Sistema (Raspberry Pi OS)

Para que todos os itens dos templates funcionem (especialmente a detecção de processos e automação de interface), execute os seguintes comandos no terminal do Raspberry:

### Atualize o sistema
sudo apt update && sudo apt upgrade -y

### Instale as dependências de monitoramento e automação
sudo apt install zabbix-agent xdotool -y

### (Opcional) Se usar o monitoramento de PowerBI com análise de imagem
sudo apt install tesseract-ocr -y

## 📋 Templates Disponíveis

- 1. Raspberry Kiosk SGA (Base)
Template fundamental que deve ser aplicado a todos os dispositivos.

Foco: Saúde do hardware.

Alertas: Sub-voltagem (essencial para RPi), temperatura da CPU, uso de memória e espaço em disco.

- 2. Painel Kanban
Destinado a TVs que exibem o fluxo de trabalho.

Configuração: Monitora se o processo do Firefox está em execução e se a URL do Kanban está acessível.

Dica: Utilize a Macro {$URL_KANBAN} no Host para definir o endereço específico.

- 3. Painel PowerBI
Otimizado para dashboards de BI que exigem atualização constante.

Recurso: Monitoramento do tempo de atualização da página.

Automação: Integrado com scripts que utilizam o xdotool para simular o "F5" ou interações necessárias para manter o login ativo.

## ⚙️ Configuração do Zabbix Agent
No arquivo /etc/zabbix/zabbix_agentd.conf, certifique-se de que as permissões permitem a execução de comandos remotos, caso utilize scripts de recuperação (como reiniciar o Firefox):

AllowKey=system.run[*]
Server=IP_DO_SEU_ZABBIX


Erro de Sub-voltagem: Verifique a fonte de alimentação. Raspberry Pis exigem fontes estáveis (mínimo 3A para RPi 4/5).
Firefox não detectado: Verifique se o nome do processo no template coincide com a versão instalada (ex: firefox-esr vs firefox).
