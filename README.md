# Grafet
Grafet jane bashkesi e nyjeve (vertex, node) dhe degeve (edges) qe i lidhin nyjet mes vet. Grafet shenohen me shkronje te madhe psh "A" ndersa rrenjet me shkronje te vogel. Grafi mund te jete i padrejtuar ose i dejtuar.

Grafi i padrejtuar (unordered graph) ka deget/rruget te cilat mund te parakalohen ne qdo drejtim (zakonisht quhen vetem grafe)

Grafi i drejutar (directed graph) ka deget/rruget te cilat mund te parakalohen vetem ne nje drejitm (zakonisht quhen digrafe) 

![image](https://github.com/blendonluta/Gg/blob/master/grap.png)

##	Matrica dhe lista e fqijnesis

Ekzistojne dy menyra qe mundemi ti ruajme informacionet per grafin ose digrafin:

1. Adjacency matrix (matrica e afersise/fqijnesise) 
2. Adjacency list (lista e afersise/fqinjesise)

![image](https://github.com/blendonluta/Gg/blob/master/fiqjn.png)

Adjacency matrix - Emrat e nyjeve jane emrat e kolonave dhe t'njejtit jane emrat e rreshtave

Adjacency list - Krijohet ni lloj linked list ku qdo node osht element i listes, dhe qdo element i listes e ka te 
                 lidhur elementin qe ka rruge me te
                 
##	    Matrica Incidente

Incidence matrix - Osht matrice qe paraqet relacionin mes nyjeve dhe degeve te nje grafi, ku rreshtat paraqesin vertices
ndersa kolonat paraqesin edges 

Jane dy lloje te Incidence matrix

E orientuar per digrafin - Ka vlera 1, -1, 0 (-1 shenohet ne ate lokacion te matrices ku elementi i drejtohet me rruge elementit tjeter, 1 shenohet lokacioni i matrices ku tek ai element vie rruga, me 0 shenohet lokacioni qe nuk ka rruge)

![image](https://github.com/blendonluta/Gg/blob/master/incidente1.png)

E paorientuar per grafin - Ka vlera 1, 0 (1 shenohet lokacioni ku ai element ka rruge ne ate edge, me 0 shenohet lokacioni ku nuk ka rruge ai element)

![image](https://github.com/blendonluta/Gg/blob/master/Incidente.png)

##	Valenca e nyjeve

Shkalla ose valenca e nyjeve - tregon se me sa rruge eshte e lidhur nje nyje dhe shenohet me "deg(n)" - psh nyja u osht e lidhne me 2 edges dhe shenohet "deg(u) = 2"

![image](https://github.com/blendonluta/Gg/blob/master/Valenca.png)

#	Searching a Graph

Algoritmi i DFS:
```
1. Vizito nje vertex, boje push ne stack dhe marko si te vizitun, pastaj vazhdo me vertex te rradhes qe nuk osht i vizitun, e 
   bon push n'stack dhe e markon si t'vizitun
2. Hapi 1 perseritet deri sa e arrin vertex-in e fundit ne bottom. Pastaj kontrollo nese vertex fillestar ka te lidhur 
   ndonje vertex qe eshte i pavizituar, dhe i largon elementet nga stack
3. Nese gjen vertex te pavizituar te lidhur me vertex-in fillestar (starting point) atehere vazhdo te njejten procedure
4. Perseriti hapat perderisa nyja fillestare nuk ka te lidhur me nyje te pavizituara
```
Algoritmi i BFS:
```
1. Gjej nje vertex me te afertin me vertexin fillestar dhe qe nuk osht vizitu, markoje si te vizitun dhe fute ne queue
2. Nese nuk ka me vertex te afert qe nuk osht i vizitun, largoj elementet nga queue dhe fillo prap prej elementit startues 
   duke kerkuar elementin e pare te afert te pavizituar
3. Nese hapi i dyte nuk mundet qe te ekzekutohet (pasi qe queue osht e zbrazet) algoritmi perfundon
```
> Video ku spjegohet me mire algoritmi i BFS: https://drive.google.com/file/d/19z6dewmFrDI70YYGF4Eot3pPWuCRbsDO/view?usp=sharing

#	 Spanning Tree

Spanning tree eshte nje subgraph i nje grafi qe i permban te gjitha nyjet e atij grafi, te lidhura. Pra eshte nje rruge (rrugetim) i nje grafi qe i kalon te gjitha nyjet e atij grafi. Nje graf mundet qe te kete disa "spanning tree", pra spanning tree nuk osht vete grafi, po osht rruga qe kalohet(neper dege) ne menyre qe te gjitha nyjet te jene te lidhura
##	Minimum Spanning Tree
Minimum spanning tree - Osht spanning tree e nje grafi me koston minimale (kosto minimale) pasi qe e dijme qe ne nje graf mundet te kete shume "spanning tree"
Egzistojne disa algoritme per Minimum Spanning Tree, me te njohurat: Algoritmi i Kruskalit, Algoritmi i Prim dhe Jarnik, Algoritmi i Dijkstra

Algoritmi i Kruskalit - Spanning Tree
```
1. Zgjidh degen me te lire te paperdorur ne graf
2. Perserite hapin 1 perveq nese krijohet qark
3. Vazhdo derisa te krijohet pema permbledhese (derisa te perfshihen te gjitha nyjet pa krijuar qark)
```
> Video ku spjegohet me mire algoritmi i Kruskalit : https://drive.google.com/file/d/1zTgvhBqLT49F-JaFUtzB4JNJzsFslHO7/view?usp=sharing

Algoritimi I Primit – Spanning Tree:

```
Fillon me degen me te lire dhe pastaj vazhdon me degen me te lire te lidhur me degen e meparshme deri
sa ti perfshine te gjitha nyjet por pa krijuar cikle.
```
> Video ku spjegohet me mire algoritmi i Primit : https://drive.google.com/file/d/11Aizgx563RSrmZrwPvM0yc-NczltB7mm/view?usp=sharing

#	Grafet e Hamiltonit

Grafi i hamiltonit i kalon te gjitha nyjet e grafit vetem nga nje here.

```
Hamilton path(shtegu):   I viziton te gjitha nyjet e grafit saktesisht njehere
Hamilton circuit(qarku): I viziton te gjitha nyjet e grafit saktesisht njehere, dhe kthehet te e njejta nyje 
                         qe ka filluar (Po ashtu osht shteg i Hamiltonit)

```

# Grafet e Eulerit

Dallimi kryesor mes grafit te Eulerit dhe atij te Hamiltonit eshte se grafi i Eulerit i shikon *deget* kurse ai i Hamiltonit i shikon *nyjet*
```
Euler path:    I viziton te gjitha deget e grafit saktesisht njehere pa perseritje
Euler circuit: I viziton te gjitha deget vetem nga njehere pa perseritje mirepo fillon dhe perfundon te e njejta nyje rruga, duke krijuar nje qark. 
```
 > Shtegu dhe qarku i Eulerit mund te mos egzistojn dhe per ata egzistojn 4 teorema

Teoremat e Eulerit
```
1: Nese grafi ka nyje me valence tek, nuk ka qark te Eulerit, mirepo nese i ka krejt qift atehere ekziston qarku Eulerian
2: Nese grafi ka me shume se dy nyje me valence tek, ai nuk mund te kete shteg te Eulerit, nese grafi ka saktesisht 2 nyje 
   te shkalles tek atehere ka se paku nje shteg te Euluerit. Ky shteg duhet te filloje ne nyjen qe ka valence teke dhe te perfundoj 
   ne nyjen tjeter me valence teke
3: Shuma e valencave te te gjitha nyjeve te grafit duhet qe te jete numer qift. Pra shuma e valencave duhet te jete sa dyfishi i 
   numrit te degeve ne graf  
```

nese ka

```
0 rrenje me valence teke: Ka qark te Eulerit
1 rrenje me valence teke: Nuk ka qark te Eulerit, nuk ka shteg te Eulerit
2 rrenje me valence teke: Nuk ka qark te Eulerit, ka shteg te Eulerit
>2 rrenje me valence teke: Nuk ka qark te Eulerit, nuk ka shteg te Eulerit
```

# Dijkstra's Algorithm for Determining the Shortest Path
Ky algoritem e gjen rrugen me te shkurter prej nje vertex te te gjithe te tjeret
Algoritmi me fjale:
Krijohet tabela per distancat mes nyjeve, fillohet prej nje vertex-i dhe zgjidhet qdohere nyja me e afert dhe kjo rruge regjistrohet ne tabele. Nese distanca mes dy nyjeve osht e njohur mirepo gjendet nje distance me e shkurter, atehere distanca e meparshme qe gjendet ne tabele zevendesohet me distancen e re te gjendur (me distancen me te vogel)
> Tabela nderrohet poashtu edhe kur e caktojme se me cilen nyje nese e marrim si nyje startuese (starting point) rruga eshte me e shkruter (shortest path)

> Video ku spjegohet me mire algoritmi i Dijakstres https://www.youtube.com/watch?v=pVfj6mxhdMw
