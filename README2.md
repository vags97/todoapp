# Auxiliar 1 Ingenería de Software
Git es un software que permite hacer control de versiones de nuestros proyectos. 
En esta actividad vamos a aprender conceptos de control de versiones con GIT, simulando un flujo de trabajo de desarrollo de software (simplificado). 

Esta es una app simple hecha en Django sacada de https://github.com/CITGuru/todoapp. 
La app es una TODO list donde pueden guardar las tareas que necesitan hacer. Al final de la actividad podrán asignarles una categoría y una fecha de término a cada tarea. 

## Actividad 

### [Paso 1: Fork del proyecto]
Hoy trabajarán todxs sobre el mismo código base, pero deberán hacer una copia de este código en su repositorio personal, para que los cambios no afecten a otras parejas. 

Para esto **una persona** de la pareja debería hacer un "fork" de este repositorio. 
En github deben hacer click arriba a la derecha donde dice Fork y seguir las instrucciones. 
![alt text](github-fork.png "Repo base")

Al hacer Fork deberían tener un repo como el de la imagen y en vez de llamarse _flouMicaza/todoapp_ debería decir _nombreusuario/todoapp_.

Desde ahora los cambios que hagan en el nuevo repositorio no afectarán el repositorio de sus compañerxs ni el repositorio original.

### [Paso 2: Clonar el proyecto] 
Desde ahora en adelante la persona que hizo el Fork será _"Persona A"_ y la otra persona de la pareja será _"Persona B_.
Para poder trabajar cada unx deberá clonar el proyecto en su computador siguiente los siguientes pasos: 
1. Copiar el enlace del repositorio donde dice "Clone or download" ![Clone or download](clone-dowload.png)
2. Clonar el repositorio en la consola de git:  `git clone https://repolink` 

### [Paso 3: Editar el proyecto]
En este paso cada integrante del grupo hará un cambio en el proyecto, que no afectará el trabajo del otro y luego ambos descargarán los cambios. 
1. __Persona A__ editará el archivo __views.py__ de la carpeta __todolist__ agregando el siguiente código: 

    `Código a agregar en views.`

2. __Persona A__ actualizará el repositorio remoto. Desde la consola de git se deberá hacer push de los cambios que se hicieron. Los pasos para hacer push a un repositorio son los siguientes (deben estar dentro de la carpeta todoapp para que git funcione): 
    + `git status` para ver qué cambios se hicieron.
    + `git add nombre-archivo` para agregar un archivo al commit. En este caso el archivo será todolist/views.py 
    + `git commit -m "descripción del cambio que se hizo" ` para hacer commit de los cambios. 
    + `git push` para subir los cambios al repositorio remoto.  
    
3. __Persona B__ editará el archivo __index.html__ de la carpeta __todolist/templates__ agregando el siguiente código: 
    `Código a agregar en index.html`
    
4.     