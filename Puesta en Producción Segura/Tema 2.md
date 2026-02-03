git branch [nombre] (crea un hijo con el nombre que hayamos puesto)
git checkout [nombre] (selecciona una rama creada anteriormente)
git checkout -b [nombre] (crea una rama y la seleccionamos)
git checkout -f [nombre] (mueve la rama)
git commit (crea un nuevo hijo de la rama anteriormente seleccionada con checkout)
git merge [nombre] (crea un nuevo hijo de la rama seleccionada con checkout anteriormente y la rama del nombre que le hemos pasado)
git rebase [nombre] (en la rama del nombre, creas un hijo del seleccionmado anteriormente)
git checkout C6
git branch -f main
git checkout HEAD~3
git branch -f bugFix C0
git reset HEAD^ (vuelve la rama seleccionada a lo anterior y elimina el commit en el que esábamos)
git revert C2 (creas un nuevo commit de algo anterior pero no elimina en el que estás)
git cherry-pick commit1 commit2 ... (copia commit1 y commit 2 y lo pega donde estes como hijos)
git rebase -i HEAD~4 (reordenadas y lo pones como quieras)
