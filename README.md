# Auxiliar 1 Ingenería de Software
Git es un software que permite hacer control de versiones de nuestros proyectos. 
En esta actividad vamos a aprender conceptos de control de versiones con Git, simulando un flujo de trabajo de desarrollo de software (simplificado). 

Esta es una app simple hecha en Django sacada de https://Github.com/CITGuru/todoapp. 
La app es una TODO list donde pueden agregar tareas, ponerles categoría y fecha de término. 
La versión de este repositorio no tiene la opción de eliminar una tarea, por lo tanto trabajarán en parejas para agregar esta funcionalidad. 
![App antes de la actividad](app-sin-eliminar.png)
## Actividad 

### [Parte 1: Fork del proyecto]
Hoy trabajarán todxs sobre el mismo código base, pero deberán hacer una copia de este código en su repositorio personal, para que los cambios no afecten a otras parejas. 

Para esto **UNA persona** de la pareja debería hacer un "fork" de este repositorio. 
En Github deben hacer click arriba a la derecha donde dice Fork y seguir las instrucciones. 
![alt text](github-fork.png "Repo base")

Al hacer Fork deberían tener un repo como el de la imagen y en vez de llamarse _flouMicaza/todoapp_ debería decir _nombreusuario/todoapp_.

Desde ahora los cambios que hagan en el nuevo repositorio no afectarán el repositorio de sus compañerxs ni el repositorio original.

### [Parte 2: Clonar el proyecto] 
Desde ahora en adelante la persona que hizo el Fork será _"Persona A"_ y la otra persona de la pareja será _"Persona B_.
Para poder trabajar, cada unx deberá clonar el proyecto en su computador siguiente los siguientes pasos: 
1. Copiar el enlace del repositorio donde dice "Clone or download" ![Clone or download](clone-dowload.png)
2. Clonar el repositorio en la consola de Git:  `git clone https://url...` 

> La versión del proyecto que encontramos en github se llama repositorio __remoto__ y la versión que está en nuestro computador se llamará local. 

### [Parte 3: Editar el proyecto]
En este paso cada integrante del grupo hará un cambio en el proyecto, que no afectará el trabajo del otro y luego ambos descargarán los cambios. 
1. __Persona A__ editará el archivo __views.py__ de la carpeta __todolist__ agregando el siguiente código donde está indicado: 

    ```python
        if "taskDelete" in request.POST: #checking if there is a request to delete a todo
            checkedlist = request.POST["checkedbox"] #checked todos to be deleted
            for todo_id in checkedlist:
                todo = TodoList.objects.get(id=int(todo_id)) #getting todo id
                todo.delete() #deleting todo

   ```

2. __Persona A__ actualizará el repositorio remoto. Desde la consola de Git se deberá hacer push de los cambios que se hicieron. Los pasos para hacer push a un repositorio son los siguientes (deben estar dentro de la carpeta todoapp para que Git funcione): 
    + `git status` para ver qué cambios se hicieron.
    + `git add nombre-archivo` para agregar un archivo al commit. En este caso el archivo será todolist/views.py 
    + `git commit -m "descripción del cambio que se hizo" ` para hacer commit de los cambios. 
    + `git push` para subir los cambios al repositorio remoto.  
    
3. __Persona B__ editará el archivo __index.html__ de la carpeta __todolist/templates__ agregando el siguiente código: 
   ```html
       <button class="taskDelete" name="taskDelete" formnovalidate="" type="submit" onclick="$('input#sublist').click();"><i class="fa fa-trash-o icon"></i>Delete Tasks</button>
   ```
    
4. __Persona B__ actualizará el repositorio remoto según las instrucciones del paso 2. Al hacer `git push` probablemente verás el siguiente error: 
![Error al hacer push](failed-to-push.png)

    Esto pasa porque __Persona A__ hizo cambios en un archivo y __Persona B__ no ha descargado estos cambios.
                                                                                                                                                                                                   
    Para arreglar esto __Persona B__ deberá descargar los cambios haciendo `git pull` .  Al hacer pull se tendrá que juntar (_merge_) la versión del repositorio con la versión local, es por esto que te aparecerá un editor con un mensaje parecido a este: 
    ![Git Merge](merge-nano.png)
    
    Se debe salir de ahí siguiendo las instrucciones de la consola y __Persona B__ ya tendrá los cambios remotos en su computador. 
    __Persona B__ deberá hacer `git push` denuevo para que sus cambios queden en el repositorio remoto. 
    
