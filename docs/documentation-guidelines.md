# Diretrizes de Documentação

Este documento define o padrão utilizado para organizar e estruturar a documentação técnica deste repositório.

O objetivo é manter consistência entre os conteúdos sem limitar sua evolução conforme novos conhecimentos e cenários forem incorporados.

## Knowledge Base

Os documentos da base de conhecimento devem priorizar a compreensão técnica e sua aplicação operacional.

Quando aplicável, podem utilizar a seguinte estrutura:

```text
# Título

## Conceito

## Funcionamento

## Visão de Troubleshooting

## Laboratórios Relacionados

## Referências
```

> Nem todas as seções são obrigatórias. Devem ser utilizadas apenas quando fizerem sentido para o conteúdo documentado.

## Laboratórios

Os laboratórios devem registrar atividades práticas de forma reproduzível.

Quando aplicável, podem utilizar a seguinte estrutura:

```text
# Título

## Objetivo

## Ambiente

## Procedimento

## Análise

## Resultado

## Conclusão
```

Em cenários envolvendo falhas ou incidentes, também podem ser utilizados:

```text
## Sintoma

## Diagnóstico

## Causa

## Resolução

## Validação
```

> As seções de diagnóstico e resolução não são obrigatórias em laboratórios destinados apenas à observação ou análise técnica.

## Organização

Os conteúdos são organizados inicialmente pelo tipo de documentação:

```text
knowledge-base/
labs/
docs/
```

Dentro das áreas técnicas, os documentos podem ser agrupados por domínio:

```text
networking/
```

Novos domínios são adicionados apenas quando houver conteúdo correspondente.

## Nomenclatura

Os nomes de arquivos e diretórios técnicos utilizam letras minúsculas e `kebab-case`.

Exemplos:

```text
osi-model/
tcpdump-ethernet-frame.md
ss-tcp-sockets.md
validation-criteria.md
```

Quando houver numeração em laboratórios, ela representa a ordem cronológica de criação.

Exemplo:

```text
01-tcpdump-ethernet-frame.md
02-ss-tcp-sockets.md
```

## Princípio de Documentação

> O repositório documenta somente conhecimentos estudados, compreendidos ou atividades efetivamente executadas.

A estrutura pode evoluir conforme a complexidade técnica do projeto aumentar.