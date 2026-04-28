# Routage-dynamique-OSPF
OSPF vs RIP : Comprendre les bases du routage dynamique 🌐🔁
Dans le cadre de mes recherches en réseaux, j'ai analysé les différences fondamentales entre deux protocoles de routage essentiels : l'historique RIP et le performant OSPF.
Voici un comparatif rapide pour mieux comprendre leurs fonctionnements. 👇
1️⃣ Les concepts clés
📖 RIP (Routing Information Protocol) : C'est un protocole à vecteur de distance . Sa métrique est le nombre de sauts . Il choisit le chemin le plus court en traversant le moins de routeurs possible, même s'ils sont lents.

📖 OSPF (Open Shortest Path First) : C'est un protocole à état de lien . Sa métrique est le coût, calculé selon la bande passante . OSPF privilégie le chemin le plus rapide, même s'il traverse plus de routeurs.
2️⃣ Pourquoi OSPF l'emporte souvent ? ⭐
OSPF offre des avantages décisifs pour la plupart des infrastructures modernes :
♾️ Plus de limite de sauts : Contrairement à RIP, qui est bloqué à 15 sauts 🛑, OSPF peut gérer des réseaux immenses sans restriction de taille.
🏗️ Une meilleure évolutivité : OSPF est conçu pour grandir ! La segmentation en aires permet d'étendre le réseau facilement tout en gardant une structure organisée ☁️.
⚡ Une convergence ultra-rapide : En cas de panne d'un routeur, OSPF met à jour la carte du réseau quasi instantanément ⏱️, assurant une continuité de service. RIP doit souvent attendre de longues secondes.
📉 Des mises à jour plus efficaces :
RIP envoie toute sa table de routage toutes les 30 secondes, ce qui gaspille de la bande passante 🔁.
OSPF est plus intelligent : il n'envoie que les modifications d'état de lien à son voisin, rendant le trafic de contrôle beaucoup plus léger et rapide.
