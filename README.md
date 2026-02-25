## Creación de Interfaz Gráfica para Usuarios

La interfaz de usuario es el medio que permite la comunicación entre una persona y una máquina. Está compuesta por todos los elementos mediante los cuales el usuario puede interactuar con un sistema informático, facilitando la ejecución de acciones de manera eficaz, precisa y segura.
Dentro de los distintos tipos de interfaces, la Interfaz Gráfica de Usuario (GUI) representa una evolución significativa respecto a la interfaz de línea de comandos (CLI), ya que permite interactuar con el sistema mediante elementos visuales como ventanas, botones, íconos y cuadros de texto, eliminando la necesidad de introducir comandos escritos.
La creación de una interfaz gráfica implica diseñar un entorno visual estructurado que permita al usuario comprender fácilmente las opciones disponibles y ejecutar acciones de forma intuitiva.

Elementos que componen una GUI

Una interfaz gráfica está formada por diversos componentes visuales, entre los cuales se encuentran:
Botones, Cuadros de texto, Listas desplegables, Grupos de selección, Contenedores, Ventanas, Panel etc.
Estos elementos se organizan de manera jerárquica en pantalla, permitiendo que el usuario identifique claramente cada función del sistema.

Principios en la creación de una interfaz gráfica

Para que una GUI sea efectiva, debe cumplir con ciertas características:
Claridad: los elementos deben ser visibles y comprensibles.
Coherencia: el diseño debe mantener uniformidad visual.
Simplicidad: evitar saturación de información.
Accesibilidad: permitir su uso a diferentes tipos de usuarios.
El objetivo principal es facilitar la interaccion y mejorar la experiencia del usuario.

Creación de Interfaces Gráficas mediante Flet

En el desarrollo actual, frameworks como Flet permiten crear interfaces gráficas utilizando programación estructurada y componentes visuales denominados controles (controls). En los programas desarrollados como ejemplo práctico (un formulario de registro y dos calculadoras), se observa la construcción organizada de la interfaz mediante elementos visuales.

Por ejemplo, en el formulario se utilizan componentes como:
```python
 txt_nombre = ft.TextField(label="Nombre *", on_change=lambda e: validar_campo(txt_nombre, "texto"))
    txt_control = ft.TextField(label="Número de control *", on_change=lambda e: validar_campo(txt_control, "numeros"))
    txt_email = ft.TextField(label="Email *", on_change=lambda e: validar_campo(txt_email, "correo"))
```
Estos controles representan elementos gráficos de entrada y acción, permitiendo que el usuario interactúe con el sistema a través de objetos visuales claramente identificables.

En las calculadoras desarrolladas, la interfaz se organiza mediante estructuras como:
```python
 controls=[
                seccion_display,
                ft.Text("Numeros y controles", size=12, weight="bold"), #etiqueta guia
                seccion_numeros,
                ft.Divider(), #linea divisora
                ft.Text("Operaciones:",size=12, weight="bold"), #etiqueta guia
                seccion_operaciones
```
Esto demuestra la organización jerárquica de los elementos en pantalla, donde cada sección cumple una función específica dentro del entorno visual.

Los programas desarrollados cumplen con la definición de Interfaz Gráfica de Usuario porque:

Presentan elementos visuales interactivos.

-Permiten la comunicación directa entre usuario y sistema.

-Están organizados estructuralmente.

-No requieren el uso de comandos de texto.

-Facilitan la ejecución de acciones mediante componentes gráficos.

## Tipos de Eventos en una Interfaz Gráfica

En el contexto de la programación, un evento es una acción o suceso que ocurre durante la ejecución de un programa y que permite que el sistema reaccione de manera interactiva. Estos eventos pueden ser generados por el usuario (clics, escritura de texto, selección de opciones) o por el propio sistema.

En el desarrollo de interfaces gráficas, los eventos son fundamentales, ya que permiten transformar una interfaz estática en una aplicación dinámica e interactiva.

En Flet, los eventos funcionan mediante callbacks, es decir, funciones que se ejecutan automáticamente cuando ocurre una acción específica. Este modelo permite que la aplicación responda en tiempo real a la interacción del usuario.

 Eventos de Interacción con Widgets

Son los eventos más comunes en aplicaciones gráficas, ya que se activan cuando el usuario interactúa directamente con un componente visual.
 Evento on_click


Se activa cuando el usuario hace clic en un botón u otro control interactivo.

En los progrmas vistos en clase se utilizan:

-Botones del formulario (por ejemplo, enviar datos).

-	Botones de las calculadoras (operaciones matemáticas).

-Botón “Send” en el chat.

-Botón “Join chat” en el cuadro de diálogo.
 
Ejemplo : 

```python
   page.add(chat, ft.Row([new_message, ft.Button("Send", on_click=send_click)]))
```

Aquí, send_click es la función que se ejecuta cuando el usuario presiona el botón, este tipo de evento pertenece a los eventos de acción directa.

Evento on_change

Se activa cuando el valor de un componente cambia.

En tus programas aparece en:
	-Campos de texto del formulario.
 
 -Dropdowns de selección.
	
 -Campos numéricos en las calculadoras.

Por ejemplo, cuando el usuario escribe en un TextField, el sistema puede validar el contenido en tiempo real, este evento pertenece a los eventos de entrada de datos, ya que reaccionan a modificaciones en la información ingresada.

Evento on_submit

Se activa cuando el usuario presiona la tecla Enter dentro de un campo de texto, es útil en formularios y aplicaciones como la calculadora o el chat, donde el usuario puede confirmar una entrada sin presionar un botón adicional.


Eventos de Navegación y Diálogo

Estos eventos se relacionan con cambios en la estructura visual de la aplicación.

En el programa de chat se observa el uso de:

```python
    page.show_dialog(
        ft.AlertDialog(
        ...................
            actions_alignment=ft.MainAxisAlignment.END,
```
Aquí se combinan:

-Evento on_click
	
-Control de diálogo (AlertDialog)

-Actualización de la página

Cuando el usuario presiona “Join chat”, se ejecuta la función join_click, lo que demuestra cómo un evento puede modificar el estado de la aplicación.

Eventos de Comunicación Interna (PubSub)

En el programa del chat aparece un tipo de evento más avanzado:
```python
 page.pubsub.send_all(
                Message(
```
Este mecanismo permite que la aplicación escuche mensajes enviados dentro del sistema.

Cuando ocurre un nuevo mensaje:
```python
 page.pubsub.send_all(
                Message(
```
Se activa automáticamente la función on_message.

Este tipo de evento pertenece a los eventos de comunicación interna, ya que no depende directamente de un clic visible, sino del intercambio de información entre componentes.

Actualización de la Interfaz como Respuesta a Eventos

En Flet, cada vez que un evento modifica un valor visual, se debe actualizar la interfaz:
```python
        page.update()
```
Esto garantiza que los cambios provocados por el evento se reflejen en pantalla.

| Tipo de Evento              | Ejemplo en tus programas                     |
|-----------------------------|----------------------------------------------|
| Evento de acción            | `on_click` en botones                        |
| Evento de entrada           | `on_change` en TextField                     |
| Evento de confirmación      | `on_submit`                                  |
| Evento de validación        | Verificación de campos vacíos en formulario  |
| Evento de comunicación      | `page.pubsub.subscribe()` en chat            |
| Evento de actualización     | `page.update()`                              |




