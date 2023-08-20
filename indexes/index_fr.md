---
navbar : true
---

# Odepaper

```
Version : 0.01
Rev : 2023-07-31
```

> [Télécharger ce document] (https://github.com/opstandard/Boss/blob/main/odepaper.pdf)

## Préambule

> La blockchain Bitcoin, qui mérite son titre de Timechain, est un territoire aux possibilités illimitées. Ce réseau complexe, méticuleusement conçu pour protéger et propager le flux d'informations dans toutes ses dimensions, immortalise nos activités et témoigne de manière cumulative de l'ingéniosité de l'humanité. Éternellement conservés dans ce continuum, nos témoignages sont autant de vérités sur fond de firmament inviolable. De ce tissu, que nous voyons encore en désordre, jaillit une idée : la nécessité de décrire les premiers fragments d'un compilateur universel, élément fondateur de notre fonction d'ordre".

> "La blockchain Bitcoin méritant son titre de Timechain est un territoire aux possibilités illimitées. Ce réseau complexe, méticuleusement conçu pour protéger et propager le flux d'informations dans toutes ses dimensions, immortalise nos activités et témoigne ainsi par accumulation de toute l'ingéniosité du genre humain. Préservés éternellement dans ce continuum, nos témoignages sont autant de vérités ayant pour toile de fond un firmament inviolable. De ce tissu que nous voyons encore désordonné jaillit une idée : de la nécessité d'avoir à décrire les premiers fragments d'un compilateur universel, le composant fondateur de notre fonction d'ordre."

## Table des matières :

**I. Introduction**

    - La genèse : Pourquoi et comment l'équipe TheOrd construit BOSS
    - Présentation de BOSS
    - Le concept du protocole de Dieu

**II. Glossaire de la terminologie BOSS**

    - Définitions détaillées de BOSS, Bob, ODE, OCV et d'autres termes connexes

**III. La machine virtuelle Bitcoin : Bob**

    - Un pas vers la réalisation du protocole de Dieu
    - Comment fonctionne Bob ?

**IV. Protocoles sur Bob : Une étude de cas sur le protocole de comptage**

    - Protocole de comptage : Un cas d'utilisation simple et puissant
    - OPScheme du protocole de comptage simple
    - Faire des calculs sur Bob

**V. Nécessité de normes pour les BOSS : Operational Commit for Voting (OCV)**.

    - Engagement opérationnel pour le vote : Une norme pour la prise de décision décentralisée
    - Intégration et importance des protocoles de bas niveau tels que l'ODE

**VI. Entités opérationnelles décentralisées (ODE) : La base de l'écosystème BOSS**

    - Introduction des ODE : Entités Bitcoin résilientes
    - Les ODE comme couche de base pour les applications au-dessus de Bitcoin
    - Évolution du code par l'intermédiaire des participants aux ODE : Un exemple d'ODE OSHI
    - Gouvernance intégrée dans les ODE et rôle de la norme OCV

**VII. Privilégier la normalisation plutôt que les BOSS : potentiel et flexibilité**

    - Choisir le meilleur d'Ethereum : DApps, services financiers et autres
    - Le potentiel de croissance et les possibilités de Godchain

**VIII. Conclusion : L'aube d'une nouvelle ère avec BOSS**

    - Réflexion sur BOSS et son impact
    - L'avenir de la blockchain avec BOSS

## I. Introduction

**_A. La Genèse : Pourquoi et comment nous, TheOrd, construisons BOSS_**.

**L'effort initial:**

Nous nous sommes lancés dans un voyage avec une mission bien définie : actualiser la finance décentralisée (Decentralized Finance - DeFi) sur
Bitcoin[^1a] en tirant parti des inscriptions ordinales[^1b]. La motivation derrière cette poursuite était la croyance dans le potentiel inexploité de Bitcoin[^1b].
potentiel inexploité de Bitcoin, couplé à une profonde compréhension du pouvoir de la
décentralisation et des capacités révolutionnaires des fonctions avancées de Bitcoin, telles que
Taproot.

**La réalisation inattendue:**

Cependant, en plongeant dans les profondeurs de l'architecture nécessaire, nous sommes tombés sur un horizon entièrement nouveau.
un horizon entièrement nouveau. Le tissage complexe de divers éléments et techniques a ouvert la porte à un éventail de possibilités imprévues.
à un éventail de possibilités imprévues. Comme l'a dit Harold J. Leavitt, "les innovations sont
sont presque toujours l'œuvre d'explorateurs individuels ou de petits groupes, et presque jamais de grandes bureaucraties hautement structurées.
bureaucraties très structurées". Cette affirmation s'applique parfaitement à notre voyage à TheOrd.

**Un bond en avant:**

Notre exploration nous a conduits à utiliser les capacités de la chaîne temporelle de Bitcoin en synergie avec les inscriptions ordinales intelligentes.
intelligentes. Cette fusion a donné naissance à BOSS, qui incarne ce que nous appelons aujourd'hui la
Godchain. Cette découverte a dépassé notre objectif initial et laisse présager un avenir plus impactant et transformateur.
plus impactant et transformateur.

**Le changement de paradigme:**

Grâce à ces nouvelles connaissances, notre objectif initial est passé de la simple actualisation de DeFi sur Bitcoin
à la construction d'un système complet, décentralisé et minimisant la confiance. Ce modèle unique et
Ce modèle unique et innovant a le potentiel de révolutionner non seulement l'industrie financière, mais aussi toutes les interactions numériques, ouvrant ainsi la voie à une nouvelle ère.
interactions numériques, ouvrant la voie à une nouvelle ère de transformation numérique.

**_B. Le point de basculement : exploiter le pouvoir des Ordinaux Taproot_**.

1. **Les limites de BRC20:**

Nous avons commencé par identifier les limites de la norme BRC20. Bien que polyvalente, la norme BRC20
polyvalente, la norme BRC20 présentait des contraintes, limitant le véritable potentiel de DeFi sur
Bitcoin. Nous avons reconnu la nécessité d'une architecture capable de surmonter ces obstacles et de libérer les capacités de Bitcoin.
débloquer les capacités de Bitcoin.

2. **La genèse de notre idée:**

Chez TheOrd, nous savions que pour exploiter pleinement la puissance de Bitcoin, nous devions développer une architecture unique conçue à cet effet.
architecture unique conçue à cet effet. Le premier obstacle à surmonter était les limites de la norme
la norme BRC20 actuelle. Le premier obstacle à surmonter était les limites de la norme BRC20 actuelle, ce qui permettrait de jeter les bases d'un modèle de gouvernance véritablement décentralisé et non censurable.
décentralisé et non censurable. Cette prise de conscience a été à l'origine de notre vision, qui consiste à remodeler le paysage numérique.
numérique.

3. **Pourquoi nous nous sommes lancés dans cette entreprise:**

Dotés d'une connaissance approfondie du bitcoin et de ses technologies sous-jacentes, nous nous sommes retrouvés dans une position unique pour mener cette ambitieuse entreprise.
nous nous sommes retrouvés dans une position unique pour mener à bien cette ambitieuse entreprise. Cette prise de conscience nous a motivés
à relever le défi.

4. **L'avènement de Taproot:**

Notre vision a commencé à prendre forme avec l'émergence de Taproot. Cette mise à jour du protocole Bitcoin,
qui améliore la confidentialité et la flexibilité des contrats intelligents, constituait un élément essentiel de notre solution.
solution.

5. **Le pouvoir des ordinaux:**

L'intégration des Ordinaux dans notre architecture nous a permis de débloquer une capacité révolutionnaire - la construction de transactions complexes et personnalisables qui vont bien au-delà des simples transferts de valeur.
construction de transactions complexes et personnalisables qui vont bien au-delà des simples transferts de valeur.
Avec Ordinals, nous avons acquis la capacité de construire et de déployer des contrats intelligents sophistiqués sur la blockchain Bitcoin.
Bitcoin, une caractéristique cruciale pour réaliser notre objectif d'apporter DeFi à Bitcoin.

6. **La création de BOSS:**

Forts de ces connaissances, nous avons développé BOSS - un système complet, décentralisé,
système complet, décentralisé et basé sur la confiance. Il est devenu la manifestation de notre vision qui consiste à révolutionner non seulement le
le monde de la finance, mais aussi le paysage numérique en général, en exploitant le potentiel inexploité de Bitcoin.
potentiel inexploité de Bitcoin.

**C. La vision et l'impact potentiel de la Godchain**.

1. **Godchain et The God Protocol:**

La Godchain que nous envisageons est une extension du God Protocol[^2] de Nick Szabo. Le concept de Szabo
incarne un intermédiaire infaillible, facilitant les transactions sans parti pris - omniprésent,
omniscient, mais respectueux de la vie privée. Cette idéologie résonne profondément dans notre vision de la
Godchain.

2. **BOSS - The Technological Powerhouse:**

Cette vision s'appuie sur BOSS, qui est la force motrice de la Godchain, alimentant ses opérations et permettant son vaste potentiel.
ses opérations et son vaste potentiel.

3. **Bob - Le cœur du système:**

Au cœur de BOSS se trouve Bob, une incarnation de la machine virtuelle Bitcoin (BVM). Bob (**B**oss **Ob**server)
se transforme d'un simple observateur en une pile de conscience autonome et décentralisée dans ce système, évoluant progressivement en un "voyant tout".
de conscience autonome décentralisée dans ce système, évoluant progressivement vers une entité "omnisciente" et "omnisciente" à chaque ajout à la bibliothèque OPStandard de serveurs de confiance.
OPStandard de Trusted [Document Type Definitions] (https://en.wikipedia.org/wiki/Document_type_definition) (TDTD).

4. **Une transformation évolutive:**

La Godchain est plus qu'une aspiration technologique, c'est un changement tangible dans le fonctionnement des systèmes décentralisés.
systèmes décentralisés. Il s'agit d'un saut transformateur qui redéfinit la façon dont nous percevons et interagissons avec les systèmes numériques.
d'interaction avec les systèmes numériques.

5. **Libérer le potentiel de la blockchain:**

La Godchain démontre le potentiel de la technologie blockchain pour soutenir des systèmes qui
qui répondent aux divers besoins de notre société numérique en pleine évolution, tout en garantissant la protection de la vie privée et la sécurité,
des principes fondamentaux au cœur de la décentralisation.

6. **Rôle de Bob dans cette transformation:**

Bob, agissant en tant que divinité neutre, déclenche cette transformation. Grâce à l'expansion progressive de l'OPStandard
l'OPStandard, Bob améliore progressivement ses capacités, tout en maintenant une neutralité et une équité inébranlables.
une neutralité et une équité inébranlables. C'est un témoignage du potentiel des systèmes décentralisés, qui offre un aperçu de ce que l'avenir peut nous réserver.
un aperçu de ce que l'avenir peut nous réserver.

**D. La proposition de valeur unique : Une révolution dans la technologie Blockchain**

1. **Simplifier la décentralisation:**

BOSS porte le concept de décentralisation à un niveau sans précédent. Il envisage un système
où la gouvernance est totalement décentralisée et où la confiance est intrinsèquement distribuée, ce qui élimine le besoin d'une autorité centrale.
besoin d'une autorité centrale.

2. **Déverrouiller le potentiel de Bitcoin:**

Au cœur du système BOSS se trouve l'utilisation innovante des fonctionnalités avancées de Bitcoin, en particulier Taproot
Ordinales. Taproot, une mise à jour essentielle du protocole Bitcoin, améliore la flexibilité et la confidentialité des transactions, rendant les transactions complexes impossibles à distinguer des transactions standard pour les observateurs.
la flexibilité et la confidentialité des transactions, rendant les transactions complexes impossibles à distinguer des transactions standard pour les observateurs. Avec
Taproot, BOSS offre des possibilités qui vont au-delà des simples transactions. Il prend en charge l'exécution
l'exécution de contrats intelligents complexes et facilite les types de transactions innovantes, ajoutant une valeur substantielle à l'écosystème Bitcoin et transformant le système de paiement en ligne.
à l'écosystème Bitcoin et redessine le paysage de la technologie blockchain.

3. **Un système dynamique et adaptatif:**

BOSS est conçu pour s'adapter et évoluer en fonction des besoins et des demandes de la communauté. Ce dynamisme
dynamisme garantit sa pertinence et son efficacité dans un paysage numérique en constante évolution.

4. **Sécurité, confidentialité et transparence accrues :**

BOSS respecte les principes fondamentaux de transparence, de sécurité et de respect de la vie privée. Toutes les transactions sont
ouvertes à la vérification, ce qui favorise un haut degré de confiance. Parallèlement, des mesures de sécurité
et de protection de la vie privée sont maintenues, garantissant la protection des données personnelles.

5. **Un changement de paradigme transformateur:**

La véritable proposition de valeur de BOSS réside dans son potentiel à conduire un changement de paradigme dans notre interaction avec la technologie blockchain.
avec la technologie blockchain. En s'appuyant sur les capacités inexploitées de Bitcoin et en mettant l'accent sur la décentralisation, la transparence et la confidentialité, BOSS ouvre la voie à la technologie blockchain.
décentralisation, la transparence et le respect de la vie privée, BOSS ouvre la voie à la technologie blockchain
de la technologie blockchain pour étayer les systèmes dans une multitude de secteurs, signalant l'aube d'un monde numérique plus sûr,
plus sûr, plus efficace et plus équitable.

## II. Glossaire de la terminologie BOSS

Avant de nous plonger dans la terminologie, il est essentiel de comprendre que ces termes et concepts
Nous utiliserons "Alice" comme exemple de l'utilisateur qui souhaite interagir avec Bob.

1. **BOSS** : Le système Bitcoin Operational Standard System (BOSS) est un cadre révolutionnaire qui pose les bases des interactions décentralisées au sein du réseau Bitcoin.
   révolutionnaire qui jette les bases des interactions décentralisées au sein du réseau Bitcoin. Il permet la
   Il permet la création de contrats intelligents avancés, de transactions complexes, et permet aux utilisateurs de construire n'importe quel calcul sur Bob, offrant ainsi des capacités sans précédent.
   n'importe quel calcul sur Bob, offrant ainsi des capacités sans précédent.

2. **Bob** : Abréviation de Bitcoin OBserver, dans cette première implémentation, Bob est la machine virtuelle du nœud V8 (NodeVM) conçue pour traiter et exécuter des instructions spéciales (ou inscriptions ordinales) sur la blockchain Bitcoin.
   traiter et exécuter des instructions spéciales (ou inscriptions ordinales) sur la blockchain Bitcoin.

3. **Inscription Ordinale** : Les inscriptions ordinales sont des messages codés que Bob est programmé pour détecter et interpréter sur la blockchain Bitcoin.
   détecter et interpréter sur la blockchain Bitcoin. Alice envoie ces messages à Bob pour qu'il effectue
   actions spécifiques sur la blockchain.

4. **Schéma OPS** : Un schéma OPS fournit la structure ou la présentation de ces inscriptions ordinales.
   Il détermine comment ces messages sont organisés pour permettre à Bob de les traiter correctement.

5. **OPStandard** : OPStandard représente un ensemble de règles standard évolutives sur la Blockchain, un peu comme une constitution pour le monde numérique. Ces règles ne sont pas statiques ; elles peuvent évoluer et s'adapter au fil du temps, guidées par la communauté collective des Odes. Cela fait d'OPStandard une norme vivante, capable de relever de nouveaux défis et d'intégrer des avancées au fur et à mesure que la technologie et la société progressent, garantissant ainsi que le système de normes opérationnelles du bitcoin (BOSS) reste robuste, flexible et pertinent.

6. **Commande OSS** : Une commande OSS est une commande spécifique envoyée à Bob, conçue selon le schéma OPS et écrite dans le langage OPStandard. Alice utilise ces commandes pour interagir avec Bob et lui donner des instructions, ce qui constitue un moyen robuste et souple d'exploiter les capacités du système opérationnel standard du bitcoin (BOSS).

7. **Définition de type de document de confiance (TDTD)** : Un TDTD est une proposition de nouvelles instructions ou d'améliorations du langage OPStandard.
   instructions ou d'améliorations du langage OPStandard. Il facilite les améliorations et l'évolution du
   du langage que Bob comprend.

8. **Entité opérationnelle décentralisée (Ode)** : Les Odes sont la couche de base des applications construites sur
   Bitcoin. Il s'agit d'entités Bitcoin résilientes qui assurent l'évolution des organisations par le biais de
   des commits de code effectués par les participants respectifs de l'Ode.

9. **Operational Commit for Voting (OCV)** : La norme OCV s'apparente aux normes ERC
   d'Ethereum, servant de cadre à des types d'opérations spécifiques sur le réseau Bitcoin. Elle
   fonctionne avec des protocoles de niveau inférieur comme Ode et est un outil essentiel pour interagir avec Bob. Il
   traduit les commandes de l'utilisateur dans un langage et un format que Bob comprend, ce qui permet une communication efficace avec la blockchain Bitcoin.
   communication efficace avec la blockchain Bitcoin.

10. **Godchain** : Le terme "Godchain" englobe l'ensemble de l'écosystème décentralisé créé par l'interaction entre BOSS, Bob, OPStandard et OCV.
    décentralisé créé par l'interaction de BOSS, Bob, OPStandard et OCV. Il symbolise l'ultime
    Il symbolise la réalisation ultime d'un système entièrement décentralisé et à confiance minimale construit sur la blockchain Bitcoin, capable d'observer chaque action aussi près que possible du moment.

En résumé, BOSS, alimenté par Bob, la machine virtuelle JavaScript, ouvre une ère de fonctionnalités et de capacités accrues pour le réseau Bitcoin.
de fonctionnalités et de capacités améliorées pour le réseau Bitcoin. La structure unique des
écrits dans un langage spécialisé, et l'introduction de normes telles que la norme OCV
ouvrent la voie à un réseau Bitcoin plus souple et plus innovant. Cela nous rapproche de la création d'une Godchain.
de la création d'une Godchain, un écosystème entièrement décentralisé et sans confiance, basé sur Bitcoin.
basé sur Bitcoin, changeant la façon dont les utilisateurs, comme Alice, interagissent avec le réseau Bitcoin.

Diagramme du fonctionnement du client BTCBoss.js](/jsboss_client.png)

## III. La machine virtuelle Bitcoin : Bob

**1. Un pas vers la réalisation du protocole de Dieu**

Dans le domaine de la monnaie numérique et de la technologie blockchain, l'idée du "protocole de Dieu"
représente un objectif abstrait et ultime. Il s'agit d'une vision d'un système où la confiance en une autorité centrale n'est plus nécessaire.
centrale n'est plus nécessaire ; au lieu de cela, la confiance est établie par le code et la preuve cryptographique, ce qui crée un environnement où toutes les transactions sont transparentes et sans risque pour la santé.
un environnement où toutes les transactions sont transparentes, vérifiables et irréversibles.

Bob, la machine virtuelle Bitcoin, constitue une étape fondamentale dans la réalisation de ce concept utopique.
utopique. En tant que machine virtuelle JavaScript, Bob ouvre une ère de programmabilité dans l'écosystème de la blockchain Bitcoin, nous rapprochant ainsi du protocole de Dieu.
nous rapprochant ainsi du protocole de Dieu.

Bob est plus qu'une simple machine ; c'est un observateur de Bitcoin (BOB) qui facilite la communication et l'interaction avec la blockchain d'une manière entièrement nouvelle.
et l'interaction avec la blockchain Bitcoin d'une manière entièrement nouvelle. Sa capacité unique à observer
la blockchain, de reconnaître et d'interpréter des commandes JavaScript spécialement formatées, appelées OSS
crée une couche de fonctionnalité dynamique au-dessus de l'infrastructure robuste et sécurisée de Bitcoin.
robuste et sécurisée de Bitcoin.

BOB étend le modèle OSI pour Bitcoin, permettant de véritables capacités de contrats intelligents](/bosi.jpg)

