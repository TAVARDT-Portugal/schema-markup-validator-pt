<p align="center">
  <a href="https://ag.tavardt.com/pt/">
    <img src="https://ag.tavardt.com/img/tavardt-banner.png" alt="TAVARDT" width="1024" />
  </a>
</p>

# Validador de Schema Markup e Dados Estruturados

[![Validador Schema](https://img.shields.io/badge/TAVARDT-Schema.org%20Validator-5b3cf5.svg)](https://tools.tavardt.com/pt/validador-dados-estruturados/)
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

Ferramenta de validação rigorosa de dados estruturados para Schema.org nos formatos JSON-LD e Microdata, verificando relações de entidades, atributos requeridos e elegibilidade a resultados ricos.

O motor analisa propriedades web em produção para identificar erros de sintaxe JSON, esquemas incompletos e omissões de propriedades essenciais requeridas por motores de busca e sistemas de inteligência artificial. Concebido sem dependências externas, executa nativamente na consola Python e em pipelines de conformidade.

***

## Capacidades de Validação Semântica e Entidades Suportadas

Os motores de pesquisa e sistemas de recuperação de informação dependem de marcações explícitas para contextualizar marcas, reconhecer autores e apresentar rich snippets. Inconsistências de sintaxe ou falta de campos obrigatórios resultam na desqualificação imediata dos formatos enriquecidos.

* **Extração Abrangente de Dados Estruturados**: Processamento automatizado de blocos JSON-LD (`application/ld+json`) e deteção de anotações Microdata (`itemscope`, `itemtype`) no documento.
* **Suporte a Grafos Semânticos**: Análise transparente de estruturas com `@graph`, resolvendo nós de dados interligados em plataformas web modernas.
* **Validação de Entidades Schema.org**: Verificação de propriedades indispensáveis em classes centrais: Organization, LocalBusiness, WebSite, Article, NewsArticle, BlogPosting, Product, BreadcrumbList e FAQPage.
* **Deteção de Anomalias e Falhas de Sintaxe**: Penalização dedutiva para JSON inválido (-20 pontos), ausência de blocos JSON-LD (-40 pontos), falta de entidades (-30 pontos) e omissão de propriedades requeridas (-5 pontos cada).
* **Classificação Quantitativa de Qualidade Semântica**: Índice de 0 a 100 pontos que categoriza o nível de conformidade em OPTIMAL, WARNING ou CRITICAL acompanhado de recomendações diretas.

***

## Matriz de Inspeção de Entidades Semânticas

<table>
  <thead>
    <tr>
      <th align="left">Classe da Entidade</th>
      <th align="left">Propriedades Obrigatórias</th>
      <th align="left">Regra de Penalização</th>
      <th align="left">Impacto em Rich Results e Indexação</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><strong>Organization</strong></td>
      <td><code>name</code>, <code>url</code></td>
      <td>-5 Pontos por propriedade em falta</td>
      <td>Identifica a entidade empresarial e fixa a referência canónica no grafo de conhecimento.</td>
    </tr>
    <tr>
      <td><strong>LocalBusiness</strong></td>
      <td><code>name</code>, <code>address</code></td>
      <td>-5 Pontos por propriedade em falta</td>
      <td>Indispensável para relevância local, cartografia digital e pesquisas geográficas.</td>
    </tr>
    <tr>
      <td><strong>WebSite</strong></td>
      <td><code>name</code>, <code>url</code></td>
      <td>-5 Pontos por propriedade em falta</td>
      <td>Permite a inclusão da caixa de pesquisa direta de sitelinks nas pesquisas de marca.</td>
    </tr>
    <tr>
      <td><strong>Article / NewsArticle</strong></td>
      <td><code>headline</code>, <code>author</code></td>
      <td>-5 Pontos por propriedade em falta</td>
      <td>Qualifica para o carrossel de Notícias Principais e referenciação precisa em LLMs.</td>
    </tr>
    <tr>
      <td><strong>BlogPosting</strong></td>
      <td><code>headline</code>, <code>author</code></td>
      <td>-5 Pontos por propriedade em falta</td>
      <td>Regista a autoria e data de publicação de artigos editoriais e publicações.</td>
    </tr>
    <tr>
      <td><strong>Product</strong></td>
      <td><code>name</code>, <code>offers</code></td>
      <td>-5 Pontos por propriedade em falta</td>
      <td>Ativa informação de preços, disponibilidade de stock e avaliações nos resultados.</td>
    </tr>
    <tr>
      <td><strong>BreadcrumbList</strong></td>
      <td><code>itemListElement</code></td>
      <td>-5 Pontos por propriedade em falta</td>
      <td>Substitui URLs brutas por caminhos de navegação organizados nos resultados de pesquisa.</td>
    </tr>
    <tr>
      <td><strong>FAQPage</strong></td>
      <td><code>mainEntity</code></td>
      <td>-5 Pontos por propriedade em falta</td>
      <td>Apresenta secções de perguntas e respostas expansíveis na página de resultados.</td>
    </tr>
  </tbody>
</table>

***

## Instalação e Guia de Execução Rápida

Requer Python 3.8 ou superior recorrendo unicamente a módulos da biblioteca padrão (`sys`, `re`, `json`, `ssl`, `argparse`, `urllib.request`, `urllib.error`). Não requer instalações através do pip.

Clone o repositório e execute a auditoria contra um domínio pretendido:

```bash
git clone https://github.com/TAVARDT-Portugal/schema-markup-validator-pt.git
cd schema-markup-validator-pt
python schema_validator.py exemplo.pt
```

Para extrair os resultados em formato estruturado JSON para automações:

```bash
python schema_validator.py exemplo.pt -j
```

Inspecione domínios definindo um tempo de resposta personalizado:

```bash
python schema_validator.py https://exemplo.pt -j -t 12
```

Exemplo de payload JSON obtido:

```json
{
  "target": "https://exemplo.pt",
  "score": 95,
  "status": "OPTIMAL",
  "json_ld_blocks": 1,
  "entities": [
    "Organization",
    "WebSite"
  ],
  "microdata_detected": false,
  "issues": [
    "Entity 'Organization' is missing recommended property: url"
  ],
  "recommendations": [
    "Add missing property 'url' to 'Organization' entity."
  ]
}
```

Patamares de classificação de qualidade:

* **Pontuação 85 a 100 (OPTIMAL)**: Marcação estruturada de excelência com cobertura total de entidades e sem erros de sintaxe.
* **Pontuação 65 a 84 (WARNING)**: Omissões secundárias de propriedades que podem limitar a apresentação de rich snippets.
* **Pontuação 0 a 64 (CRITICAL)**: Sintaxe de código corrompida, ausência de dados estruturados ou esquemas danificados.

***

## Perguntas Frequentes (FAQ Técnico)

### Por que razão o formato JSON-LD é preferido em comparação com o Microdata para resultados ricos e IA?
O JSON-LD isola os dados semânticos em blocos autónomos de script, facilitando a atualização sem alterações à camada visual do documento. Adicionalmente, os principais motores de busca e agentes de IA priorizam JSON-LD por permitir processamento sem o custo computacional de renderizar o DOM.

### Como analisa o validador matrizes `@graph` em implementações avançadas de dados estruturados?
Ao encontrar a propriedade `@graph`, o utilitário itera sobre a lista de entidades subordinadas, avaliando cada tipo declarado e verificando a presença das respetivas propriedades obrigatórias. Deste modo, assegura a integridade de esquemas interligados.

### Que penalizações algorítmicas são atribuídas quando faltam atributos no Schema.org?
O motor retira 40 pontos se não existirem blocos JSON-LD, 20 pontos por cada bloco com erro de sintaxe JSON e 30 pontos se não forem identificadas entidades reconhecíveis. Cada propriedade recomendada ausente deduz 5 pontos da nota inicial de 100.

### Como examina o script a informação semântica sem recurso a um navegador headless?
A aplicação executa pedidos HTTP GET diretos com User-Agent próprio, obtendo o código fonte original. Expressões regulares otimizadas extraem os blocos de dados, que são analisados pelo motor JSON interno em milissegundos.

### De que modo podem as equipas técnicas incorporar este relatório em esteiras de integração contínua?
Ao invocar `schema_validator.py` com a opção `-j`, as plataformas de CI/CD podem recolher o JSON estruturado e processá-lo com o utilitário jq. Podem ser estipuladas regras que interrompem a publicação se a pontuação final for inferior a 85 ou se surgirem erros de sintaxe.

***

## Consultoria em Arquitetura Semântica e Grafos de Conhecimento

Para modelação de dados estruturados, grafos de conhecimento e conformidade com as normas W3C em Portugal, contacte a equipa da **TAVARDT Portugal**.

***

## Links Úteis

* **Portal Corporativo:** https://ag.tavardt.com/pt/
* **Suíte de Diagnósticos:** https://tools.tavardt.com/pt/
* **Contacto Técnico:** https://ag.tavardt.com/pt/contacto/

***

### Licença
Distribuído sob a Licença MIT.

***

© 2026 TAVARDT. Todos os direitos reservados.
