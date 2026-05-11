# Monitoramento de Impressoras Corporativas 🖨️

Este diretório contém templates SNMP otimizados para frotas de impressoras HP e OKI, focados em gestão de suprimentos e continuidade operacional.

## 🛠️ Configuração de Rede (SNMP)

Para que o Zabbix consiga recolher os dados, as impressoras devem estar configuradas da seguinte forma:

* **Protocolo**: SNMP v1 ou v2c (v1 recomendado para maior compatibilidade com modelos antigos).
* **Community**: `public` (ou a community definida na sua rede).
* **Porta**: 161 (UDP).

## 📊 Recursos Monitorados

| Recurso | Descrição |
| :--- | :--- |
| **Suprimentos** | Descoberta automática de toners, tambores e kits de manutenção com cálculo de % restante. |
| **Contadores** | Total de impressões acumulado e cálculos de volume (24h, 7 dias, 30 dias). |
| **Status Físico** | Alertas de atolamento de papel (Paper Jam), porta aberta e falta de papel. |
| **Inventário** | Recolha automática de Número de Série e Modelo via SNMP. |

## 🚀 Como Implementar

1. Importe o ficheiro `.yaml` correspondente à marca no Zabbix.
2. No Host da impressora, adicione a **Interface SNMP**.
3. Associe o template e aguarde o intervalo de descoberta (LDR) para os suprimentos aparecerem.

---
[Guia Específico HP](./hp/README.md) | [Guia Específico OKI](./oki/README.md)
