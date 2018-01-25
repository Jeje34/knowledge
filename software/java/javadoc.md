# Javadoc

## @index

Permet de spécifier des tags qui seront utilisé pour la recherche

    public class JavadocIndexDemonstrator {
        /**
         * This method complies with the {@index IEEE 754} standard.
         */
        public void doEffectiveJava3Example() {}
        /**
         * Accuracy of the floating-point Math methods is measured in
         * terms of {@index ulps}, "units in the last place."
         */
        public void doMathUlpsExample() {}
        /**
         * This method uses a version of the {@index Dual-Pivot Quicksort}.
         */
        public void doDualPivotQuicksort() {}
    }
    
<br>
    
    <div class="block">This method uses a version of the <a id="Dual-Pivot" class="searchTagResult">Dual-Pivot</a>.</div>
    ...
    <div class="block">This method complies with the <a id="IEEE" class="searchTagResult">IEEE</a> standard.</div>
    
Because spaces are not allowed in the HTML "id" attributes, use one of the following workarounds :
- Remove spaces
- Replace spaces with allowable character (for example, hyphen) 
- Use a separate {@index} for each word in phrase 
- Use {@index} only on most important terms in phrase 
- Represent multiple word phrase with common single word representation

Source : https://dzone.com/articles/adding-terms-to-javadoc-search-with-java-9