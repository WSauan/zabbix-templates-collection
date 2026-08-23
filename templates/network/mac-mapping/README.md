# Zabbix Network Templates 🚀

Este repositório contém templates otimizados para o Zabbix, focados no monitoramento de infraestrutura de redes (Switches L2/L3). A abordagem utilizada foca na extração inteligente de dados via LLD (Low-Level Discovery) e pré-processamento via JavaScript para manter o banco de dados do Zabbix leve e performático.

## 📁 Diretório: `network/mac-mapping/`

Contém templates para mapeamento automático de endereços MAC por porta física. Este recurso elimina a necessidade de "bater cabo" fisicamente no rack, entregando a localização exata dos dispositivos (telefones, câmeras, PCs) diretamente na interface do Zabbix.

### Diferenciais destes templates:
- **Filtro Anti-Trunk Automático:** Um script JavaScript nativo analisa a contagem de MACs por porta antes da criação dos itens. Portas com mais de 55 MACs (uplinks, trunks, cascatas) são silenciosamente ignoradas. Isso evita a criação de milhares de itens inúteis no banco de dados.
- **Conversão Hexadecimal:** Converte o OID SNMP de formato decimal diretamente para o formato padrão de MAC (AA:BB:CC:DD:EE:FF).

### Templates Disponíveis:

#### 1. `template_mac_mapping_qbridge.yaml`
- **Recomendado para:** Switches gerenciáveis modernos (Aruba, HP, Cisco) que suportam a MIB Q-BRIDGE (`1.3.6.1.2.1.17.7.1.2.2.1.2`).
- **Vantagem:** Extrai nativamente a VLAN de cada MAC conectado e permite a criação de Tags de identificação personalizadas (ex: "VLAN 10 - Gerência").

#### 2. `template_mac_mapping_bridge_classica.yaml`
- **Recomendado para:** Switches Huawei, modelos legados ou equipamentos que não expõem a tabela de VLANs na MIB Q-BRIDGE.
- **Como funciona:** Utiliza a BRIDGE-MIB tradicional (`1.3.6.1.2.1.17.4.3.1.2`). Não mapeia a VLAN, mas garante a localização precisa da porta física.

## 🛠️ Como utilizar (Deploy)

1. Faça o download do arquivo `.yaml` desejado.
2. No seu Zabbix Server, navegue até **Data collection -> Templates**.
3. Clique em **Import** e selecione o arquivo baixado.
4. (Opcional - Apenas Q-BRIDGE): Edite a regra de pré-processamento JavaScript do LLD para adicionar o dicionário de nomes das VLANs do seu ambiente.
5. Associe o template ao Host desejado (Recomendamos utilizar a técnica de *Template Stacking*, mantendo seu template de hardware do fabricante juntamente com este).