5. __Persona A__ hace `git pull` en la consola de Git y podrá ver los cambios hechos por __Persona B__ sin problemas. 

>Generalmente para evitar tener problemas al hacer push de los cambios, se recomienda hacer `git pull` antes de hacer los pasos del punto 2.
Así te aseguras de arreglar cualquier error que pueda producirse entre el código remoto y tus cambios locales antes de crear el commit. 

### [Parte 4: Editar el mismo archivo]
Al final del README están las instrucciones de cómo correr la app en local. Ambas personas deberán seguir estos pasos y asegurarse que la app funciona. 
Hasta ahora tenemos una TODO list en la que podemos agregar y eliminar tareas. 

¿Qué pasa si ahora __Persona B__ quiere quitarle el subtítulo que dice "A DJANGO TODO APP" y __Persona A__ decide modificar el subtítulo sin avisar? 

1. __Persona B__ quitará el subtítulo que aparece en la app eliminando la siguiente línea del archivo __index.html__ de la carpeta __todolist/templates__: 
   ```html
      <p class="tagline">a Django todo app</p>
   ```
2. __Persona B__ actualizará el repositorio remoto según las instrucciones del punto 2, Parte 3. 

3. __Persona A__ (_SIN DESCARGAR LOS CAMBIOS DE LA OTRA PERSONA_) editará la siguiente linea del archivo __index.html__ de la carpeta __todolist/templates__: 
    ```html
      <p class="tagline">a Django todo app</p>
   ``` 
   modificando donde dice "a Django todo app" por otro texto. 

4. __Persona A__ actualizará el repositorio remoto según las instrucciones del punto 2, Parte 3. 
Al hacer `git push ` __Persona A__ verá que hay un conflicto como pasó en la parte anterior. 

    Para resolver esto se debe hacer `git pull` y aparecerá este mensaje: 
    ![Merge fallido](merge-failed.png) 

    Esto pasa cuando dos personas editan en mismo archivo del proyecto. Muchas veces Git puede solucionar estos conflictos automáticamente, pero otras veces la persona que desarrolla tendrá que decidir cuál será el código definitivo. 

5. __Persona A__ verá que su archivo __index.html__ está modificado y le agregaron algunas líneas: 
    
    Lo primero que se ve es  
    ```html 
       <<<<<<< HEAD 
            <codigo local>
        >>>>>>>> 
   ```
   HEAD representa la punta de la rama en la que se está trabajando. En este caso como ya se creó el commit, HEAD será la versión del código que __Persona A__ editó recién. El código que aparecerá en esta parte será, entonces, la versión del código __en conflicto__ de la rama local. 
   
   Luego veremos lo siguiente: 
   ```html 
        <codigo remoto>
   >>>>>>> 17ed5a8a2f2b44e4daf2302d63f6a6b8163xxxxx
   ```
   Por lo tanto el código que aparecerá ahí será la versión del código de la rama remota. En este caso sería el código que subió __Persona B__.
   El número largo que aparecerá es el identificador del último commit remoto. 
   
   > Git hace esto para mostrarnos las dos versiones del código y que la persona que esté desarrollando pueda decidir cuál será la versión definitiva. 
   Hay que tener cuidado al hacer este procedimiento porque podríamos eliminar trabajo de otras personas. 
   
6. __Persona A__ decidirá que quiere dejar su versión y no la de su pareja, por lo que eliminará todo el código que Git agregó incluyendo los símbolos <, HEAD e identificadores de commit. 
Viendo los códigos del punto 5 debería quedar solo `<codigo local>`. 
  
7. Finalmente __Persona A__ deberá subir el resultado del merge. Para eso se debe: 
    + Volver a agregar los archivos modificados durante el merge haciendo `git add todolist/templates/index.html` 
    + `git commit` para hacer commit del merge. Aquí no es necesario poner -m y un mensaje porque se está haciendo merge. 
    + `git push` para terminar de subir los cambios locales y el arreglo de los conflictos. 
    
Si revisan los commits en github verán que se crearon dos commits. Un commit por hacer merge de la rama remota y la local y otro commit que representa los cambios que hizo __Persona A__. 
> Lo bueno de esto que es que si hay problemas al momento de resolver los conflictos, se podrá volver a una versión anterior del código. 

