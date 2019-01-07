# test-doyouno
Script pour résoudre petite enigme

Test initial :
Find a 8*-letter string containing only letters from: " acdegilmnoprstuw", such that the hash(this_string) is 24682779393128*With hash defined by the following pseudo-code:

hash (string s) {

h = 7

letters = "acdegilmnoprstuw"

for(i = 0; i < s.length; i++) {

h = (h * 37 + letters.indexOf(s[i]))

}

return h

}

Résolution:
On nommera P[i] = letters.indexOf(s[i])
Si on déroule la boucle, on a :
i=0 : h= 37*h + P[0]
i=1 : h = h(37h+P[0])+p[1] = 37h² + P[0]*h + P[1]*h^0
...
i=7 : h =37*h^8 + P[0]*h^7 + P[1]*h^6 ... + P[6]*h + P[7] = HASH à décoder

le traitement revient à convertir le HASH en base 37.
En faisant le calcul modulo/reste sur ce nombre et en bouclant sur le nombre de caractères attendus, on obtient la position de chaque caractère dans la chaine stockée dans la variable letters, et donc la chaine initiale.

Le HASH etant large, on utilisera la classe BigInteger pour les calculs.