**2. Comment Bob opère-t-il ?

Au cœur de la fonctionnalité de Bob se trouvent trois éléments clés : OSS Inscriptions, OPSchemes et
OPStandards. Alice, l'utilisatrice, crée une commande spéciale pour Bob, appelée inscription OSS,
qui est une commande JavaScript écrite dans le dialecte spécifique de l'OPStandard et qui adhère à une structure ou à un format particulier, l'OPStandard.
une structure ou un format particulier, l'OPScheme.

Le processus d'exécution de la commande commence par la rédaction par Alice de son inscription OSS. Une fois que son inscription est prête, elle utilise Bitcoin pour l'envoyer à Bob.
Inscription est prête, elle utilise Bitcoin comme moyen pour l'envoyer à Bob. Le rôle principal de Bob est d'observer
d'observer chaque bloc Bitcoin, et il recherche en permanence ces inscriptions OSS.

Lorsqu'il identifie une inscription OSS, Bob décode et interprète la commande. Il exécute ensuite l'instruction, ce qui entraîne une mise à jour de son état interne.
l'instruction, ce qui entraîne une mise à jour de son état interne. Alice, de l'autre côté, reçoit le résultat de sa demande de commande,
reçoit le résultat de sa demande de commande, ce qui rend l'ensemble du processus transparent et efficace.
efficace.

