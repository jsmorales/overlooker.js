# overlooker.js
Plugin para validación de formularios pormedio de expresiones regulares.

<br>

<h3>Comenzando</h3>

<p>Para comenzar a validar formularios dentro de nuestra aplicación solo debemos incluir el plugin en nuestra página.
Luego se hace la instancia desde el formulario de la siguiente forma:
</p>

<code>
    $("#form_page").overlooker();
</code>

<p>De esta forma conseguiremos por defecto una validación por defecto para campos vacíos cada vez que se ejecute el evento change.</p>

<p>
Para designar una validación específica para cada campo en nuestro formulario se debe cargar un array de objetos que llevan 
las validaciones para cada uno de los campos, para hacer esto posible se escribe de la siguiente manera:
</p>

<code>
$("#form_page").overlooker({<br>
    validations:[<br>
        {<br>
            id : "email",<br>
            expresion : "email",<br>
            evento : "change"<br>
        }<br>
})<br>
</code>

<p>Este array lleva un objeto que se compone del id del campo a validar, la expresion regular a ejecutar y el evento en el cual
debe ejecutar dicha validación.</p>

<hr>

<h3>Set de validaciones incuidas</h3>

<p>Este plugin cuenta con una cantidad de validaciones incluidas, que son las que se usan en la mayoría de aplicaciones web.
Si la validación no se encuentra dentro de este set también es posible añadir más según sea necesario.</p>

<h4>solo_letras</h4>
<code>
solo_letras : [<br> 
                {<br>
                  valor:/^[a-z A-Z]*$/,<br>
                  err_mens:"Este campo solo permite letras mayúsculas o minúsculas."<br>
                }<br>
              ]<br>
</code>

<h4>solo_numeros</h4>
<code>
solo_numeros : [<br> 
                  {<br>
                    valor:/^[\d]*$/,<br>
                    err_mens:"Este campo solo permite números."<br>
                  }<br>
                ]<br>              
</code>

<h4>no_vacio</h4>
<code>
no_vacio : [<br> 
              {<br>
                valor:/^[^]+$/,<br>
                err_mens:"Este campo no puede ser vacío."<br>
              }<br>
            ]<br>
</code>

<h4>telefono</h4>
<code>
telefono : [<br> 
              {<br>
                valor:/^\d{5,15}$/,<br>
                err_mens:"Este campo no es un número de teléfono válido.[Solo números 5 a 15 caractéres.]"<br>
              }<br>
            ]<br>
</code>


<h4>doc_identidad</h4>
<code>
doc_identidad : [<br> 
                  {<br>
                    valor:/^\d{6,12}$/,<br>
                    err_mens:"Este campo no es un número de identidad válido.[Solo números 6 a 12 caractéres.]"<br>
                  }<br>
                ]<br>
</code>

<h4>email</h4>
<code>
email : [<br> 
          {<br>
            valor:/([a-zA-Z0-9_\.\-])+\@(([a-zA-Z0-9\-])+\.)+([a-zA-Z0-9]{2,4})/,<br>
            err_mens:"La dirección de correo no es válida."<br>
          }<br>
        ]<br>              
</code>

<hr>

<h3>Añadiendo nuevas validaciones</h3>

<p>Para añadir nuevas validaciones se debe agregar el objeto de validación en las opciones y hacer referencia al mismo por medio
del array validations.</p>
<code>
$("#form_page").overlooker({<br>
    solo_3numeros:[<br> 
              {<br>
                valor:/[0-9]{1,3}/,<br>
                err_mens:"El número que ingresó no es válido.[Solo números de máximo 3 dígitos.]"<br>
              }<br>
            ],<br>
    validations:[<br>
        {<br>
            id : "numero",<br>
            expresion : "solo_3numeros",<br>
            evento : "change"<br>
        }<br>
})<br>
</code>