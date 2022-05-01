# training_gcp_cloud_engineer_associate

# Table of Contents
- [training_gcp_cloud_engineer_associate](#training_gcp_cloud_engineer_associate)
- [Table of Contents](#table-of-contents)
- [1 - Google Cloud Regions and Zones](#1---google-cloud-regions-and-zones)
  - [Regions and Zones](#regions-and-zones)
- [2 - Google Compute Engine](#2---google-compute-engine)
  - [Features](#features)
  - [Family](#family)
    - [Example](#example)
  - [Image](#image)
  - [Internal and External IP](#internal-and-external-ip)
    - [Static IP](#static-ip)
  - [Startup Scripts](#startup-scripts)
  - [Instance Template](#instance-template)
  - [Custom image](#custom-image)
- [3 - Optimizing Costs and Perfomance](#3---optimizing-costs-and-perfomance)
  - [Sustained use discounts](#sustained-use-discounts)
  - [Committed use discounts](#committed-use-discounts)
  - [Preemptible VM](#preemptible-vm)
  - [Google Compute Engine - Billing](#google-compute-engine---billing)
  - [Compute Engine: Live Migration & Availability Policy](#compute-engine-live-migration--availability-policy)
  - [Custom Machine Types](#custom-machine-types)
  - [GPUs](#gpus)
  - [Virtual Machine - Remember](#virtual-machine---remember)
  - [Virtual Machine - Best Practices](#virtual-machine---best-practices)
  - [Scenarios](#scenarios)
- [4 - Gcloud](#4---gcloud)



# 1 - Google Cloud Regions and Zones
## Regions and Zones
Los recursos de Compute Engine se alojan en varias ubicaciones en todo el mundo. Estas ubicaciones se componen de `regions` y `zones`. Una `region` es una ubicación geográfica específica donde puedes alojar recursos. Las `regions` se dividen en tres o más `zones`. Por ejemplo, la región `us-west1` corresponde a una región en la costa oeste de Estados Unidos que tiene tres zonas: `us-west1-a`, `us-west1-b` y `us-west1-c`.

Algunos recursos como las `instances` o los `Persistent Disk` son recursos de `zone`. Otros como las `IP estáticas` son `regionals`. Los recursos `regionals` pueden ser usados por cualquier recurso de esa región.

Solo ciertos recursos son específicos de una región o zona. Otros recursos como las `images` son globales.

Compute Engine implementa una capa de abstracción entre las zonas y los clústeres físicos donde se alojan las zonas. Un clúster representa una infraestructura física distinta que se aloja en un centro de datos. Cada zona está alojada en uno o más clústeres y Compute Engine asigna de forma independiente las zonas a los clústeres de cada organización. Por ejemplo, es posible que la `us-central1-a` zona de su organización no se asigne al mismo clúster que la `us-central1-a` zona de otra organización.

El cliente elige la `region` o `zones` donde aloja sus recursos, elegir una `zone` y `region` es importante por varios motivos:
* __Handling failures__ (manejo de fallas): distribuya sus recruso en varias zonas y regiones para tolerar fallos
* __Decreased network latency__ (latencia de red reducida): Para disminuir la latencia de red es posible que desee elegir una region o zona que esté más cera de su punto de servicio.

* __Regions__: Las regiones son colecciones de zonas.
* __Zones__: Es un área de despliegue dentro de una región.

Ciertos recursos como `Images`, `Elastics IP`, `firewall rules` y `VPC networks`, __tienen límites de `Quota definidos para todo el proyecto y límites de quota por region__. Si supera alguno de los límites de quota afectados, no podrá agregar más recursos del mismo tipo en ese proyecto o region.

* [Regions-zones](https://cloud.google.com/compute/docs/regions-zones)
* [Global/Regional/Zonal Resources](https://cloud.google.com/compute/docs/regions-zones/global-regional-zonal-resources)
* [Virtualization](https://cloud.google.com/compute/docs/regions-zones/zone-virtualization)

# 2 - Google Compute Engine
## Features
* Creación y manejo del ciclo de vida de las `VM instances`
* `Load balancing` y `auto scaling` para múltiples `VM instances`
* Añadir `storage` (& `network storage`) para las `VM instances`
* Manejo de `network connectivity` y `configuration` para las `VM instances`

* [General Instances](https://cloud.google.com/compute/docs/instances)

## Family
Existen diferentes tipos de familas para distintos Workloads.
* General Purpose (E2, N2 N2D, N1):
  * Para la mayoría de Workloads.
  * Web and applications servers, Small-medium databases, Dev environments
* Memory Optimized (M2, M1):
  * Ultra high memory workloads
  * Large in-memory databases and in-memory analytics
* Compute Optimized (C2): 
  * Compute intensive Workload
  * Gaming applications

### Example
* e2-standard-2:
  * e2: Machine Type Family
  * standar - Type of workload
  * 2 - Number of CPUs

A la par que se elige una máquina superior, las capabilities de Memory, Disk y Netwoking van incrementando.
* [Family](https://cloud.google.com/compute/docs/machine-types)

## Image
Image type:
* `Public Images`: Provided & maintained by Google or Open Source communities or third party vendors
* `Custom Images`: Imágenes custom creadas por usted

## Internal and External IP
### Static IP
* Las Static IPs pueden ser intercambiadas entre VM instances
* Permanecen adjuntas aunque reinicimos la VM instance
* Se factura aunque no esté en uso

* [IP Address](https://cloud.google.com/compute/docs/ip-addresses?hl=en)

## Startup Scripts
* [Startup Scripts](https://cloud.google.com/compute/docs/instances/startup-scripts/linux?hl=es-419)

## Instance Template
Permite definir: 
* tipo de máquina
* Imagen
* Etiquetas
* Scripts
* ...

Una vez creada una plantilla, no puede cambiarla, puede hacer una copia de la plantilla, cambiarla y crear una nueva.

Otra caracteristica es que puede especificar una Image family (debia-9)

No hay costo asociado a la creación de plantillas, pero si por la creación de VM instances.

* [Instance Template](https://cloud.google.com/compute/docs/instance-templates?hl=es_419)

## Custom image
Cuando instalamos paquetes en una instancia limpia, puede demorarse mucho el tiempo de inicio.
Podemos creaer una imagen custom con todos las actualizaciones y el software pre-instalado y crear una Instance Template con la imagen Custom a partir de un disco

Una imagen custom puede ser compartida con otros proyectos.
Una de las ventajas de crear una Custom Image es garantizar que todos los estandares de seguridad se cumplan.

# 3 - Optimizing Costs and Perfomance
## Sustained use discounts
* Automatic discounts para VM instances. Si está utilizando familias N1 o N2 con más de un uso del 25% del mes puedes obtener un 20% to 50% de descuento en cada minuto incremental
* Se aplica cuando se lanzan instancias en GCE o en GKE
* No se aplica a todas las máquinas, por ejemplo E2 y A2.
* Si está utilizando APP Enginx flexible o Dataflow para crear las VMs no se aplican los descuentos.

* [Sustains Discounts](https://cloud.google.com/compute/docs/sustained-use-discounts)

## Committed use discounts
* Utilizados para cargas de trabajo predecibles
* Puede decir que necesitará una máquina 1 año o 3 años
* Dependiendo el tipo de máquia y la GPUs que utilce puede obtener hasta un 70% de descuento.
* Aplicable por GCE y GKE
* No aplicable para App Engine Flexible y Dataflow
* [Comitted Discounts](https://cloud.google.com/compute/docs/instances/signing-up-committed-use-discounts?hl=es_419#:~:text=When%20you%20purchase%20a%20committed,like%20machine%20types%20or%20GPUs.)

## Preemptible VM
* VM más baratas y de corta duración
* El tiempo máximo que puede ejecutar estas instancias es de 24h
* GCP puede acabar con la instancia en cualquier momento dentro del periodo de 24h. (Recibirá una advertencía de 30s)
* Utilizalas cuando tu app sea __fault tolerant__
* __Cost sensitive__
* Your workload is __NOT inmmediate__
* Es posible que no siempre estén disponibles
* No tienen SLA y no pueden ser migradas a regular VM.
* No pueden ser reiniciadas automáticamente.
* No es aplicable al Free Tier Credits.

* [Preemptible VM](https://cloud.google.com/compute/docs/instances/preemptible)


## Google Compute Engine - Billing
* Se le factura por segundo a partir del primer minuto.
* Si para una VM no se le cobrará por el recurso, pero si por el almacenamiento.
* Recomendación: creeate Budgets alerts

* [Budgets](https://cloud.google.com/billing/docs/how-to/budgets)

## Compute Engine: Live Migration & Availability Policy
Cuando GCP necesita realizar alguna actualizción de hardware o software donde corre su VM, tienen una función llamada Live Migration, que permite la migración a otro Host en la misma zona, includas las que hacen uso de SSDs.
No es compatible con las VM que hacen uso de GPU.

Esto se configura en la Availability Policy, y puede configurar dos cosas importantes:
* Durante el mantenimiento de un host:
  * Por defecto se migra
  * Terminate
* Reinicio automático

* [Availability Policies](https://cloud.google.com/compute/docs/instances/setting-instance-scheduling-options?hl=es_419)

## Custom Machine Types
* Puede crear MAchine Type personalizadas
* Puede ajustar CPUs, memory and GPUs
  * Solo disponible para algunos tipos demáquinas como E2, N2 o N1
  * Variedad de OS
  * Se facturará por CPU y Memoria provisionada

* [Custom Machine Type](https://cloud.google.com/compute/docs/instances/creating-instance-with-custom-machine-type)

## GPUs
Para AI/ML
* Alto rendimiento para intensive workloads
* Coste Elevado
* utiliza imagenes con GPU Libraries
* No es compatible con todos los tipos de máquinas, por ejemplo no es adminitada en máquinas con shared-core or memory-optimized
* En las Availability Policies, On host maintenance, solo puede tener "Terminate VM instance"
* Automatic restart On

## Virtual Machine - Remember
* Associate with a project
* La disponibilidad de tipos de máquinas puede variar entre regiones.
* Puede cambiar el tipo de instance o ajustar CPU y Memory una vez detenida.
* Puede filtrar sus máquinas virtuales por propiedades o labels
* Son Zonales, se ejecutan en una específica zona de una región
* Las imágenes son globales
* Las Instances Templates son globales
* Automatic Basic Monitoring is enabled
  * CPÛ, Network, Disc
  * For memory and Disk Space, Cloud Monitoring agent is needed

## Virtual Machine - Best Practices
* Elija la Zone and Region en base a:
  * Cost, Regulations, Availability needs, Latency and Specific Hardwared needs
* Elija el tipo de máquinas que necesite
* Haga reservas de "commited use discounts" para workloads constantes
* Use preemptible instances for fault-toleratn, NON time critical workloads
* Utiliza labels

## Scenarios

* Prerequisitos para crear una VM
  * Project
  * Billing Account
  * Compute Engines APIs enabled
* Hardwared dedicado
  * Sole-tenants nodes
* Parcheo de miles de máquinas
  * VM Manager
* Logging to your VM
  * Shh into it
* you do not want to expones a VM to internet
  * Do not assing an external IP
* You want allow _HTTP trafffic to your VM
  * configure Firewall Rules

# 4 - Gcloud
