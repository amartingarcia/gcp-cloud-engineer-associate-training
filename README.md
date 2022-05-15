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
  - [Gcloud example commands](#gcloud-example-commands)
  - [Syntax](#syntax)
- [5 - Instance Groups](#5---instance-groups)
  - [Updating](#updating)
  - [Instance Group Scenarios](#instance-group-scenarios)
  - [Some commands](#some-commands)
- [6 - Load Balancing](#6---load-balancing)
  - [Terminology](#terminology)
  - [Features](#features-1)
- [7 - App Engine](#7---app-engine)
  - [Compute Engine vs App Engine](#compute-engine-vs-app-engine)
  - [App Engine Environments](#app-engine-environments)
  - [Hierarchy](#hierarchy)
  - [Standard vs flexible](#standard-vs-flexible)
  - [Scaling instances](#scaling-instances)
  - [Request routing](#request-routing)
  - [Deploying new versions without downtime](#deploying-new-versions-without-downtime)
  - [Split traffic between multiple versoins?](#split-traffic-between-multiple-versoins)
  - [Commands](#commands)
    - [Instances](#instances)
    - [Services and versions](#services-and-versions)
  - [Cronjobs](#cronjobs)
  - [Others files](#others-files)
  - [Remember](#remember)
- [8 - Cloud Run](#8---cloud-run)
- [9 - Block and File Storage](#9---block-and-file-storage)
  - [Block Storage](#block-storage)
  - [File Storage](#file-storage)
  - [Types](#types)
  - [Local SSDs](#local-ssds)
  - [Persistent Disk](#persistent-disk)
  - [PD vs SSDs](#pd-vs-ssds)
  - [PD - Standard vs Balanced vs SSD](#pd---standard-vs-balanced-vs-ssd)
  - [PD Snaphots](#pd-snaphots)
    - [Recommendations](#recommendations)
  - [Compares](#compares)
  - [Command line](#command-line)
    - [Disks](#disks)
    - [Images](#images)
  - [Filestore](#filestore)
  - [Review](#review)



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
* Command line interface to interact with Google Cloud Resources
* Most GCP services can be managed from CLI using Gcloud:
  * GCE
  * GKE
  * Databases
  * etc
* You can create/delete/update/read existing resources and perform actions like deployemnts as well
* SOME GCP services have specific CLI Tools:
* Cloud Storage - gsutil
* Cloud Big Query - bq
* Cloud Bigtable - cbt
* Kubernetes - kubectl

## Gcloud example commands
```sh
# gcloud config list project
[core]
project = centering-aegis-348716

Your active configuration is: [default]

# gcloud config configurations list
NAME     IS_ACTIVE  ACCOUNT                        PROJECT                 COMPUTE_DEFAULT_ZONE  COMPUTE_DEFAULT_REGION
default  True       adrian.cloud.test.2@gmail.com  centering-aegis-348716  europe-west4-a        europe-west4

# gcloud config configurations activate default
Activated [default].

# gcloud config list
[compute]
region = europe-west4
zone = europe-west4-a
[core]
account = adrian.cloud.test.2@gmail.com
disable_usage_reporting = False
project = centering-aegis-348716

Your active configuration is: [default]

# gcloud config configurations describe default
is_active: true
name: default
properties:
  compute:
    region: europe-west4
    zone: europe-west4-a
  core:
    account: adrian.cloud.test.2@gmail.com
    project: centering-aegis-348716

# gcloud compute instances list
Listed 0 items.

# gcloud compute instances create my-first-instance-from-gcloud
Created [https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/europe-west4-a/instances/my-first-instance-from-gcloud].
NAME                           ZONE            MACHINE_TYPE   PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP    STATUS
my-first-instance-from-gcloud  europe-west4-a  n1-standard-1               10.164.0.2   34.147.92.235  RUNNING

# gcloud compute instances describe my-first-instance-from-gcloud
canIpForward: false
cpuPlatform: Intel Skylake
creationTimestamp: '2022-05-03T11:37:18.872-07:00'
deletionProtection: false
disks:
- autoDelete: true
  boot: true
  deviceName: persistent-disk-0
  diskSizeGb: '10'
  guestOsFeatures:
  - type: UEFI_COMPATIBLE
  - type: VIRTIO_SCSI_MULTIQUEUE
  - type: GVNIC
  index: 0
  interface: SCSI
  kind: compute#attachedDisk
  licenses:
  - https://www.googleapis.com/compute/v1/projects/debian-cloud/global/licenses/debian-11-bullseye
  mode: READ_WRITE
  source: https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/europe-west4-a/disks/my-first-instance-from-gcloud
  type: PERSISTENT
fingerprint: ni9zVBsQDBI=
id: '5128937407023728818'
kind: compute#instance
labelFingerprint: 42WmSpB8rSM=
lastStartTimestamp: '2022-05-03T11:37:24.595-07:00'
machineType: https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/europe-west4-a/machineTypes/n1-standard-1
metadata:
  fingerprint: SSsPC5hcgKU=
  kind: compute#metadata
name: my-first-instance-from-gcloud
networkInterfaces:
- accessConfigs:
  - kind: compute#accessConfig
    name: external-nat
    natIP: 34.147.92.235
    networkTier: PREMIUM
    type: ONE_TO_ONE_NAT
  fingerprint: 4exhl26iz-o=
  kind: compute#networkInterface
  name: nic0
  network: https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/global/networks/default
  networkIP: 10.164.0.2
  stackType: IPV4_ONLY
  subnetwork: https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/regions/europe-west4/subnetworks/default
scheduling:
  automaticRestart: true
  onHostMaintenance: MIGRATE
  preemptible: false
  provisioningModel: STANDARD
selfLink: https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/europe-west4-a/instances/my-first-instance-from-gcloud
serviceAccounts:
- email: 431680528914-compute@developer.gserviceaccount.com
  scopes:
  - https://www.googleapis.com/auth/devstorage.read_only
  - https://www.googleapis.com/auth/logging.write
  - https://www.googleapis.com/auth/monitoring.write
  - https://www.googleapis.com/auth/pubsub
  - https://www.googleapis.com/auth/service.management.readonly
  - https://www.googleapis.com/auth/servicecontrol
  - https://www.googleapis.com/auth/trace.append
shieldedInstanceConfig:
  enableIntegrityMonitoring: true
  enableSecureBoot: false
  enableVtpm: true
shieldedInstanceIntegrityPolicy:
  updateAutoLearnPolicy: true
startRestricted: false
status: RUNNING
tags:
  fingerprint: 42WmSpB8rSM=
zone: https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/europe-west4-a

# gcloud compute instances delete my-first-instance-from-gcloud
The following instances will be deleted. Any attached disks configured to be auto-deleted will be deleted unless they are attached to any other instances or the `--keep-disks` flag is 
given and specifies them for keeping. Deleting a disk is irreversible and any data on the disk will be lost.
 - [my-first-instance-from-gcloud] in [europe-west4-a]

Do you want to continue (Y/n)?  Y

Deleted [https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/europe-west4-a/instances/my-first-instance-from-gcloud].

# gcloud compute zones list
NAME                       REGION                   STATUS  NEXT_MAINTENANCE  TURNDOWN_DATE
us-east1-b                 us-east1                 UP
us-east1-c                 us-east1                 UP
us-east1-d                 us-east1                 UP
us-east4-c                 us-east4                 UP
us-east4-b                 us-east4                 UP
us-east4-a                 us-east4                 UP
us-central1-c              us-central1              UP
us-central1-a              us-central1              UP
us-central1-f              us-central1              UP
us-central1-b              us-central1              UP
us-west1-b                 us-west1                 UP
us-west1-c                 us-west1                 UP
us-west1-a                 us-west1                 UP
europe-west4-a             europe-west4             UP
europe-west4-b             europe-west4             UP
europe-west4-c             europe-west4             UP
europe-west1-b             europe-west1             UP
...................................

# gcloud compute regions list
NAME                     CPUS  DISKS_GB  ADDRESSES  RESERVED_ADDRESSES  STATUS  TURNDOWN_DATE
asia-east1               0/8   0/2048    0/4        0/8                 UP
asia-east2               0/8   0/2048    0/4        0/8                 UP
asia-northeast1          0/8   0/2048    0/4        0/8                 UP
asia-northeast2          0/8   0/2048    0/4        0/8                 UP
asia-northeast3          0/8   0/2048    0/4        0/8                 UP
asia-south1              0/8   0/2048    0/4        0/8                 UP
asia-south2              0/8   0/2048    0/4        0/8                 UP
....................

# gcloud compute machine-types list
 
# gcloud compute machine-types list --filter zone:asia-southeast2-b
NAME            ZONE               CPUS  MEMORY_GB  DEPRECATED
e2-highcpu-16   asia-southeast2-b  16    16.00
e2-highcpu-2    asia-southeast2-b  2     2.00
e2-highcpu-32   asia-southeast2-b  32    32.00
e2-highcpu-4    asia-southeast2-b  4     4.00
e2-highcpu-8    asia-southeast2-b  8     8.00
e2-highmem-16   asia-southeast2-b  16    128.00
e2-highmem-2    asia-southeast2-b  2     16.00
e2-highmem-4    asia-southeast2-b  4     32.00
e2-highmem-8    asia-southeast2-b  8     64.00
e2-medium       asia-southeast2-b  2     4.00
e2-micro        asia-southeast2-b  2     1.00
e2-small        asia-southeast2-b  2     2.00
e2-standard-16  asia-southeast2-b  16    64.00
e2-standard-2   asia-southeast2-b  2     8.00
e2-standard-32  asia-southeast2-b  32    128.00
e2-standard-4   asia-southeast2-b  4     16.00
e2-standard-8   asia-southeast2-b  8     32.00
..............

# gcloud compute machine-types list --filter "zone:(asia-southeast2-b asia-southeast2-c)"
# gcloud compute zones list --filter=region:us-west2
NAME        REGION    STATUS  NEXT_MAINTENANCE  TURNDOWN_DATE
us-west2-a  us-west2  UP
us-west2-b  us-west2  UP
us-west2-c  us-west2  UP

# gcloud compute zones list --sort-by=region
# gcloud compute zones list --sort-by=~region
# gcloud compute zones list --uri
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-east1-b
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-east1-c
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-east1-d
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-east4-c
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-east4-b
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-east4-a
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-central1-c
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-central1-a
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-central1-f
https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/us-central1-b
...

# gcloud compute regions describe us-west4
creationTimestamp: '1969-12-31T16:00:00.000-08:00'
description: us-west4
id: '1430'
kind: compute#region
name: us-west4
quotas:
- limit: 8.0
  metric: CPUS
  usage: 0.0
- limit: 2048.0
  metric: DISKS_TOTAL_GB
  usage: 0.0
- limit: 8.0
  metric: STATIC_ADDRESSES
  usage: 0.0
- limit: 4.0
...

# gcloud compute instance-templates list
Listed 0 items.

# gcloud compute instance-templates create instance-template-from-command-line
Created [https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/global/instanceTemplates/instance-template-from-command-line].
NAME                                 MACHINE_TYPE   PREEMPTIBLE  CREATION_TIMESTAMP
instance-template-from-command-line  n1-standard-1               2022-05-03T11:44:40.740-07:00

# gcloud compute instance-templates describe instance-template-from-command-line
creationTimestamp: '2022-05-03T11:44:40.740-07:00'
description: ''
id: '7160651478575400695'
kind: compute#instanceTemplate
name: instance-template-from-command-line
properties:
  canIpForward: false
  disks:
  - autoDelete: true
    boot: true
    deviceName: persistent-disk-0
    index: 0
    initializeParams:
      sourceImage: https://compute.googleapis.com/compute/v1/projects/debian-cloud/global/images/family/debian-11
    kind: compute#attachedDisk
...

# gcloud compute instance-templates delete instance-template-from-command-line
The following instance templates will be deleted:
 - [instance-template-from-command-line]

Do you want to continue (Y/n)?  Y

Deleted [https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/global/instanceTemplates/instance-template-from-command-line].
```

## Syntax
* gcloud GROUP SUBGROUP ACTION ...
  * GROUP - config or compute or container or iam or ...
    * Service Group
  * SUBGROUP - instances or images or machines-types or regions or zones ...
    * Subgroup
  * ACTION - Creat or list, or start or stop or describe ...

* Example:
  * gcloud compute instances list
  * gcloud compute zones list
  * gcloud compute regions list
  * ...

# 5 - Instance Groups
* Instance Group - Group of VM instances managed as a simple entity
  * Managed (MIG):
    * Created using a instance template
    * Features: 
      * Autoscaling
      * Autohealing
      * Managed releases (Rolling update or Canary) 
      * Add Load Balancer to distributed load
  * Unmanaged:
    * Does NOT offer Autoscaling, autohealing & other services
    * NOT Recommended unless you need different kinds of VMs
* Location can be Zonal or Regional
  * Regional gives you higher availability (RECOMMENDED)

* [Instance Group](https://cloud.google.com/compute/docs/instance-groups)
* [Instance Group Stateful/Stateless](https://cloud.google.com/compute/docs/instance-groups/stateful-migs?hl=es-419)
* [Instanee Group Unmanaged](https://cloud.google.com/compute/docs/instance-groups/creating-groups-of-unmanaged-instances?hl=es_419#:~:text=An%20unmanaged%20instance%20group%20is,individual%20configuration%20settings%20or%20tuning.)

## Updating
* Rolling update - Gradual update of instances in an instance group to the new instance template
  * Specify new template
  * Specify how you want the update to be done
* Rolling Restart/replace: Gradual restart or replace of all instances in the group
  * No change in template but replace/restart existing VMs
  * Configure Max surge, Max unavailable and What you want to do?

* [MaxSurge](https://cloud.google.com/compute/docs/instance-groups/rolling-out-updates-to-managed-instance-groups?_ga=2.102081153.-100830343.1651250286#max_surge)
* [MaxUnavailable](https://cloud.google.com/compute/docs/instance-groups/rolling-out-updates-to-managed-instance-groups?_ga=2.102081153.-100830343.1651250286#max_unavailable)

## Instance Group Scenarios
* You want MIG managed application to survive Zonal Failures
  * Create multiple zone MIG (or regional MIG)
* You want create VMs of different configurations in the same group
  * Create un-managed Instance Group
* You want to preserve VM state in an MIG
  * Stateful MIG - Preserve VM states (instance name, attached Disk and metadata). Recommended for stateful workloads (database, data processing group)
* You want high availability in an MIG even when there are hardware/software updates
  * Use an instance template with availability policy automatic restart: enabled & on-host maintenance: migrate. Ensure live migration and automatic restart.
* You want unhealthy instances to be automaticall y replaced
  * Configure health check on the MIG (self healing)
* Avoid frequent scale up & downs
  * Cool-down period/initial delay


## Some commands
```bash
gcloud compute instances create my-test-vm --source-instance-template=my-instance-template-with-custom-image
gcloud compute instance-groups managed list
gcloud compute instance-groups managed delete my-managed-instance-group
gcloud compute instance-groups managed create my-mig --zone us-central1-a --template my-instance-template-with-custom-image --size 1
gcloud compute instance-groups managed set-autoscaling my-mig --max-num-replicas=2 --zone us-central1-a
gcloud compute instance-groups managed stop-autoscaling my-mig --zone us-central1-a
gcloud compute instance-groups managed resize my-mig --size=1 --zone=us-central1-a
gcloud compute instance-groups managed recreate-instances my-mig --instances=my-mig-85fb --zone us-central1-a
gcloud compute instance-groups managed delete my-managed-instance-group --region=us-central1
```

# 6 - Load Balancing
* Distributes user traffic across instances of an application in single region or multiple regions
  * Fully distributed, software defined managed service
  * Important features:
    * Health check - Route to healthy instances
      * Recover from failures
    * AutoScaling
    * Global load balancing with single anycast IP
      * Also supports internal load balancing
* Enables:
  * HA
  * AutoScaling
  * Resiliency


* [Load Balancing Overview](https://cloud.google.com/load-balancing/docs/load-balancing-overview?hl=es)
* [Types](https://cloud.google.com/load-balancing/docs/choosing-load-balancer?hl=es_419#lb-summary)
* [Functions](https://cloud.google.com/load-balancing/docs/features?hl=es_419)

## Terminology
* Backend - Group of endpoints that receive traffic from a Google Cloud load balancer (AWS Target Group) (example: instnce groups)
* Frontend - Specify an Ip address, port and protocosl (AWS LB Listener). This IP address is the frontend IP for your clients requets
  * For SSL a certificate must also be assigned
* Host and path rules - (For HTTP(S) Load Balancing) - Define rules redirecting the traffic to different backends


* Client to load balancer: over internet
  * https recommended
* Load Balancer to VM instance: Through Google internal network
  * HTTP is ok. HTTPS is preferred
* SSL/TLS Termination/Offloading
  * Client to loader Balancer: HTTPS/TLS
  * Load balancer To vm Instance: HTTP/TCP


* [Backend](https://cloud.google.com/load-balancing/docs/backend-service?hl=es_419)
* [Forwarding rules](https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts)

## Features

* External HTTP(S)
  * Type of traffic: Global, External, HTTP or HTTPS
  * proxy or pass-through: proxy
  * Destination ports:
    * HTTP: 80 oR 8080
    * HTTPS on 443
* Internal HTTP(S)
  * Type of traffic: Global, External, HTTP or HTTPS
  * proxy or pass-through: proxy
  * Destination ports:
    * HTTP: 80 oR 8080
    * HTTPS on 443
* SSL Proxy:
  * Type of traffic: Global, External, TCP with SSL offload
  * proxy or pass-through: proxy
  * Destination ports:
    * a big list
* TCP Proxy:
  * Type of traffic: Global, External, TCP without SSL offload
  * proxy or pass-through: proxy
  * Destination ports:
    * a big list
* External Network TCP/UDP:
  * Type of traffic: Regional, External, TCP or UDP
  * proxy or pass-through: pass-through
  * Destination ports:
    * any
* Interla TCP/UDP:
  * Type of traffic: Regional, External, TCP or UDP
  * proxy or pass-through: pass-through
  * Destination ports:
    * any


# 7 - App Engine
* Simplest way to deploy and scale your applications in GCP
  * Provides end-to-end application management
* Support:
  * Go, Java, .NET, PHP, Python
  * Use custom run-time and write code in any language
  * Connect to variety of Google Cloud storage products (Cloud SQL, etc)
* No usage chartes - Pay for resources provisioned
* Features:
  * Automatic load balancing & Auto Scaling
  * Managed platform updates & Application health monitoring
  * Application versioning
  * Traffic splittin

## Compute Engine vs App Engine
* Compute Engine
  * IAAS
  * More Flexibility
  * MORE Responsability
    * Choosing image
    * Installing software
    * Chosing Hardwareç
    * Fine grained Access/Permissions (Certificates/Firewall)
    * Availability etc
* APP Engine
  * PaaS
  * Serverless
  * LESSER Responsability
  * LOWER Flexibility

* [App Engine](https://cloud.google.com/appengine/docs?hl=es-419)

## App Engine Environments
* Standard: Applications run in language specific sandboxes
  * Complete isolation from OS/Disk/Other App
  * V1: Java, Python, PHP, Go (Old Versions)
    * Only For python and PHP runtimes:
      * Restricted network Access
      * Only white-listed extensions and libraries are allowed
    * No Restictions for Java and Go runtimes
  * V2: Java, Python, PHP, Node.js, Ruby, Go (Newer versions)
    * Full Network Access and No restrictions on Language Extensions
* Flexible - Applications instance run within Docker containers
  * Make use of Compute Enting virtual machines
  * Support ANY runtime
  * Provides access to backgroud processes and local disks

* [Standard](https://cloud.google.com/appengine/docs/standard?hl=es_419)
* [Flexible](https://cloud.google.com/appengine/docs/flexible?hl=es_419)

## Hierarchy
* Application: One App per project
* Services: Multiple Microservices or App componentes
  * You can have multiple services in a single application
  * Each Service can have different settings
  * Earlier called Modules
* Versions: Each version associated with code and configuration
  * Each Version can run in one or more instances
  * Multiple versions can co-exist
  * Options to rollback and split traffic

## Standard vs flexible

* [Comparison](https://cloud.google.com/appengine/docs/the-appengine-environments)
* [Comparison V2](https://medium.com/10decoders/how-to-choose-app-engine-environment-standard-flexible-9f4c26a723b0)

## Scaling instances
* Automatic - Automatically scale instances based on the load:
  * Recommended for Continuously Running Workloads
    * Auto scale based on:
      * Target CPU Utilization
      * Target Throughput Utilization
      * Max Concurrents Requets
    * Configure Max Instances and Min instances
* Basic
  * Recommended for Adhoc Workloads
    * Instances ar shutdown if ZERO requets:
      * Tries to keep costs low
      * High latency is possible
    * NOT supported by App Engine Flexible Environment
    * Configure Max Instances and Idle Timeout
* Manual Configure specific number of instances to run
  * Adjust number of instances manually over time


* [Scaling](https://cloud.google.com/appengine/docs/flexible/java/how-instances-are-managed?hl=es_419)

```sh
cd default-service
gcloud app deploy
gcloud app services list
gcloud app versions list
gcloud app instances list
gcloud app deploy --version=v2
gcloud app versions list
gcloud app browse
gcloud app browse --version 20210215t072907
gcloud app deploy --version=v3 --no-promote
gcloud app browse --version v3
gcloud app services set-traffic split=v3=.5,v2=.5
gcloud app services set-traffic splits=v3=.5,v2=.5
watch curl https://melodic-furnace-304906.uc.r.appspot.com/
gcloud app services set-traffic --splits=v3=.5,v2=.5 --split-by=random
 
cd ../my-first-service/
gcloud app deploy
gcloud app browse --service=my-first-service
 
gcloud app services list
gcloud app regions list
 
gcloud app browse --service=my-first-service --version=20210215t075851
gcloud app browse --version=v2
gcloud app open-console --version=v2
gcloud app versions list --hide-no-traffic
```

## Request routing
* you can use a combination of three approaches:
  * Routing with URL:
    * `https://<PROJECT_ID>.<REGION_ID>.r.appspot.com`(Default service called)
    * `https://<SERVICE>-dot-<PROJECT_ID>.<REGION_ID>.r.appspot.com` (Specific service)
    * `https://<VERSION>-dot-<PROJECT_ID>.<REGION_ID>.r.appspot.com` (Specific version of service)
    * Replace -dot- with . if using custom domain
  * Routing with a dispatch file:
    * Configure dispatch.yaml with routes
    * gcloud app deploy dispatch.yaml
  * Routing with Cloud Load Balancing
    * Configure routes on Load Balancing instante

## Deploying new versions without downtime
* How do I go from V1 to V2 without downtime?
* Option 1: I'm very confident - Deploy & shift all traffic at once:
  * Deploy and shift all traffic at once from v1 to v2: gcloud app deploy
* Option 2: I want to manage the migration from v1 to v2:
  * STEP 1: Deploy v2 without shifting traffic (--no-promote)
    * gcloud app deploy --no-promote
  * STEP 2: Shift traffic to V2:
    * OPTION 1: (all at once Migration); migrate all at once to v2
      * gcloud app services set-traffic s1 --splits V2=1
    * OPTION 2: Gradual migration - Gradually shift traffic to v2. Add --migrate option.
      * Gradual migration is not supported by app engine Flexible environment
    * OPTION 3: (Splitting): Control the place of migration
      * gcloud app services set-traffic s1 --splits=v2=.5,v1=.5
      * Useful to perform A/B testing

## Split traffic between multiple versoins?
* IP splitting - Based on requets IP address
  * IP addresses can change causing accuracy issues!
  * If all requets originate from a corporate vpn with single IP, this can cause all requests to go to the same version
* Cookie Splitting - Based on a cookie (GOOGAPPUID)
  * Cookies can be controlled from your application
  * Cookie splitting accurately assing users to versions
* Random - Do it randomly

* Include --split-by option in gcloud app services set-traffic command
  * values: cookie, ip and random

## Commands
* Syntax: gcloud app brose/create/deploy/describe/open-console
  * glcoud app create --region=us-central
  * gcloud app deploy app.yaml
    * --image-url: Only for flexible environments. Deploy docker image
      * gcloud app deploy --image-url gcr.io/PROJECT-ID/hellow-world:0.0.1
      * --promote --no-promte (Should new versions receive traffic?)
      * --stop-previous-version --no-stop-previous-versoin (Should old verions be stopped after new versions recevies all traffic?)
      * --version (assing a version. Otherwise, a version number is generated)
  * gcloud app browse --service="myService" --version="v1"
  * gcloud app open-console --service="myService" --version="v1"
  * gcloud app open-console logs
  * gcloud app logs tail
  * gcloud app regions list

### Instances
* glcoud app instances delete/describe/list/scp/ssh
  * gcloud app instances delete i1 --service=s1 --version=v1
  * gcloud app instances describe --service=s1 --versions=v1
  * gcloud app instances list
  * gcloud app instances scp --service=s1 --verions=v1 --recurse local_dir i1:remote_dir
  * glcoud app instnaces ssh --service=s1 --version=v1 i1

### Services and versions
* glcoud app services browse/delete/describe/list/set-traffic
  * gcloud app services list
  * gcloud app services browse myservice --version=v1
  * gcloud app services delete s1 s2
  * gcloud app services describe s1
  * glcoud app services set-traffic app1 --splits-v1=0.9,2=0.1

* gcloud app versions browse/delete/describe/list/migrate/start/stop
  * gcloud app versions list
    * --hide-no-traffic (Only show versions that are receiving traffic)
  * gcloud app versions browse/delete/describe v1 --service=s1
  * gcloud app versions migrate v2 --service=s1
  * gcloud app verions start/stop v1 
    * --service=s1 Only start v1 of service s1

## Cronjobs
```yaml
cron:
- description: "daily summary job"
  url: /task/summary
  schedule: every 24 hours
```
* Allows to run scheduled jobs at pre-defined intervals
* Use cases:
  * Send a report by email every day
  * Refresh cache data every 30 minutes
* Configured using cron.yaml
* Run this command - gcloud app deploy cron.yaml
  * Performs a HTTP GET request to the configured URL on schedule

## Others files
* dispatch.yaml - override routing rules
```yaml
dispatch:
  - url: "*/mobile/*"
    service: mobile-frontend
  - url: "*/work/*"
    service: static-backend
```

* queue.yaml - manage task queues
```yaml
queue:
- name: fooqueue
  rate: 1/s
  retry_parameters:
    task_retry_limit: 7
    task_age_limit: 2d
```

## Remember
* AppEngins is REgional
  * you cannot change an applications region
* Good option for simple microsercices:
  * Use standard v2 when uo are using supported languages
  * Use Flexible if you are building containereized apps
* Be aware - ATLEAST one container is always running when using Flexible:
  * Go for Standard if you want to be able to scale down the number of instances to zero when there is NO load
* Use a combination of resident and dynamic instances
  * Resident Instances: Run continuously
  * Dynamic instances: added based on load
    * Use all dynamic instnaces if you are cost sensitve
    * If you are not very cost sensitive, keep a set of resident instances running always

# 8 - Cloud Run
* Cloud Run - Container to Production in Seconds
  * Built on top of an open standard - Knative
  * Fully managed serverless platform for containerized applications
    * Zero infrastructure management
    * Pay per use (CPU Ram, Requests and Networking)
* Fully integrated end-to-end developer experience:
  * No limitations in languages, binaries and dependencies
  * Cloud Code, Cloud Build, Cloud Monitoring & Cloud Logging Integrations
* Anthos - Run Kubernetes clusters anywhere
  * Cloud, multi Cloud and On-Premise
* Cloud Run for Anthos - Deploy your worklodas to Anthos clusters running on-premises or on Google Cloud

# 9 - Block and File Storage
## Block Storage
* Use case: Harddisks attached to your computers
* Typically, ONE Block Storage device can be connectoed to ONE virtual server
  * EXCEPTION - You can attach read only bock devices with multiple virtual servers and certain cloud providers are exploring multi-writer disks as well
* HOWEVER, you can connect multiple different block storage devices to one virtual server
* Use as:
  * Direct-attached storage (DAS) - Similiar to a hard disk
  * Storage Area Network (SAN) - High-speed network connection a pool of storage devices
    * Used database

## File Storage
* Media workflows need huge shared storage for supporting processes like video editing
* Enterprise users need a quick way to share files in a secure and organized way
* These file shares are shared by serveral virtual servers

## Types
* Block Storage:
  * Persistent Disks: Network Block Storage
    * Zonal: data replicated in a one zone
    * Regional: Data replicated in multiple zones
  * Local SSDs: Local Block storage
* File Storage:
  * Filestore: High perfomance file storage


## Local SSDs
* Physically attached to the host of VM instance:
  * Provide very high (IOPS) and very low latency
  * (BUT) ephemeral storage - Temporary data (Data persists only until instances is running)
    * Enable live migration for data to survive maintenance events
  * Data automatically encrypted
    * HOWEVER, you CANNOT configure encryption keys
  * Lifecycle tied to VM instance
  * ONLY some machine types support local SSDs
  * Supports SCSI and NVMe interfaces
* Remember:
  * Choose NVMe-enabled and multi-queue SCSI images for best perfomance
  * Large Local SSDs (more sotrage), more vCPUs (attached to VM)

* Advantages
  * Very Fast I/O 
    * higher throughput and lower latency
  * Ideal for use cases needing high IOPs while storing temporary information
    * Examples: Caches, temporary data, scratch files, etc
* Disadvantages
  * Ephemeral storage
    * Lower durability, lower availability, lower flexibility compared to PDs
  * you cannot detach and attach it to another vm instance

## Persistent Disk
* Network block storage attached to your VM instance
* Provisioned capacity
* Very flexible:
  * Increase size when you need it - when attached to VM instance
  * Perfomance scales with size
    * For higher perfomance, resize or add more PDs
* Independent lifecycle from VM instance
  * Attach/Detach from one VM instance to anocher
* Options: Regional and Zonal
  * Zonal PDs replicated in single zone. Regional PDs replicated in 2 zones in same Region.
  * Typically Regional PDs are 2X the cost of Zonal PDs
* Use case: Run your custom database

## PD vs SSDs

| Feature  | Persistent Disks  | Local SSDs  |
|---|---|---|
| Attachment to VM instance  | As a network drive  | Physically attached  |
| Lifecycle  | Separate from VM instance  | Tied with VM instance  |
| I/O Speed  | Lower (network latency)  | 10-100X of PDs  |
| Snapshots  | Supported  | Not supported  |
| Use case  | Permanent storage  | Ephemeral storage  |

## PD - Standard vs Balanced vs SSD
| Feature  | Standard  | Balanced  | SSD |
|---|---|---|---|
| Underlying Storage  | Hard Disk Drive  | Solid State Drive  | Solid State Drive  |
| Referred to as  | pd-standard  | pd-balanced  | pd-ssd  |
| Performance - Sequential IOPS (Big Data/Batch)  | Good  | Good   | Very Good  |
| Performance - Random IOPS (transactional APPS)  | Bad  | Good   |  Very Good  |
| Cost  | Cheapest | In Between  | Expensive  |
| Use case  | Big Data (cost efficient)  | Balance between cost and performance  | High Performance  |


## PD Snaphots
* Take point-in-time snapshots of your Persistent Disks
* You can also schedule snapshots (configure a schedule):
  * You can also auto-delete snapshots after X days
* Snapshots can be Multi-regional and REgional
* You can share snapshots across projects
* You can create new disks and instances from snapshots
* Snapshots are incremental:
  * Deleting a snapshots only deletes data which is NOT needed by other snapshots
* Keep similar data together on a Persistent Disk:
  * Separate your OS, volatile data and permanent data
  * Attach multiple disks if needed
  * This helps to better organize your snapshots and images

### Recommendations
* Avoid taking snapshots more often than once an hour
* Disk volume is available for use but Snapshots reduce performance
  * Schedule snapshots during off-peak hours
* Creaing snapshots from disk is faster than creating from images
  * But creating disks from image faster than creating from snapshots
  * if you are repeatedly creating disks from a snapshot
    * Create and image from snapshot and use the image to create disks
* Snapshots are incremental:
  * But you dont lose data vy deleting older snapshots
  * Deleting a snapshot only deletes data which is NOT needed by other snapshots
  * Do not hesitate to delete unnecesssary snapshots

## Compares
| Scenarios  | Machine Image  | PD snapshot  | Custom Image  | Instance template  |
|---|---|---|---|---|
| Single disk backup  | yes  | yes  | yes  | no  |
| Multiple disk backup  | yes  | no  | no  | no  |
| Differential backup  | yes  | yes  | no  | no  |
| Instance cloning and replication  | yes  | no  | yes  | yes  |
| VM instance configuration  | yes  | no  |  no | yes  |

## Command line
### Disks
* gcloud compute disks list/create/delete/resize/snapshot
  * gcloud compute disks create my-disk-1 --zone=us-east1-a
    * --size= (1GB or 2TB)
    * --type= (default pd-standard)
    * --image --image-family --source-disk --source-snapshot
    * --kms-key --kms-project
  * gcloud compute disks resize example-disk-1 --size=6TB
    * Only increasing disk size is supported
  * gcloud compute disks snapshot test --zone=us-central1-a --snapshot-names=?snapshot-test

### Images
* gcloud compute images
* Actions: create/delete/deprecate/describe/export/import/list/update
  * creating images
    * gcloud compute images create my-image
      * --source-disk --source-disk-zone
      * --source-snapshot
      * --source-image --source-image-project
      * --source-image-family --source-image-project
  * deprecate image
    * gcloud compute images deprecate IMAGE --state=DEPRECATED
  * exports virtual disk images
    * gcloud compute images export --image=my-image --destination-uri=gs://my-bucket/... --export-format=vmdk --project=my-project

## Filestore
* shared cloud file storage
  * supports NFSv3 protocol
  * Provisoned capacity
* Suitable for high performance workloads
  * up to 320 TB with throughput of 16 GB/s and 480K IOPS
* Support HDD (general purpose) and SSD
* Use cases: file share, media workflows and contenct management

## Review
* Global
  * Images
  * Snapshots
  * Instances templates
* Regional
  * Regional managed IG
  * REgional PD
* Zonal
  * Zonal managed IG
  * Instances
  * Persistent Disks