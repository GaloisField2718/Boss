# Recherches RUNES

Le but est de **trouver l'enveloppe** utilisée sur Bitcoin pour fournir et interagir avec RUNES. 

## RSIC

Au 24/01/24, RSIC (Rune Specific Inscription Circuit) vient d'être publié et airdrop aux propriétaires des principales collections ordinals. Au Halving (appelé halvening dans la [doc officielle](runecoin.io)), les runes commenceront à être mintées : bloc 840 000.
[Un long thread](https://x.com/OrdinalsGlobal_/status/1749756861824241830?s=20) de [@OrdinalGlobal_](https://twitter.com/OrdinalsGlobal_) à propos de RSIC.
Le code de RSIC avec des détails ainsi que les inscriptions sont disponibles dans le [thread de 0xG](https://x.com/0x0000G/status/1749415831388274843?s=20).

RSIC part de [l'inscription #126](https://www.ord.io/126) à partir de la [RSIC factory](https://www.ord.io/56711443) qui est un HTML contenant tous les RSICs superposés ^[1]. 


[1] : On notera que le sat d'inscription date de 2009. Est-ce un hasard ?

## RUNES

Le point de départ pourrait être le [Talk de Casey](https://www.youtube.com/watch?v=IS406ToIRo4&list=TLPQMjMwMTIwMjQGr0OCXwqz-Q) lors de la conférence de Taipei à propos de RUNES. Néanmoins, si ce n'est des considérations générales sur RUNES et une comparaison de RUNES avec tous les protocoles sur Bitcoin de brc-20 à Counterparty en passant par les ERC-20 Ethereum. 

Cela ne devrait pas nous aider dans notre quête de l'enveloppe. On peut noter que la commande `ord runes` est disponible quand `ord` est lancé en testnet.

Via une commande de la forme : `ord-13 --testnet --cookie-file=/Volumes/Crucial\ X8/bitcoin/Bitcoin/testnet3/.cookie --index=/Volumes/Crucial\ X8/bitcoin/ordinals/indexes/index-testnet_runes.redb --index-runes runes`

Où : 
- `ord-13` est le nom de mon binaire ;
- `--testnet` active le testnet ;
- `--cookie-file` spécifie le chemin absolu du cookie de `bitcoind` ;
- `--index` spécifie le chemin absolu de l'index utilisé (build avec le flag`--index-runes`) ;
- `runes` la sous-commande elle-même de `ord`.

On obtient alors la sortie : 

```JSON
{
  "runes": {
    "ARUNESBETA": {
      "burned": 0,
      "divisibility": 0,
      "end": null,
      "etching": "d1d7120c6251071ee5c5127511fdcd147db1a80fe5591d18d1ab27d28f922b80",
      "height": 2573049,
      "id": "2573049/118",
      "index": 118,
      "limit": null,
      "number": 1845,
      "rune": "ARUNESBETA",
      "spacers": 33,
      "supply": 21000000,
      "symbol": "A",
      "timestamp": "2024-01-16T06:03:36Z"
    },
    "BRUNESBETA": {
      "burned": 0,
      "divisibility": 0,
      "end": null,
      "etching": "20999ea4903992cfd324dc47fac30f9497bedae176816779bcf7e054eae86ee4",
      "height": 2573049,
      "id": "2573049/71",
      "index": 71,
      "limit": null,
      "number": 1844,
      "rune": "BRUNESBETA",
      "spacers": 33,
      "supply": 21000000,
      "symbol": "B",
      "timestamp": "2024-01-16T06:03:36Z"
    },
    ...
}
```



Exemple d'une transaction de [deploy rune en testnet](https://mempool.space/testnet/tx/d1d7120c6251071ee5c5127511fdcd147db1a80fe5591d18d1ab27d28f922b80) à partir de *ARUNESBETA*.

Je ne vois pas d'enveloppe clairement définie. 
De plus, on remarque dans l'`OP_RETURN` qu'il y a : `OP_PUSHBYTES_9 52554e455f54455354` qui se traduit pas : `RUNE_TEST` ainsi que `OP_PUSHBYTES_21 020104818fb98f88cc5c0321054100008980dd4001` qui quant-à-lui ne se traduit par aucun texte compréhensible. 


## Références

### Officiel & Code

- [Doc officielle](runecoin.io)
- [RSIC.js by 0xGh](https://gist.github.com/0xGh/3941f93e4e0d3da8632f825f4cd923b5)
- [Wallets officiels de la team](https://x.com/rune_coin/status/1749494254081061275?s=20)
- [Code source de rune](https://github.com/ordinals/ord/tree/master/src/runes)

### Vidéos & présentations

- [Talk de Casey | Taipei](https://www.youtube.com/watch?v=IS406ToIRo4&list=TLPQMjMwMTIwMjQGr0OCXwqz-Q)
- [The Rise and Fall of Casey Rodarmor: Ordinal Takeover 🟧4️⃣🟧](https://www.youtube.com/watch?v=m98pddxD_Lg&list=TLPQMjMwMTIwMjQGr0OCXwqz-Q&index=3)
- [Bitcoin Civil War is ON! Will Runes Kill the BRC20 Ordinals Standard? BIG NEWS!](https://www.youtube.com/watch?v=QdA-0D7dmS0&list=TLPQMjMwMTIwMjQGr0OCXwqz-Q&index=4)
- [Runes MANIA Starts NOW! Are RSICs Casey’s Secret Project?!](https://www.youtube.com/watch?v=vmPNji3ur3Q&list=TLPQMjMwMTIwMjQGr0OCXwqz-Q&index=7)
- [Forgotten Runes Bitcoin Ordinal Shadow Mint, Explained!](https://www.youtube.com/watch?v=ARJoYK89FBE&list=TLPQMjMwMTIwMjQGr0OCXwqz-Q&index=6) Peut être intéressant mais pas écoutée attentivement encore.


### Accounts

- [@rune_coin](https://twitter.com/rune_coin)
- [@runesdev](https://twitter.com/the_runedev)

### Threads

- [Thread de @OrdinalGlobal_](https://x.com/OrdinalsGlobal_/status/1749756861824241830?s=20)
- [Thread de @0x0000G contenant le code js](https://x.com/0x0000G/status/1749415831388274843?s=20)

