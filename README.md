# Zabbix Infrastructure Monitoring 🚀

Repositório centralizado de templates e guias para monitoramento de infraestrutura corporativa utilizando **Zabbix 7.0**. Este projeto foca em soluções otimizadas para impressoras de rede e dashboards baseados em Raspberry Pi.

## 📂 Estrutura do Repositório

* **templates/printers/**: Templates SNMP otimizados para HP e OKI, com foco em contadores de página, suprimentos e status de hardware.
* **templates/raspberry/**: Soluções para Kiosks (SGA, Kanban, PowerBI), incluindo monitoramento de sub-voltagem, temperatura e processos de interface (Firefox/Kiosk).
* **scripts/**: Scripts de apoio para automação e coleta de dados nos Raspberrys.

## 🛠️ Requisitos
- **Zabbix Server/Proxy**: Versão 7.0 ou superior.
- **Protocolos**: SNMP v1/v2c (Impressoras) e Zabbix Agent (Raspberry Pi).
- **Hardware**: Raspberry Pi 3, 4 ou 5 rodando Raspberry Pi OS (Debian 12/13).

## 🚀 Como Utilizar

1.  **Impressoras**:
    * Vá em *Data collection* -> *Templates* -> *Import*.
    * Selecione o arquivo `.yaml` desejado na pasta `templates/printers/`.
    * Certifique-se de que o Host possui a interface SNMP configurada corretamente (Porta 161).

2.  **Raspberry Pi**:
    * Importe o template base `Raspberry Kiosk SGA.yaml`.
    * Siga o guia específico dentro de `templates/raspberry/[pasta]/` para instalar as dependências necessárias no sistema operacional.

## 📝 Notas de Versão
- **v1.0**: Ajuste global de UUIDs para o padrão v4 e correção de OIDs para modelos OKI específicos.
