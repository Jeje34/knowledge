# Unix
 
## ls 

**List directory contents**

**-a** do not ignore entries starting with

**-l**     use a long listing format

**-r**            reverse order while sorting

## grep

* Search lines with 2 strings

        grep "000000000000200353" catalina.out | grep "000000000000172857"
        
* **-A** Afficher n lignes supplémentaires après (**A**FTER) la ligne correspondante
* **-B** Afficher n lignes supplémentaires avant (**B**EFORE) la ligne correspondante

        grep -A 10 -B 10 "000000000000195605"
