#1 Ejecutar en visual studio, ya que este crea el contendor.
#2 Para funcionar necesita tener la compatibilidad con contenedores docker y visual studio.
#3 En caso no contar con ella:
#4 Ir a herramientas -> Adminstrador de paquetes NuGuet-> Consola de paquetes -> Ejecute el siguiente comando.
NuGet\Install-Package Microsoft.VisualStudio.Azure.Containers.Tools.Targets -Version 1.20.1
#5 Una vez creado el contendor podra utilizarlo, para hacer peticiones ya sea desde visual studio.
#6 ver contendor para accedr a el.
docker ps
#7 para hacerlo desde consola es necesario entrar como root.
docker exec -u 0 -it ID_Contendor /bin/bash
docker exec -u 0 -it f042557086c3 /bin/bash
#8 Descargar curl
apt-get update
apt-get install curl
#9 petición.
curl https://localhost:8081/api/Carreras.
#10 Si da problemas con los certificados, ejecutar el siguiente comando:
curl -k https://localhost:8081/api/Carreras.
