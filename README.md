# Artefatos da RNDS "ajustados" e empacotados em NPM Package

O conteúdo de dados enviados para a RNDS (_payload_) pode
ser validado por meio de artefatos FHIR disponibilizados pelo Ministério da Saúde (Brasil).

> O presente projeto realiza "ajustes" nos artefatos visando a produção de um NPM Package.

**IMPORTANTE**: este conteúdo não é produzido pelo Ministério da Saúde (Brasil). Nenhuma garantia é oferecida. Trata-se de um trabalho em andamento.

# Guia de mudanças

## Descrição

Mudanças foram feitas nos arquivos disponibilizados pela RNDS no [simplifier](https://simplifier.net/RedeNacionaldeDadosemSaude) para ficarem compativeis com o padrão FHIR, versão R4. Essas mudanças são mínimas e visam manter total coerência com os artefatos originais disponibilizados.

| Resource Type       | arquivo                                                                              | ERRO                                                                                                                                                                                                                              | Mudança                                                                                                                                                                                                                                                                                                        |
| ------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| StructureDefinition | StructureDefinition-BRAgendamentoRegulacaoAssistencial                               | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BRStatusAgendamentoRegulacaoAssistencial a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável, do tipo required | Substitui o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BRStatusAgendamentoRegulacaoAssistencial pelo original http://hl7.org/fhir/ValueSet/appointmentstatus, tendo em vista que o Value Set brasileiro é apenas uma tradução do oficial.                                                              |
| CodeSystem          | CodeSystem-BRCondicaoMaternal                                                        | Tanto a variável "meta.lastUpdate" quanto a variável "date" estão no formato errado                                                                                                                                               | Foi adicionado "Z" ao final do valor das variáveis para indicar o fuso horário.                                                                                                                                                                                                                                 |
| ConceptMap          | ConceptMap-COVID-19VaccineMarketingAuthorizationHolderManufacturerBRImunobiologicoUE | Elemento "id" ultrapassava o limite superior de 64 caracteres                                                                                                                                                                     | Substitui o id COVID-19VaccineMarketingAuthorizationHolderManufacturerBRImunobiologicoUE por cOVID-19VaccineMarketingAuthorizationManufacturerBRImunobiologico, como "id" é um identificador lógico, servindo somente para identifica-lo no servidor local, essa mudança não o afeta.                          |
| ConceptMap          | ConceptMap-BRImunobiologicoUECOVID-19VaccineMarketingAuthorizationHolderManufacturer | Elemento "id" ultrapassava o limite superior de 64 caracteres                                                                                                                                                                     | Substitui o id ImunobiologicoUECOVID-19VaccineMarketingAuthorizationHolderM por ImunobiologicoCOVID-19VaccineMarketingAuthorizationM, como "id" é um identificador lógico, servindo somente para identifica-lo no servidor local, essa mudança não o afeta.                                                    |
| ValueSet            | ValueSet-BRGrupoAtendimento-1.0                                                      | A variável "date" esta no formato errado                                                                                                                                                                                          | Foi adicionado "Z" ao final do valor da variável para indicar o fuso horário.                                                                                                                                                                                                                                  |
| StructureDefinition | StructureDefinition-BRRegistroImunobiologicoAdministradoRotina-1.0                   | A variável "date" esta no formato errado                                                                                                                                                                                          | Foi adicionado "Z" ao final do valor da variável para indicar o fuso horário.                                                                                                                                                                                                                                  |
| ValueSet            | ValueSet-BRTipoDocumento-1.0                                                         | Duplicidade de instâncias desse Value Set                                                                                                                                                                                         | Uma dessas instâncias foi deletada.                                                                                                                                                                                                                                                                            |
| CodeSystem          | CodeSystem-BRNomeExameLOINC                                                          | Duplicidade de instâncias desse Code System                                                                                                                                                                                       | Uma dessas instâncias foi deletada.                                                                                                                                                                                                                                                                            |
| CodeSystem          | CodeSystem-BROrgaoExpedidor                                                          | Códigos duplicados, todos os códigos de um Code System devem ser únicos                                                                                                                                                           | Uma das definições dos códigos foi deleta. Code = CRBM.                                                                                                                                                                                                                                                        |
| CodeSystem          | CodeSystem-BRTipoIdentificador                                                       | Códigos duplicados, todos os códigos de um Code System devem ser únicos                                                                                                                                                           | Uma das definições dos códigos foi deleta. Code = BRACRBM.                                                                                                                                                                                                                                                     |
| CodeSystem          | CodeSystem-BRMedicamento                                                             | Códigos duplicados, todos os códigos de um Code System devem ser únicos                                                                                                                                                           | Uma das definições dos códigos foi deleta. Códigos duplicados: BR0272780U0042, BR0268345U0042, BR0328810U0087, BR0340783U0087, BR0267271U0042, BR0268084U0042, BR0340783U0062, BR0278283U0042, BR0296742, BR0273675, BR0420463, BR0292240, BR0363056U0106 e BR0449186.                                  |
| StructureDefinition    | StructureDefinition-BRImunobiologicoAdministrado-2.0                                 | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoEvento-1.0 a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável, do tipo required                       | Substituição o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoEvento-1.0 pelo original http://hl7.org/fhir/ValueSet/immunization-status. O Value Set Brasileiro engloba mais definições do que são restritas pelo conjunto do Value Set original, podendo gerar transtornos futuros.               |
| StructureDefinition    | StructureDefinition-BRImunobiologicoAdministradoCampanha-2.0                         | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoEvento-1.0 a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável, do tipo required                       | Substituição o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoEvento-1.0 pelo original http://hl7.org/fhir/ValueSet/immunization-status. O Value Set Brasileiro engloba mais definições do que são restritas pelo conjunto do Value Set original, podendo gerar transtornos futuros.               |
| StructureDefinition    | StructureDefinition-BRMedicamento                                                    | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoSolicitacaoMedicamento-1.0 a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável, do tipo required       | Substituição o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BREstadoSolicitacaoMedicamento-1.0 pelo original http://hl7.org/fhir/ValueSet/medication-status. O Value Set Brasileiro engloba mais definições do que são restritas pelo conjunto do Value Set original, podendo gerar transtornos futuros. |
| CodeSystem | CodeSystem-BRDivisaoGeograficaBrasil.json | Incompleto (apenas uma única cidade) | Atualizado com os municípios e versão para 2023-12-14 |
| ValueSet   | ValueSet-BRMunicipio-1.0                  | Asterisco (*) em versões gera erro HAPI FHIR | Fornecida versão específica 2023-12-14 |
| ValueSet | ValueSet-BRTipoDocumentoIndividuo-1.0 | Atribuição de um ValueSet (http://hl7.org/fhir/ValueSet/identifier-type) em local restrito a CodeSystem. Além disso, esse ValueSet é da versão 5.| O ValueSet foi substituido pelo CodeSystem (http://terminology.hl7.org/CodeSystem/v2-0203). Esse CodeSystem estava totalmente incluso no ValueSet e o ValueSet não incluia outro CodeSystem.|
| StructureDefinition | StructureDefinition-BREndereco-1.0 | Elemento fhirVersion identificado como na versão 4.0.0 | Atribuição da versão 4.0.1 |
| StructureDefinition | StructureDefinition-BREndereco-1.0 | Dificuldade de identificar os slices no slicing do elemento address.line | Retirada do slicing do elemento address.line | 
| StructureDefinition | StructureDefinition-BRParentesIndividuo-1.0 | Vinculação a ValueSet (http://www.saude.gov.br/fhir/r4/ValueSet/BRParentesco-1.0) não disponibilizado. | Subistituição do ValueSet o ValueSet http://www.saude.gov.br/fhir/r4/ValueSet/BRParentesco-1.0, que não foi divuldado pelo http://hl7.org/fhir/ValueSet/relatedperson-relationshiptype de relacionamentos já definidos pelo FHIR. |
| StructureDefinition | StructureDefinition-BRParentesIndividuo-1.0 | Binding não estava no local adequado, ocasionando na não validação dos códigos | Ajustou o binding para o local certo |
| StructureDefinition | StructureDefinition-BRParentesIndividuo-1.0 | Uso do tipo de dados "code" para binding de um ValueSet que inclui mais de um CodeSystem | Troca do tipo de dados "code" para o tipo "CodeableConcept" |
| ValueSet | ValueSet-BRLocalAplicacao-1.0 | O perfil de imunizante StructureDefinition-BRImunobiologicoAdministrado-2.0 tem um binding para o ValueSet ValueSet-LocalAplicacao-1.0 , contudo esse ValueSet não foi encontrado | Criação do ValueSet ValueSet-BRLocalAplicacao-1.0, o ValueSet inclui todos os códigos do CodeSystem CodeSystem-BRLocalAplicacao |
| StructureDefinition | StructureDefinition-BRDiagnosticoCOVID19-TesteRapido-01.01 | O elemento value[x], que é um valueCodeableConcept, da Observation StructureDefinition-BRDiagnosticoCOVID19-TesteRapido-01.01 tem um binding para o ValueSet http://www.saude.gov.br/fhir/r4/ValueSet/BRResultadoQualitativoExame-1.0, esse ValueSet não foi encontrado | Existe o ValueSet http://www.saude.gov.br/fhir/r4/ValueSet/BRResultadoQualitativoExame-2.0, dessas forma o binding foi atribuido ao ValueSet que foi disponibilizado|
| ValueSet | ValueSet-BRNaturezaJuridica-1.0 | O perfil StructureDefinition-BRPessoaJuridicaProfissionalLiberal-1.0.json tem um biding para o ValueSet http://www.saude.gov.br/fhir/r4/ValueSet/BRNaturezaJuridica-1.0 e esse ValueSet não foi disponbilizado no serviço simplifier | No portal https://servicos-datasus.saude.gov.br/detalhe/UZQjoYDDFN foi baixado os artefatos da RNDS disponibilizados e lá foi encontrado o ValueSet http://www.saude.gov.br/fhir/r4/ValueSet/BRNaturezaJuridica-1.0 que foi incrementado nos artefatos desse repositório. |
| CodeSystem | CodeSystem-BRNaturezaJuridica | O ValueSet ValueSet-BRNaturezaJuridica-1.0 inclui o CodeSystem http://www.saude.gov.br/fhir/r4/CodeSystem/BRNaturezaJuridica que não foi disponibilizado no simplifier.| No portal https://servicos-datasus.saude.gov.br/detalhe/UZQjoYDDFN foi baixado os artefatos da RNDS disponibilizados e lá foi encontrado o CodeSystem http://www.saude.gov.br/fhir/r4/CodeSystem/BRNaturezaJuridica que foi incrementado nos artefatos desse repositório |
| StructureDefinition | StructureDefinition-BRRacaCorEtnia-1.0 | Binding da extensão "race" e "indigenousEthnicity" não estava no local adequado, dessa forma não efetivando a ação do binding | Ajuste do binding para o local correto |
| * | ValueSet-RoupasUsadasMedicao, StructureDefinition-BRObservacaoDescritiva-1.0, ValueSet-BROrigemMedida, ValueSet-BRPosicaoIndividuo, ValueSet-BRTipoObservacao-1.0 | Essas instâncias de recursos FHIR faziam referência para o CodeSystem LOINC com o valor da URI incorreto. URI referenciada: https://loinc.org/. URI do CodeSystem LOINC: http://loinc.org|  Foi feita a substituição da URI referenciada pela URI do CodeSystem LOINC|
| * | * | Elemento "fhirVersions" em versões diferentes. | Foi retirado o elemento "fhirVersions" de todas as instâncias de recursos. |
| * | * | Instâncias de recursos sem o elemento "id" ou com o elemento "id" duplicado | Foi gerado um [UUID](https://stackoverflow.com/questions/1155008/how-unique-is-uuid) e acrescentado a cada instância de recurso no elemento "id" |
| * | * | Instâncias utilizando código "eng" e "pt-br" para referenciar línguas, agrupadas no ValueSet http://hl7.org/fhir/ValueSet/languages. Contudo, para refereciar Inglês Americano e Português do Brasil os códigos são "en-US" e "pt-BR", respectivamente. Códigos de um CodeSystem são case sensitive, ou seja, diferenciam caractere maiúsculo de minúsculo. | Substituição de "eng" por "en-US" e "pt-br" por "pt-BR", quando referente a línguas |
| CodeSystem | CodeSystem-BRDivisaoGeograficaBrasil | Alguns códigos definidos nesse CodeSystem estavam declarados sem aspas no json o que acarretou um erro na decodificação do JSON. | Foi acrescentado aspas aos códigos que não tinham. |
| StructureDefinition | StructureDefinition-BRIndividuo-1.0 | Slicing declarado de forma inadequada no elemento "address.line". | Retirada do slicing |
| ValueSet | ValueSet-BREstadoDocumento-1.0 | O elemento "name" tem o mesmo valor que a instância http://www.saude.gov.br/fhir/r4/ValueSet/BRTipoDocumento-1.0, comprometendo o utilização de ferramentas externas | Trocando o valor do elemento "name" para "Estado do Documento", essa alteração não acarreta em prejuízos |
| ValueSet | ValueSet-BRNomeExameTRCOVID19LOINC-1.0 | O elemento "name" tem o mesmo valor que a instância http://www.saude.gov.br/fhir/r4/ValueSet/BRNomeExame-2.0, comprometendo o utilização de ferramentas externas | Trocando o valor do elemento "name" para "Nome do Exame TR COVID-19 LOINC", essa alteração não acarreta em prejuízos |
| StructureDefinition | StructureDefinition-BRProcedimentoRealizado-1.0 | licing declarado de forma inadequada no elemento "performer". | Foi acrescentado o discriminator no elemento "performer". |

## Desenvolvedores FHIR

Os passos abaixo dependem dos aplicativos **hapi-fhir-cli.jar** disponível em https://github.com/hapifhir/hapi-fhir/releases e **fhir** disponível em 
https://fire.ly/products/firely-terminal/.

- Para gerar o NPM Package execute
```
java -jar hapi-fhir-cli.jar create-package --version 0.0.1 -v r4 --description "rnds.ajustes" --name rnds.ajustes --include-package "./*.json"
```

- Para instalar localmente o NPM Package gerado
```
fhir install rnds.ajustes-0.0.1.tgz --file
```

- Para validar artefatos (diretório exemplos)
```
java -jar validador_cli.jar exemplos\paciente-01.json -version 4.0.1 -watch-mode all -ig artefatos
```