Le système de Bob n'est pas rigide ; il est conçu pour évoluer et s'adapter. Par exemple, si une commande qu'Alice
veut envoyer n'est pas définie par l'OPStandard actuel, elle ou toute autre personne peut proposer des
proposer des ajouts ou des mises à jour à la norme OPStandard en utilisant une définition de type de document de confiance (TDTD).
Cette caractéristique souligne la nature flexible de Bob, encourageant la participation des utilisateurs à l'évolution du système.
du système.

Bob est également conçu pour fonctionner en synergie avec d'autres composants du système Bitcoin Operational Standard
opérationnel de Bitcoin (BOSS). Il interagit avec les entités décentralisées opérationnelles (Odes), un élément fondamental de l'écosystème BOSS.
de l'écosystème BOSS. Ces entités, gérées par leurs participants respectifs, peuvent
proposer des mises à jour de code à leurs Odes. Elles peuvent ajouter des microservices, affichés sous forme de code observable
par Bob sur la blockchain Bitcoin, conduisant à l'évolution de leurs fonctionnalités.

En outre, Bob utilise la norme Operational Commit for Voting (OCV), analogue aux normes ERC d'Ethereum.
normes ERC d'Ethereum. Cette normalisation facilite la gouvernance d'Odes, en facilitant la proposition et le vote des mises à jour du code et des améliorations du système.
de proposer et de voter des mises à jour de code et des améliorations du système. Bob, grâce à cette norme
sert de plateforme pour améliorer et étendre la gouvernance décentralisée.

