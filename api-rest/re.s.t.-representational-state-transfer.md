# Re.S.T. : REpresentational State Transfer

## **Ce qu’une API ReST n’est pas**

* ReST n’est pas un standard mais un **style d’architecture**.

## **Roy Thomas FIELDING : Papa du ReST**

* L’origine du style ReST date des années 90. Ce style d'architecture a servi à définir les standards HTTP et URI.
* Cf. [Architectural Styles and the Design of Network-based Software Architectures by Roy Thomas FIELDING](https://www.ics.uci.edu/~fielding/pubs/dissertation/fielding_dissertation.pdf)

## Description du ReST

Le style d'architecture ReST impose 5 contraintes, définies dans le chapitre suivants, qui permettent de définir des systèmes hypermedia distribués.

> The name “Representational State Transfer” is intended to evoke an image of how a well-designed Web application behaves: a network of web pages \(a virtual state-machine\), where the user progresses through the application by selecting links \(state transitions\), resulting in the next page \(representing the next state of the application\) being transferred to the user and rendered for their use

## Resource-Oriented Architecture vs ReST

La plupart des APIs nommées ReST ou ReSTful le sont à tort. En effet, l'une des contraintes principales du style ReST est le "hypermedia as the engine of application state" où toutes les transitions d'états doivent être définies par relations hypermedia afin d'éviter tout couplage entre clients et serveurs.  
**En appliquant toutes les autres contraintes sauf cette dernière, nous nous écartons du style ReST et définissons alors simplement une Resource-Oriented Architecture \(ROA\).**

Tel que Fielding le présente dans sa thèse, le style ReST n'est pas destiné à tous les usages.  
Il est donc préférable de parler d'APIs HTTP ou APIs ROA que d'APIs ReST qui ne le sont pas.

Cf. [https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven](https://roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven)

