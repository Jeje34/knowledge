# jQuery

## Show / hide an element

    $( ".target" ).hide();
    $( ".target" ).show();
    $( ".target" ).toggle(); // cache si affiché, affiche si caché
    
## Add / remove a class

    $( "p" ).removeClass( "myClass noClass" );
    $( "p" ).addClass( "yourClass" );
    
## Check if an element has a given class
    
    $( "#mydiv" ).hasClass( "foo" )

## Check if checkbox is checked
    
    $("#isAgeSelected").is(':checked')
    
## Loop on an array
        
    $.each(sensors, function(i, sensor) {
        // ...
    });
    
## Add li in an existing ul

    $('#content ul').append(
        $('<li>').append(
            $('<a>').attr('href','/user/messages').append(
                $('<span>').attr('class', 'tab').append("Message center")
    ))); 

## Get element by attribute

    $( "input[value='Hot Fuzz']" )
    
## Setting a boolean attribute 

    $('#element').prop('attribute', true);
    

## Select all element with custom attribute

    $('p[MyTag]')
    
## Event right click

    $( "#target" ).contextmenu(function() {
        alert( "Handler for .contextmenu() called." );
    });

## Disable submit button until file selected for upload

    $('input:file').on("change", function() {
        $('input:submit').prop('disabled', !$(this).val()); 
    });

## Get brothers and sisters

    $("li.start").siblings()
