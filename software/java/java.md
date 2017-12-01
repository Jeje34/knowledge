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

## toString arrays

    String lines[] = ...;
    System.out.println(java.util.Arrays.toString(lines));

## Pourquoi le type primitif long n'est pas autorisé dans un switch ?

// String[] availableLocalesString = Arrays.stream(availableLocales).map(Locale::toString).toArray(String[]::new);
   		