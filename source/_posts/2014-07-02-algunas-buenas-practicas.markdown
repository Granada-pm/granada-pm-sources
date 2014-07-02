---
layout: post
title: "Algunas buenas prácticas"
date: 2014-07-02 19:47:11 +0200
comments: true
categories: [best-practices,trucos,hacks]
---
En el [curso de Perl](http://cevug.ugr.es/perl) virtual que venimos
impartiendo observamos que hay una serie de malas costumbres que se
repiten, sea porque todo el mundo sigue los mismos ejemplos (que,
ejem, algunos son nuestros) o porque simplemente han aprendido a
programar en sitios similares. Siguiendo una serie de buenas prácticas
Perleras, pero también de casi cualquier otro lenguaje, se hacen los
programas más legibles, se programa de forma más eficiente y los
programas son más mantenibles. Y en esto el manual definitivo es el
[Perl Best Practices de Damien Conway](https://www.amazon.es/dp/B002L4EXI8?tag=atalaya-21&camp=3634&creative=24822&linkCode=as4&creativeASIN=B002L4EXI8&adid=0Y9FGAY72E8FH4AWVJ46&),
pero también [Modern Perl](modernperlbooks.com/mt/index.html) tiene un
enfoque que anima a usarlas. 

En todo caso, hay muchas (y herramientas para llevarlas a cabo), pero
estas tratan de atajar ciertas cosas que se encuentran repetidamente
en nuestros cursos

* No se deben usar
  [`GLOB`s](http://stackoverflow.com/questions/4865447/demystifying-the-perl-glob). Para
  entendernos, esto es un GLOB 
 ```
  open(FILE, ">este_es_un_file")
 ```
 En Perl previo a la versión 5, era la forma estándar de usar
 ficheros. Sin embargo, ahora se puede usar
  ```
  open(my $file, ">este_es_un_file")
 ```
 y luego el `$file` lo puedes pasar como cualquier otra variable
 
 * Siempre, siempre, `use strict`y `use warnings`. Siempre. ¿He dicho
  siempre? Para evitar errores comunes y también alguna mala práctica,
  como no declarar el ámbito de las variables.
  
  * Usa un método consistente para darle nombre a las variables, y el
    mejor es `$este_metodo`. Nada de CamelCaps y muchopeor
    `$nicamelnicaps` porque no hay forma de entenderse.
	
* Sigue las convenciones a la hora de nombrar variables (minúsculas)
  módulos (primera mayúscula y cada letra después de un _) y
  constantes y GLOBS (todo mayúsculas).
  
 * En general, las funciones no deben de incluir "presentación". Eso
   quiere decir que una rutina no debe ni de pedir información al
   usuario (más sobre esto más tarde) ni de imprimir cosas. Que
   devuelva información y el cliente de la función se encargue de
   formatearla como el cliente quiera.
   
 * Los menús en pantalla son taaaan de los años 80. "A continuación,
   pulse el número de la opción correspondiente" me trae a mi época
   del BASIC del Spectrum. Hoy en día hay muchas otras formas de
   elegir opciones. O haces un GUI como el FSM manda, usando `curses`
   o `Tk`  o lo que te dé la gana, o introduces opciones desde línea
   de órdenes o entrada estándar. Los programas en Perl deben estar
   (en general) preparados para ser encadenados de esta forma
   `mi_primer_programa.pl | ./segundo_programa.pl | y_este_tercero.pl
   -o foo`  igual que "Introduce un nombre de fichero". Usa el
   [operador diamante](http://campusvirtual.ull.es/ocw/file.php/43/perlexamples/node173.html)
   para leer nombres de ficheros o entrada estándar indistintamente. 
   
 * Usa control de versiones. De veras, úsalo. Usa
   [git](https://www.amazon.es/dp/B00K515GL2?tag=atalaya-21&camp=3634&creative=24822&linkCode=as4&creativeASIN=B00K515GL2&adid=0QWZJD8TM41S32VW42EF&)
   
 
No es que sean las únicas buenas prácticas, pero sí unas convenientes
y no demasiado complicadas. 
