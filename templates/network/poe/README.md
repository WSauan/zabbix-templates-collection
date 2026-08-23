# PoE (Power over Ethernet) Templates ⚡

Esta pasta contém templates focados no monitoramento de fornecimento de energia (PoE) por porta em switches de rede (gerenciamento de ativos como telefones IP, câmeras de CFTV e Access Points).

## 📁 Templates Disponíveis

### 1. `template_poe_universal.yaml` (Recomendado para a maioria do parque)
* **Padrão:** Baseado na **RFC 3621** (`POWER-ETHERNET-MIB`).
* **Compatibilidade:** Funciona em grande parte dos switches corporativos modernos do mercado que seguem o padrão da indústria (HP/Aruba, Cisco, etc.).
* **O que coleta:** 
  * Consumo de potência por porta em tempo real (convertido automaticamente de miliwatts para Watts).
  * Status da porta PoE (ex: Fornecendo Energia, Avaliando, Sobrecarga).

### 2. `template_huawei_poe.yaml` (Específico)
* **Padrão:** Baseado na MIB proprietária `HUAWEI-POE-MIB`.
* **Compatibilidade:** Exclusivo para switches da linha Huawei (VRP).
* **O que coleta:** 
  * Potência consumida (Watts).
  * Corrente fornecida (Amperes).
  * Voltagem atual da porta (Volts).

---

## 🛠️ Como Utilizar

1. Faça o download do arquivo `.yaml` correspondente ao seu fabricante.
2. No Zabbix Server, vá em **Data collection -> Templates** e clique em **Import**.
3. Associe o template ao host desejado (utilize a técnica de *Template Stacking* junto ao template de hardware do switch).
4. O Zabbix fará a descoberta automática: se a porta não for PoE ou se o switch for de modelo simples, a descoberta será ignorada silenciosamente sem gerar erros.