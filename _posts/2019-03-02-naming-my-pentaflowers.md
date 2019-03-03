---
layout: post
title: Naming My Pentaflowers
date:   2019-02-22
---

Since you were wondering, I will elaborate on how names are automatically generated for my pentaflowers (part of my [artomata]({% post_url 2019-03-02-artomata-cellular-automata-as-art %}) project).

I wanted to be able to name my creations, but I am not very good at naming things (it is one of the [2 hard things in computer science](https://twitter.com/codinghorror/status/506010907021828096?lang=en), after all). So I added a feature to my pentaflower [javascript library](https://github.com/tyleryasaka/artomata/tree/master/packages/pentaflower-svg) which automatically generates a name for each pentaflower, in the form of `[adverb] [adjective] [flower]` (e.g. "Unaccountably Yummy Scarlet Sage"). The names are generated by using a simplified [hashing function](https://en.wikipedia.org/wiki/Hash_function) to derive an arbitrary number from the input parameters. I then take the [modulo](https://en.wikipedia.org/wiki/Modulo_operation) of this number and the number of words in my dictionary for the word type (e.g. adjectives), which results in an index between 1 and the number of words in the dictionary. The word at this index in the dictionary is the chosen word for this pentaflower. The adverb, adjective, and flower name are each selected this way.

Actually, the adjective is based on a hash of only the colors, the flower on a hash of only the pattern (*rings* and *generation*), and the adverb on a hash of all of the parameters. I set it up this way because I like the idea of 2 pentaflowers with different colors but the same pattern having the same flower in their name, as well as 2 pentaflowers with different patterns but the same colors having the same adjective.

The adverb was added in order to keep my names reasonably [collision-resistant](https://en.wikipedia.org/wiki/Collision_resistance) (no 2 pentaflowers having the exact same name). The intuition behind why the adverb adds collision resistance is that if you kept the colors constant and created several pentaflowers with only varying patterns, you'd quickly run into a collision within the 169 flower names in my dictionary. It is, however, much less likely that a collision in the adverb would happen at the same time as a collision in the flower name.

I was pleasantly surprised to discover that the adverb not only adds collision resistance to the names, but also makes them funnier.

Case in point: [Abnormally Average Osteospermum](http://www.artomata.io/pentaflower/create?rings=35&generation=118&color1=%23FCDA97&color2=%23E2711D&color3=%23E2711D)