#Ejecutar en visual studio, ya que este crea el contendor.
#Para funcionar necesita tener la compatibilidad con contenedores docker y visual studio.
#En caso no contar con ella:
#Ir a herramientas -> Adminstrador de paquetes NuGuet-> Consola de paquetes -> Ejecute el siguiente comando.
NuGet\Install-Package Microsoft.VisualStudio.Azure.Containers.Tools.Targets -Version 1.20.1
#Una vez creado el contendor podra utilizarlo, para hacer peticiones ya sea desde visual studio.
#ver contendor para accedr a el.
docker ps
#para hacerlo desde consola es necesario entrar como root.
docker exec -u 0 -it ID_Contendor /bin/bash
docker exec -u 0 -it f042557086c3 /bin/bash
#Descargar curl
apt-get update
apt-get install curl
#petición.
curl https://localhost:8081/api/Carreras.
#Si da problemas con los certificados, ejecutar el siguiente comando:
curl -k https://localhost:8081/api/Carreras.
