# overlooker.js
Plugin para validación de formularios por medio de expresiones regulares.

<br>

<h3>Comenzando</h3>

<p>Para comenzar a validar formularios dentro de nuestra aplicación solo debemos incluir el plugin en nuestra página.

Luego se hace la instancia desde el formulario de la siguiente forma:
</p>

```JavaScript
    $("#form_page").overlooker();
```

<p>De esta forma conseguiremos una validación por defecto para campos vacíos cada vez que se ejecute el evento change en los elementos del formulario.</p>

<p>
Para designar una validación específica para cada campo en nuestro formulario se debe configurar un array de objetos que llevan las validaciones para cada uno de los campos, para hacer esto posible se configura el plugin de la siguiente manera:
</p>

```JavaScript
$("#form_page").overlooker({
    validations:[
        {
            id : "email",
            expresion : "email",
            evento : "change"
        }
})
```

<p>Este array lleva un objeto que se compone del id del campo a validar, la expresion regular a ejecutar y el evento en el cual
debe ejecutar dicha validación.</p>

<hr>

<h3>Set de validaciones incuidas</h3>

<p>Este plugin cuenta con una cantidad de validaciones incluidas, que son las que se usan en la mayoría de aplicaciones web.
Si la validación no se encuentra dentro de este set también es posible añadir más validaciones según sea necesario.</p>

<h4>solo_letras</h4>

```JavaScript
solo_letras : [ 
                {
                  valor:/^[a-z A-Z]*$/,
                  err_mens:"Este campo solo permite letras mayúsculas o minúsculas."
                }
              ]
```

<h4>solo_numeros</h4>

```JavaScript
solo_numeros : [ 
                  {
                    valor:/^[\d]*$/,
                    err_mens:"Este campo solo permite números."
                  }
                ]
```

<h4>no_vacio</h4>

```JavaScript
no_vacio : [ 
              {
                valor:/^[^]+$/,
                err_mens:"Este campo no puede ser vacío."
              }
            ]
```

<h4>telefono</h4>

```JavaScript
telefono : [ 
              {
                valor:/^\d{5,15}$/,
                err_mens:"Este campo no es un número de teléfono válido.[Solo números 5 a 15 caractéres.]"
              }
            ]
```


<h4>doc_identidad</h4>

```JavaScript
doc_identidad : [ 
                  {
                    valor:/^\d{6,12}$/,
                    err_mens:"Este campo no es un número de identidad válido.[Solo números 6 a 12 caractéres.]"
                  }
                ]
```

<h4>email</h4>

```JavaScript
email : [ 
          {
            valor:/([a-zA-Z0-9_\.\-])+\@(([a-zA-Z0-9\-])+\.)+([a-zA-Z0-9]{2,4})/,
            err_mens:"La dirección de correo no es válida."
          }
        ]
```

<hr>

<h3>Añadiendo nuevas validaciones</h3>

<p>Para añadir nuevas validaciones se debe agregar el objeto de validación en las opciones y hacer referencia al mismo por medio
del array validations.</p>

```JavaScript
$("#form_page").overlooker({
    solo_3numeros:[
              {
                valor:/[0-9]{1,3}/,
                err_mens:"El número que ingresó no es válido.[Solo números de máximo 3 dígitos.]"
              }
            ],
    validations:[
        {
            id : "numero",
            expresion : "solo_3numeros",
            evento : "change"
        }
})
```
