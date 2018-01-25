# Java

## Check whether a string is not null and not empty


    if (custNum != null && !custNum.isEmpty()) {
        ...
    }

or

    import org.apache.commons.lang.StringUtils;
    
    if (StringUtils.isNotBlank(str)) {
        ...
    } 

## Iterate over each Entry in a Map

    for (Map.Entry<String, Integer> entry : items.entrySet()) {
        System.out.println("Item : " + entry.getKey() + " Count : " + entry.getValue());
    }
    
<br>

Java 8 :

        items.forEach((k,v)->{
            System.out.println("Item : " + k + " Count : " + v);
            if("E".equals(k)){
                System.out.println("Hello E");
            }
        });

## toString arrays

    String lines[] = ...;
    System.out.println(java.util.Arrays.toString(lines));

## Operator "OR" in switch case

    switch(val){    
        case 1:
        case 3:
            // if val equals 1 OR 3 do stuff
            break;    
        case 2:
            // do Stuff
            break;    
        default:
            // do Stuff
            break;    
    }
## Pourquoi le type primitif long n'est pas autorisé dans un switch ?

// String[] availableLocalesString = Arrays.stream(availableLocales).map(Locale::toString).toArray(String[]::new);
   		
   		
// dailyPrices = dailyPrices.stream().sorted(Comparator.comparing(dp -> DataHelper.getProductLabel(dp.getCode(), site))).collect(Collectors.toList());
