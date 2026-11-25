# Validador de Schema Markup e Dados Estruturados

[![Validador Schema](https://img.shields.io/badge/TAVARDT-Schema.org%20Validator-5b3cf5.svg)](https://tools.tavardt.com/pt/validador-dados-estruturados/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Auditoria de dados estruturados e marcacao Schema.org no espaco digital de Portugal, validando entidades semanticas e compatibilidade com motores de busca modernos.

Desenvolvido e mantido pela divisao de engenharia de busca e normas semanticas da **TAVARDT Portugal**.

***

## Capacidades de Validacao Semantica

* **Extracao de Dados Estruturados**: Análise de blocos JSON-LD (`application/ld+json`) e atributos semanticos Microdata.
* **Deteção de Entidades Centrais**: Identificacao de tipos normalizados Schema.org (Organization, LocalBusiness, WebSite, Article, Product, FAQPage).
* **Validacao de Integridade e Sintaxe**: Rastreio de erros no parse de JSON, links quebrados e omissao de propriedades requeridas.
* **Classificacao de Conformidade**: Avaliacao rigorosa de 0 a 100 com indicacoes de correcao para motores de busca globais.

***

## Instalação e Execucao

Requer Python 3.8 ou superior, utilizando unicamente a biblioteca padrao.

```bash
git clone https://github.com/TAVARDT-Portugal/schema-markup-validator-pt.git
cd schema-markup-validator-pt
python schema_validator.py exemplo.pt
```

Para exportacao em JSON:

```bash
python schema_validator.py exemplo.pt -json
```

***

## Plataforma Online de Validacao

Para auditorias semanticas continuas e análise de elegibilidade para Rich Snippets:

* **Validador de Dados Estruturados Oficial**
* **[Portal Corporativo TAVARDT](https://ag.tavardt.com/pt/)**

***

## Consultoria Semantica e Otimizacao Estruturada

Para apoio tecnico avancado de marcacao semantica segundo Padroes W3C e Diretrizes Semanticas Europeias, consulte a **TAVARDT**.

***



## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT. Consulte o arquivo [LICENSE](LICENSE) para obter detalhes completos.

***

© 2026 TAVARDT. All rights reserved.
