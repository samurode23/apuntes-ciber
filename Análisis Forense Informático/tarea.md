1.Definir con “export” una variable para la ubicación de los plugins
Primero, vamos a colocarnos en /images/lab03
cd /images/lab03

1.1. Variable para los plugins
export VOL_PLUGINS=/images/lab03

1.2. Variable para el perfil
export VOL_PROFILE=LinuxRtkCentOSx64

1.2. Variable para la memoria
export VOL_MEM=/images/lab03/rootkit-memory.lime

Para verificar que todo esté bien, ejecutamos lo siguiente:
echo $VOL_PLUGINS
echo $VOL_PROFILE
echo $VOL_MEM