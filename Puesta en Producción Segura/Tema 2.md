git branch [nombre] (crea un hijo con el nombre que hayamos puesto)
git checkout [nombre] (selecciona una rama creada anteriormente)
git checkout -b [nombre] (crea una rama y la seleccionamos)
git checkout -f [nombre] (mueve la rama)
git commit (crea un nuevo hijo de la rama anteriormente seleccionada con checkout)
git merge [nombre] (crea un nuevo hijo de la rama seleccionada con checkout anteriormente y la rama del nombre que le hemos pasado)
git rebase [nombre] (en la rama del nombre, creas un hijo del seleccionmado anteriormente)
^ es para ir atrás
git checkout HEAD~3 (para ir 3 niveles atrás el HEAD)