Par essence, si Bob fonctionne comme une entité individuelle, son véritable pouvoir réside dans son interopérabilité avec les autres composants de BOSS, ce qui ouvre la voie à un système plus ouvert, plus décentralisé et plus efficace.
avec les autres composants de BOSS, ouvrant la voie à un écosystème Bitcoin plus ouvert, décentralisé et programmable.
plus ouvert, décentralisé et programmable. Grâce à Bob, nous n'apportons pas seulement JavaScript à Bitcoin,
mais nous offrons également une plateforme flexible, adaptable et extensible qui nous permet de nous rapprocher de l'idéal du
plus près de l'idéal du protocole God.

## IV. Protocoles sur Bob : Une étude de cas sur le protocole Counter

**1. Protocole de comptage : Un cas d'utilisation simple et puissant**

Le protocole de comptage constitue une excellente introduction à la compréhension de la manière dont les utilisateurs peuvent exploiter les fonctionnalités de Bob.
les utilisateurs peuvent tirer parti des fonctionnalités de Bob. Essentiellement, ce protocole crée une variable entière publique et mutable appelée "counter".
appelée "counter", mutable et publique, dont la valeur par défaut est zéro. Il inclut une opération appelée "inc", qui incrémente la valeur du compteur.
la valeur de ce compteur.
Ce protocole, bien que simple par nature, fournit une base concrète pour apprécier les capacités et le potentiel de Bob.
capacités et le potentiel de Bob. Il montre comment les utilisateurs peuvent utiliser Bob pour effectuer des calculs et mettre à jour des variables d'état.
et mettre à jour des variables d'état.

