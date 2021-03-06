# Helpers (CSS/Sass)
Los helpers son ayudas al trabajo que fueron llamadas utilidades en la versión anterior de ed-grid. Se pueden usar con CSS (cssHelpers) o Sass.
## Alineación de elementos
Se aplica al mismo elemento que se quiere alinear (no a su contenedor). Tenga en cuenta que se usa `float` y se requiere declarar un ancho para que funcione bien. Puede declarar anchos usando clases al igual que con los ed-item.
### Versión con css
```markup
<div class="to-left s-50"><!-- Se envia a la izquierda 50% de ancho desde small--></div>
<div class="to-right m-80"><!-- Se envia a la derecha 80% de ancho desde medium --></div>
<div class="to-center l-75"><!-- Se envia al centro 75% de ancho desde large--></div>
```
### Versión con Sass
```scss
// Uso con Sass
// El primer parámetro es el ancho (con su unidad)
// El segundo (opcional) es el margin
// toCenter() no requiere segundo parametro
.selector1 { @include toRight(50%,10px) }
.selector2 { @include toLeft(70%,1em) }
.selector3 { @include toCenter(500px) }
```
Compila a
```css
.selector1{
  float:right;
  width:50%;
  margin-left:10px;
}

.selector2{
  float:left;
  width:70%;
  margin-right:1em;
}

.selector3{
  display:table;
  width:500px;
  margin-left:auto;
  margin-right:auto;
}
```
## Limpiar floats
### Versión con css
```markup
<!--Version css-->
<div class="clearfix"><!-- la clase clearfix limpia los floats--></div>
```
### Versión con Sass
```scss
// Uso con Sass
.selector { @include clearfix }
```
## Forzar ancho total
Hace que un elemento siempre mida el 100% del ancho disponible
### Versión con css
```markup
<!-- Version CSS -->
<div class="full"><!-- Este elemento medirá 100% de ancho siempre --></div>
```
### Versión con Sass
```scss
// Uso con Sass
.selector { @include full }
```
## Hacer un elemento circular
Tenga en cuenta que si el alto y el ancho no son iguales, el elemento no será circular sino oval.
### Versión con css
```markup
<!-- Version CSS -->
<div class="circle"><!-- Este elemento será circular --></div>
```
### Versión con Sass
```scss
// Uso con Sass
.selector { @include circle }
```
## Controlar el padding
En ed-grid la separación entre los ed-item se genera a través de padding laterales (la separación entre uno y el siguiente es dos veces el tamaño del padding, por defecto 15px).

Puede ocurrir que en algunos casos complejos para forzar la alineación requiera añadir o quitar los padding por defecto a cualquier elemento (no solo ed-container y ed-item).
### Versión con css
```markup
<!-- Version CSS -->
<div class="padding"><!-- Añade un padding si el elemento no lo tenia --></div>
<div class="padding-2"><!-- Añade un padding doble --></div>
<div class="padding-3"><!-- Añade un padding triple --></div>
<div class="ed-container no-padding"><!-- Elimina el padding de todos sus ed-item internos--></div>
<div class="ed-item no-padding"><!-- Elimina el padding de solo este ed-item--></div>
```
### Versión con Sass
```scss
// Uso con Sass

// el mixin padding() recibe un número como parámetro
// este número puede ser 0 para eliminar el padding
.selector1 { @include padding(3) }

// El mixin noPaddingContainer tiene efecto
// solo aplicado a un .ed-container y elimina
// el padding de sus ed-item hijos
.selector2 { @include noPaddingContainer }
```
