## Indépendant de la plateforme

- Indépendant de la plateforme (exécutable sur n'importe quelle machine, n'importe quel OS), ce qui n'est pas le cas de C et C++
- Pourquoi ? Car le code s'execute sur la JVM qui elle est dépendante de la plateforme. Chaque OS a sa propre implémentation de la JVM.
- JVM prend en entrée du byte code (.class) et le convertie en code machine
- Byte code (.class) généré par le compilateur JavaC

## Pas de pointeurs

- Pas de pointeurs contrairement a C et C++
- Il existe des pointeurs (restricted pointers) pour le fonctionnement interne de Java mais non accessible aux utilisateurs

## Compilateur et interpréteur

- Utilise les deux alors que souvent les autres languages en utilisent qu'un

## Pas d'héritage multiple

- Java ne supporte par l'héritage multiple, car Java se base sur le monde réel, et l'héritage multiple n'est pas possible dans le monde réel
- Peut etre implémenté à l'aide des interfaces

## Pas d'instructions "goto"

- Instruction goto = instruction qui permet de sauter des lignes

## Source

https://codepumpkin.com/java-vs-other-programming-languages/
