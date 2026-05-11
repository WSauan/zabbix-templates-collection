# Painel Kanban - Monitoramento de Fluxo 📋

Este template é otimizado para a exibição contínua de quadros Kanban (Trello, Jira, ClickUp, etc.) em Raspberry Pi 3 ou superior.

## 🚀 Funcionalidades
- **Monitoramento de Processo**: Alerta se o Firefox/Chromium fechar.
- **Validação de Conteúdo**: O Zabbix verifica se uma palavra-chave (ex: "To Do") está presente na tela.
- **Auto-Healing**: Possibilidade de reiniciar o navegador remotamente via Zabbix.

## 🛠️ Configuração do Script de Inicialização
Recomenda-se o uso de um script `run_kiosk.sh` na home do usuário:

```bash
#!/bin/bash
# Desativa proteção de tela e gerenciamento de energia
xset s off
xset s noblank
xset -dpms

# Abre o navegador em modo Kiosk
firefox-esr --kiosk "{$URL_KANBAN}" &
```

## ⚙️ Macros Necessárias
Configure estas macros no Host dentro do Zabbix:

Macro	| Descrição	| Exemplo
{$URL_KANBAN}	| URL completa do quadro| https://kanban.empresa.com
{$TEXTO_VALIDACAO} | Palavra que deve existir na página |	A Fazer