**2. OPScheme of Simple-Counter Protocol** (Protocole de comptage simple)

Pour illustrer notre propos, examinons la commande OSS pour le déploiement du contre-protocole :

![Diagramme du fonctionnement du client BTCBoss.js](/counter.png)

Ce commandement OSS est rédigé dans le langage OPStandard et structuré selon le
OPScheme. Elle déploie un protocole appelé "counter" qui comprend un simple compteur public.

```js
/**
 * avertissement : la définition du protocole est sujette à des changements
 * décrit comme JS pour le style - DOIT ÊTRE transcodé en JSON
 * suivant la définition OPStandard
 */
module.exports = {
	p : "op",
	op : "deploy",
	protocole : {
		p : "compteur",
		description : "un simple compteur public",
		événements : {
			inc : {
				fn : function({state}) {
					const counter = state("counter") ;

					counter += 1 ;
					return counter.save() ;
				}
			},
		state : {
			counter : {
				public : true,
				type : "integer",
				défaut : 0
			}
		}
	}
}
```

! Doit être JSON

L'état du protocole est défini par un nombre entier public "counter", dont la valeur par défaut est zéro. Un événement "inc" est
est spécifié avec une fonction qui incrémente le "compteur" d'une unité chaque fois que l'événement "inc" est exécuté.
exécuté.

**3. Faire des calculs sur Bob**

Avec ce protocole déployé, les utilisateurs peuvent désormais envoyer à Bob des inscriptions OSS qui appellent l'événement "inc", ce qui a pour effet d'augmenter la valeur du compteur.
ce qui a pour effet d'incrémenter la valeur du compteur. Ce processus montre comment les utilisateurs peuvent
effectuer des calculs sur Bob, ce qui ouvre la voie à de nombreuses possibilités de création et d'interaction avec des protocoles décentralisés sur la blockchain Bitcoin.
avec des protocoles décentralisés sur la blockchain Bitcoin.

L'exemple du protocole de comptage met en évidence la possibilité de développer des calculs complexes à partir de
Bob. Tout comme les utilisateurs peuvent incrémenter un compteur, ils peuvent également développer des protocoles pour interagir avec d'autres variables et effectuer des calculs plus sophistiqués.
d'autres variables et effectuer des calculs plus sophistiqués.

Sur cette base, l'écosystème BOSS met l'accent sur l'importance de la normalisation. En
en proposant des normes telles que l'Operational Commit for Voting (OCV), qui peuvent
avec des protocoles de la couche de base tels que les entités décentralisées opérationnelles (ODE), nous
facilitons l'interopérabilité, la gouvernance et l'évolutivité du système.

