## Unidad 1  Interfaz Gráfica de usuarios.
En este trabajo se aborda el desarrollo de una interfaz gráfica utilizando Flet, un framework que permite crear aplicaciones interactivas en Python de manera estructurada y multiplataforma. A lo largo del desarrollo se explicó cómo se construye una interfaz gráfica, qué tipos de eventos permiten que el usuario interactúe con la aplicación y cómo se manejan dichos eventos mediante funciones que responden automáticamente a acciones como clics o cambios de texto.
Asimismo, se analizaron los componentes gráficos de control utilizados en los programas desarrollados, como formularios, calculadoras y un sistema de chat , estos ejemplos permitieron comprender cómo se organizan los elementos visuales, cómo capturan información y cómo se conectan con la lógica del programa para generar aplicaciones dinámicas.
## Creación de Interfaz Gráfica para Usuarios

La interfaz de usuario es el medio que permite la comunicación entre una persona y una máquina. Está compuesta por todos los elementos mediante los cuales el usuario puede interactuar con un sistema informático, facilitando la ejecución de acciones de manera eficaz, precisa y segura.
Dentro de los distintos tipos de interfaces, la Interfaz Gráfica de Usuario (GUI) representa una evolución significativa respecto a la interfaz de línea de comandos (CLI), ya que permite interactuar con el sistema mediante elementos visuales como ventanas, botones, íconos y cuadros de texto, eliminando la necesidad de introducir comandos escritos.
La creación de una interfaz gráfica implica diseñar un entorno visual estructurado que permita al usuario comprender fácilmente las opciones disponibles y ejecutar acciones de forma intuitiva.

**Elementos que componen una GUI**

Una interfaz gráfica está formada por diversos componentes visuales, entre los cuales se encuentran:
Botones, Cuadros de texto, Listas desplegables, Grupos de selección, Contenedores, Ventanas, Panel etc.
Estos elementos se organizan de manera jerárquica en pantalla, permitiendo que el usuario identifique claramente cada función del sistema.

**Principios en la creación de una interfaz gráfica**

Para que una GUI sea efectiva, debe cumplir con ciertas características:
Claridad: los elementos deben ser visibles y comprensibles.
Coherencia: el diseño debe mantener uniformidad visual.
Simplicidad: evitar saturación de información.
Accesibilidad: permitir su uso a diferentes tipos de usuarios.
El objetivo principal es facilitar la interaccion y mejorar la experiencia del usuario.

**Creación de Interfaces Gráficas mediante Flet**

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

**Eventos de Interacción con Widgets**

Son los eventos más comunes en aplicaciones gráficas, ya que se activan cuando el usuario interactúa directamente con un componente visual.
 Evento on_click

Se activa cuando el usuario hace clic en un botón u otro control interactivo.

En los progrmas vistos en clase se utilizan:

-Botones del formulario (por ejemplo, enviar datos).

Botones de las calculadoras (operaciones matemáticas).

-Botón “Send” en el chat.

-Botón “Join chat” en el cuadro de diálogo.
 
Ejemplo : 

```python
   page.add(chat, ft.Row([new_message, ft.Button("Send", on_click=send_click)]))
```

Aquí, send_click es la función que se ejecuta cuando el usuario presiona el botón, este tipo de evento pertenece a los eventos de acción directa.

**Evento on_change**

Se activa cuando el valor de un componente cambia.

En tus programas aparece en:
-Campos de texto del formulario.
 
 -Dropdowns de selección.
	
 -Campos numéricos en las calculadoras.

Por ejemplo, cuando el usuario escribe en un TextField, el sistema puede validar el contenido en tiempo real, este evento pertenece a los eventos de entrada de datos, ya que reaccionan a modificaciones en la información ingresada.

**Evento on_submit**

Se activa cuando el usuario presiona la tecla Enter dentro de un campo de texto, es útil en formularios y aplicaciones como la calculadora o el chat, donde el usuario puede confirmar una entrada sin presionar un botón adicional.


**Eventos de Navegación y Diálogo**

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

**Eventos de Comunicación Interna (PubSub)**

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

| Tipo de Evento              | Ejemplo en programas                         |
|-----------------------------|----------------------------------------------|
| Evento de acción            | `on_click` en botones                        |
| Evento de entrada           | `on_change` en TextField                     |
| Evento de confirmación      | `on_submit`                                  |
| Evento de comunicación      | `page.pubsub.subscribe()` en chat            |
| Evento de actualización     | `page.update()`                              |


## Manejo de eventos 

El manejo de eventos es el proceso mediante el cual una aplicación responde a las acciones del usuario dentro de una interfaz gráfica. En Flet, este proceso se realiza a través de funciones denominadas event handlers, las cuales se asignan a propiedades específicas de los controles, como on_click o on_change.

Cuando ocurre un evento, el sistema ejecuta automáticamente la función asociada, permitiendo modificar valores, validar información o actualizar la interfaz.

