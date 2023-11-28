# Guia de mudanças
## Descrição
Mudanças foram feitas nos arquivos disponibilizados pela RNDS no [simplifier](https://simplifier.net/RedeNacionaldeDadosemSaude) para ficarem compativeis com o padrão FHIR, versão R4. Essas mudanças são mínimas e visam manter total coerência com os artefatos originais disponibilizados.

| Resource Type | arquivo | ERRO | Mudança
| ------------- | ------------- | ------------- | ------------- |
| StructureDefinition | StructureDefinition-BRAgendamentoRegulacaoAssistencial | Foi vinculado o Value Set http://www.saude.gov.br/fhir/r4/ValueSet/BRStatusAgendamentoRegulacaoAssistencial a variável "status" e esse Value Set não é um subconjunto do Value Set já vinculado a essa variável | Substitui o Value Set BRStatusAgendamentoRegulacaoAssistencial pelo original appointmentstatus\|4.0.1, tendo em vista que o Value Set brasileiro é apenas uma tradução do oficial.
| CodeSystem | CodeSystem-BRCondicaoMaternal | Tanto a variável "meta.lastUpdate" quanto a variável "date" estão no formato errado | Foi adcionado "Z" ao final do valor das variáveis para indicar o fuso horário.
| ConceptMap | ConceptMap-COVID-19VaccineMarketingAuthorizationHolderManufacturerBRImunobiologicoUE | Elemento "id" ultrapassava o limite superior de 64 caracteres | Substitui o id COVID-19VaccineMarketingAuthorizationHolderManufacturerBRImunobiologicoUE por cOVID-19VaccineMarketingAuthorizationManufacturerBRImunobiologico, como "id" é um identificador lógico, servindo somente para identifica-lo no servidor local, essa mudança não o afeta.
| ConceptMap | ConceptMap-BRImunobiologicoUECOVID-19VaccineMarketingAuthorizationHolderManufacturer | Elemento "id" ultrapassava o limite superior de 64 caracteres | Substitui o id ImunobiologicoUECOVID-19VaccineMarketingAuthorizationHolderM por ImunobiologicoCOVID-19VaccineMarketingAuthorizationM, como "id" é um identificador lógico, servindo somente para identifica-lo no servidor local, essa mudança não o afeta.
| ValueSet | ValueSet-BRGrupoAtendimento-1.0 | A variável "date" esta no formato errado | Foi adicionado "Z" ao final do valor da variável para indicar o fuso horário.
| StructureDefinition | StructureDefinition-BRRegistroImunobiologicoAdministradoRotina-1.0 | A variável "date" esta no formato errado | Foi adicionado "Z" ao final do valor da variável para indicar o fuso horário.
| ValueSet | ValueSet-BRTipoDocumento-1.0 | Duplicidade de instâncias desse Value Set | Uma dessas instâncias foi deletada. |
| CodeSystem | CodeSystem-BRNomeExameLOINC | Duplicidade de instâncias desse Code System | Uma dessas instâncias foi deletada. |
| CodeSystem | CodeSystem-BROrgaoExpedidor | Códigos duplicados, todos os códigos de um Code System devem ser únicos | Uma das definições dos códigos foi deleta. Code = CRBM.
| CodeSystem | CodeSystem-BRTipoIdentificador | Códigos duplicados, todos os códigos de um Code System devem ser únicos | Uma das definições dos códigos foi deleta. Code = BRACRBM.


