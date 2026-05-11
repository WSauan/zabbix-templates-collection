# Painel PowerBI - Telemetria Avançada 📊

Template focado em dashboards complexos do PowerBI que exigem garantia de atualização dos dados (Data Refresh).

## 👁️ Monitoramento via OCR
Diferente de um ping comum, este template utiliza o **Tesseract OCR** para tirar um print da tela, recortar a área onde fica a "Hora da Última Atualização" e transformar em texto para o Zabbix.

## 📥 Instalação do Script de Telemetria
Crie o arquivo `/usr/local/bin/get_pbi_time.sh`:

```bash
#!/bin/bash
export DISPLAY=:0
# Tira o print da tela inteira
import -window root /tmp/screenshot.png
# Recorta a área do relógio (ajuste as coordenadas X e Y conforme sua TV)
convert /tmp/screenshot.png -crop 150x30+1700+10 /tmp/clock_area.png
# Converte imagem em texto
tesseract /tmp/clock_area.png /tmp/pbi_time -l por > /dev/null 2>&1
cat /tmp/pbi_time.txt
```
## ⚙️ Macros Necessárias

Macro | Descrição
{$URL_POWERBI} | Link do dashboard publicado.
{$PBI_UPDATE_INTERVAL} | Tempo máximo aceitável sem atualização (Ex: 1h).
