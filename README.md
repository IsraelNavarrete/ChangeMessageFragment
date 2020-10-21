19/10

1º
Explicacion fragments

https://moronlu18.com/wordpress/courses/deint/178-1931

2º
Explicacion Modelo Vista Ccontrolador

https://moronlu18.com/wordpress/courses/deint/178-1954

3º
Explicacion ciclo de vida de un fragment

https://moronlu18.com/wordpress/courses/deint/178-1932

4º
Creamos un nuevo proyecto (copiamos el ya existente y cambiamos el nombre)
Renombrar package changemessage -> changemessagefragment y el build.gradle

Creamos 2 nuevos fragment blank en la carpeta ui

Me ha ocurrido un ERROR donde el nombre de los paquetes son diferentes (cambia una letra mayuscula en el import de la clase y sale
ERROR en R)

5º
Cogemos la vista de activity_send_message y la pegamos en el fragment_send_message ya que es quien se encarga de la vista
Borramos to.do el xml y lo reemplazamos por un frame layout

Cambiamos el nombre de SendMessageActivity a MainActivity y su activity igual

Copiamos el codigo de mainactivity a SendMessageFragment y cambiamos los this por getActivity()


20/10

1º
Copiamos la información del activity_send_message al fragment y borramos el activity

Copiamos la informacion del ViewMessageActivity al fragment y borramos el activity (no toda la clase)

2º
Explicacion librerias de soporte de fragments

https://moronlu18.com/wordpress/courses/deint/178-1997

3º
En main activity creamos el fragment manager y el fragment transaction

Añadimos en activity_main una id

Creamos una nueva interfaz y añadimos el metodo onAttach(context)

Obligamos que la clase que use la SendMessageFragment de error si no implementa la interfaz.
Tambien creamos un objeto de tipo ShowListenerMessage

Si da error recogemos el error y lanzamos un error personalizado donde le decimos que implemente la interfaz

4º
Implementamos la interfaz en mainActivity y sobreescribimos el metodo

Recogemos la informacion del bundle en ViewMessageFragment

21/10

1º
Corregido error nullPointer. El error era que intentaba buscar el Message en la activity
cuando habia que cogerlo del view del fragment

2º
Sobreescribimos todos los metodos de ciclo de vida de los fragment en ambas clases para ver porque si cambiamos la pantalla
a horizontal se reinicia la activity y se buguea.

Este error ocurre debido a que al cambiar la pantalla (al cambiar configuracion el idioma tambien ocurre)
se vuelve a crear la activity por tanto, se ejecuta de nuevo tanto el SendMessageFragment
(debido a que se crea la activity) y el ViewMessageActivity (debido que es la pantalla que estamos cargando)

Para controlar este error en el método OnCreate() de la activity el Bundle savedInstanceState preguntamos si es null
hacemos que cree el fragment, de no serlo que no haga nada


3º
Añadimos los fragments a su pila para que cuando le demos al boton back del movil no se cierre automaticamente
ft.addToBackStack(null);


Arreglamos el boton ShowAbout creando un metodo onClick()

4º
Explicacion de guardado de estado.
Los widget que utilizamos ya guardan de por si su propio estado por tanto no es necesario hacer nada pero
si por ejemplo añadieramos algo que no es un widget nosotros nos tendriamos que encargar de guardar el estado
de ese objeto cuando se reinicie la activity

Para guardar los datos utilizamos el metodo onSaveInstanceState(Bundle outstate) ahí guardariamos los datos solo si se cambia
la configuracion (SOLO DATOS PEQUEÑOS si son datos de gran tamaño o lo guardamos en un fichero json o xml o en la bd)

5º
Creamos los metodos onSaveInstanceState() y on onRestoreInstanceState() MainActivity y en SendMessageFragment

6º
Explicacion estado dinámico
Creamos una variable number la cual utilizaremos como ejemplo de que se puede
guardar el fragment sin borrarlo con setRetainInstance(true) en el metodo onCreate() de SendMessageCreate()

Para que no de error hemos de asegurarnos que si el fragment ya se ha creado 1 vez y se cambia la configuracion no se vuelva a
crear para ello hay 2 formas la primera de ellas esta comentada en el método onCreate de MainActivity y la 2a es la que se utiliza
tambien en el metodo de MainActivity