**Modelo de Manejo de Eventos en Flet**

En Flet, los eventos se gestionan mediante un modelo basado en:

-Definición de una función manejadora (event handler).

-Asignación de esa función a un control.

-Ejecución automática cuando ocurre el evento.

-Actualización de la interfaz con page.update().

Este proceso permite que la aplicación reaccione dinámicamente a la interacción del usuario.

**Estructura general de un controlador de eventos**

La estructura básica utilizada en los programas es:

```python
def nombre_funcion(e):
    # lógica del evento
    page.update()
```

Dónde:
e : representa el objeto del evento.

Dentro de la función se coloca la lógica que se desea ejecutar.

page.update()Actualiza la interfaz para mostrar los cambios.

**Manejo de Eventos en los Programas**

a) Manejo del evento on_click(Botones)

Ejemplo del programa de chat:

```python
def send_click(e):
    page.pubsub.send_all(...)
    new_message.value = ""
    page.update()

```
Aquí el manejo del evento consiste en:

1.-Capturar el clic del usuario.

2.-Procesar el mensaje.

3.-Limpiar el campo de texto.

4.-Actualizar la interfaz.

Esto demuestra que el evento no solo detecta la acción, sino que ejecuta lógica interna.

b) Manejo de validaciones (Formulario)

En el formulario, cuando el usuario presiona un botón:
```python
def join_click(e):
    if not user_name.value:
        user_name.error_text = "Name cannot be blank!"
    else:
        ...
    page.update()

```

Aquí el manejo del evento incluye:

1.-Validación de datos.

2.-Asignación de mensajes de error.

3.-Control del flujo del programa.

4.-Actualización visual.

Este es un ejemplo claro de cómo el manejo de eventos controla la lógica del sistema.

c) Manejo de eventos en comunicación interna (Chat)
En el programa de chat:
```python
    page.pubsub.subscribe(on_message)

```

Cuando aparece un nuevo mensaje:
```python
    def on_message(message: Message):
        if message.message_type == "chat_message":
            chat.controls.append(ft.Text(f"{message.user}: {message.text}"))
        elif message.message_type == "login_message":
            chat.controls.append(
                ft.Text(message.text, italic=True, color=ft.Colors.BLACK_45, size=12)
            )
```
Aquí el evento se maneja mediante una función que escucha cambios y actualiza el contenido dinámicamente, este tipo de manejo demuestra un modelo más avanzado, donde los eventos no solo provienen de botones, sino de cambios en el estado de la aplicación.

## Manejo de componentes graficos de control.

Los componentes gráficos de control son los elementos visuales que permiten al usuario interactuar con una aplicación. Estos controles funcionan como intermediarios entre el usuario y el sistema, ya que capturan información, ejecutan acciones y muestran resultados.

En el desarrollo de interfaces con Flet, los componentes gráficos se implementan mediante controles (controls), los cuales se organizan dentro de contenedores como Column y Row para estructurar la interfaz.



**Componentes de Entrada de Datos**

Son aquellos que permiten al usuario ingresar información.

**TextField**

Se utiliza para capturar texto ingresado por el usuario.

En los programas aparece en : 

-Formulario → captura nombre, datos personales.

-Calculadora → ingreso de números.

-Chat → escritura de mensajes.

ejemplo : 

```python
    new_message = ft.TextField()
```
Este componente permite que el usuario introduzca información que luego será procesada por la aplicación.

**Dropdown**

Permite seleccionar una opción de una lista desplegable.

En el formulario se utiliza para seleccionar opciones como carrera o categoría.

```python
    dd_carrera = ft.Dropdown(
        label="Carrera *",
```
Este control facilita la selección estructurada de datos.

**Componentes de Acción**


Son controles que ejecutan una operación cuando el usuario interactúa con ellos.

**Button**

En los programas se utilizan botones para:

-Enviar formulario.

-Realizar operaciones matemáticas.

-Enviar mensajes en el chat.

-Ingresar al chat (“Join chat”).

Ejemplo:

```python
ft.Button("Send", on_click=send_click)
```
Este componente conecta la interfaz con la lógica del programa.

**Componentes de Organización**

Estos controles estructuran visualmente la interfaz.

**Column**

Organiza los elementos de forma vertical.

Ejemplo del chat:

```python
chat = ft.Column()
```

Aquí se almacenan los mensajes que se agregan dinámicamente.

**Row**
Organiza los elementos horizontalmente.

Ejemplo:
```python
ft.Row([new_message, ft.Button("Send")])
```

**Componentes de Diálogo**

En el programa del chat se utiliza:
```python
page.show_dialog(
    ft.AlertDialog(
        title=ft.Text("Welcome!"),
        ...
    )

```
Este componente muestra una ventana emergente para solicitar información antes de ingresar al chat.
Los diálogos son importantes para controlar el flujo de interacción.


