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

