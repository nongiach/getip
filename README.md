getip
=====

outil qui permet d'avoir l'ip d'un utilisateur sur le réseaux Epitech

Usage : getip patern [user | ip | promo | state]

Install:
git clone https://github.com/nongiach/getip
sudo cp getip/getip /usr/bin
rm getip -rf

##exemple:
```
shell$ getip martin_6
10.2.1.19

shell$ ping $(getip manaa_m)
shell$ client $(getip manaa_m) 4242
```

####cas ou plusieur ip:
```
shell$ getip devoil_g
10.18.207.251 
10.18.207.251 
10.18.208.3 
10.18.207.198

shell$ getip devoil_g ip client
10.18.207.251 bns-0.9.6 [ bNetSoul rocks ] 
10.18.207.251 bns-0.9.6 [ bNetSoul rocks ] 
10.18.208.3 none 
10.18.207.198 -=[QNetSoul v1.5c]=- 

shell$ getip 'devoil_g.*QNetSoul'
10.18.207.198
```

####tout les users actif:
```
shell$ getip 'actif' user
```

####promo 2017 et 2016:
```
shell$ getip "_201[6-7]" user ip promo
```