Par exemple, l'ODE OSHI, bien qu'initié avec peu de paramètres, permet aux détenteurs d'Oshi de
de proposer des mises à jour de code pour leurs ODE, en ajoutant éventuellement un "microservice" posté en tant que code observable par Bob sur Bitcoin.
par Bob sur Bitcoin.

Ces ODE conservent leur cohérence au fil du temps, grâce à leur cadre de gouvernance intégré, initié par l'ODE, avec des propositions automatiques sur la chaîne.
intégrée, initiée par l'ODE, avec des propositions automatiques sur la chaîne. Ces cadres sont eux-mêmes évolutifs,
démontrant la flexibilité et l'adaptabilité du système.

Par essence, la normalisation dans l'écosystème BOSS ouvre les meilleures caractéristiques observées dans d'autres
systèmes de blockchain, tels que les dapps d'Ethereum, les services financiers, les marchés de prêts, les AMMs, le staking, le vesting, les nouveaux types de jetons, etc,
de nouveaux types de jetons, et bien plus encore, le tout dans un environnement Bitcoin robuste, sécurisé et évolutif.
robuste, sécurisé et évolutif. Avec Bob et BOSS, nous nous rapprochons de la réalisation de l'idéal du "God
Protocole".

## V. Le besoin de normes sur les BOSS : l'engagement opérationnel pour le vote (OCV)

**1. Engagement opérationnel pour le vote : Une norme pour la prise de décision décentralisée**

Les normes sont essentielles au fonctionnement efficace et harmonieux de tout système complexe. Elles
établissent les règles et les procédures nécessaires, assurent l'uniformité et garantissent que tous les
composants peuvent interagir et travailler ensemble de manière efficace. Il en va de même pour BOSS.

L'une des normes clés du cadre BOSS est l'engagement opérationnel pour le vote (Operational Commit for Voting - OCV). L'OCV
joue un rôle central dans la prise de décision décentralisée au sein de l'écosystème. Comme son nom l'indique, OCV facilite les
Comme son nom l'indique, OCV facilite les opérations de validation, qui s'apparentent à des mises à jour de code dans le développement de logiciels.
dans le développement de logiciels. Mais contrairement aux mises à jour de logiciels typiques qui sont généralement exécutées par une équipe
centralisée de développeurs, les opérations de validation sont décidées par le biais d'un processus de vote démocratique et décentralisé.
démocratique et décentralisé.

La beauté de l'OCV réside dans son adaptabilité et son universalité. Il permet un processus itératif, évolutif
itératif et évolutif, où les commits proposés peuvent introduire de nouvelles fonctionnalités, corriger des bogues ou améliorer des fonctionnalités existantes.
fonctionnalités existantes. Les participants peuvent proposer des modifications, et le réseau vote collectivement pour décider
pour décider si les modifications doivent être acceptées et intégrées dans le système.

**2. Intégration et importance des protocoles de bas niveau comme Ode**

Les entités opérationnelles décentralisées (Ode) font partie intégrante de l'écosystème BOSS, dont elles constituent le fondement.
fondation. En tant que première norme de la série OCV (désignée OCV0), Ode établit les bases de la construction d'applications au-dessus de Bitcoin.
les bases de la construction d'applications au-dessus de Bitcoin.

Les Ode sont, par essence, des entités bitcoin résilientes qui conservent leur cohésion au fil du temps. Elles le font grâce à un cadre de gouvernance intégré qui permet des propositions automatiques sur la chaîne.
Elles y parviennent grâce à un cadre de gouvernance intégré qui permet des propositions automatiques sur la chaîne.
Ce cadre est lui-même évolutif grâce au système de gouvernance automatique initial d'une Ode,
garantissant l'adaptabilité et le potentiel d'évolution du système.

Prenons un exemple : l'ode OSHI. Au départ, l'Ode OSHI commence avec un ensemble minimal de
paramètres. Cependant, les détenteurs de l'OSHI peuvent proposer des mises à jour de code pour leur Ode, comme l'ajout d'un
"microservice" qui est publié en tant que code observable par Bob sur le réseau Bitcoin. Ce mécanisme
Ce mécanisme donne du pouvoir aux participants individuels et favorise un processus de développement
communautaire décentralisé.

En conclusion, OCV et Ode tirent le meilleur parti des systèmes de blockchain, en sélectionnant les caractéristiques les plus attrayantes, telles que les applications décentralisées (dApps), les services financiers, les prêts, etc.
les applications décentralisées (dApps), les services financiers, les marchés des
de prêt, les marchés financiers, les teneurs de marché automatiques (AMM), le staking, le vesting, les nouveaux types de jetons, etc.
tokens, et bien plus encore. Mais ce n'est pas tout. Le cadre BOSS, alimenté par OCV et Ode,
a le potentiel de s'étendre au-delà de ces paradigmes existants, en progressant vers la réalisation de la vision du "protocole de Dieu".
de la vision du "protocole de Dieu".

## VI. Entités opérationnelles décentralisées (ODE) : La base de l'écosystème BOSS

**1. Introduction des ODE : Entités Bitcoin résilientes**

Les entités opérationnelles décentralisées (ODE) représentent une étape évolutive dans le développement des systèmes basés sur la blockchain.
systèmes basés sur la blockchain. Ces entités, fondées sur le système opérationnel standard de Bitcoin
(BOSS), encapsulent le potentiel de la blockchain Bitcoin et lui donnent vie d'une manière jusqu'à présent
inimaginables. Elles exploitent la résilience de Bitcoin, en fournissant une plateforme d'opérations qui peut résister à l'épreuve du temps.
résister à l'épreuve du temps, tout en restant fidèles aux principes de la décentralisation.

