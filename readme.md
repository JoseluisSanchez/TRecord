# TRecord

Clase que permite manejar un buffer de registro sobre un fichero DBF. Realiza un scatter/gather sobre el registro actual del dbf con alguna funcionalidad añadida. 

Clase original proporcionada por Marcelo Via Giglio en http://forums.fivetechsupport.com/viewtopic.php?f=6&t=34402

**Métodos**

new()		Crea 

loadFromAlias(alias)	carga los valores del registro del fichero dbf del alias en datas del objeto buffer, creando una data por cada campo del dbf

saveToAlias( cAlias )	guarda los valores de las datas del objeto buffer en los  correspondientes campos del fichero dbf

Una particularidad de la clase, es que permite crear una data del objeto buffer inexistente en el dbf y asociarle un valor, por ejemplo: 

bAR:nArCatalo   := iif( AR->ArCatalo, 1, 2 )

donde se crea una data numérica a partir de un valor lógico para poder usarla en un radiobutton que requiere una variable numérica. 



**Ejemplo de uso de la clase**

LOCAL bAR   := TRecord():New()

SELECT AR

bAR:loadFromAlias( 'AR' )

bAR:nArCatalo   := iif( AR->ArCatalo, 1, 2 )

...

bAR:ArCatalo   := ( bAR:nArCatalo == 1 )

bAR:saveToAlias( 'AR' )