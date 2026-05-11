# Monitoramento de Kiosks Raspberry Pi 🖥️

Este diretório contém os templates voltados para Raspberry Pi (modelos 3, 4 e 5) configurados como painéis de monitoramento (Kiosk Mode).

## 🛠️ Preparação do Sistema (Raspberry Pi OS)

Para que todos os itens dos templates funcionem (especialmente a detecção de processos e automação de interface), execute os seguintes comandos no terminal do Raspberry:

# Atualize o sistema
sudo apt update && sudo apt upgrade -y

# Instale as dependências de monitoramento e automação
sudo apt install zabbix-agent xdotool -y

# (Opcional) Se usar o monitoramento de PowerBI com análise de imagem
sudo apt install tesseract-ocr -y
