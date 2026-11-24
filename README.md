# Validador de Dados Estruturados Schema.org

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Validador Schema](https://img.shields.io/badge/TAVARDT-Schema.org%20Validator-5b3cf5.svg)](https://tools.tavardt.com/pt/validador-dados-estruturados/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)

Auditoria de dados estruturados JSON-LD e Microdata, validacao de propriedades obrigatorias de entidades Schema.org e análise de fragmentos enriquecidos.

Desenvolvido e mantido pela divisao de arquitetura semantica da **TAVARDT Portugal**.

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

© 2026 TAVARDT Portugal. Todos os direitos reservados. Soberania e Defesa de Infraestrutura.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/
