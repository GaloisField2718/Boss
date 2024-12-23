<!--
Author: GaloisField
Translator: Arkano1dev
License: GNU-GPL v3 license
Description: A general course about Ordinals Protocol (ES).
Date: 21/07/23
Date of translation: 21/12/24
-->
# Curso sobre Ordinals

*Ordinals* es un nuevo protocolo construido sobre Bitcoin que trae consigo nuevas oportunidades, nuevos riesgos y grandes promesas.
Es un protocolo de código abierto que puede cambiar muchas cosas en Bitcoin.
Para lograrlo, propongo a continuación una base de curso lo más completa posible. No creo ser capaz de redactar todo este curso solo y propongo a todos los interesados en *Ordinals* unirse a mí para intentar presentar este curso de la mejor manera y lo antes posible.

Este curso me parece esencial en el ecosistema de Bitcoin, en la era de *RGB*, [RGB Protocol on Bitcoin, What is it? | Trust Machines](https://trustmachines.co/learn/what-is-the-rgb-protocol-on-bitcoin/#:~:text=The%20RGB%20network%20is%20a,assets%20on%20the%20Bitcoin%20blockchain.), los anuncios de *Ark*, [Bitcoin Developer Introduces New Layer 2 Protocol Ark - Bitcoin Magazine - Bitcoin News, Articles and Expert Insights](https://bitcoinmagazine.com/technical/bitcoin-developer-introduces-new-layer-2-protocol-ark) y una tendencia creciente en las inscripciones [Bitcoin Ordinals Analysis](https://dune.com/dgtl_assets/bitcoin-ordinals-analysis).
¡Comprender este nuevo protocolo y especialmente los últimos desarrollos basados en este protocolo me parece crucial!

A continuación encontrará el índice, seguido de un plan detallado y de las secciones que deben ser exploradas. También encontrará una sección [vocabulario](#vocabulaire) que se puede completar con el tiempo para hacer este curso lo más claro y accesible posible.

Estoy disponible para cualquier pregunta o comentario sobre este repositorio o por correo electrónico: galoisfield2718@gmail.com.

# Tabla de Contenidos

## Introducción

## I/ Historia
### 1) Primeros rastros del archivo en Github y el Taller de Casey
####	a) Una primera publicación
####	b) La presentación *por* Casey
####	c) La llegada de [*degens*](#vocabulario) y técnicos
####    d) Declaración del Open Ordinals Institute©️ y cambios <!--Problema: ¡Requiere noticias actuales! Sección para actualizar regularmente -->
### 2) Ideas antiguas, traídas de vuelta a la vida <!--¡Necesita completarse! ¡Entrevistar a personas que las experimentaron y transcribir aquí! -->
#### 	a) Monedas coloreadas
#### 	b) Counterparty
#### 	c) Ethereum y ABIs
### 3) El equipo principal
####	a) Github
####	b) Twitter
####	c) Pasando la antorcha

## II) Teoría e implementación
### 1) Contar los sats
#### 	a) El método <!--Bien detallar esta parte -->
####	b) Las elecciones de Casey
####	c) En busca de los sats raros
### 2) La inscripción
####	a) La idea
####	b) La práctica
####	c) El código <!-- Proporcionar una mirada precisa sobre este último. -->
### 3) El cliente
####	a) Bitcoin Core <!-- Simplemente proporcionar un buen tutorial para todos los sistemas operativos! -->
####	b) `ord`
####	c) Los comandos básicos 

## III) Uso y últimas novedades
### 1) Herramientas en línea
####	a) Billeteras
####	b) Plataformas
####	c) Mercado
### 2) JSON y nuevos protocolos
#### 	a) Inicio de `sns`
####	b) Llegada de `brc-20`
#### 	c) Un Meta Protocolo: BOSS
### 3) Algunas técnicas implementadas
###     a) Las inscripciones malditas
###     b) Bitmap y los nombres
###     c) Inscripciones recursivas


## Conclusión
### Reflexión sobre la historia
### ¿Qué futuro nos espera?
### Para involucrarse



## Anexos 

### Vocabulario
### Referencias

### Anexo A: Uso sin conexión del sitio iancoleman.com para la generación de direcciones bech32.
### Anexo B: Escritura de scripts con `bitcoin-cli`


![calavera](./assets/greenpeace_skull.png)
[*inscripción*](https://ord.link/1187713)

## Introducción

-----------
El objetivo de este curso es dirigirse a todos los perfiles y sus partes deben poder ser leídas de forma independiente
-----------


¡ES UN **PROTOCOLO SOBRE BITCOIN**!

*¿Cómo es eso?*

En una transacción de Bitcoin se puede incluir un mensaje.
-> Una transacción de Bitcoin es un mensaje
Este mensaje debe seguir una estructura específica y utilizar "funciones" del protocolo Bitcoin.
Estas "funciones" se llaman <u>operaciones</u>. El conjunto de estas operaciones se llama `OP_CODE`.
Estas operaciones se envían a la *red de Bitcoin* en transacciones.
Se llama <u>red de Bitcoin</u> al conjunto de máquinas que ejecutan el protocolo Bitcoin. Se puede encontrar un detalle de los clientes utilizados para acceder a la red de Bitcoin en [Coin Dance | Resumen de Nodos de Bitcoin](https://coin.dance/nodes/share).

A través del `OP_CODE` se pueden realizar operaciones algorítmicas en la red de Bitcoin, esto se llama un `script`. Para más detalles: [Opcodes utilizados en Bitcoin Script - Bitcoin Wiki](https://wiki.bitcoinsv.io/index.php/Opcodes_used_in_Bitcoin_Script) 



## Para profundizar: ¿Qué es una transacción de Bitcoin?
-> Mención del conjunto UTXO
-> Mención de la firma

Ordinals (como otros antes) propone un estándar de transacción, llamado `envelope`:
```
OP_FALSE
OP_IF
  OP_PUSH "ord"
  OP_PUSH 1
  OP_PUSH "text/plain;charset=utf-8"
  OP_PUSH 0
  OP_PUSH "Hola, mundo!"
OP_ENDIF
```

Inicialmente, el `OP_RETURN` se utilizaba para registrar e indexar texto (detallado en I.2: Ideas antiguas, renovadas). Desde las recientes actualizaciones, esto ha podido evolucionar (como veremos en II.2: Teoría e implementación, *el registro*).

Por lo tanto, este protocolo ha podido ser utilizado desde la llegada del arte generativo elemental (I.1.c: la llegada de los degens y los techos) hasta hoy.

El metaprotocolo [BOSS (Bitcoin Operating Standard System)](https://github.com/galoisfield2718/boss) (III.2.c) ha sido abandonado y el curso se está actualizando para tener en cuenta esta evolución.

Las evoluciones son múltiples y no es posible seguir todo. Por lo tanto, el objetivo aquí es brindar una primera visión general de la teoría de los [`Ordinals`](https://www.youtube.com/watch?v=g-isJScvFlE).
> Nota de vocabulario: En inglés se habla de 'Ordinal Theory', la cuenta de GitHub que gestiona la carpeta principal `ord` se llama `ordinals`. Es común hablar de Ordinals y la palabra 'ordinal' suele estar en plural. Por lo tanto, parece natural traducir al español "la Teoría de los Ordinales".

## I/ Historia

En esta sección, el objetivo es explorar la historia de este protocolo y la persona detrás de él.
El objetivo no es ser técnico, sino comprender de dónde viene, quién está involucrado y con qué motivaciones.
Comprender quiénes son los participantes y permitir que cada uno se informe más sobre estos desarrolladores.

### 1) Primeras huellas de la carpeta en Github y el Workshop de Casey
-> Mención de la numeración en serie en Bitcoin ver https://bitcointalk.org/index.php?topic=117224.0

El desarrollador destacado de este protocolo es Casey Rodarmor ([Casey (@rodarmor) | Twitter](https://twitter.com/rodarmor/), [R O D A R M O R](https://rodarmor.com/), [casey (Casey Rodarmor) | Github](https://github.com/casey/)).
En 2015, trabajó activamente en Bitcoin Core donde realizó una serie de lotes (actualizaciones) y la reestructuración de parte del código de Bitcoin Core ([Currículum de Casey Rodarmor](https://rodarmor.com/resume/index.html)).


<!--
Taproot: en pocas palabras, a partir de la reducción del peso de las direcciones y el aumento del tamaño de la *witness* (ver sección II.1) esto permite aumentar el tamaño del script asociado a la transacción.
> Nota: La traducción de esta *witness* a `hex to text` no funciona tal como está. Para probar esto, prueba la *witness* de una inscripción en [CyberChef](https://gchq.github.io/CyberChef/). En este sentido, algunas de las primeras soluciones se encuentran en [Tweet @Blockcryptology](https://x.com/blockcryptology/status/1708454640373686299?s=46&t=V6rDQiBqyYm5XAi9Qbj6Ew)
-->

-> SegWit => Reducción de los tamaños de las transacciones mediante la separación de las direcciones en primer lugar y las testigos (witness) en otra sección que contienen los scripts de firma
-> Taproot => Más específicamente TapScript (BIP 342) permite cualquier tipo de script (A verificar)
> Sobre el *witness program* asociado a una transacción de Bitcoin, se puede encontrar [el bip-0141](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki): "The `witness` is a serialization of all witness fields of the transaction. Each txin is associated with a witness field. A witness field starts with a `var_int` to indicate the number of stack items for the txin. It is followed by stack items, with each item starts with a `var_int` to indicate the length. Witness data is NOT script."
> Al definir una transacción que contiene una testigo (*witness*) como
```
    [nVersion][marker][flag][txins][txouts][witness][nLockTime]
```
![construcción de id de transacción](./assets/transaction_id_building.png)

Entre los importantes contribuyentes se encuentran [raphjaph (raph)](https://github.com/raphjaph), un estudiante de informática en la Universidad de Munich y [veryordinally (ordinally)](https://github.com/veryordinally?tab=overview&from=2015-12-01&to=2015-12-31) cuyo perfil fue creado en 2015 pero solo estuvo activo en Ordinals.

> En Ordinals hay menos información que en los otros y este perfil parece bastante extraño. Sería interesante investigar más a fondo y detallar a los demás contribuyentes: [Contributors to ordinals/ord](https://github.com/ordinals/ord/graphs/contributors).

Adentrémonos en las primeras publicaciones realizadas por Casey Rodarmor antes de detallar su presentación e intentar rastrear la historia de la llegada de los 'degens' a través del trabajo aún por estudiar de los primeros técnicos (rocks, taproot wizard y otros arte generativo).

#### a) Una primera publicación

<img src="./assets/Create_ord_casey.png" alt="creation ord" width="450" height="300">
*Esta información ya no está disponible en el perfil de Casey (tomada el 22/05/23).*

Con el commit de inicialización del README el 12 de Diciembre de 2021: [Primer commit](https://github.com/ordinals/ord/commit/4ee262e3456b82120f20474ee89eab22930ac0fe)

<img src="./assets/init_commit.png" alt="init" width="500" height="200">
Se puede encontrar el primer README [aquí](./assets/first_README.md).

Así que vemos un trabajo pensado durante un año por Casey antes de su [presentación](https://www.coindesk.com/consensus-magazine/2023/02/23/casey-rodarmor-why-i-developed-the-ordinals-bitcoin-nft-project-coindesk/) en Octubre de 2022, sobre la cual volveremos.

Vemos el primer lanzamiento [0.0.1](https://github.com/ordinals/ord/commit/da839875b9500d769e2877f6702978bd49391669) el 5 de junio de 2022.
<img src="./assets/0.0.1_casey.png" alt="0.0.1" width="500" height="200">

#### b) La presentación de Casey
-> [Taller de Ordinals con Casey Rodarmor](https://www.youtube.com/watch?v=MC_haVa6N3I)

Este taller fue la primera presentación en vivo por parte de Casey de este nuevo protocolo.
Tuvo lugar en Austin, Texas, el 27 de Agosto de 2022 [Taller de Ordinals con Rodamar, sáb. 27 de agosto de 2022, 12:00 | Meetup](https://www.meetup.com/fr-FR/pleb-lab/events/287948415/). Presentó en vivo su teoría, qué son los Ordinals y los recursos ofrecidos.

Una presentación de sus motivaciones a través del arte generativo y dar la oportunidad a los artistas de inscribir sus obras en Bitcoin.

> Una presentación bastante difícil de lo que él entiende por "contar los sats", sobre lo cual volveremos con más detalle más adelante. Con una demostración en vivo del sitio web [ordinals.com](https://ordinals.com), una descripción de la carpeta en Github y finalmente la presentación de un algoritmo en Python que muestra cómo contar los satoshis.

Esta presentación se centró más en la teoría de los sats que en la aplicación del protocolo. No hubo ejemplos de uso del comando `ord` en la línea de comandos para registrar desde el terminal, ni una demostración de registros, solo una explicación del funcionamiento teórico.

####	c) La llegada de los degens y los techs

Hubo que esperar hasta diciembre de 2022 para tener la primera inscripción [Inscripción #0](https://ord.link/0) realizada por **bc1qv8zhcjzpjw4m4tdyc5zn3dmax0z6rr6l78fevg**, quien no la conservó ya que la transfirió inmediatamente a otra dirección [Actividad de bc1qv8zhcjzpjw4m4tdyc5zn3dmax0z6rr6l78fevg | Ordiscan](https://ordiscan.com/address/bc1qv8zhcjzpjw4m4tdyc5zn3dmax0z6rr6l78fevg/activity). La dirección final que posee la inscripción #0 es bastante activa [Actividad de bc1pz4kvfpurqc2hwgrq0nwtfve2lfxvdpfcdpzc6ujchyr3ztj6gd9sfr6ayf | Ordiscan](https://ordiscan.com/address/bc1pz4kvfpurqc2hwgrq0nwtfve2lfxvdpfcdpzc6ujchyr3ztj6gd9sfr6ayf/activity).

Los Bitcoin rocks [Bitcoin Rocks | Ordiscan](https://ordiscan.com/collection/bitcoin-rocks) fueron la primera colección minteada entre 71 y 247 inscripciones. Fueron la puerta de entrada de los 'Degens'. Permitieron mostrar cómo publicar una colección en Ordinals.

Los [Taproot Wizard](https://taprootwizards.com/) inspirados en Bitcoin Wizard 🧙🧙‍♀️ en reddit mintieron la mayor parte de la colección en un solo bloque [colaboración con Luxor mining pool](https://www.coindesk.com/tech/2023/02/02/giant-bitcoin-taproot-wizard-nft-minted-in-collaboration-with-luxor-mining-pool/amp/) y tuvieron un gran éxito en la comunidad. Hoy en día representan una pieza de OG y una parte de la historia de Ordinals. Los datos sobre Taproot Wizard se pueden encontrar en [OXALUS.io](https://oxalus.io/nft/ordinals/bitcoin-wizards).

Para una [descripción](https://unisat.io/market/collection?collectionId=bitcoin-wizards): Taproot Wizard es un proyecto Ordinal NFT que celebra el décimo aniversario de la colección original Bitcoin Wizard creada por mavensbot. Magic Internet Money es una publicidad icónica del subreddit de bitcoin. Creado el lunes 18 de febrero de 2013 por u/mavensbot, rápidamente se convirtió en la publicidad más popular de reddit. mavensbot es el padre de Magic Internet Money: Bitcoin Wizard.


[*Inscripción #652*](https://ord.link/652)
 <img src="./assets/first_wizard.jpg" alt="primerMago" width="450" height="450">



Hasta hace poco, incluso añadiendo el 29 de junio de 2023: 


 <img src="./assets/last_wizard.webp" alt="últimoMago" width="450" height="450">

[*Inscripción #14,163,842*](https://ord.link/14163842)

¡Más que un simple proyecto, son un símbolo de los inicios de Ordinals y de bitcoin en reddit e Internet!

Esta colección trajo la liquidez inicial necesaria para el desarrollo del ecosistema y sigue siendo una parte histórica importante. 

Los degens continuaron su viaje....

Hoy en día, muchas colecciones se intercambian a precios exorbitantes. Hemos visto el regreso de los [cryptopunks](https://www.larvalabs.com/cryptopunks) en Bitcoin, el surgimiento de los [Bitcoin Punks](https://bitcoinpunks.com/), el nacimiento de los [Bitcoin Frogs](https://twitter.com/BitcoinFrogs) e incluso el regreso de Pepe con fuerza. Sin embargo, la ola de degens del principio parece no estar aquí por el momento. La llegada de los brc-20 ha cambiado el panorama...
Hoy en día, muchas cosas han sucedido, los Puppets han llegado, OMB representa una gran comunidad en Ordinals y las Runes han causado mucho revuelo antes de experimentar su primer invierno. 


#### d) Declaración del Instituto de Ordinals Abiertos©️ y cambios
[Instituto de Ordinals Abiertos en X: "El equipo de protocolo de Ordinals se enorgullece de anunciar el lanzamiento del Instituto de Ordinals Abiertos, una organización sin fines de lucro 501(c)(3) para fomentar el crecimiento y avance del protocolo Bitcoin Ordinals. Las donaciones se pueden hacer en nuestro sitio web: https://t.co/H7ymKSL4VR" / X](https://twitter.com/ordinalsorg/status/1686435373780746242)


### 2) Ideas antiguas, renovadas

> Aquí, sería interesante entrevistar a personas que lo hayan experimentado para obtener su retroalimentación. 

#### 	a) Counter Party (2012)

[Counterparty](https://counterparty.io/) es un protocolo en Bitcoin que ha evolucionado desde 2012. Muchos degens lo recordarían en ese momento. Sin embargo, ha seguido adelante y hoy en día es uno de los componentes de [elements](https://github.com/ElementsProject/elements). Este es un buen ejemplo porque [elements](https://github.com/ElementsProject/elements) busca permitir a las empresas o redes construir sidechains indexadas en Bitcoin. Un servicio que se está desarrollando en esta red es, por ejemplo: [liquid network](https://liquid.net/). Una red que está construida como una "side-chain" basada en Bitcoin.

Aquí se presentan algunas ideas posibles a través de la llegada de un nuevo protocolo. Esto ocurrió hace 12 años.
[Ordinals ha celebrado su primer aniversario](https://twitter.com/realizingerin/status/1735272834321326090) recientemente.

**NOTAS:** *Bitcoin-dev-digest, Vol 99, Issue45*\
"Por favor, corríjanme si me equivoco, pero creo que Counterparty ha codificado sus datos en el pasado dentro de los datos de clave pública, por lo que esta preocupación no es hipotética." de Russell O'Connor \<roconnor@blockstream.com\>

 <img src="./assets/bitcoin-digest_counter_party.jpg" alt="bitcoin-digest" width="450" height="450">


#### 	b) Las monedas coloreadas (2014)

Un artículo interesante sobre este tema [Monedas coloreadas, qué son y cómo funcionan en la cadena de bloques de Bitcoin | Bitcoinist.com](https://bitcoinist.com/colored-coins-work-bitcoin-blockchain/).


Un explorador que ya no está disponible pero accesible a través de [Wayback Machine](https://web.archive.org/): [coinprism](https://web.archive.org/web/20150213225601/https://www.coinprism.info/assets).

Es necesario investigar la visualización de estas transacciones. En el sitio de coinprism solo se encuentran direcciones en forma de: `AJxuLADi8stt7DpKEedhFEqCuB9dcV1EZd` que no son ni transacciones ni direcciones de Bitcoin.


#### 	c) Ethereum y los ABI (2015)

Los ABI (Interfaz Binaria de Aplicación) son archivos JSON que representan el contrato desplegado en Ethereum. Estos ABI son utilizados por las interfaces `javascript`, `typescript` y otros para permitir al usuario interactuar con los contratos ETH.

<u>Nota</u>: Sería necesario detallar el uso de los ABIs, su interés y su utilización.

**Pregunta**: ¿Se pueden asociar estos JSON a los protocolos basados en JSON ([Vocabulary](#vocabulaire)) en Ordinals?


### 3) El equipo principal

Aunque Casey es la cara visible de este proyecto, ¡obviamente no está solo!

Solo unos pocos han participado muy activamente en el código, pero muchas personas han contribuido sin las cuales no tendríamos una herramienta tan completa como la actual.
Las diferentes cuestiones y discusiones también constituyen contribuciones en sí mismas, pero desafortunadamente no están registradas en los commits ^^. 

Nos toca a nosotros buscar e indexar para rendirles homenaje ;)

####	a) Github
[Contribuidores a ordinals/ord](https://github.com/ordinals/ord/graphs/contributors)

 <img src="./assets/core_team1.png" alt="core1" width="250" height="300">

<img src="./assets/core_team2.png" alt="core2" width="250" height="300">

<img src="./assets/core_team3.png" alt="core3" width="250" height="300">

####	b) Twitter

Una lista de Twitter que reúne a los principales desarrolladores principales [lista de desarrolladores de ordinals](https://twitter.com/i/lists/1627776735210098708?s=20).

####	c) La transmisión de la antorcha
[Casey: "No he podido darle a ord la atención que merece, ¡así que me complace anunciar que @raphjaph ha aceptado asumir el rol de mantenedor principal! Raph es un estudiante empobrecido, y su trabajo en ord será financiado íntegramente por donaciones. Si puedes, ¡por favor considera donar!…"](https://twitter.com/rodarmor/status/1662617512700420096)

## II) Teoría e implementación

La documentación más técnica disponible actualmente se encuentra en [bip.mediawiki](https://github.com/ordinals/ord/blob/0.0.2/bip.mediawiki).

### 1) Contar los sats

Casey parte de la idea de numerar cada satoshi en Bitcoin

> Cada satoshi está numerado en serie, comenzando en 0, en el orden en que se extrae. Estos números se denominan "números ordinales" o "ordinales", ya que son números ordinales en el sentido matemático, dando el orden de cada satoshi en el suministro total. La palabra "ordinal" es claramente no ambigua, ya que no se utiliza en otro lugar en el protocolo Bitcoin.
> Los números ordinales de las entradas de transacción se transfieren a las salidas en orden de llegada, de acuerdo con el tamaño y el orden de las entradas y salidas de las transacciones.

> Si se extrae una transacción con el mismo ID de transacción que las salidas actualmente en el conjunto UTXO, siguiendo el comportamiento de Bitcoin Core, las nuevas salidas de transacción desplazan las entradas más antiguas del conjunto UTXO, destruyendo los ordinales contenidos en cualquier salida no gastada de la primera transacción. Esta regla es necesaria para manejar los dos pares de transacciones de la red principal con IDs de transacción duplicadas, a saber, las transacciones de coinbase de los bloques 91812/91842 y 91722/91880, extraídas antes de que BIP-34 hiciera imposible la creación de transacciones con IDs duplicados. 

> A efectos del algoritmo de asignación, se considera que la transacción coinbase tiene una entrada implícita igual en tamaño al subsidio, seguida de una entrada por cada transacción que paga una comisión en el bloque, en el orden en que dichas transacciones aparecen en el bloque. La entrada implícita del subsidio lleva los ordinales recién creados del bloque. Las entradas implícitas de las comisiones llevan los ordinales que se pagaron como comisiones en las transacciones del bloque.

> No pagar completamente el subsidio no cambia los números ordinales de los satoshis minados en bloques posteriores. Los ordinales dependen únicamente de cuántos satoshis podrían haberse minado, no de cuántos realmente se minaron.

#### 	a) El método

-> Detallado extensamente en su taller y presentado arriba, se debe hacer una síntesis en español.

> Los ordinales pueden ser escritos como el número ordinal seguido del indicador ordinal en idioma Romance °, por ejemplo 13°.

Un satpoint puede ser usado para indicar la ubicación de un ordinal dentro de una salida. Un satpoint consiste en un outpoint, es decir, un ID de transacción y un índice de salida, con la adición del desplazamiento del ordinal dentro de esa salida. Por ejemplo, si el ordinal en cuestión está en el desplazamiento 6 en la primera salida de una transacción, se puede escribir como:

`680df1e4d43016571e504b0b142ee43c5c0b83398a97bdcfd94ea6f287322d22:0:6`

Un slot puede ser usado para indicar la salida de un ordinal sin hacer referencia a un ID de transacción, sustituyendo la altura del bloque e índice de transacción dentro del bloque por el ID de transacción. Se escribe como un cuádruple punteado. Por ejemplo, el ordinal en el desplazamiento 100 en la salida en el desplazamiento 1, en la transacción coinbase del bloque 83 se puede escribir como:

`83.0.1.100`

Los satoshis con ordinales que no son valiosos o notables pueden ser referidos como cardinales, ya que su identidad no importa, solo la cantidad. Una salida cardinal es aquella cuyos ordinales no son importantes para el propósito en cuestión, por ejemplo, una salida utilizada solo para proporcionar relleno para evitar crear una transacción con una salida por debajo del límite de polvo.

> Cualquier transferencia ordinal puede ser realizada en una sola transacción, pero la transacción resultante puede contener salidas por debajo del límite de polvo, y por lo tanto ser no estándar y difícil de incluir en un bloque. Considere un escenario donde Alice posee una salida que contiene el rango de ordinales [0,10], el límite de polvo actual es de 5 satoshis, y Alice desea enviar los ordinales 4° y 6° a Bob, pero retener el ordinal 5°. Alice podría construir una transacción con tres salidas de tamaño 5, 1 y 5, conteniendo los ordinales [0,4], 5 y [6,10]. La segunda salida está por debajo del límite de polvo, por lo que dicha transacción sería no estándar. 

Esta transferencia, y de hecho cualquier transferencia, se puede realizar dividiendo la transferencia en múltiples transacciones, con cada transacción realizando una o más divisiones y fusionando salidas de relleno según sea necesario.

Es decir, Alice podría realizar la transferencia deseada en dos transacciones. La primera transacción enviaría los ordinales [0,4] a Bob, y devolvería como cambio los ordinales [5,10] a Alice. La segunda transacción tomaría como entradas una salida de al menos 4 satoshis, la entrada de cambio y una entrada adicional de al menos un satoshi; y crearía una salida de tamaño 5 a la dirección de Bob, y el resto como una salida de cambio. Ambas transacciones evitan crear salidas no estándar, pero aún logran la misma transferencia deseada de ordinales.

Técnicamente:

```
# subsidy of block at given height
def subsidy(height):
  return 50 * 100_000_000 >> height // 210_000

# first ordinal of subsidy of block at given height
def first_ordinal(height):
  start = 0
  for height in range(height):
    start += subsidy(height)
  return start

# assign ordinals in given block
def assign_ordinals(block):
  first = first_ordinal(block.height)
  last = first + subsidy(block.height)
  coinbase_ordinals = list(range(first, last))

  for transaction in block.transactions[1:]:
    ordinals = []
    for input in transaction.inputs:
      ordinals.extend(input.ordinals)

    for output in transaction.outputs:
      output.ordinals = ordinals[:output.value]
      del ordinals[:output.value]

    coinbase_ordinals.extend(ordinals)

  for output in block.transaction[0].outputs:
    output.ordinals = coinbase_ordinals[:output.value]
    del coinbase_ordinals[:output.value]
```

#### b) Las elecciones de Casey

Casey ha elegido nombrar los sats además de numerarlos.

Una notación interesante es la notación por grados. Cada sat se numera según su posición después de uno de los cuatro eventos siguientes:
- *Bloque*: Posición en cada nuevo bloque minado. Si es el primero: 0'''.
- *Ajuste de dificultad*: Posición en relación con el último ajuste de dificultad (cada 2016 bloques). Si es el primero: 0''.
- *Halving*: Posición en relación con el último bloque de halving (cada 210,000 bloques). El primero se nota: 0'.
- *Ciclos*: Un evento especial que es el ajuste de dificultad al mismo tiempo que un *halving*. Esto ocurre cada 6 *halvings*. El próximo debería ser en 2032. Se nota el primero: 0°.

La ventaja de esta notación es su visibilidad en comparación con las rarezas propuestas por Casey que se pueden ver [aquí](https://docs.ordinals.com/overview.html). Todos los sats que contienen al menos un 0 no serán comunes.
Por ejemplo: 1°1'0''0''' es raro.
1◦ 2do ciclo
1′ No es el primer bloque de una *halving epoch*
0′′ Primer bloque de un ajuste de dificultad
0′′′ 1er sat del bloque

Sin embargo, esta notación tiene la desventaja de ser difícil de encontrar tal cual desde un explorador.
Para obtener más detalles sobre los sats raros, consulte [c) En busca de los sats raros](#c). 

El recuento de sats es parte de las decisiones de Casey. Recientemente, ha habido discusiones sobre si se debe elegir el primer sat de la UTXO o el último como el que contiene la inscripción. Sin embargo, desde el principio, Casey había construido una cola *First-In-First-Out* (FIFO) para asignar los sats en una transacción.

[//](#c)
####	c) En busca de sats raros

Las rarezas iniciales (históricas) son:
- `común`: Todos los sats que no son los primeros de su bloque.
- `poco común`: El primer sat de cada bloque.
- `raro`: El primer sat de cada ajuste de dificultad.
- `épico`: El primer sat de cada halving.
- `legendario`: El primer sat de cada ciclo.
- `mítico`: El primer sat del bloque génesis (¡Único!).

Sin embargo, ¡han surgido nuevas rarezas! Puedes consultar un buen resumen en el hilo de [@@0xBes](https://twitter.com/0xBes): [Hilo: Categorización de los Sats raros 💎](https://x.com/0xBes/status/1739987968922632240?s=20).

También puedes encontrar [sating](https://sating.io):

<img src="./assets/sats_rarity.png" alt="satsRarity" width="350" height="300">

Hoy en día, la búsqueda y el estudio de los sats raros se está convirtiendo en una disciplina separada: [satología](https://x.com/ZedZeroth/status/1710287026061267348?s=20).

**Para buscarlos**:

Para una búsqueda manual en Sparrow Wallet, tenemos [Franken | Cómo encontrar y extraer sats raros de tu billetera Bitcoin](https://www.youtube.com/watch?v=4Gro5AmFdfY).
También puedes hacerlo a través de la línea de comandos siguiendo la [documentación oficial | 7.3 Caza de Sats](https://docs.ordinals.com/guides/sat-hunting.html). Aún no lo he probado.

¡Por supuesto, lo más fácil es hacerlo en línea! Cada vez más herramientas incorporan la visualización de sats raros. Nuevas categorías se agregan regularmente, así que mantente actualizado al respecto.

[Escáner de Sats | sating](https://sating.io/), una de las primeras herramientas para hacerlo.

### 2) La inscripción

Ahora que sabemos contar los sats, podemos manipularlos.
Ordinals, específicamente la línea de comandos `ord`, permite inscribir en estos sats.
En esta sección nos enfocaremos en la línea de comandos, también conocida como el cliente `ord`.

####	a) La idea 

Cuando se realiza una transacción, se puede almacenar los datos en el primer sat de la tx.

Técnicamente se utiliza una doble tx de commit y reveal. Esto proviene de la actualización de SegWit (Segregated Witness) con la integración del campo witness, del cual se puede obtener más detalles en [Segregated witness road to implementation](https://www.coingecko.com/learn/segregated-witness-road-to-implementation). Esto permitiría conocer el output e inscribir en el sat correcto.

El uso de la witness de forma nativa tuvo que realizarse a partir del commit [Add commands to mint and verify NFTs (#211) · ordinals/ord@15ed050](https://github.com/ordinals/ord/commit/15ed050d59de6e0f1d581de5a92e3809d0069b0c). Se realiza mediante el uso de la nueva clase `Witness` desde `blockdata` de la librería rust [bitcoin](https://docs.rs/bitcoin/latest/bitcoin/).
![index.rs](index.rs_0.0.0_witness_integration.png)

Para poder inscribir en Bitcoin, necesitaremos un "sobre" que estará contenido en la transacción y estará adjunto al script en la transacción. De esta manera, podremos transferir de direcciones a direcciones este script adjunto a la transacción que representará la inscripción. Técnicamente, esto se almacena en el `scriptPubKey` asociado a la [utxo (unspent transaction output)](https://academy.bit2me.com/fr/que-es-una-utxo/).

<u>Nota</u>: Disculpa por los términos técnicos, pero son los términos exactos que se deben recordar para comprender completamente el concepto de inscripción.


####	b) La práctica

En la práctica, no es necesario comprender por qué funciona de esta manera para utilizarlo.

Sin embargo, después de una inscripción con el cliente `ord`, se obtiene una salida json de la forma:

```JSON
{
  "commit": "0bdbae349b685c0a59fa275f18d4ad14c3972fb5998d513399a478d87d805e00",
  "inscription": "d4ad4cd729fdd4dfaa5279aed4910e4afcfac6e3be25900ba40a2faebef28a9fi0",
  "reveal": "d4ad4cd729fdd4dfaa5279aed4910e4afcfac6e3be25900ba40a2faebef28a9f",
  "fees": 8440
}

```

En la práctica, el [sobre](https://docs.ordinals.com/inscriptions.html) tiene esta forma:

```
OP_FALSE
OP_IF
  OP_PUSH "ord"
  OP_PUSH 1
  OP_PUSH "text/plain;charset=utf-8"
  OP_PUSH 0
  OP_PUSH "Hello, world!"
OP_ENDIF
```

Leamos un poco sobre esto para aclarar este script y luego veamos en [mempool.space](https://mempool.space) cómo se ve en la práctica.

El `OP_FALSE` se utiliza para finalizar el script anterior al registro. Se puede notar que un registro siempre está al final del script (para más detalles sobre los scripts, ver [vocabulario](#vocabulaire)). 

El `OP_CODE` `OP_IF` ... `OP_ENDIF` corresponde al núcleo del protocolo Ordinals. De hecho, gracias a esto podremos "empaquetar" datos en nuestra transacción que serán: grabados en la transacción, fácilmente "transportables" e "interpretables" así como muy personalizables. Ordinals es una propuesta de uso de este `OP_IF`...`OP_ENDIF` pero puede haber muchas otras [^1]. 

Luego, usamos una sucesión de `OP_PUSH` para enviar correctamente todos los datos. Esto se traduce en Bitcoin como: `OP_PUSHBYTES_xx` donde xx es un número calculado en función de la longitud de la cadena de caracteres.

Por lo tanto, comenzamos enviando el texto `ord` en formato hexadecimal en nuestra transacción: `OP_PUSHBYTES_3 6f7264` seguido de un `OP_PUSHBYTES_1 01`. 

Luego, como se indica en el párrafo anterior, *pusheamos* el tipo de archivo siguiendo el formato [MIME](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) con la codificación. Un archivo `json` generalmente se enviará a la red con el formato: `text/plain;charset=utf-8` o `application/json`. 

¿Qué nos queda por enviar? ¡Los datos mismos! Por lo tanto, dependiendo de los datos, estos serán cifrados previamente siguiendo una base específica antes de ser convertidos a hexadecimal. 

¿Qué significa esto? 

Si tengo una imagen que quiero registrar en formato JPEG, comenzaré especificando el tipo: `image/jpeg`.

Luego convertiré mi imagen a base64. Esto se hace fácilmente con herramientas como [Image to Base64 | guru](https://base64.guru/converter/encode/image) o paquetes en cualquier lenguaje de programación. 

Una vez convertido a base64, debo convertirlo a formato hexadecimal para que sea aceptado por la red de Bitcoin. Para esto, podemos usar [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')) que nos proporciona una serie de herramientas muy potentes en una interfaz gráfica y API/paquetes. 

##### Lectura de una inscripción desde mempool.space

Ahora tenemos todas las herramientas para leer una inscripción directamente desde el explorador [mempool.space](https://mempool.space)

Por simplicidad, trataremos una transacción de tipo texto para no tener demasiados datos que transcribir.

Tomemos la transacción: [`b61b0172d95e266c18aea0c624db987e971a5d6d4ebc2aaed85da4642d635735`](https://mempool.space/tx/b61b0172d95e266c18aea0c624db987e971a5d6d4ebc2aaed85da4642d635735) [^2], la inscripción de `deploy` de la computadora (veremos más adelante a qué se refiere esto más específicamente, por ahora simplemente la "descompilaremos").

<img src="./assets/tx_deploy_ordi.png" alt="Transacción de deploy ordi" width="400" height="300">

<img src="./assets/p2tr_deploy_ordi.png" alt="Script P2TR de deploy ordi" width="450" height="250">

A continuación se reproduce el script que nos interesa (p2tr) contenido en esta transacción:

```
OP_PUSHBYTES_32 9e2849b90a2353691fccedd467215c88eec89a5d0dcf468e6cf37abed344d746
OP_CHECKSIG
OP_0
OP_IF
OP_PUSHBYTES_3 6f7264
OP_PUSHBYTES_1 01
OP_PUSHBYTES_24 746578742f706c61696e3b636861727365743d7574662d38
OP_0
OP_PUSHDATA1 7b200a20202270223a20226272632d3230222c0a2020226f70223a20226465706c6f79222c0a2020227469636b223a20226f726469222c0a2020226d6178223a20223231303030303030222c0a2020226c696d223a202231303030220a7d
OP_ENDIF
```
La lectura se realizará exclusivamente con [CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex('Auto')).

El `OP_PUSHBYTES32 ...` y el `OP_CHECKSIG` no nos interesan para el estudio de la inscripción. Siéntase libre de investigar más sobre esta parte.

Comenzamos con: `OP_PUSHBYTES_3 6f7264`, `6f7264` efectivamente se traduce a `ord` [ord | CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex%28%27Auto%27%29From_Base64%28%27A-Za-z0-9%2B%2F%3D%27,false,false/disabled%29From_Hexdump%28/disabled%29&input=NmY3MjY0).

Luego obtenemos el tipo de archivo con: `OP_PUSHBYTES_24 746578742f706c61696e3b636861727365743d7574662d38`, `746578742f706c61696e3b636861727365743d7574662d38` se traduce correctamente a `text/plain;charset=utf-8` [text/plain | CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex%28%27Auto%27%29From_Base64%28%27A-Za-z0-9%2B%2F%3D%27,false,false/disabled%29From_Hexdump%28/disabled%29&input=NzQ2NTc4NzQyZjcwNmM2MTY5NmUzYjYzNjg2MTcyNzM2NTc0M2Q3NTc0NjYyZDM4)

El `OP_0` indica que vamos a pasar a los datos propiamente dichos: `OP_PUSHDATA1 7b200a20202270223a20226272632d3230222c0a2020226f70223a20226465706c6f79222c0a2020227469636b223a20226f726469222c0a2020226d6178223a20223231303030303030222c0a2020226c696d223a202231303030220a7d` que resulta en: 
```
{ 
  "p": "brc-20",
  "op": "deploy",
  "tick": "ordi",
  "max": "21000000",
  "lim": "1000"
}
```

[desplegar inscripción | CyberChef](https://gchq.github.io/CyberChef/#recipe=From_Hex%28%27Auto%27%29From_Base64%28%27A-Za-z0-9%2B%2F%3D%27,false,false/disabled%29From_Hexdump%28/disabled%29To_Quoted_Printable%28/disabled%29Defang_URL%28false,false,false,%27Only%20full%20URLs%27/disabled%29URL_Encode%28false/disabled%29URL_Encode%28false/disabled%29&input=N2IyMDBhMjAyMDIyNzAyMjNhMjAyMjYyNzI2MzJkMzIzMDIyMmMwYTIwMjAyMjZmNzAyMjNhMjAyMjY0NjU3MDZjNmY3OTIyMmMwYTIwMjAyMjc0Njk2MzZiICAgIDIyM2EyMDIyNmY3MjY0NjkyMjJjMGEyMDIwMjI2ZDYxNzgyMjNhMjAyMjMyMzEzMDMwMzAzMDMwMzAyMjJjMGEyMDIwMjI2YzY5NmQyMjNhMjAyMjMxMzAzMDMwMjIwYTdk)

Por lo tanto, aquí hemos recuperado la inscripción `deploy` desde la transacción Bitcoin `b61b0172d95e266c18aea0c624db987e971a5d6d4ebc2aaed85da4642d635735`.


Puedes practicar con cualquier inscripción en [ordinals.com](https://ordinals.com). Para obtener la id, elimina `i0` y pégalo en el explorador [mempool.space](https://mempool.space) para divertirte descifrando el script.

El explorador [ordpool.space](https://ordpool.space) hace todo esto automáticamente.



[^1]: En este sentido, se destaca el protocolo [Atomicals](https://github.com/atomicals) (una parte de este curso se dedicará a Atomicals en el futuro). Atomicals utiliza el mismo principio de `OP_IF`...`OP_ENDIF` pero llena este "empaquetado" de manera diferente.

[^2]: Se debe tener en cuenta que la id de una inscripción se da por [txid]i0. El i0 determina la entrada, se puede tener algo diferente a i0 pero la mayoría son con i0. Si hay varias entradas, tendremos i1, i2,... . Pero la construcción de la id de la inscripción sigue siendo la misma.

[^3]: El término *flag* es más general en informática. La notación para las líneas de comandos varía pero a menudo son `[OPTIONS]`. Es más para informar sobre los términos en informática.  

##### Discusión de metadatos

Una característica añadida e integrada recientemente ([metadatos de confirmación de octubre de 2023](https://github.com/ordinals/ord/commit/aeb5f558bbedb0a7ddd095cee2f3ed0b4b495718)
) es la gestión de [metadatos](https://docs.ordinals.com/inscriptions/metadata.html). Veremos en [3.](#3) cómo se aplica esto a la línea de comandos.

Aquí nos centraremos en el sobre propuesto con la transacción de Bitcoin en sí.


####	c) El código

> [ordinals/ord/src/subcommand/wallet/inscribe.rs](https://github.com/ordinals/ord/tree/master/src/subcommand/wallet/inscribe.rs)

El objetivo no es analizar TODO el código, sino detallar algunas funciones importantes como `create_inscription_transactions` y `build_reveal_transaction`.

> Para los desarrolladores, este archivo `inscribe.rs` debe poder ser modificado moderadamente sin afectar al resto del programa cliente `ord`. Por ejemplo, las tarifas utilizadas para realizar las transacciones deben poder ser modificadas. Una discusión profunda con pruebas de implementación avanzadas podría ser interesante.


Para las operaciones: 
```
- content_type, with a tag of 1, whose value is the MIME type of the body.
- pointer, with a tag of 2, see pointer docs.
- parent, with a tag of 3, see provenance.
- metadata, with a tag of 5, see metadata.
- metaprotocol, with a tag of 7, whose value is the metaprotocol identifier.
- content_encoding, with a tag of 9, whose value is the encoding of the body.
- delegate, with a tag of 11, see delegate.
```


### 3) El cliente
[//]: # (3)

La referencia para esta parte es este video: [Cómo configurar un nodo Bitcoin y una billetera Ord](https://www.youtube.com/watch?v=tdC8kmjn5N0&list=LL&index=1&t=0s)
Este video está hecho en Windows y al estar en Mac con un nodo en un disco duro externo, propondré los comandos para configurar esto en Linux y Mac.

####	a) Bitcoin Core

Requisitos:
- Aprox. 700 GB de almacenamiento, preferiblemente en SSD.
- Una buena conexión a internet.

Ya sea que tenga una computadora vieja y ejecute el nodo Bitcoin en ella, o le recomiendo que compre un disco duro externo SSD de 1 TB. Puede encontrar uno por menos de cien euros en internet en general.


[jonasnick/bitcoin-node: "Cómo ejecutar un nodo Bitcoin" folleto](https://github.com/jonasnick/bitcoin-node)


La instalación ya ha sido abordada en DécouvreBitcoin [tutoriales/node/bitcoin-core-mac-windows](https://github.com/GaloisField2718/sovereign-university-data/tree/main/tutorials/node/bitcoin-core-mac-windows) y [tutoriales/node/bitcoin-core-linux](https://github.com/GaloisField2718/sovereign-university-data/tree/main/tutorials/node/bitcoin-core-linux).

<!--
**Instalación paso a paso de Bitcoin Core**
1) Ir a: [Descargar - Bitcoin](https://bitcoin.org/en/download) y descargar la versión que corresponda a su sistema operativo;

2) Abra el paquete que debería verse así:
Insertar una imagen

3) Seguir las instrucciones

4) Configurar a través de `bitcoin.conf` para que la ubicación de almacenamiento sea de la forma:
*En Mac*:
- `/Volumes/mon_disque/bitcoin`

*En Linux*:
- `/media/mon_disque/bitcoin`

*En Windows*:
- `C:/mon_disque`

5) Línea de comandos:
*En Mac*:
```
./bitcoin/bin/bitcoind --conf=/Volumes/mon_disque/bitcoin/bitcoin.conf --txindex=1
```
3) Seguir las instrucciones

4) Configurar a través de `bitcoin.conf` para que la ubicación de almacenamiento sea de la forma:
*En Mac*:
- `/Volumes/mon_disque/bitcoin`

*En Linux*:
- `/media/mon_disque/bitcoin`

*En Windows*:
- `C:/mon_disque`

5) Línea de comandos:
*En Mac*:
```
./bitcoin/bin/bitcoind --conf=/Volumes/mon_disque/bitcoin/bitcoin.conf --txindex=1
```
Si esto no es suficiente para forzar la descarga de la cadena de bloques en `mon_disque`, entonces agregue las banderas `--data-dir=/Volumes/mon_disque/bitcoin/Bitcoin --blocksdir=/Volumes/mon_disque/bitcoin/Bitcoin/blocks --settings=/Volumes/mon_disque/bitcoin/Bitcoin/settings.json --walletdir=/Volumes/mon_disque/bitcoin/Bitcoin/wallets --txindex=1`

*En Linux*:


*En Windows*:
-->


Para su configuración, debe ejecutarse en `bitcoind` con la bandera `--txindex=1` (o agregarla a `bitcoin.conf`).

> En Mac logré hacerlo funcionar en mi disco duro externo especificando cada ruta para las banderas: `--conf, --datadir, --blocksdir, --walletdir`.
> Lo inicio con `cd /Volumes/Crucial\ X8/Bitcoin/bitcoin/bin && ./bitcoind --conf=/Volumes/Crucial\ X8/bitcoin/Bitcoin/bitcoin.conf --datadir=/Volumes/Crucial\ X8/bitcoin/Bitcoin --blocksdir=/Volumes/Crucial\ X8/bitcoin/Bitcoin/blocks --settings=/Volumes/Crucial\ X8/bitcoin/Bitcoin/settings.json --walletdir=/Volumes/mon_disque/bitcoin/Bitcoin/wallets --txindex=1`.


####	b) `ord`

Una vez que el nodo esté completamente descargado, se puede descargar y ejecutar el cliente `ord`. Se habla de cliente para referirse a la línea de comandos que se utiliza para interactuar con el protocolo ordinals.

Para descargar e instalar Bitcoin Core + `ord`, sigue el excelente tutorial de [@pazNGMI: How To Setup A Bitcoin Node & Ord Wallet](https://www.youtube.com/watch?v=tdC8kmjn5N0).
*Está en inglés... "¡Oooooh!" ¿Cuándo estará disponible en español?* 


Bitcoin Core: [Releases - bitcoincore](bitcoincore.org/en/releases)
`ord`: [Releases · ordinals/ord](https://github.com/ordinals/ord/releases)


----------------

Para especificar la ubicación de destino del archivo `index.redb`, simplemente usa `--index=/CHEMIN/VERS/index.redb`. Esto se llama un *flag*[^3] o una *opción*. Se agrega a nuestro comando **antes** del comando principal (que no es un flag). Ejemplo: `ord --cookie-file=/CHEMIN/VERS/.cookie --index=/CHEMIN/VERS/index.redb index update`.

----------------

Ahora que has descargado e instalado `ord`, ¿qué haces a continuación? Escribe `ord help` y continúa a la siguiente sección ;)

####	c) Comandos básicos 

Como has visto, `ord help` lista todos los comandos. Primero, necesitarás crear un archivo que indexe los ordinales. Para hacerlo, usa `ord [FLAGS] index update`. Los flags se llaman `[OPTIONS]` en la ayuda.

<u>Nota</u>: Como has aprendido, sabes que un protocolo debe ser indexado para existir. Por eso, este comando es importante. Sin embargo, no es obligatorio ya que se ejecuta automáticamente al usar `wallet`, `server` y otros que requieren el uso del índice (base de datos). 

Luego, tendrás que crear una billetera. Para esto, usa `ord [OPTIONS] wallet create`, que generará toda la información que debe ser almacenada asociada a la billetera.

Después, ejecuta `ord [OPTIONS] wallet receive` para fondear la dirección. Esto mostrará una dirección asociada a la billetera recién creada.

Finalmente, `ord [OPTIONS] --fee-rate=xx wallet inscribe CHEMIN/VERS/fichier.xxx` se utilizará para inscribir el archivo deseado. El flag `--fee-rate`, expresado en sats/vBytes, indicará la tasa de comisión deseada. Verifica en [mempool.space](https://mempool.space) para ver el nivel actual. Siempre es recomendable agregar un poco más si deseas que tu transacción se realice rápidamente.

**Lista si es necesario**

*OPCIONES*:
`--cookie-file=RUTA/HACIA/.cookie`: Especifica la ruta hacia el archivo `.cookie` de su nodo bitcoincore.
`--index=RUTA/HACIA/index.redb`: Archivo de índice ordinales.
`-t`: Modo testnet.

*COMANDOS*:
`ord help` Devuelve todos los comandos

`ord index update`: Actualiza la base de datos (índice)

`ord wallet help` Lista los subcomandos de la billetera

`ord wallet create` Crea una nueva billetera

`ord wallet balance` Da el balance de la billetera ord actual

`ord wallet inscribe` Permite inscripsiones mediante la sintaxis: `ord wallet inscribe path/to/file.ext  --fee-rate=xxx` donde `ext` es uno de los siguientes tipos: txt, json, webp, html,

`ord wallet inscriptions`

Se puede notar que existen los comandos: `ord server` y `ord preview` que sirven para generar su propio explorador web local ordinales basado en el sitio [ordinals.com](https://ordinals.com).

## III) Uso y últimas novedades

Obviamente, no todo el mundo va a utilizar el cliente `ord` con el nodo completo de Bitcoin.

Por lo tanto, se necesitan herramientas más accesibles y en línea.
Estas herramientas en línea a veces presentan ciertas ventajas, como la optimización de tarifas, mucho más difícil de lograr solo con el cliente, inscripciones especiales a través de plantillas para ciertos protocolos (ver III.2), o las inscripciones malditas (cursed inscriptions) (ver III.3).

Por lo tanto, permiten una integración sencilla y avanzada de las últimas funcionalidades ofrecidas por el protocolo ordinals.

Entremos entonces en estas herramientas antes de abordar los protocolos construidos sobre Ordinals y las Inscripciones Malditas y otras alegrías técnicas actuales.

### 1) Herramientas en línea
Las herramientas en línea son necesarias para el desarrollo del ecosistema y trataremos de abordarlas en profundidad.

**ATENCIÓN: Todo esto aún está en desarrollo. No coloque o deje demasiado Bitcoin en ellas. Próximamente podrían descubrirse vulnerabilidades y esto podría resultar en pérdidas totales de ordinals y su dinero. Nada es 100% seguro y estas plataformas son muy nuevas.**
*Nota: Hoy en día, Ledger gestiona Ordinals. Le recomiendo que se informe (y lo agregue a este curso ;) sobre este tema. Siempre es más seguro almacenar sus activos en billeteras de hardware conectadas lo menos posible a internet!* 

>  Son bienvenidos tutoriales sobre cada una de estas herramientas ;)

####	a) Billeteras

Un artículo sobre las billeteras ordinales de calidad: [¡Las billeteras Ordinales de Bitcoin han Llegado: Una Guía Para Principiantes y Expertos](https://nftnow.com/news/bitcoin-ordinals-wallets-have-arrived/).

- [Unisat](https://unisat.io/)

- [OrdinalsWallet](https://ordinalswallet.com/)

- [Xverse](https://www.xverse.app/)

- [Hiro](https://wallet.hiro.so/) *Personalmente, no me inspira confianza. Posibles vulnerabilidades.*

####	b) Plataforma de creación

Similar a las billeteras, se deben agregar:

- [lookordinals.com](https://lookordinals.com) (probablemente el más económico del mercado actualmente, recomendado por @0xGrug)

- [Gamma.io](https://gamma.io)

####	c) Mercado

Son menos numerosos. Se encuentran:

- [Unisat Marketplace](https://unisat.io/marketplace)

- [Mercado de billeteras Ordinals](https://ordinalswallet.com/marketplace)

- [Magic Eden - Mercado de NFT de Bitcoin](https://magiceden.io/ordinals)

### 2) JSON y nuevos protocolos

Rápidamente, dado el alto costo de registrar imágenes, las personas se han vuelto hacia el registro de archivos de texto (yo primero [galoisfield.btc](https://ord.link/187784)). Sin embargo, ¿cómo nos orientamos con simples archivos de texto? ¿Cómo los encontramos? ¿Cómo los **INDEXAMOS**? ¿Y cómo definimos **un marco** y reglas?

> Esta cuestión del indexado es crucial en el protocolo Ordinals y en los protocolos construidos sobre Ordinals.

Pero entonces, ¿cómo funciona?

¡Sumergámonos en la historia!

#### 	a) Inicio de `sns`

Un actor importante en el ecosistema ordinales es [@domodata](https://twitter.com/domodata).

Llegó con su nodo completo el 24 de febrero [domo: "Full node finally running. Will soon find out if the feeling of owning a wallet full of UTXOs, redolent with the scent of rare and exotic sats, is beyond compare."](https://twitter.com/domodata/status/1629134663842254848) y rápidamente propuso nuevos estándares.

El primero que utilizó es `sns` para Servicio de Nombres de Sats:
![domo-sns](./assets/domo_sns.png)
[domo: "@sats-names"](https://twitter.com/domodata/status/1630948879737794561) 


Siendo el primer protocolo construido en Ordinals, tiene dos formas de ser utilizado.

1. La primera es muy simple, simplemente consiste en registrar un archivo de texto con `.sats`. Esto no es lo que nos interesa aquí.

2. Definir un archivo JSON que contenga las siguientes especificaciones:
   a) El nombre del protocolo a través de `"p" : "sns"`, aquí el protocolo utilizado es `sns`;
   b) La operación deseada a través de `"op": "reg"`, aquí `reg` significa que se está definiendo un nuevo nombre;
   c) El nombre elegido a través de: `"name" : "my_name.sats"`, elejimos `my_name.sats`.

3. También hay dos parámetros opcionales en este protocolo:
   a) Asociar un nombre sats con una dirección btc a través de `"rev" : "bc1q...."`;
   b) Asociar un nombre sats con una inscripción a través de `"relay" : "...i0"`.

Puede encontrar la documentación en la siguiente dirección [Mint names - Sats Names](https://docs.sats.id/sats-names/sns-spec/mint-names)

La idea del protocolo `sns`, que será la que seguiremos a lo largo de estos subprotocolos, es el uso de un JSON que siempre verifica más o menos esta estructura.

Aquí hay un ejemplo:
```JSON
{
 "p" : "sns",
 "op" : "reg",
 "name" : "galoisfield.sats",
 "rev" : "1A1zP1eP5QGefi2DMPTfTL5SLmv7DivfNa"
}
```

Así que aquí hemos construido un protocolo cuyos elementos son fácilmente identificables entre todas las inscripciones y que permiten a cualquiera *indexar* estos elementos y utilizarlos en cualquier aplicación.

> Para los desarrolladores experimentados, pueden intentar desarrollar o integrar este protocolo en una aplicación para permitir el inicio de sesión de usuarios o la verificación de logros en su aplicación.

#### Llegada de `brc-20`

Ahora que hemos entendido cómo funciona el protocolo `sns`, será muy fácil para nosotros entender otros protocolos como por ejemplo `brc-20`.

Presentado por primera vez por *@domodata* [domo: "Usando la inspiración de @sats_names y @redphonecrypto, me pregunté si el concepto podría expandirse a tokens fungibles. Esto es lo que se me ocurrió."](https://twitter.com/domodata/status/1633658976931037184).

La idea es simple: replicar el concepto de protocolo como `sns` para crear tokens en Bitcoin.

Se mantiene: el protocolo, la operación, se reemplaza `name` por `tick`, se agrega `amt` para la cantidad de tokens considerados y se distinguen las operaciones de despliegue, de mint y de transferencia.

La operación más *tricky* es la de transferencia, sobre la cual volveremos más adelante.

Una restricción impuesta por Domo es que el ticker de un brc-20 debe tener solo 4 caracteres.

> Encontrar una referencia de por qué 4 caracteres.

Para obtener más detalles en video sobre estas explicaciones, puedes consultar [The Only BRC-20 Guide You Will Need](https://www.youtube.com/watch?v=XftBkRZ9jqk).

Vamos a hacer el esquema completo de un token `DBTC` para DécouvreBitcoin (el token ya existe y no está relacionado, esto es solo a modo indicativo y no constituye una invitación a hacer mint, comprar u otras acciones):

1. El despliegue

Tenemos nuestro ticker, ahora debemos decidir una cantidad. Para ser coherente con el ya desplegado, tomemos 21,000.
```JSON
{ 
 "p": "brc-20",
 "op": "deploy",
 "tick": "DBTC",
 "amt" : "21000",
 "lim" : "1"
}
```

La instrucción `lim` determina cuánto(s) token(s) se pueden mintear a la vez.

Si `lim = 1` pero mintee 2, entonces no obtendré ningún token porque su instrucción no será válida según el protocolo.
¡Preste mucha atención a esto cuando haga mint!

![DBTC](./assets/DBTC.png)

2. El mint

Una vez que nuestro token está desplegado, podemos hacer mint. Para ello, debes ingresar el siguiente JSON:

```JSON
{
 "p" : "brc-20",
 "op": "mint",
 "tick": "DBTC",
 "amt": "1"
}
```

Una vez que la inscripción se haya minado en un bloque, tendrás 1 DBTC asociado a tu dirección de mint.

3. La transferencia

Ahora que has minteado el token `DBTC`, puedes transferirlo (a tu mejor amigo, tu pareja o alguien que desee comprártelo).

Para hacerlo, debes seguir dos pasos:

A. La inscripción de la operación `transfer`

```JSON
{
 "p": "brc-20",
 "op": "transfer",
 "tick": "DBTC",
 "amt": "1"
}
```

Ahora tienes 1 DBTC transferible según el protocolo `brc-20`.

Entonces puedes transferirlo.

B. La transferencia del token

Ahora debes hacer una transacción de Bitcoin.
Debes enviar la inscripción de transferencia a la persona deseada.


A través de las billeteras en línea, simplemente haga clic en `Transferir` o `Enviar`.

A través del cliente ord, necesitará:
- listar sus inscripciones con el comando `ord wallet inscriptions`;
- seleccionar la que le interese;
- ingresar el comando `ord --cookie-file=/Volumes/mon_disque/bitcoin/.cookie wallet send --fee-rate 3 bc1pxsa6d95jrwald4jjsu0kwu4pyaztmjvh6rdjyrztfv0yx2gakk9qse5sjf acddd636c4ab0fb45c9f70ce2598cffa205c88594de916832a5789e3e58ca688i0`.

Si ya conoce la inscripción de transferencia, ingrese directamente el último comando (adaptado a su contexto, especialmente para la ubicación del `cookie-file` si es necesario).

Por lo tanto, hemos cubierto todas las operaciones realizables con `brc-20`. En este punto, debería tener una mejor comprensión de cómo funcionan estos protocolos construidos en Ordinals.

Habría mucho que decir sobre las discusiones que han animado los diferentes discords y telegrams relacionados con `brc-20`, y esto podría ser objeto de artículos adicionales.

#### c) Un Meta Protocolo: BOSS

Ahora que hemos entendido cómo funcionan estos dos protocolos, podemos abordar un tema muy importante que aún está en desarrollo, el Meta Protocolo [**BOSS (Bitcoin Operationnal Standard System)**](https://github.com/opstandard/Boss).

BOSS ofrece un futuro prometedor con la idea de Meta Protocolos. Creando un estándar para todos estos protocolos salvajes, así como una máquina virtual. Se espera que muchas soluciones futuras se construyan sobre BOSS. En cualquier caso, BOSS será un campo de experimentación bastante loco en Bitcoin.

Se proponen regularmente nuevas cosas. Interfaces mejoradas, código por aclarar, artículos por escribir, tutoriales por realizar, las novedades no faltan y debemos mantenernos informados para estar donde se están desarrollando las cosas.

### 3) Algunas anécdotas técnicas

#### a) Las inscripciones malditas

Las inscripciones "malditas" (Cursed Inscriptions). Estas inscripciones aparecieron unos meses después del lanzamiento de Ordinals. Una inscripción maldita es básicamente una inscripción que no es válida a priori para el protocolo Ordinals.

####	i)El Git issue #2062

En el git issue [Inscription numbers off by one, or the curious case of transaction `c1e0db6368a43...d9e4117151` · Issue #2062 · ordinals/ord](https://github.com/ordinals/ord/issues/2062) se encontró algo extraño.
¡Una inscripción con 0 satoshis adjuntos!

¡Carajo! Dijimos que debían inscribirse en satoshis. ¿Cómo es posible?

¿Es esta la única forma de inscripción no válida?

¡NO!

Se han podido inscribir muchas inscripciones no válidas según el protocolo Ordinals, de las cuales se puede obtener más detalles en la issue abierta por Casey [Cursed Inscription Tracking Issue · Issue #2045 · ordinals/ord](https://github.com/ordinals/ord/issues/2045).

Inscripciones múltiples, inscripciones con otros `OP_CODE` como el `op_code`, `OP_66` que no está indexado por `ord`, ...

Para integrar las inscripciones malditas en el mercado y en el índice, se decidió inicialmente indexarlas con un número negativo antes de considerarlas válidas y positivas en la nueva actualización [Leonidas.og: "¡La versión 0.6.0 del Protocolo Ordinals acaba de ser lanzada! Aquí tienes todo lo que necesitas saber sobre esta importante actualización"](https://twitter.com/LeonidasNFT/status/1665437076450336768).

Apenas estamos comenzando y muchas cosas están destinadas a cambiar. Las inscripciones malditas serán algo histórico para el ecosistema. Aunque no es necesario sumergirse completamente en este tipo de inscripciones, es importante ver que ha sido un paso importante en la integración de nuevas formas de inscripciones en Ordinals.
Ordinals es un protocolo muy joven y en constante evolución. Seguir este tipo de eventos ayuda a comprender mejor lo que puede suceder a continuación y a saber cómo manejar las novedades en las inscripciones.

Para más detalles sobre los `OP_CODE` de Bitcoin, se puede consultar [Opcodes used in Bitcoin Script - Bitcoin Wiki](https://wiki.bitcoinsv.io/index.php/Opcodes_used_in_Bitcoin_Script).

-> Referencias adicionales sobre las inscripciones malditas
[Bitcoin Ordinals and the mystery of the 'cursed Inscriptions' - AMBCrypto](https://ambcrypto.com/bitcoin-ordinals-and-the-mystery-of-the-cursed-inscriptions/)
[Inscriptions in Reverse: The Quirky Journey of Cursed Ordinals - Influencive](https://www.influencive.com/inscriptions-in-reverse-the-quirky-journey-of-cursed-ordinals/)
[Bitcoin Ordinals rolls out upgrade to rectify 'Cursed Inscriptions' issue](https://cointelegraph.com/news/bitcoin-ordinals-upgrade-rectify-cursed-inscriptions-issue) 

#### ii) Desarrollo

La actualización de ordinales para tener en cuenta las inscripciones malditas en la versión (0.6.0) publicada el 4 de junio de 2023.

[raph: "Acabo de lanzar una nueva versión de ord (0.6.0), que implementa los primeros pasos para reconocer más tipos de inscripciones (inscripciones malditas). Además, ahora puedes pasar credenciales RPC a través de banderas de línea de comandos, variables de entorno o un archivo de configuración. https://t.co/Xi6C92cC6z"](https://twitter.com/raphjaph/status/1665367103342362625)

La aceptación de estas inscripciones malditas ahora permite manipular "legalmente" múltiples inscripciones en una misma transacción y en un mismo satoshi.

-> ¡Deberíamos preparar un taller sobre este tema!

#### b) bitmap y los nombres

Algunas inscripciones se han popularizado escribiendo solo texto en las últimas. Algunos modos han funcionado bien y uno que me gusta son los [nombres 𝕏](https://ordinalswallet.com/collection/%F0%9D%95%8F-names).

> Completar con la documentación de bitmap.

#### c) Inscripciones recursivas

Recientemente se han desplegado la mayoría de los frameworks de JavaScript en inscripciones.
[Ord.io en X: "¡React ahora está completamente en la cadena de Bitcoin!](https://twitter.com/ord_io/status/1694024434485538819)

Aquí encontrarás algunas herramientas inscritas:
- [ordengine-react@0.0.1](https://ordinals.com/content/faa7b9b0b7884360f6c2b34693855a0d60df5f344727c72e3691a80f84ec6a81i0)
- [React@18.2.0](https://ordinals.com/content/7f403153b6484f7d24f50a51e1cdf8187219a3baf103ef0df5ea2437fb9de874i0)
- [React-DOM@18.2.0](https://ordinals.com/content/89295aaf617708128b95d22e7099ce32108d4b918386e6f90994e7979d22ba72i0)

Estas nuevas inscripciones abren el camino a nuevas inscripciones y a un nuevo web en Bitcoin.

# Conclusión

Una de las cosas más poderosas ofrecidas por Ordinales es sin duda BOSS. Actualmente en desarrollo, las promesas de BOSS son bastante locas.
Deberíamos dedicar un artículo completo a las características que anuncia BOSS y un estudio profundo del lightpaper.

Un taller coordinado con un desarrollador JS que haya estudiado las propuestas técnicas de la BVM (Máquina Virtual de Bitcoin) propuesta por BOSS y un "teórico" que destaque la arquitectura del proyecto podría ser muy interesante para comprender mejor BOSS. 

Obviamente, hay más que solo BOSS. ¡Quedan muchas cosas por descubrir y crear!
Este curso, por más completo que sea, está lejos de cubrir todo y aún requiere un extenso trabajo en profundidad, así como investigación individual y académica para estar completo.

### Para involucrarse

-> Participar en la redacción de este curso.

-> Tutoriales en Youtube, transmisiones en vivo, contenido, acompañamiento de personas interesadas.

-> Desarrollo mediante bifurcación de unisat o lookordinals.

-> Desarrollo de nuevas ideas a través de inscripciones HTML o interpretación de código en formato txt a través de un nuevo indexador que se puede intentar.

-> Familiarizarse con BOSS tan pronto como el código esté disponible. Para un técnico en JS, coordinarse para organizar el taller discutido anteriormente.

### Anexos

Una serie de anexos en evolución para aclarar ciertos puntos de este curso.

#### Vocabulario

[//]: # (vocabulario)

- <u>**degens**</u> : Abreviatura de "degenerates" (degenerados). Se refiere a aquellos que ponen grandes cantidades de BTC en cosas nuevas, a menudo aún no comprendidas. Participan en la financiación de los primeros desarrollos y vierten una gran cantidad de liquidez en el mercado emergente. Se les encuentra menos en mercados considerados "más maduros", pero siguen estando presentes siendo menos poderosos porque son menos numerosos.

- <u>**sat**</u> : Un satoshi (o sat) es la unidad más pequeña de Bitcoin 1 sat = $10^{-8}$ BTC ;

- <u>**Virtual Bytes**</u> : Abreviado como vBytes o vB, esto corresponde al método actual de cálculo del tamaño de una transacción. La equivalencia es: 1 vB = 4 Bytes. Las tarifas (fees) en Bitcoin se calculan en sats/vB. En otras palabras, para una transacción que pesa 400 Bytes, pesará en Bitcoin 100 vB, con una tasa de 40 sats/vB, por lo tanto costará: 4,000 sats (~ 2€ actualmente) ;

- <u>**Protocolo**</u> : Llamo Protocolo a cualquier conjunto de reglas seguidas por una red y que permiten producir un servicio. Concretamente, son reglas que, al ser respetadas, permitirán hacer *algo*: producir un token, registrar datos, otorgar derechos, etc. Es importante tener en cuenta que un protocolo no depende de un lenguaje, ya que son reglas. Entonces hablamos de implementación del protocolo (o cliente). ¡Bitcoin es un protocolo! Existen varios clientes de Bitcoin que permiten interactuar con el protocolo, pero el principal utilizado es [Bitcoin Core](https://github.com/bitcoin/bitcoin). Para obtener detalles poco claros sobre los clientes actualmente utilizados: [Coin Dance | Bitcoin Blocks (historical) Summary](https://coin.dance/blocks/historical) ; 

- <u>**Indexador**</u> : Algoritmo que permite leer los datos asociados a un protocolo. Una vez recuperados a través de un indexador, simplemente hay que mostrarlos en un formato "amigable para el usuario". Dado que estos datos son bastante crudos, se puede crear un indexador con cualquier lenguaje (ya que las reglas están escritas en lenguaje humano) y se pueden extraer los datos en cualquier formato. En general, los datos indexados tienen una estructura y se intenta conservarla.

- <u>**Explorador**</u> : Un explorador es un sitio web que permite visualizar las operaciones realizadas en un protocolo dado. Se observa que el explorador va de la mano con el indexador. El explorador principal de Bitcoin es [mempool.space](https://mempool.space), el explorador oficial de ordinals es [ordinals.com](https://ordinals.com) y un muy buen explorador de Bitcoin + Ordinals es: [ordpool.space](https://ordpool.space);

- <u>**Script**</u> : Un script es una secuencia de instrucciones que ejecutan operaciones en una dirección. El script está escrito en [`OP_CODE`](https://wiki.bitcoinsv.io/index.php/Opcodes_used_in_Bitcoin_Script). El script de Bitcoin, al igual que los scripts en general, no es un lenguaje [Turing completo](https://fr.wikipedia.org/wiki/Turing-complet#:~:text=6.1%20Articles-,Langages%20de%20programmation%20Turing%2Dcomplets,de%20la%20m%C3%A9moire%20des%20ordinateurs), es decir, no se pueden programar todas las [funciones calculables](https://fr.wikipedia.org/wiki/Fonction_r%C3%A9cursive). En otras palabras, faltan piezas para programar todo lo que se desee. En contraste, [Solidity](https://soliditylang.org/) es un lenguaje Turing completo;

- <u>**OP_CODE**</u> : Conjunto de operaciones disponibles en Bitcoin para realizar operaciones algorítmicas complejas;

- <u>**Inscripciones**</u> : Datos almacenados en una transacción de Bitcoin;

- <u>**Protocolo basado en JSON**</u> : Llamo así a los protocolos como `brc20` y `sns`. Estos son protocolos definidos y que actúan a través de archivos JSON registrados en Bitcoin a través de Ordinals. Atención: cbrc20 no es un protocolo basado en JSON ya que se basa en los metadatos en el protocolo Ordinals.

<!--
- <u>****</u>
-->
#### Referencias

> Criptografía: En el commit [@15ed05](https://github.com/ordinals/ord/commit/15ed050d59de6e0f1d581de5a92e3809d0069b0c) se añadió el paquete para la gestión de la firma de Schnorr a través de `secp256k1` al archivo `main.rs`
![schnorr](https://assets-global.website-files.com/5f75fe1dce99248be5a892db/65675d9184b6e14799543eb9_6552522ea592a6c95fb7ea99_6524562a3a64ae68224a1269_ECDSA-vs-Schnorr-Signatures-Diagram.png)

> [Documentación oficial de Inscripciones](https://docs.ordinals.com/inscriptions.html)

> [ordpool.space | Explorador Bitcoin + Visualización de transacciones Ordinals](https://ordpool.space)

> [Descompilar una transacción con imagen](https://twitter.com/Blockcryptology/status/1708454640373686299)

> [Script - Bitcoin Wiki](https://en.bitcoin.it/w/index.php?title=Script&oldid=69733)


##### Para profundizar

- [7 Pasos Requeridos Para Asegurar Tus iFrames – Reflectiz](https://www.reflectiz.com/blog/iframe-security/#:~:text=The%20main%20security%20threat%20of,and%20keystrokes%20through%20an%20iFrame.). Necesitamos tener en cuenta que `https://ordinals.com/inscription/inscription_id/content` proporciona la ejecución del contenido a través de un IFrame. El código estará incrustado en etiquetas IFrame. ¿Qué sucede si te doy una URL del contenido de ordinals? En ese caso, ordinals.com podría ser vulnerable a ataques... Necesitamos pensar en ello.
