# Google Maps JavaScript API V3

## Affichage d'une carte

    <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="fr">
        <head>
            <title>Tutoriel Google Maps</title>
            <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
            <!-- Elément Google Maps indiquant que la carte doit être affiché en plein écran et
            qu'elle ne peut pas être redimensionnée par l'utilisateur -->
            <meta name="viewport" content="initial-scale=1.0, user-scalable=no" />
            <!-- Inclusion de l'API Google MAPS -->
            <!-- Le paramètre "sensor" indique si cette application utilise détecteur pour déterminer la position de l'utilisateur -->
            <script type="text/javascript" src="http://maps.google.com/maps/api/js?sensor=false"></script>

            <script type="text/javascript">
                function initialiser() {
                    var options = {
                        center: new google.maps.LatLng(46.779231, 6.659431),
                        zoom: 19,
                        mapTypeId: google.maps.MapTypeId.ROADMAP
                    };
                    var carte = new google.maps.Map(document.getElementById("carte"), options);
                }
                google.maps.event.addDomListener(window,'load', initialiser);
            </script>
        </head>

        <body>
            <div id="carte" style="width:100%; height:100%"></div>
        </body>
    </html>

### Options de la carte

- **center** : centre de la carte (coordonnées en latitude et longitude)
- **zoom** : agrandissement de la carte (0 à 20
- **mapTypeId** : type de la carte (google.maps.MapTypeId.ROADMAP, ...SATELLITE, ...HYBRID, ...TERRAIN)
- **disableDoubleClickZoom** : si = true, désactive l'agrandissement en faisant un double-clic
- **draggable** : si = true, désactive le fait de pouvoir faire glisser la carte
- **scrollwheel** : si = true, désactive l'agrandissement avec le scroll de la souris

## Création d'overlay

Un overlay est un élément graphique que l'on peut poser ou dessiner sur une carte Google Maps.

### Les marqueurs

Un *marqueur** permet de situer un point précis sur une carte.

    var marqueur = new google.maps.Marker({
        position: new google.maps.LatLng(46.779231, 6.659431),
        map: carte,
        icon: "./mon_image.png",
        draggable: true
    });

### Les polylines

Les **polylines** permettent de dessiner des lignes droites attachées les unes aux autres sur la carte. Ceci peut permettre, par exemple, de dessiner un itinéraire.

    var parcoursBus = [
        new google.maps.LatLng(46.781367900048, 6.6401992834884),
        new google.maps.LatLng(46.780821285011, 6.6416348016222),
        new google.maps.LatLng(46.780496546047, 6.6421830461926),
        new google.maps.LatLng(46.779835306991, 6.6426765713417)
	];

	var traceParcoursBus = new google.maps.Polyline({
	    map : carte,
        path: parcoursBus, //chemin du tracé
        strokeColor: "#FF0000", //couleur du tracé
        strokeOpacity: 1.0, //opacité du tracé
        strokeWeight: 2 //grosseur du tracé
	});

### Les polygones

    //sommets du polygone
	var parcelleHeig = [
        new google.maps.LatLng(46.779733557514, 6.660767535),
        new google.maps.LatLng(46.780189079483, 6.6595337188532),
        new google.maps.LatLng(46.779114923142, 6.6580590403695),
        new google.maps.LatLng(46.778462483896, 6.6592118537714)
	];

	polygoneParcelleHeig = new google.maps.Polygon({
	    map : carte,
        paths: parcelleHeig, //sommets du polygone
        strokeColor: "#0FF000", //couleur des bords du polygone
        strokeOpacity: 0.8, //opacité des bords du polygone
        strokeWeight: 2, //épaisseur des bords du polygone
        fillColor: "#0FF000", //couleur de remplissage du polygone
        fillOpacity: 0.35 //opacité de remplissage du polygone
	});

## Gestion des évènements souris

- **click** : clic la souris
- **rightclick** : clic-droit avec la souris
- **dblclick** : double-clic avec la souris
- **drag** : déplace un objet au moyen de la souris par un glisser-déposer (généré plusieurs fois tout au long de cette action)
- **dragstart** : une fois tout au début d'un déplacement d'un objet au moyen de la souris par un glisser-déposer
- **dragend** : une fois tout à la fin d'un déplacement d'un objet au moyen de la souris par un glisser-déposer
- **mouseover** : lorsque le pointeur de la souris entre sur la surface d'un objet
- **mouseout** : lorsque le pointeur de la souris sort de la surface d'un objet

<br>

    var tabMarqueurs = new Array();
    google.maps.event.addListener(carte, 'click', function(event) {
        tabMarqueurs.push(new google.maps.Marker({
            position: event.latLng, //coordonnée de la position du clic sur la carte
            map: carte
        }));
    });


## Définir les bords de la carte

var bounds = new google.maps.LatLngBounds();
bounds.extend(myLatLng);
map.fitBounds(bounds);

# Sources

- https://openclassrooms.com/courses/google-maps-javascript-api-v3