necesidad de crear dos archivos separados: xml y dtd, en dtd especificar en lugar de CDATA >> #PCDATA

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE numeros [
<!ELEMENT numeros (#PCDATA)>
]>
<numeros>
52
</numeros>

La segunda foto: 
ELement <partido> no está cerrado en su XML; es necesario añadir la etiqueta de cierre </partido> para cada partido. En su DTD, tiene un atributo 'goles' para el elemento <visitante>, pero debería ser un atributo para <local>. También hay un orden incorrecto de atributos en <ATTLIST local>; el atributo 'goles' debe ir después de #PCDATA.
<!DOCTYPE ligaDeFutbol [
<!ELEMENT ligaDeFutbol (partido*)>
<!ELEMENT partido (local, visitante)>
<!ELEMENT local (#PCDATA)>
<!ATTLIST local goles CDATA #REQUIRED>
<!ELEMENT visitante (#PCDATA)>
<!ATTLIST visitante goles CDATA #REQUIRED>
]>


<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE ligaDeFutbol SYSTEM "ejemplo.dtd">
<ligaDeFutbol>
  <partido>
    <local goles="0">Real Madrid</local>
    <visitante goles="1">Barcelona</visitante>
  </partido>
  <partido>
    <local goles="3">Hércules</local>
    <visitante goles="3">Albacete</visitante>
  </partido>
  <partido>
    <local goles="4">Balmis</local>
    <visitante goles="0"></visitante>
  </partido>
</ligaDeFutbol>
