O _split module_ é uma subtécnica de modificabilidade, que faz parte da cateogoria de "aumentar coesão", cujo objetivo é reduzir os casos em que uma modificação afete múltiplos módulos.

## Conceito Central

Essa técnica consiste em refatorar um módulo grande e complexo com baixa coesão em vários módulos menores e mais coesos. A ideia principal é que, quando um módulo reúne responsabilidades que não têm um propósito comum ou não estão fortemente relacionadas, o custo de modificação aumenta, pois alterações podem impactar funcionalidades que não deveriam estar conectadas.

## Princípios Fundamentais

Foco na Coesão: A técnica atua diretamente sobre o princípio da coesão — ou seja, o quanto as responsabilidades dentro de um módulo estão relacionadas entre si.

Redução do Impacto das Mudanças: Ao criar módulos mais focados, diminui-se a chance de uma mudança afetar partes não relacionadas.

Decomposição Racional: A divisão não é arbitrária (não é cortar o código no meio), mas sim feita com base no agrupamento lógico das responsabilidades.

## Relação com Conceitos Fundamentais

Acoplamento vs. Coesão: Enquanto reduzir o acoplamento trata das relações entre módulos, aumentar a coesão trata das relações dentro de um módulo.

Tamanho do Módulo: Reflete o princípio de que módulos grandes tendem a ser mais difíceis e caros de modificar, e mais suscetíveis a bugs.
