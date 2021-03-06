---

copyright:
  years: 2018, 2019
lastupdated: "2019-33-22"

Keywords: frequently asked questions, critical security parameters, cryptographic module, Security Level

subcollection: hs-crypto

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}

# Perguntas mais frequentes
{: #faqs}

É possível usar as seguintes Perguntas mais frequentes para ajudá-lo com o {{site.data.keyword.cloud}} {{site.data.keyword.hscrypto}}.

## Certificações do HSM
{: #HSM-certifications}

### Como posso validar se um IBM Crypto Card (HSM) foi validado para atender ao FIPS 140-2 Nível 4?
{: #FIPS-L4}

O FIPS 140-2 Nível 4 é um nível de proteção muito alto que não está amplamente disponível no mercado. A IBM é o principal fornecedor para HSMs certificados de nível mais alto e tem investido pesadamente para manter essa validação para cada nova geração de cartões. O requisito para o alto nível de garantia foi coletado de requisitos do governo. Para validação da certificação, você é direcionado para a página inicial do NIST porque a certificação foi publicada lá. 

### Qual é a diferença entre FIPS 140-2 Níveis 2, 3 e Nível 4?
{: #FIPS-levels}

* FIPS 140-2 Nível 2: requisitos para evidência de violação feita por selos, travas resistentes à escolha em tampas e portas removíveis. Revestimentos ou selos invioláveis são colocados em um módulo de criptografia para que o revestimento ou o selo seja quebrado para obter acesso físico às chaves criptográficas de texto sem formatação e aos critical security parameters (CSPs) dentro do módulo. O Nível de segurança 2 requer, no mínimo, a autenticação baseada em função, na qual um módulo de criptografia autentica a autorização de um operador para assumir uma função específica e executar um conjunto correspondente de serviços.
 
* FIPS 140-2 Nível 3: os mecanismos de segurança física necessários no Nível de segurança 3 são destinados a ter uma alta probabilidade de detecção e resposta a tentativas de acesso físico, uso ou modificação do módulo de criptografia. O Nível de segurança 3 requer mecanismos de autenticação baseada em identidade, aprimorando a segurança fornecida pelos mecanismos de autenticação baseada em função especificados para o Nível de segurança 2.  

* FIPS 140-2 Nível 4: nesse nível de segurança, os mecanismos de segurança física fornecem um envelope completo de proteção ao redor do módulo de criptografia com a intenção de detectar e responder a todas as tentativas não autorizadas no acesso físico. A penetração do invólucro do módulo de criptografia de qualquer direção tem uma probabilidade muito alta de ser detectada, resultando na imediata zeragem de todos os CSPs (Critical Security Parameters) de texto sem formatação. Os módulos de criptografia do Nível de segurança 4 são úteis para operação em ambientes fisicamente desprotegidos. O Nível de segurança 4 também protege um módulo de criptografia contra um compromisso de segurança devido a condições ou flutuações ambientais fora dos intervalos normais de operação do módulo para voltagem e temperatura. Excursões intencionais além dos intervalos normais de operação podem ser usadas por um invasor para impedir as defesas de um módulo de criptografia.   

## Gerenciamento de chave
{: #key-management}

### O {{site.data.keyword.hscrypto}} pode ser usado em combinação com o serviço {{site.data.keyword.keymanagementserviceshort}}?

 O {{site.data.keyword.hscrypto}} é um Serviço de criptografia gerenciado fornecido com uma API totalmente compatível do {{site.data.keyword.keymanagementserviceshort}}, que tem uma experiência de usuário idêntica ao do Key Protect. A principal diferença é que o {{site.data.keyword.hscrypto}} depende de um HSM que tenha sido certificado pelo FIPS 140-2 Nível 4. Além disso, ele fornece controle total com a chave mestra do HSM sendo gerenciada pelo cliente (KYOK). O serviço é dedicado por instância em comparação com a configuração de diversos locatários para o {{site.data.keyword.keymanagementserviceshort}}. O {{site.data.keyword.hscrypto}} também oferece recursos do HSM para operações criptográficas como assinatura/verificação, geração de chave, hashing criptográfico, criptografia/decriptografia e agrupamento/desagrupamento. 

### Qual é o limite de comprimento de um nome da chave?
{: #key_names}

É possível usar um nome da chave que tenha até 50 caracteres de comprimento.

### Posso usar caracteres de idioma como parte do nome da chave?
{: #key_chars}

Caracteres de linguagem, como caracteres chineses, não podem ser usados como parte do nome da chave.

### O que acontece quando eu excluo uma chave?
{: #key_destruction}

Quando você excluir uma chave, fragmentará permanentemente os seus conteúdos e os dados associados. Os dados que foram criptografados com a chave não serão mais acessíveis.

Antes de excluir uma chave, verifique se você não precisa mais de acesso a algum dado que esteja associado à chave.

<!-- ## Pricing
{: #pricing}

### Where can I find the detailed pricing information?
{: #pricing_info}

You can refer to the **Pricing** tab on the [{{site.data.keyword.hscrypto}} home page ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/hyper-protect-crypto){: new_window} for details.

### Is there a pricing example I can refer to?
{: #pricing_example}

Here is one. If you have a requirement of 5000 keys to be crypto-processed, for high availability, you need to set up two crypto units. The amount is $3140 ($1570 per crypto unit) per month. The first 1,000,000 API calls are free of charge. However, if you perform 2,000,000 API calls per month, you will be charged additional $1 ($0.01 per 10,000 API calls over 1,000,000 API calls). In total, there will be a monthly charge of $3141 ($3140 for the crypto units and $1 for the additional API calls) for your service instance.

The following table contains the pricing details.

| Pricing components | Cost per month |
|-----|----------------|
| Crypto unit 1 | $1570 |
| Crypto unit 2 | $1570 |
| First 1,000,000 API calls | $0 |
| 1,000,000 additional API calls (10,000 API calls x 100) | $1 ($0.01 x 100) |
| End of month charge | $3141  |

*Table 1. Charge of two crypto units with a monthly API calls of 2,000,000* -->
