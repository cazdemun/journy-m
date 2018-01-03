# Conociendo a un enemigo - CSS

Tengo que admitirlo, ¡no sé CSS!

Siempre lo evadí, porque el desarrollo web me marea demasiado.

Tengo que admitir que no soy bueno leyendo HTML, es un dolor de ojos y mi cerebro duele.

Y por esa razón nunca toqué CSS.

Pensé que en la vida solo necesitaria HTML y JavaScript... boy I was wrong.

Pero al parecer necesitaré CSS para jQuery, Justice, y para BlockChain... ugh.

Bueno, en fin, es hora de aprender, estoy siguiendo [esta guía][2] de [esta lista][1] por ahora

## Primer paso, codecademy

Codeacademy... pensé que nunca lo volvería ver.

Resumen de los 17 ejercicios:

### Primer ejercicio

Poner la siguiente línea:

```html
<link href="style.css" type="text/css" rel="stylesheet">
```

Aquí

```html
<head>
    <link href='https://fonts.googleapis.com/css?family=Roboto:400,300,500,100' rel='stylesheet' type='text/css'>
	<link href="style.css" type="text/css" rel="stylesheet">
  </head>
```

La finalidad es, bueno, referenciar un archivo CSS y ver que tan diferente se ve con respecto a un HTML normal.

### 2. Inline Styles

Añadir

```html
style="font-family: Arial;"
```

En

```html
<p style="font-family: Arial;">The world is full of fascinating places. Planning the perfect vacation involves packing up, leaving home, and experiencing something new.</p>
```

Se puede poner CSS en las mismas etiquetas... aunque no es recomendable.

### 3. The \<style> Tag

Añadir

```html
  <style>
    p {
      color: red;
      font-size: 20px;
      font-family: Arial;
    }
  </style>
```

En

```
<head>
  <title>Vacation World</title>
  
  <style>
    p {
      color: red;
      font-size: 20px;
      font-family: Arial;
    }
  </style>
</head>
```

Creo que empiezo a notar un patrón en estos ejercicios.

### 4. The .css file

Lo mismo que la 1, básicamente...

### 5. Linking the CSS File

Lo mismo que la 1, básicamente...

### 6. Tag Name

Lo importante aquí es que los tag se seleccionan con el nombre a secas, nada más.

En style.css:

```css
p {
  color: red;
  font-size: 20px;
  font-family: Arial;
}

h1 {
  color: maroon;
}
```

### 7. Class Name

Las clases son parte de HTML, ¿no?

En fin, aquí vemos como se seleccionan las clases, que es un punto y el nombre de la clase, wu.

Por algún motivo las reglas de la clase sobreescriben a las reglas de las etiquetas... ¿supongo que es porque es más específico? Tal vez tiene que ver el orden.

¿Qué pasa cuando tengo dos etiquetas con la misma clase. ¿Está permitido? ¿Es buena práctica?

En style.css:

```css
p {
  color: red;
  font-size: 20px;
  font-family: Arial;
}

h1 {
  color: maroon;
}

.title {
  color: teal;
}
```

Nota: 7 ejercicios en 20 minutos, wuju, solo 17 más...

### Paréntesis: Circulos

Estuve tratando de hacer círculos



# Links

[1]: https://github.com/thedaviddias/Resources-Front-End-Beginner#learn-css
[2]: https://www.codecademy.com/learn/learn-css
