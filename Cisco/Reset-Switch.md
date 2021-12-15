---
title: Reset Switch Cisco
description: 
published: true
date: 2021-12-15T21:25:02.407Z
tags: 
editor: markdown
dateCreated: 2021-11-17T09:36:44.612Z
---

# Réinitialisation rapide du commutateur
Cette section décrit comment réinitialiser le commutateur en relançant la Configuration rapide. La réinitialisation du commutateur peut être requise dans les cas suivants : 
  * Liste à puceVous avez installé le commutateur dans votre réseau et vous ne pouvez pas vous y connecter car l'adresse IP attribuée est incorrecte.
  * Vous voulez effacer toutes les configurations du commutateur et attribuer une nouvelle adresse IP.
  * Vous tentez d'entrer en mode Configuration rapide et les DEL du commutateur commencent à clignoter lorsque vous appuyez sur le bouton Mode, ce qui signifie que le commutateur est déjà configuré avec des informations IP.
{{ :bouton_mode.png?200|}}Pour réinitialiser le commutateur, appuyez sur le bouton Mode et maintenez-le enfoncé. Après environ 3 secondes, les DEL du commutateur commencent à clignoter. Continuez à maintenir le bouton Mode enfoncé. Les DEL cessent de clignoter après 7 secondes supplémentaires, puis le commutateur redémarre. Relâchez le bouton.
Le commutateur agit dorénavant comme s'il n'était pas configuré.

# Procédure de réinitialisation complète du commutateur vers les réglages d’usine par défaut
Si vous n’accédez plus au commutateur même après une réinitialisation rapide, il existe une autre réinitialisation, en 5 étapes, permettant de retrouver les paramètres d’usine par défaut.

  * Étape 1 - redémarrage du switch
Dans cet ordre : connecter le câble de la console, mettre sous tension le switch et dans les 15 secondes suivant la mise sous tension, maintenir le bouton Mode appuyé (situé en façade). Pendant ce temps, la LED système clignote en vert. Cette même LED système passera à l’orange un court instant avant de virer au vert, cette fois sans clignoter. C’est à ce moment, et à ce moment seulement, qu’il faut relâcher la pression du bouton Mode.
Cela interrompt le processus de démarrage avant que le système de fichiers Flash peut initialiser, et après un court moment (maintenez le bouton “mode”), vous verrez le message suivant :

![console2.png](/cisco/reset/console2.png)

  * Étape 2 - réinitialisation de la mémoire flash du switch
Initialiser le système de fichiers flash avec la commande:
  switch: flash_init

{{ :console3.png?400 |}}
![console3.png](/cisco/reset/console3.png)
  * Étape 3 - suppression du fichier de configuration
Supprimez le fichier config.text à partir du répertoire flash.
  switch: del flash:config.text

![console5.png](/cisco/reset/console5.png)
  * Étape 4 - suppression des vlans
Supprimez le fichier vlan.dat à partir du répertoire flash.
  switch: del flash:vlan.dat
  
{{ :console6.png?400 |}}
![console6.png](/cisco/reset/console6.png)
  * Étape 5 - redémarrage du switch

  switch: boot

![console7.png](/cisco/reset/console7.png) 
 
# Pour une simple réinitialisation du switch : 

  switch>en
  switch# erase nvram:
  switch# delete flash:vlan.dat
  switch# reload
  switch# end
  
