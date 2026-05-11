# Scripts e Parâmetros para Raspberry Pi 🛠️

Este diretório contém os scripts de automação e arquivos de configuração necessários para o pleno funcionamento dos templates de monitoramento.

## 1. Monitoramento de Energia (Undervoltage)

Para detectar se o Raspberry está recebendo energia insuficiente, crie o arquivo de configuração no agente:

**Caminho:** `/etc/zabbix/zabbix_agent2.d/raspberry.conf`
**Conteúdo:**
```conf
UserParameter=rpi.undervoltage,vcgencmd get_throttled | cut -d'=' -f2
```

## 2. Telemetria de PowerBI (OCR)Este script captura a tela do Kiosk, recorta a área do relógio e converte em texto para o Zabbix validar a última atualização.
Arquivo: /usr/local/bin/get_pbi_time.sh
Permissão necessária: sudo chmod +x /usr/local/bin/get_pbi_time.sh
```bash
	#!/bin/bash

	export DISPLAY=:0

	# Tira o print da tela inteira
	import -window root /tmp/screenshot.png

	# Recorta a área do relógio (Ajuste X e Y conforme sua tela)
	# LARGURAxALTURA+X+Y
	convert /tmp/screenshot.png -crop 150x30+1700+10 /tmp/clock_area.png

	# Transforma a imagem em texto (OCR)
	tesseract /tmp/clock_area.png /tmp/pbi_time -l por > /dev/null 2>&1
	cat /tmp/pbi_time.txt
```
## 🔍 Comandos de Diagnóstico
Utilize estes comandos no terminal do Raspberry para testar o funcionamento:
### Objetivo | Comando
- Testar OCR | zabbix_agent2 -t pbi.last_update
- Print Manual | DISPLAY=:0 scrot /tmp/teste.png
- Simular Enter | DISPLAY=:0 xdotool key Return
- Simular F5 | DISPLAY=:0 xdotool key F5


## 2. Telemetria de PowerBI (OCR)

Este script captura a tela do Kiosk, recorta a área do relógio e converte em texto para o Zabbix validar a última atualização.

Arquivo: `/usr/local/bin/get_pbi_time.sh`
Permissão necessária: `sudo chmod +x /usr/local/bin/get_pbi_time.sh`
```bash
	#!/bin/bash
	export DISPLAY=:0
	
	# Tira o print da tela inteira
	import -window root /tmp/screenshot.png
	
	# Recorta a área do relógio (Ajuste X e Y conforme sua tela)
	# LARGURAxALTURA+X+Y
	convert /tmp/screenshot.png -crop 150x30+1700+10 /tmp/clock_area.png
	
	# Transforma a imagem em texto (OCR)
	tesseract /tmp/clock_area.png /tmp/pbi_time -l por > /dev/null 2>&1
	cat /tmp/pbi_time.txt
```

## 🔍 Comandos de Diagnóstico
Utilize estes comandos no terminal do Raspberry para testar o funcionamento:

Objetivo	Comando
Testar OCR	zabbix_agent2 -t pbi.last_update
Print Manual	DISPLAY=:0 scrot /tmp/teste.png
Simular Enter	DISPLAY=:0 xdotool key Return
Simular F5	DISPLAY=:0 xdotool key F5
