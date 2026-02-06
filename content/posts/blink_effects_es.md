+++
date = '2026-02-06T17:29:27-03:00'
draft = false
title = 'Extender el Rich Text'
cover = { image = "images/data/blink.png", alt = "Configuracion en godot", caption = "Como se configura el richeffect" }
tags = ["Godot", "Devlog", "Juego", "MPVP"]
+++

### La idea

Vengo trabajando en un juego que quiero intentar presentar dentro de MPVP de ADVA 2026, y una parte del look and feel es que sea una terminal vieja. Algo que destaca mucho en las terminales son los símbolos parpadeantes esperando el input del usuario; sé que la nueva versión de Godot tiene pulse, pero quería probar armar una función que me haga el blink únicamente y de paso aprender a hacer algo similar.

### El codigo

```
extends RichTextEffect
class_name BlinkEffect

var bbcode = "blink"

func _process_custom_fx(char_fx_transform: CharFXTransform) -> bool:
    var time = char_fx_transform.elapsed_time
    var visible = fmod(time, 1.0) < 0.5
    char_fx_transform.visible = visible
    return true
```

Es tan simple como esto: con solo extender de RichTextEffect y sobrescribir la función de _process_custom_fx, podemos crear un nuevo tag para usar dentro de los RichText, por ahí es muy simple y está lejos de ser la funcionalidad, pero bueno, lo quería compartir.

En el código vemos como primero marcamos el nombre del tag, blink en mi caso, luego con la propiedad elapsed_time, podemos saber cuánto pasó desde que se creó el texto. Con este tiempo hacemos una división simple para quedarnos con el resto de la misma, esto nos sirve como booleano para prender o apagar nuestra funcionalidad.

Como parte final basta con agregar este script dentro del componente de godot, y asi exstender su comportamiento.

Les debo el ejemplo de cómo se ve, pero todavía me estoy acostumbrando a Hugo, y no quiero perder un par de horas peleando con un gif y un recurso estático que no sé por qué no muestra.