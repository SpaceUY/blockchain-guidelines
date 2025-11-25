---
title: Subgraphs
layout: home
parent: The Graph
---

# Subgraphs

Un subgraph es una definicion que describe como indexar datos desde blockchain y permite hacer consultas de esos datos usando [GraphQL](https://graphql.org/) en lugar de depender de llamadas a nodos RPC.

## Cuando puede ser de utilidad

Cuando es necesario consultar datos historicos, obtener informacion agregada o filtrada sin hacer multiples llamadas o tener datos en tiempo real.

## Como aprender

La documentacion en la web oficial esta actualizada y es una buena fuente para aprender sobre como usar y crear sub grafos https://thegraph.com/docs
Se puede usar el [explorer](https://thegraph.com/explorer) para buscar sub grafos y probar hacer queries desde ahi mismo.
Asi mismo crear un subgraph se puede hacer desde el [studio](https://thegraph.com/studio/) con pasos intuitivos.

TheGraph ademas ofrece un paquete [graph-client](https://github.com/graphprotocol/graph-client) para conectarse y hacer estas queries, pero tambien es posible hacerlo con herramientas tradicionales como [Apollo](https://www.apollographql.com/) o [URQL](https://commerce.nearform.com/open-source/urql/)

Adicionalmente hay recursos en video para poder hacer un quickstart Subgraph quickstart https://youtu.be/EJ2em_QkQWU?si=pa_gm5_uQY9eFHCJ

# GRC20

Diving into GRC-20 https://www.youtube.com/watch?v=QEH5vLdZ4h0
Spec: https://github.com/graphprotocol/graph-improvement-proposals/blob/main/grcs/0020-knowledge-graph.md

## Core concepts

Entities & relations -> everything can be connected

Todo tiene un global ID que puede ser referenciado para ser vinculado

Triples como unidad básica, compuesta por una entidad, un atributo y un valor, por ejemplo, la entidad Albert Einstein tiene el atributo cumpleaños, cuyo valor es 14 de marzo