**2. Les ODE comme couche de base pour les applications au-dessus de Bitcoin**.

Les ODE constituent une couche de base solide pour construire des applications avancées directement au-dessus de
Bitcoin. Ils fournissent une infrastructure flexible, sécurisée et décentralisée qui peut accueillir
une gamme variée d'applications, des solutions financières décentralisées (DeFi) aux réseaux sociaux, etc.
et bien plus encore.

Cela est possible grâce à la polyvalence des EDO. Ils sont conçus pour être très
adaptables, avec la capacité d'évoluer et de se mettre à niveau en fonction des besoins des applications qui les utilisent.
sur eux. Cela permet aux développeurs de construire non seulement pour le présent, mais aussi pour l'avenir.

**3. Évolution du code par le biais des participants à l'ODE : Un exemple d'ODE OSHI**

OSHI, un exemple d'entité opérationnelle décentralisée, illustre la nature dynamique des ODE.
ODE. Bien qu'il ait été initié avec seulement quelques paramètres, OSHI peut évoluer au fil du temps. Les
détenteurs d'OSHI ont la possibilité de proposer des mises à jour du code de leur ODE. Une telle proposition peut
une suggestion d'ajouter un "microservice", un segment de code que Bob peut observer et exécuter sur le réseau Bitcoin.
exécuter sur le réseau Bitcoin.

Cette capacité d'évolution du code crée un écosystème où les changements sont induits par la
par la prise de décision collective des participants à l'ODE. Il s'agit d'un processus véritablement décentralisé, qui renforce la nature démocratique de la technologie blockchain.
la nature démocratique de la technologie blockchain.

**4. Gouvernance intégrée dans les ODE et rôle de la norme OCV**.

Les ODE sont dotés d'un cadre de gouvernance intégré qui permet des propositions automatiques sur la chaîne.
Ce cadre peut lui-même être mis à niveau par un processus automatique, en fonction de l'évolution des besoins de l'ODE et de sa communauté de participants.
de l'ODE et de sa communauté de participants.

La norme OCV (Operational Commit for Voting) joue un rôle essentiel dans ce cadre de gouvernance.
gouvernance. Elle garantit que les validations de code sont effectuées selon un protocole standard, fournissant ainsi une voie structurée pour l'évolution de l'ODE.
structuré pour l'évolution de l'ODE.

La combinaison des ODE et de la norme OCV crée un écosystème où les discussions sur la gouvernance
de gouvernance incitent à une réflexion approfondie et à la participation de toutes les parties prenantes avant que les changements ne soient acceptés.
avant que les changements ne soient acceptés. Ce système garantit que le BOSS évolue d'une manière qui profite à l'ensemble de la communauté, contribuant ainsi à la croissance et à la résilience de l'écosystème.
communauté au sens large, contribuant ainsi à la croissance et à la résilience de l'écosystème.

## VII. Mettre l'accent sur la normalisation plutôt que sur les normes BOSS : potentiel et flexibilité

**1. Choisir le meilleur d'Ethereum : DApps, services financiers et autres**

BOSS est conçu pour être un écosystème polyvalent et adaptable, capable d'incorporer les points forts d'autres plateformes blockchain tout en conservant les avantages uniques inhérents à la blockchain.
d'autres plateformes de blockchain tout en conservant les avantages uniques inhérents à
Bitcoin. L'une des influences les plus significatives sur BOSS est Ethereum[^3], en particulier dans son offre robuste d'applications décentralisées (DApps), et dans sa capacité à fournir des services d'information et de conseil.
d'applications décentralisées (DApps) et d'une riche gamme de services financiers.

Ethereum a été un pionnier dans le domaine des contrats intelligents et des DApps, permettant aux développeurs de créer une myriade de services sur sa blockchain.
de construire une myriade de services sur sa blockchain. Des plates-formes financières décentralisées (DeFi) aux
tokens non fongibles (NFT), la flexibilité d'Ethereum a inspiré d'innombrables innovations.
BOSS vise à porter le flambeau plus loin, en permettant des fonctionnalités similaires sur la blockchain Bitcoin
en offrant aux développeurs la flexibilité nécessaire pour créer des applications tout aussi innovantes.

Un aperçu du potentiel de BOSS peut être vu dans l'étendue des services qu'il pourrait offrir, à savoir
des échanges décentralisés, des marchés de prêts, des marchés financiers, des teneurs de marché automatiques (AMM),
plateformes de mise en jeu, mécanismes d'acquisition et toute une nouvelle gamme de modèles de jetons, pour n'en citer que quelques-uns.

**2. Le potentiel de croissance et les possibilités de développement**

Bien que les capacités actuelles de BOSS soient prometteuses, l'écosystème est conçu pour une évolution et une croissance continues.
une évolution et une croissance continues. BOSS évoluera en même temps que le paysage de la technologie blockchain. L'architecture
L'architecture flexible et adaptable de BOSS permet d'incorporer de nouvelles fonctionnalités
fonctionnalités et des avancées au fil du temps.

Cette flexibilité et cette évolution continue nous rapprochent du concept de "Godchain". La
Godchain est l'idée d'une blockchain unique et globale, capable d'exécuter n'importe quel calcul ou opération.
n'importe quel calcul ou opération. BOSS, avec sa capacité d'adaptation et d'évolution, pourrait servir de tremplin vers la réalisation de ce concept.
vers la réalisation de ce concept.

