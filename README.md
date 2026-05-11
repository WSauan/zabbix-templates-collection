# IT Infrastructure Monitoring - Zabbix 7.0 🚀

Este repositório reúne templates profissionais e scripts de automação para monitoramento de ativos de TI, focado em alta disponibilidade e telemetria avançada.

## 📂 Organização do Projeto

* **[Templates/Printers](./templates/printers/)**: Monitoramento de impressoras HP e OKI (Suprimentos, Contadores e Status).
* **[Templates/Raspberry](./templates/raspberry/)**: Soluções para Kiosks (SGA, Kanban e PowerBI).
* **[Scripts](./scripts/raspberry/)**: Inteligência externa para OCR e automação de interface.

## 🛠️ Tecnologias Utilizadas
- **Zabbix 7.0**: Exportação em formato YAML com UUIDs v4.
- **SNMP v1/v2c**: Para comunicação com ativos de rede.
- **Tesseract OCR**: Para leitura de telas de PowerBI.
- **JavaScript**: Para pré-processamento e limpeza de dados no Zabbix.

## 🚀 Como Começar
1. Importe os templates da pasta `templates/` para o seu Zabbix.
2. Configure as **Macros** necessárias (como `{$URL_KANBAN}`) nos Hosts.
3. Instale as dependências nos Raspberrys seguindo o [Guia de Instalação](./templates/raspberry/README.md).

---
**Desenvolvido por seu_nome** - Focado em Infraestrutura Corporativa.