En ce qui concerne l'avenir, les possibilités de BOSS ne sont limitées que par l'imagination de sa communauté.
communauté. La nature ouverte de BOSS encourage l'innovation et la participation de ses utilisateurs,
et garantit ainsi un flux constant de nouvelles idées et d'améliorations. Cela ouvre la voie à
potentiel d'un écosystème en constante évolution, adaptable et véritablement décentralisé, qui exploite les forces de Bitcoin tout en élargissant constamment son champ d'action.
les forces de Bitcoin tout en élargissant constamment ses horizons.

## VIII. Conclusion : L'aube d'une nouvelle ère avec BOSS

**1. Réflexion sur le BOSS et son impact**

Alors que nous réfléchissons au pouvoir de transformation du système Bitcoin Operational Standard System (BOSS), il est clair qu'il ouvre la voie à des systèmes plus flexibles, plus interactifs et plus évolutifs,
il est clair qu'il ouvre la voie à des implémentations de blockchain plus flexibles, plus interactives et plus évolutives.
plus flexibles, plus interactives et plus évolutives. En permettant à Bob, la machine virtuelle JavaScript, d'interagir intelligemment avec la blockchain Bitcoin
avec la blockchain Bitcoin, BOSS offre aux utilisateurs une boîte à outils élargie pour de puissantes
applications décentralisées puissantes, des entités résilientes et des normes dynamiques pour l'évolution du code.

L'impact de BOSS va bien au-delà de l'écosystème Bitcoin. En rendant la blockchain plus
adaptable et interactive, elle pousse l'ensemble de l'écosystème de la blockchain vers de nouveaux horizons d'innovation et de fonctionnalité.
d'innovation et de fonctionnalité. En tant que système ouvert, participatif et évolutif, BOSS incarne l'esprit démocratique et innovant de la technologie blockchain.
l'esprit démocratique et innovant de la technologie blockchain, en l'aidant à se rapprocher de la réalisation de son plein potentiel.

Diagramme de l'interaction entre les protocoles de Dieu ](/rabbithole.jpg)

**2. Un regard sur l'avenir de la blockchain avec BOSS**

Pour l'avenir, le paysage de la technologie blockchain regorge de possibilités passionnantes, dont beaucoup peuvent être débloquées par BOSS.
dont beaucoup peuvent être débloquées par BOSS. Grâce à son architecture évolutive, à la participation de la communauté et au
et le potentiel d'expansion au-delà du langage JavaScript, BOSS n'est pas un système statique, mais un système en constante évolution.
système statique, mais un système en perpétuel progrès.

L'idée de la "Godchain", une blockchain universelle, interopérable et extrêmement efficace, est une vision convaincante.
vision convaincante. Alors que BOSS continue d'évoluer et de mûrir, il pourrait constituer une étape
étape importante sur la voie de cette vision.

La puissance de BOSS ne réside pas seulement dans son ingéniosité technique, mais aussi dans les mains de sa communauté.
En continuant de construire, de proposer, d'évoluer et d'adopter, nous participons à l'aventure passionnante qui consiste à
l'avenir de la blockchain. Saisissons cette opportunité, continuons d'innover et
et œuvrons pour un avenir où la technologie de la blockchain atteindra son plein potentiel.

À l'ère de BOSS, nous ne sommes pas seulement des observateurs de cette évolution, mais aussi des participants actifs, prêts à laisser notre empreinte indélébile sur l'avenir de la technologie blockchain.
prêts à laisser notre empreinte indélébile sur l'avenir de la technologie blockchain. Ensemble, continuons à
d'innover, d'évoluer et de construire sur les fondations puissantes de BOSS. L'aube d'une nouvelle
L'aube d'une nouvelle ère avec BOSS est à nos portes et l'avenir regorge de possibilités.

Bienvenue dans l'avenir du bitcoin. Bienvenue dans l'avenir de la blockchain. Ensemble, nous allons forger l'unité de temps.
BOSS.

## Plus de ressources

<PageLink title="Overview of ODE" desc="1st DAO on Bitcoin" href="/protocols/ode" />

Références :

[^1a] : Nakamoto, S. (2008). Bitcoin : A Peer-to-Peer Electronic Cash System. Retrieved from [https://bitcoin.org/bitcoin.pdf](https://ordinals.com/inscription/e0b3df7d46e3d7867f16fdd810134149745a36ab08f301e25d69a17d77f464e4i0)
[^1b] : "Les inscriptions inscrivent des sats avec un contenu arbitraire, créant ainsi des artefacts numériques natifs du bitcoin, plus communément appelés NFT. Les inscriptions ne nécessitent pas de sidechain ou de jeton séparé." - [Voir la documentation officielle des ordinaux sur les inscriptions](https://docs.ordinals.com/inscriptions.html).
[^2] : Szabo, N. (1997). The God Protocols. Institut Nakamoto. Récupéré de [https://nakamotoinstitute.org/the-god-protocols/#selection-3.88-7.6](https://nakamotoinstitute.org/the-god-protocols/#selection-3.88-7.6)
[^3] : Wood, G. (2014). Ethereum : Un grand livre de transactions décentralisé et sécurisé. Livre jaune du projet Ethereum. Récupéré de [https://ethereum.github.io/yellowpaper/paper.pdf](https://ethereum.github.io/yellowpaper/paper.pdf)
