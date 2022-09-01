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
  - [Reduce the number of steps when create and configure VM instance](#reduce-the-number-of-steps-when-create-and-configure-vm-instance)
    - [Startup Scripts](#startup-scripts)
  - [Instance Template](#instance-template)
  - [Custom image](#custom-image)
- [3 - Optimizing Costs and Perfomance](#3---optimizing-costs-and-perfomance)
  - [Sustained use discounts](#sustained-use-discounts)
  - [Committed use discounts](#committed-use-discounts)
  - [Discounts for Preemptible VM instances](#discounts-for-preemptible-vm-instances)
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
    - [Examples:](#examples)
- [5 - Instance Groups](#5---instance-groups)
  - [Updating](#updating)
  - [Instance Group - Scenarios](#instance-group---scenarios)
  - [Some commands](#some-commands)
- [6 - Cloud Load Balancing](#6---cloud-load-balancing)
  - [Terminology](#terminology)
  - [Features](#features-1)
  - [Scenarios](#scenarios-1)
- [7 - App Engine](#7---app-engine)
  - [Compute Engine vs App Engine](#compute-engine-vs-app-engine)
  - [Environments](#environments)
  - [Hierarchy](#hierarchy)
  - [Standard vs flexible](#standard-vs-flexible)
  - [Scaling instances](#scaling-instances)
  - [Some commands](#some-commands-1)
  - [Request routing](#request-routing)
  - [Deploying new versions without downtime](#deploying-new-versions-without-downtime)
  - [Split traffic between multiple versions?](#split-traffic-between-multiple-versions)
  - [Apps](#apps)
    - [Instances](#instances)
    - [Services and versions](#services-and-versions)
  - [Cronjobs](#cronjobs)
  - [Others files](#others-files)
  - [Remember](#remember)
  - [Scenarios](#scenarios-2)
- [8 - Cloud Functions](#8---cloud-functions)
  - [Concepts](#concepts)
- [9 - Cloud Run](#9---cloud-run)
  - [Command line](#command-line)
- [10 - Block and File Storage](#10---block-and-file-storage)
  - [Block Storage](#block-storage)
  - [File Storage](#file-storage)
  - [Types](#types)
  - [Local SSDs](#local-ssds)
  - [Persistent Disk](#persistent-disk)
  - [PD vs SSDs](#pd-vs-ssds)
  - [PD - Standard vs Balanced vs SSD](#pd---standard-vs-balanced-vs-ssd)
  - [PD Snaphots](#pd-snaphots)
    - [PD Recommendations](#pd-recommendations)
  - [Compares](#compares)
  - [Command line](#command-line-1)
    - [Disks](#disks)
    - [Images](#images)
  - [Scenarios - Persistent Disks](#scenarios---persistent-disks)
  - [Filestore](#filestore)
  - [Review](#review)
  - [Scenarios - Block and File Storage](#scenarios---block-and-file-storage)
- [11 - Object Storage](#11---object-storage)
  - [Object Cloud Storage](#object-cloud-storage)
  - [Object Cloud Objects and Buckets](#object-cloud-objects-and-buckets)
  - [Object Cloud Classes](#object-cloud-classes)
  - [Object Cloud Object Versioning](#object-cloud-object-versioning)
  - [Object Cloud Lifecycle Management](#object-cloud-lifecycle-management)
  - [Object Cloud Encryption](#object-cloud-encryption)
  - [Object Cloud Scenarios](#object-cloud-scenarios)
  - [Object Cloud Commands](#object-cloud-commands)
- [12 - IAM](#12---iam)
  - [IAM](#iam)
  - [Roles](#roles)
    - [Roles - Example permissions](#roles---example-permissions)
  - [Members, Role and Policy](#members-role-and-policy)
    - [Policy](#policy)
  - [Some commands](#some-commands-2)
  - [Service Accounts](#service-accounts)
    - [Service Accounts - Scenarios](#service-accounts---scenarios)
  - [ACLs](#acls)
- [13 - Choosing Database](#13---choosing-database)
  - [Database Categories](#database-categories)
  - [Relational Database](#relational-database)
  - [OLTP Relational Databases](#oltp-relational-databases)
  - [OLAP Relational Databases](#olap-relational-databases)
  - [OLTP vs OLAP](#oltp-vs-olap)
  - [NoSQL](#nosql)
  - [In-Memory](#in-memory)
  - [Summary](#summary)
  - [Scenarios](#scenarios-3)
- [14 - Exploring Database](#14---exploring-database)
  - [CloudSQL](#cloudsql)
  - [Commands](#commands)
  - [CloudSQL Features](#cloudsql-features)
  - [Cloud Spanner](#cloud-spanner)
  - [Cloud Datastore and Cloud Firestore](#cloud-datastore-and-cloud-firestore)
  - [BigTable](#bigtable)
  - [Memorystore](#memorystore)
  - [BigQuery](#bigquery)
  - [Commands](#commands-1)
    - [Commands - gcloud sql](#commands---gcloud-sql)
    - [Commands - bq](#commands---bq)
    - [Commands - cbt](#commands---cbt)
  - [Summary](#summary-1)
- [15 - Pub/Sub](#15---pubsub)
  - [Pub/Sub - Summary](#pubsub---summary)
  - [Pub/Sub - Commands](#pubsub---commands)
- [16 - Cloud VPC](#16---cloud-vpc)
  - [VPC](#vpc)
  - [Firewall Rules](#firewall-rules)
  - [Ingress and Egress Rules](#ingress-and-egress-rules)
  - [Shared VPC](#shared-vpc)
  - [VPC Peering](#vpc-peering)
  - [Cloud VPN, Cloud Interconnect and Direct Peering](#cloud-vpn-cloud-interconnect-and-direct-peering)
    - [Cloud VPN](#cloud-vpn)
  - [Cloud Interconnect](#cloud-interconnect)
  - [Direct Peering](#direct-peering)
- [17 - Operations](#17---operations)
  - [Cloud Monitoring](#cloud-monitoring)
    - [Cloud Monitoring - Workspace](#cloud-monitoring---workspace)
    - [Cloud Monitoring - VM](#cloud-monitoring---vm)
  - [Cloud Logging](#cloud-logging)
  - [Cloud Audit Logs](#cloud-audit-logs)
  - [Cloud Routing Logs and Exports](#cloud-routing-logs-and-exports)
  - [Cloud Trace](#cloud-trace)
  - [Cloud Debugger](#cloud-debugger)
  - [Cloud Profiler](#cloud-profiler)
  - [Error Reporting](#error-reporting)
  - [Operations - Scenarios](#operations---scenarios)
- [18 - Organizations and IAM](#18---organizations-and-iam)
  - [Projects, Folders and Organization](#projects-folders-and-organization)
    - [Projects, Folders and Organization - Recommendations](#projects-folders-and-organization---recommendations)
  - [Billing Accounts](#billing-accounts)
    - [Billing Accounts - Budget, Alerts and Exports](#billing-accounts---budget-alerts-and-exports)
  - [IAM Best Practices](#iam-best-practices)
  - [User Identity Management](#user-identity-management)
  - [IAM members/Identities](#iam-membersidentities)
    - [IAM members/Identities - use Cases](#iam-membersidentities---use-cases)
  - [Policy Service](#policy-service)
  - [IAM Roles](#iam-roles)
    - [IAM Roles - Organization, Billing and Project Roles](#iam-roles---organization-billing-and-project-roles)
    - [IAM Roles - GCE](#iam-roles---gce)
    - [IAM Roles - Google App Engine](#iam-roles---google-app-engine)
    - [IAM Roles - GKE](#iam-roles---gke)
    - [IAM Roles - Google Cloud Storage](#iam-roles---google-cloud-storage)
    - [IAM Roles - Google Cloud BigQuery](#iam-roles---google-cloud-bigquery)
    - [IAM Roles - Logging and Service Accounts](#iam-roles---logging-and-service-accounts)
    - [IAM Roles - Other importante IAM Roles](#iam-roles---other-importante-iam-roles)
- [20 - Other Services](#20---other-services)
  - [Cloud Deployment Manager](#cloud-deployment-manager)
  - [Cloud Marketplace (Cloud Launcher)](#cloud-marketplace-cloud-launcher)
  - [Cloud DNS](#cloud-dns)
  - [Cloud Dataflow](#cloud-dataflow)
  - [Cloud Dataproc](#cloud-dataproc)
- [21 - Extras](#21---extras)



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
  * Best price-perfomance ratio.
  * Para la mayoría de Workloads.
  * Web and applications servers, Small-medium databases, Dev environments
* Memory Optimized (M2, M1):
  * Ultra high memory workloads
  * Large in-memory databases and in-memory analytics
* Compute Optimized (C2): 
  * Compute intensive Workload
  * Gaming applications

### Example
Una vez elige la familia, deberá elegir el tipo de instancia, por ejemplo E2:
* e2-standard-2:
  * e2 - Machine Type Family
  * standar - Type of workload
  * 2 - Number of CPUs
  * _En el caso de las standard la RAM=VCPUs*4 = 8Gb de Memoria RAM_
* e2-highmem-2:
  * e2 - Machine Type Family
  * standar - Type of workload
  * 2 - Number of CPUs
  * _En el caso de las highmem la RAM=VCPUs*8 = 16Gb de Memoria RAM_
* e2-highcpu-2:
  * e2 - Machine Type Family
  * standar - Type of workload
  * 2 - Number of CPUs
  * _En el caso de las highcpu la RAM=VCPUs = 2Gb de Memoria RAM_

A la par que se elige una máquina superior, las capabilities de Memory, Disk y Netwoking van incrementando.
* [Family](https://cloud.google.com/compute/docs/machine-types)

## Image
Image type:
* `Public Images`: Mantenidas por Google o alguna comunidad Open Source or proveedor externo.
* `Custom Images`: Imágenes custom creadas por usted para sus proyecto específicos.

## Internal and External IP
* __External__: IPs accesibles desde internet.
* __Internal__: IPs accesibles internamente desde la red corporativa.
> No puede haber dos recursos con la misma `External IP`. Sin embargo pude haber dos recursos que tengan la misma `Internal IP`, siempre que sean redes distintas, en caso contrario habría colisión de paquetes.
* Todas las `VM Instances` tienen asignada al menos una `Internal IP`.
* Debe tener encuenta que si una VM Instance es parada, perderá su `external IP`, excepto cuando se configura una `Static IP`.

### Static IP
* Las Static IPs pueden ser intercambiadas entre `VM instances`.
* Deberá reservarse en la misma región que su `VM instance`.
* Permanecen adjuntas aunque reinicimos la `VM instance`.
* Se factura aunque no esté en uso.

* [IP Address](https://cloud.google.com/compute/docs/ip-addresses?hl=en)

## Reduce the number of steps when create and configure VM instance
Existen múltiples opciones para configurar una `VM instance`:
* `Startup Script`.
* `Instance Template`.
* `Custom Image`.

### Startup Scripts
* [Startup Scripts](https://cloud.google.com/compute/docs/instances/startup-scripts/linux?hl=es-419)

## Instance Template
Si queremos lanzar varias VM instances debemos indicar cada vez atributos como el tipo de máquina, o la imagen, sin embargo podemos apoyarnos en `Instance Templates` para evitar repetir los mismos pasos.

El uso de `Instance Template` permite definir: 
* `Machine type`
* `Image`
* `Labels`
* `Startup Script`
* ...

Una vez creado un `Instance Template` no puede ser cambiado pero si puede hacer una copia y realizar las modificaciones necesarias.

Otra caracteristica es que puede especificar una `Image family` (debia-9), de esta forma utilizará la última versión de la familia cuando se lance.

No hay costo asociado a los `Instance Template`, pero si por la creación de `VM instance`.

* [Instance Template](https://cloud.google.com/compute/docs/instance-templates?hl=es_419)

## Custom image
* Cuando instalamos paquetes en una imagen limpia, puede demorarse mucho el tiempo de inicio.
* Podemos crear una `Custom Image` con todas las actualizaciones y el software pre-instalado y crear una `Instance Template` a partir de un disco o un snapshot.
* Una imagen custom puede ser compartida con otros proyectos.
* Puede marcar imágenes como obsoletas.
* Una de las ventajas de crear una `Custom Image` es garantizar que todos los estandares de seguridad se cumplan.
* Es más recomendable el uso de `Custom Imagen` que `Startup Script`.
* Las Image pueden ser `Regional` o `Multi-regional`.

* [Custom Image](https://cloud.google.com/compute/docs/images/create-custom)



# 3 - Optimizing Costs and Perfomance
## Sustained use discounts
* `Automatic discounts` para `VM instances`. Si está utilizando familias N1 o N2 con más de un uso del 25% del mes puedes obtener un 20% to 50% de descuento en cada minuto incremental.
* El descuento aumenta con el uso.
* No necesita realizar ninguna acción para habilitarlo.
* Se aplican automáticamente cuando se lanzan instancias en `Google Kubernetes Engine` o `Google Compute Engine`.
* __NO__ se aplica a todas las `machine types`, por ejemplo E2 y A2.
* Si está utilizando `APP Enginx flexible` o `Dataflow` para crear las VMs __NO__ se aplicarán los descuentos.

* [Sustains Discounts](https://cloud.google.com/compute/docs/sustained-use-discounts)

## Committed use discounts
* Utilizados para cargas de trabajo predecibles.
* Puede decir que necesitará una máquina __1 año__ o __3 años__.
* Dependiendo el tipo de máquina y la GPUs que necesite puede obtener hasta un 70% de descuento.
* Aplicable por GCE y GKE
* No aplicable para `App Engine Flexible` y `Dataflow`.
* [Comitted Discounts](https://cloud.google.com/compute/docs/instances/signing-up-committed-use-discounts?hl=es_419#:~:text=When%20you%20purchase%20a%20committed,like%20machine%20types%20or%20GPUs.)

## Discounts for Preemptible VM instances
* GCP puede acabar con la instancia en cualquier momento dentro del periodo de 24h (Recibirá una advertencía de 30s).
* VM más baratas y de corta duración.
* El tiempo máximo que puede ejecutar estas instancias es de 24h
* Utilízalas cuando tu app sea __fault tolerant__
* __Cost sensitive__
* Your workload is __NOT inmmediate__
* Es posible que no siempre estén disponibles.
* __NO__ tienen SLA y no pueden ser migradas a regular VM.
* __NO__ pueden ser reiniciadas automáticamente.
* __NO__ es aplicable al [Free Tier Credits](https://cloud.google.com/free/docs/free-cloud-features?hl=es).

* [Preemptible VM](https://cloud.google.com/compute/docs/instances/preemptible)

## Google Compute Engine - Billing
* Se le __factura por segundo__ a partir del primer minuto.
* Si para una VM no se le cobrará por el recurso, pero si por el `Storage`.
* Buenas práticas es creaer siempre [Budgets alerts](https://cloud.google.com/billing/docs/how-to/budgets).

## Compute Engine: Live Migration & Availability Policy
Cuando GCP necesita realizar alguna actualizción de hardware o software donde corre su VM, tienen una función llamada `Live Migration`, que permite la migración a otro `Host` en la misma zona.

* __NO__ cambia ningún atributo o propiedad de la VM.
* Soportado por VM que hacen uso de local SSDs.
* __NO__ es compatible con las VM que hacen uso de GPU y preemtible instances.

Se configura en `Availability Policy`:
* `On host maintenance`:
  * __Migrate__: Migrate VM to other hardware.
  * __Terminate__: Stop the VM.
* `Automatic restart`.

* [Availability Policies](https://cloud.google.com/compute/docs/instances/setting-instance-scheduling-options?hl=es_419)

## Custom Machine Types
* Puede crear `Custom Machine Type` cuando las opciones proporcionados por Google no se ajustan a las necesidades.
* Puede ajustar CPUs, Memory and GPUs.
  * Solo disponible para algunos tipos de máquinas como E2, N2 o N1.
  * Soporta múltiples Sistemas Operativos.
  * Se facturará por CPU y Memory provisionada.

* [Custom Machine Type](https://cloud.google.com/compute/docs/instances/creating-instance-with-custom-machine-type)

## GPUs
Las [GPUs](https://cloud.google.com/compute/docs/gpus) son unidades de procesamiento gráfico.
Son utilizadas para cargas de trabajo AI/ML.
* Alto rendimiento para intensive workloads.
* Coste elevado.
* Utiliza imagenes con `GPU Libraries` instaladas, en caso constrario no se hará uso de ellas.
* __NO__ es compatible con todos los tipos de máquinas, por ejemplo son soportadas en máquinas con `shared-core` or `memory-optimized`.
* `On host maintenance`, solo puede seleccionar `Terminate VM instance`.
* Use `Automatic restart On`.

## Virtual Machine - Remember
* Associate with a project.
* La disponibilidad de tipos de máquinas puede variar entre regiones.
* Solo puede cambiar el tipo de instance o ajustar CPU y Memory una vez detenida.
* Puede filtrar sus máquinas virtuales por propiedades o labels.
* Son `Zonals`, se ejecutan en una específica zona de una región.
* Las imágenes son `Globals`.
* Las `Instances Templates` son `Globals`.
* `Automatic Basic Monitoring` está habilitada.
  * Default metrics: CPU utilization, Network bytes o Disc throughput.
  * Para la Memory y Disk Space, `Cloud Monitoring Agent` es necesario.

## Virtual Machine - Best Practices
* Elija la `Zone` and `Region` en base a:
  * Cost, Regulations, Availability needs, Latency and Specific Hardwared needs.
  * Distribuya instancias en múltiplews zonas y regiones para el HA.
* Elija el tipo de máquinas que necesit:
  * Por ejemplo, si tiene cargas de trabajos intensas de computación utilice máquinas con CPU optimizada.
  * Utilice instancias con GPU cuando lo necesite.
* Haga reservas de `commited use discounts` para workloads constante.
* Use `preemptible instances` para aplicaciones tolerantes a fallos.
* Utiliza labels, por ejemplo para identificar el entorno o el centro de coste.

## Scenarios
| Scenario  | Solution  |
|---|---|
| Prerequisitos para crear una VM  | Project, Billing Account, Compute Engines APIs enabled  |
| Hardwared dedicado  | [Sole-tenants nodes](https://cloud.google.com/compute/docs/nodes/sole-tenant-nodes?hl=es-419)  |
| Parcheo de miles de máquinas  | [VM Manager](https://cloud.google.com/compute/docs/vm-manager?hl=es-419) |
| Logging to your VM  | Shh into it  |
| you do not want to expones a VM to internet | Do not assing an external IP |
| You want allow _HTTP trafffic to your VM | configure [Firewall Rules](https://cloud.google.com/vpc/docs/firewalls) |



# 4 - Gcloud
* __Command line interface__ para interactuar `Google Cloud Resources`.
* La mayoría de servicios pueden ser administrados usando `Gcloud`:
  * GCE
  * GKE
  * Databases
  * etc

* Puedes crear/eliminar/actualizar/leer recursos existentes y también realizar implementaciones.
* Existen otras herramientas CLI, específicas de algunos servicios:
* Cloud `gsutil`
* Cloud Big Query - `bq`
* Cloud Bigtable - `cbt`
* Kubernetes - `kubectl`

## Gcloud example commands
```sh
# `gcloud config list project`
[core]
project = centering-aegis-348716

Your active configuration is: [default]

# `gcloud config configurations list`
NAME     IS_ACTIVE  ACCOUNT                        PROJECT                 COMPUTE_DEFAULT_ZONE  COMPUTE_DEFAULT_REGION
default  True       adrian.cloud.test.2@gmail.com  centering-aegis-348716  europe-west4-a        europe-west4

# `gcloud config configurations activate default`
Activated [default].

# `gcloud config list`
[compute]
region = europe-west4
zone = europe-west4-a
[core]
account = adrian.cloud.test.2@gmail.com
disable_usage_reporting = False
project = centering-aegis-348716

Your active configuration is: [default]

# `gcloud config configurations describe default`
is_active: true
name: default
properties:
  compute:
    region: europe-west4
    zone: europe-west4-a
  core:
    account: adrian.cloud.test.2@gmail.com
    project: centering-aegis-348716

# `gcloud compute instances list`
Listed 0 items.

# `gcloud compute instances create my-first-instance-from-gcloud`
Created [https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/europe-west4-a/instances/my-first-instance-from-gcloud].
NAME                           ZONE            MACHINE_TYPE   PREEMPTIBLE  INTERNAL_IP  EXTERNAL_IP    STATUS
my-first-instance-from-gcloud  europe-west4-a  n1-standard-1               10.164.0.2   34.147.92.235  RUNNING

# `gcloud compute instances describe my-first-instance-from-gcloud`
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

# `gcloud compute instances delete my-first-instance-from-gcloud`
The following instances will be deleted. Any attached disks configured to be auto-deleted will be deleted unless they are attached to any other instances or the `--keep-disks` flag is 
given and specifies them for keeping. Deleting a disk is irreversible and any data on the disk will be lost.
 - [my-first-instance-from-gcloud] in [europe-west4-a]

Do you want to continue (Y/n)?  Y

Deleted [https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/zones/europe-west4-a/instances/my-first-instance-from-gcloud].

# `gcloud compute zones list`
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

# `gcloud compute regions list`
NAME                     CPUS  DISKS_GB  ADDRESSES  RESERVED_ADDRESSES  STATUS  TURNDOWN_DATE
asia-east1               0/8   0/2048    0/4        0/8                 UP
asia-east2               0/8   0/2048    0/4        0/8                 UP
asia-northeast1          0/8   0/2048    0/4        0/8                 UP
asia-northeast2          0/8   0/2048    0/4        0/8                 UP
asia-northeast3          0/8   0/2048    0/4        0/8                 UP
asia-south1              0/8   0/2048    0/4        0/8                 UP
asia-south2              0/8   0/2048    0/4        0/8                 UP
....................

# `gcloud compute machine-types list`
 
# `gcloud compute machine-types list --filter zone:asia-southeast2-b`
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

# `gcloud compute machine-types list --filter "zone:(asia-southeast2-b asia-southeast2-c)"`
# `gcloud compute zones list --filter=region:us-west2`
NAME        REGION    STATUS  NEXT_MAINTENANCE  TURNDOWN_DATE
us-west2-a  us-west2  UP
us-west2-b  us-west2  UP
us-west2-c  us-west2  UP

# `gcloud compute zones list --sort-by=region`
# `gcloud compute zones list --sort-by=~region`
# `gcloud compute zones list --uri`
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

# `gcloud compute regions describe us-west4`
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

# `gcloud compute instance-templates list`
Listed 0 items.

# `gcloud compute instance-templates create instance-template-from-command-line`
Created [https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/global/instanceTemplates/instance-template-from-command-line].
NAME                                 MACHINE_TYPE   PREEMPTIBLE  CREATION_TIMESTAMP
instance-template-from-command-line  n1-standard-1               2022-05-03T11:44:40.740-07:00

# `gcloud compute instance-templates describe instance-template-from-command-line`
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

# `gcloud compute instance-templates delete instance-template-from-command-line`
The following instance templates will be deleted:
 - [instance-template-from-command-line]

Do you want to continue (Y/n)?  Y

Deleted [https://www.googleapis.com/compute/v1/projects/centering-aegis-348716/global/instanceTemplates/instance-template-from-command-line].
```

## Syntax
* gcloud GROUP SUBGROUP ACTION ...
  * GROUP - `config` or `compute` or `container` or `iam` or `functions` ...
  * SUBGROUP - `instances` or `images` or `machines-types` or `regions` or `zones` ...
  * ACTION - `Create` or `list` or `start` or `stop` or `describe` ...

### Examples:
* Google Compute Engine:
  * `gcloud compute instances create` [NAME]
    * Options examples:
      * `--mahine-type` n1-standard-1
      * `--custom-cpu` 6 `--custom-memory` 3072MB `--custom-vm-type` (n1/n2) (Custom Machine)
      * `--image`
      * `--image-family`
      * `--source-snapshot`
      * `--source-instance-template`
      * `--source-machine-image`
      * `--service-account` or `--no-service-account`
      * `--zone`
      * `--tags`
      * `--preemptible`
      * `--restart-on-failure`
      * `--deletion-protection`
      * `--metadata/metadata-from-file`
* gcloud compute images/regions/zones-disk-types list
* gcloud compute instances/disks/snapshots list
  * `--filter="zone:VALUE"`
  * `--sort-by`
  * `--uri`
    * gcloud compute images list --sort-by NAME --filter "PROJECT:(windows-cloud ubuntu-os-cloud)"
* comandos con iam, roles, policies
* comandos con service accounts
* comandos configuración proyecto



# 5 - Instance Groups
`Instance Group` es un grupo de VM instances administradas como una sola entidad.
Existen dos tipos de `Instance Groups`:
* [Managed (MIG)](https://cloud.google.com/compute/docs/instance-groups):
  * Idénticas VMs creadas usando una `instance template`, por lo tanto tienen la misma configuración.
  * Features: 
    * `Autoscaling`
    * `Autohealing`
    * `Managed releases` ([Rolling update or Canary](https://www.techtarget.com/searchitoperations/answer/When-to-use-canary-vs-blue-green-vs-rolling-deployment)) 
    * Permiten añadir un `Load Balancer` para el balanceo de carga.
* [Unmanaged](https://cloud.google.com/compute/docs/instance-groups/creating-groups-of-unmanaged-instances?hl=es_419):
  * Puede tener VMs con diferentes configuraciones.
  * __NO__ permiten el uso de `Autoscaling`, `autohealing`.
  * __NO__ recomendadas a menos que necesite difernetes tipos de VMs.
* Pueden ser `Zonal` o `Regional`.

* [Instance Group Stateful/Stateless](https://cloud.google.com/compute/docs/instance-groups/stateful-migs?hl=es-419)

## Updating
* `Rolling update` es una actualización gradual de la VMs de un `IG` a una nueva `instance template`.
  * Especifica nueva `template`. Opcional `canary test`.
  * Especifica como debe realizarse la actualización. 
  * [Maximun surge](https://cloud.google.com/compute/docs/instance-groups/rolling-out-updates-to-managed-instance-groups?_ga=2.102081153.-100830343.1651250286#max_surge).
  * [Maximun Unavailable](https://cloud.google.com/compute/docs/instance-groups/rolling-out-updates-to-managed-instance-groups?_ga=2.102081153.-100830343.1651250286#max_unavailable).
* `Rolling Restart/replace` es una reinicio o reemplazo gradual de todas las VMs del `IG`.
  * No hay cambios en el `Instance template` pero le gustaría reiniciarlas o reemplazarlas todas.
  * Configure `Maximun surge` o `Max unavailable`.

## Instance Group - Scenarios
| Scenario | Solution |
|---|---|
| Quires un MIG managed application que sobreviva a Zonal Failures | Crea un MIG multi zona (o regional MIG) |
| You want create VMs of different configurations in the same group  |  Create un-managed Instance Group |
| You want to preserve VM state in an MIG  | Stateful MIG - Preserve VM states (instance name, attached Disk and metadata). Recommended for stateful workloads (database, data processing group) |
| You want high availability in an MIG even when there are hardware/software updates | Use an instance template with availability policy automatic restart: enabled & on-host maintenance: migrate. Ensure live migration and automatic restart. |
| You want unhealthy instances to be automaticall y replaced | Configure health check on the MIG (self healing) |
| Avoid frequent scale up & downs | Cool-down period/initial delay
 |

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



# 6 - Cloud Load Balancing
`Cloud Load Balancing` es un servicio que permite distribuir el tráfico entre VMS de una aplicación en una o múltiples regiones.
  * `Managed Service` y `Fully distributed`.
  * Features importantes:
    * `Health check `- Route to healthy instances.
      * Recover from failures.
    * `AutoScaling`.
    * Global load balancing with single anycast IP.
      * Also supports internal load balancing.
* Benefits:
  * `HA`.
  * `AutoScaling`.
  * `Resiliency`.

* [Load Balancing Overview](https://cloud.google.com/load-balancing/docs/load-balancing-overview?hl=es)
* [Types](https://cloud.google.com/load-balancing/docs/choosing-load-balancer?hl=es_419#lb-summary)
* [Functions](https://cloud.google.com/load-balancing/docs/features?hl=es_419)

## Terminology
* `Backend` es un grupo de `endpoints` que reciven el tráfico desde __Google Cloud Load Balancer__ por ejemplo, los `IGs`. El recurso de AWS sería `AWS Target Group`. Un mismo `Load Balancer` puede servir múltiples `backends`, por ejemplo `IGs` de microservicios.
* `Frontend` permite especificar IP address, port and protocols. Estos atributos son facilitados a los clientes para la conexión. El recurso de AWS sería AWS LB Listener.
  * Si usa SSL, un certificado debe ser asignado al `Cloud Load Balancer`.
* `Host and path rules` específico del `HTTP(S) Load Balancing`. Define reglas para la redirección del tráfico a los diferentes backends.
  * Basado en `path` - test.com/a vs test.com/b
  * Basado en `Host` - test.com vs b.test.com
  * Basado en `HTTP headers` (Authorization header) and methods (POST, GET, etc)

| Scenario | Termination Solution |
|---|---|
| Aplicación expuesta a internet | HTTPS |
| Load Balancer a VM instance pasando por Google internal network | HTTP está bien pero preferible HTTPS |
| SSL/TLS Termination/Offloading | Client to loader Balancer: HTTPS/TLS. Load balancer To vm Instance: HTTP/TCP |

* [Backend](https://cloud.google.com/load-balancing/docs/backend-service?hl=es_419)
* [Forwarding rules](https://cloud.google.com/load-balancing/docs/forwarding-rule-concepts)
* [Choose LB](https://cloud.google.com/static/load-balancing/images/choose-lb.svg?hl=es-419)

## Features
| Load Balancer | Type of Traffic | Proxy or pass-through | Destination Ports |
|---|---|---|---|
| External HTTP(S) | Global, External, HTTP or HTTPS | Proxy | HTTP on 80 or 8080 / HTTPS on 443 |
| Internal HTTP(S) | Global, External, HTTP or HTTPS | Proxy | HTTP on 80 or 8080 / HTTPS on 443 |
| SSL Proxy | Global, External, TCP with SSL offload | Proxy | A big list |
| TCP Proxy | Global, External, TCP without SSL offload | Proxy | A big list |
| External Network TCP/UDP | Regional, External, TCP or UDP | Pass-through | any |
| Internal TCP/UDP | Regional, External, TCP or UDP | Pass-through | any |

## Scenarios
| Scenario | Solution | 
|---|---|
| Solo las instancias healthy recivan tráfico | Configure health check |
| HA para tus VM | Crea múltiple MIG para tus VMs in múltiples regiones y utiliza LB para balancear el tráfico |
| Enrutar tráfico a múltiples microservicios utilizando el mismo LB  | Crea MIGs y backends para cada microservicio. Crear Host y path rules para redireccionar a cada microservicio. También puedes apuntar un backend a Cloud Storage |
| Balancear la carga del tráfico HTTPS externo en varias regiones | Utiliza External HTTP(S) Load Balancer  |
| Quieres terminación SSL para el tráfico no HTTPS | Utilice SSL Proxy Load Balancer |



# 7 - App Engine
* La forma más sencilla de implementar y escalar aplicaciones en GCP.
  * Proporciona gestión de aplicaciones end-to-end.
* Soporta lenguajes como:
  * Go, Java, .NET, Node.js, PHP, Python, Ruby, usando `pre-configured runtimes`.
  * Puede utilizar `custom run-time` y escribir en cualquier lenguaje.
  * Conectividad con variedad de servicios de Google Cloud storage (Cloud SQL, etc)
* __NO__ hay cargos por uso, se factura por recursos provisionados.
* Features:
  * `Automatic load balancing` & `Auto Scaling`
  * `Managed platform updates` & `Application health monitoring`
  * `Application versioning`
  * `Traffic splittin`

## Compute Engine vs App Engine
* Compute Engine
  * IAAS
  * More Flexibility
  * More Responsability
    * Choosing image
    * Installing software
    * Choosing Hardware
    * Fine grained Access/Permissions (Certificates/Firewall)
    * Availability etc
* APP Engine
  * PaaS
  * Serverless
  * Lesser Responsability
  * Lower Flexibility

* [App Engine](https://cloud.google.com/appengine/docs?hl=es-419)

## Environments
* [Standard](https://cloud.google.com/appengine/docs/standard?hl=es_419) - Applications run in language specific sandboxes.
  * Aislamiento completo del OS/Disk/Other Apps.
  * `V1`: Java, Python, PHP, Go (Old Versions).
    * Solo para Python and PHP runtimes:
      * Acceso restringido a la red.
      * Solo algunas extensiones y librearías son permitidas.
    * __NO__ hay restricciones para Java y Go runtimes.
  * `V2`: Java, Python, PHP, Node.js, Ruby, Go (Newer versions).
    * Acceso completo a la red y no existen restricciones en las extensiones de los lenguajes.
* [Flexible](https://cloud.google.com/appengine/docs/flexible?hl=es_419) - Las instancias se ejecutan dentro de contenedores Docker.
  * Cuando usa este tipo está utilizando VM de `Google Compute Engine`.
  * Soporta cualquier runtime siempre que pueda crear una imagen Docker.
  * Obtiene acceso a procesos en segundo plano que se ejecunta en la VM y puede adjuntar local disks.

## Hierarchy
* `Application`: Solo puede crear una aplicación por proyecto.
* `Services`: Multiple Microservices or App componentes.
  * You can have multiple services in a single application.
  * Each `Service` can have different settings.
  * Earlier called Modules.
* `Versions`: Each version associated with code and configuration.
  * Each `Version` can run in one or more instances.
  * Multiple versions can co-exist.
  * Options to rollback and split traffic.

## Standard vs flexible
| Feature  | Standard  | Flexible  |
|---|---|---|
| Pricing Factors  | Instance Hours  | vCPU, Memory & Persistent Disks  |
| Scaling  | Manual, Basic, Automatic  | Manual, Automatic  |
| Scaling to zero  | Yes  | No. Minium one instance  |
| Instance startup time  | Seconds  | Minutes  |
| Rapid Scaling  | Yes  | No  |
| Max. request timeout  | 1 to 10 minutes  | 60 minutes  |
| Local disk  | Mostly (except forPython, PHP). Can write to /tmp  | Yes. Ephemeral. New Disk on startup.  |
| SSH for debugging  | No  | Yes  |

* [Comparison](https://cloud.google.com/appengine/docs/the-appengine-environments)
* [Comparison V2](https://medium.com/10decoders/how-to-choose-app-engine-environment-standard-flexible-9f4c26a723b0)

## Scaling instances
* `Automatic` - Escalado automático en base a carga.
  * Recomendado para cargas de trabajo de ejecución continua.
    * Auto scale based on:
      * `Target CPU Utilization.`
      * `Target Throughput Utilization`.
      * `Max Concurrents Requets`.
    * Configure `Max Instances` and `Min instances`.
* `Basic` - Instancias que son creadas cuando reciben tráfico.
  * Recomendado para Adhoc Workloads
    * Las instancias se terminan cuando no hay solicitudes.
      * Trate de mantener sus costos bajos.
      * Alta latencia por falta de instancias para atender las primeras peticiones.
    * __NO__ soportado por `App Engine Flexible` Environment
    * Configure `Max Instances` and `Idle Timeout`.
* `Manual` - Configure el número de instancias.
  * Adjust number of instances manually over time.

* [Scaling](https://cloud.google.com/appengine/docs/flexible/java/how-instances-are-managed?hl=es_419)

## Some commands

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
* Puedes usar la combinación de los siguientes tres enfoques:
  * Enrutamiento por URL:
    * `https://<PROJECT_ID>.<REGION_ID>.r.appspot.com`(Default service called)
    * `https://<SERVICE>-dot-<PROJECT_ID>.<REGION_ID>.r.appspot.com` (Specific service)
    * `https://<VERSION>-dot-<PROJECT_ID>.<REGION_ID>.r.appspot.com` (Specific version of service)
    * Replace `-dot-` with `.` si utiliza un dominio custom.
  * Enrutamiento a través del fichero dispath:
    * Configurar `dispatch.yaml` con las rutas.
    * `gcloud app deploy dispatch.yaml`
  * Enrutamiento con `Cloud Load Balancing`.
    * Configure routes on Load Balancing instante

## Deploying new versions without downtime
* Option 1: I'm very confident - Deploy & shift all traffic at once:
  * Deploy and shift all traffic at once from v1 to v2: `gcloud app deploy`
* Option 2: I want to manage the migration from v1 to v2:
  * STEP 1: Deploy v2 without shifting traffic (--no-promote)
    * `gcloud app deploy --no-promote`
  * STEP 2: Shift traffic to V2:
    * OPTION 1: (all at once Migration); migrate all at once to v2
      * `gcloud app services set-traffic s1 --splits V2=1`
    * OPTION 2: Gradual migration - Gradually shift traffic to v2. Add --migrate option.
      * Gradual migration __NO__ es soportada por App Engine Flexible environment.
    * OPTION 3: (Splitting): Control the place of migration
      * `gcloud app services set-traffic s1 --splits=v2=.5,v1=.5`
      * Useful to perform A/B testing

## Split traffic between multiple versions?
* `IP splitting` - Based on requets IP address
  * La dirección IP pùede cambiar causando problemas.
  * Si todas las peticiones se envían desde una VPN coorporativa, probablemente salgan con la misma IP y por lo tanto accederá a la misma versión.
* `Cookie Splitting` - Based on a cookie (`GOOGAPPUID`)
  * Cookies pueden ser controladas por tu aplicación.
  * Cookie splitting accurately assing users to versions
* `Random` - Do it randomly

* Include `--split-by` option in `gcloud app services set-traffic` command
  * values: `cookie`, `ip` and `random`

## Apps
* Syntax: `gcloud app browse/create/deploy/describe/open-console`
  * `gcloud app deploy app.yaml`
    * `--image-url`: Only for App Engine Flexible environments. Deploy docker image.
      * `gcloud app deploy --image-url gcr.io/PROJECT-ID/hellow-world:0.0.1`
      * `--promote` or `--no-promote` (Should new versions receive traffic?)
      * `--stop-previous-version` or `--no-stop-previous-version` (Should old verions be stopped after new versions recevies all traffic?)
      * `--version` (assing a version. Otherwise, a version number is generated)
  * `gcloud app browse --service="myService" --version="v1"`
  * `gcloud app open-console --service="myService" --version="v1"`
  * `gcloud app open-console logs`
  * `gcloud app logs tail`
  * `gcloud app regions list`

### Instances
* `gcloud app instances delete/describe/list/scp/ssh`
* `gcloud app instances delete i1 --service=s1 --version=v1`
* `gcloud app instances describe --service=s1 --versions=v1`
* `gcloud app instances list`
* `gcloud app instances scp --service=s1 --verions=v1 --recurse local_dir i1:remote_dir`
* `glcoud app instnaces ssh --service=s1 --version=v1 i1`

### Services and versions
* `glcoud app services browse/delete/describe/list/set-traffic`
* `gcloud app services list`
* `gcloud app services browse myservice --version=v1`
* `gcloud app services delete s1 s2`
* `gcloud app services describe s1`
* `glcoud app services set-traffic app1 --splits-v1=0.9,2=0.1`

* `gcloud app versions browse/delete/describe/list/migrate/start/stop`
* `gcloud app versions list`
    * `--hide-no-traffic` (Only show versions that are receiving traffic)
* `gcloud app versions browse/delete/describe v1 --service=s1`
* `gcloud app versions migrate v2 --service=s1`
* `gcloud app verions start/stop v1 `
  * `--service=s1` (Only start v1 of service s1)

## Cronjobs
```yaml
cron:
- description: "daily summary job"
  url: /task/summary
  schedule: every 24 hours
```
* Permite ejecutar trabajos programados en intervalos predefinidos.
* Casos de uso:
  * Enviar reportes por email cada día.
  * Refrescar los datos de la cache cada 30 minutos.
* Se configura en el fichero `cron.yaml`.
* Run this command - `gcloud app deploy cron.yaml`

## Others files
* `dispatch.yaml` - override routing rules
```yaml
dispatch:
  - url: "*/mobile/*"
    service: mobile-frontend
  - url: "*/work/*"
    service: static-backend
```

* `queue.yaml` - manage task queues
```yaml
queue:
- name: fooqueue
  rate: 1/s
  retry_parameters:
    task_retry_limit: 7
    task_age_limit: 2d
```

## Remember
* App Engine es `Regional`.
  * __NO__ puedes cambiar la región de tu applicación.
* Buena opción para microservicios simples (múltiples microservicios).
  * Usa `Standard v2` cuando necesites utilizar algún leguaje soportado.
  * Usa `Flexible` si necesitas dockerizar aplicaciones.
* AppEngine puede reducirse a 0 execpto cuando se utiliza `App Engine Flexible`, siempre habrá un contenedor en ejecución.
  * Utiliza Standar cuando necesites reducir el número de instancias a 0.
* Combine instancias residentes y dinámicas.
  * `Resident Instances`: Se ejecutan continuamente.
  * `Dynamic instances`: Añadidas bajo demanda de carga de trabajo.
    * Si es muy sensible a los costes utilice siempre `Dynamic instances`.

## Scenarios
| Scenario  | Solution  |
|---|---|
| Crear dos aplicaciones de Google App Engine en el mismo proyecto  | No es posible, solo puede tener una applicación por proyecto. Sin embargo puede tener múltiples servicios y múltiples versiones para cada servicio.  |
| Quiero crear dos servicios de Goole App engine dentro de la misma aplicación  | Puedes crear múltiples servicio bajo la misma aplicación. Cada servicio puede tener múltiples versiones.  |
| Quiero mover mi aplicación de Google App Engine a una región diferente  | La aplicación es creada en una región específica. Unav ez creada no puede ser movida a otra región.  |
| Quieres realizar Canary Deploymentes  | `gcloud app deploy --no-promote` y una vez desplegado `gcloud app services set-traffic s1 --splits v1=0.9,v2=0.1`  |



# 8 - Cloud Functions
* Ejecuta tu código en la nube sin servidores ni contenedores.
* No necesita preocuparse por el escalado o la disponibilidad de su función.
* `Cloud Functions` automáticamente giran entorno a las respuestas de los eventos que ocurren en la plataforma.
  * Escalan horizontalmente.
* Recomendadas para respuestas a eventos:
  * `Cloud Functions` no es una buena idea para largos procesos.

## Concepts
* `Event` - Por ejemplo, subió un fichero a `Cloud Storage`.
* `Trigger` - Respuesta de evento con una llamada a `Cloud Function`.
  * `Trigger` - a que Function debo invocar con este evento?.
  * `Functions` las funciones toman los datos del Event y ejecutan acciones.
* Las Functions pueden activarse desde variedad de lugares:
  * Cloud Storage
  * Cloud Pub/Sub
  * HTTP POST/GET/DELETE/PUT/OPTIONS
  * Firebase
  * Cloud Firestore
  * Stack driver logging



# 9 - Cloud Run
* `Cloud Run` permite ejecutar contenedores en producción en cuestión de segundos sin necesidad de llegar a necesitar tecnologías como Kubernetes.
  * Estandard abierto `Knative`
  * Fully managed serverless platform para la containerización de aplicaciones..
    * __NO__ es necesario gestionar infraestructura.
    * Pago por uso (CPU, Memory, Requests and Networking)
* Completa integeración end-to-end para la experiencia de los developers:
  * __NO__ hay limitaciones de lenguajes, binarios y dependencias.
  * Portable, porque está basado en la arquitectura de contendores.
  * Integración con otros servicios como `Cloud Code`, `Cloud Build`, `Cloud Monitoring` & `Cloud Logging`.
* `Anthos`, ejecuta clusters de Kubernetes donde quieras.
  * Cloud, Multi Cloud and On-Premise.
* `Cloud Run for Anthos` - Deploy your worklodas to Anthos clusters running on-premises or on Google Cloud.

## Command line
| Description  | Command  |
|---|---|
| Deploy a new container  | `gcloud run deploy SERVICE_NAME --image IMAGE_URL --revision-suffix v1`  |
| List available revisions  | gcloud run revisions list  |
| Adjust traffic assignmets  | `gcloud run services update-traffic myservice --to-revisions=v2=10,v1=90` |



# 10 - Block and File Storage
## Block Storage
* Caso de uso: Disco duro conectado a un ordenador.
* Generalmente un Block Storage puede ser conectado a una VM.
* Puedes conectar múltiples Block storages a una misma VM.
* Use as:
  * Direct-attached storage (DAS) - Similiar to a hard disk.
  * Storage Area Network (SAN) - High-speed network connection a pool of storage devices.
    * Used database.

## File Storage
* Media workflows need huge shared storage for supporting processes like video editing
* Enterprise users need a quick way to share files in a secure and organized way
* These file shares are shared by serveral virtual servers

## Types
* `Block Storage`:
  * [Persistent Disks](https://cloud.google.com/compute/docs/disks#pdspecs): Network Block Storage.
    * [Zonal](https://cloud.google.com/compute/docs/disks#zonal-pds): Datos replicados en una zona.
    * [Regional](https://cloud.google.com/compute/docs/disks#repds): Datos replicados en múltiples zonas.
  * [Local SSDs](https://cloud.google.com/compute/docs/disks#localssds): Local Block storage.
* `File Storage`:
  * [Filestore](https://cloud.google.com/architecture/filers-on-compute-engine#filestore): High perfomance file storage.

## Local SSDs
* Físicamente conectados al host donde se encuentra la VM.
  * Obtiene un alto [IOPS](https://es.wikipedia.org/wiki/IOPS) y baja latencia.
  * Almacenamiento efímero pensado para datos temporales (Los datos solo persisten mientras la instancia está corriendo).
    * Habilita `Live Migration` si desea que los datos se mantengan.
  * Los datos son automáticamente encriptados, pero no puede configurar las `encryption keys`.
  * `Lifecycle` adjuntado a la VM.
  * Solo algunas máquinas soportan `Local SSDs`.
  * Soportan `SCSI` and `NVMe` interfaces.
* Remember:
  * Choose `NVMe-enabled` and `multi-queue SCSI` images for best perfomance.
  * Large `Local SSDs` (more storage), more vCPUs (attached to VM).

* Advantages.
  * Very Fast I/O.
    * Alto rendimiento y baja latencia.
  * Ideal para casos de uso en los que necesites altos IOPS mientras se almacena información temporal.
    * Examples: Caches, temporary data, scratch files, etc.
* Disadvantages.
  * Almacenamiento efímero.
    * Baja durabilidad, baja disponibilida, baja flexibilidad comparado con los `PDs`.
  * __NO__ puedes detach y attach a otra VM.

## Persistent Disk
* Network block storage attached a tu VM.
* Capacidad para provisionar la cantidad que desea.
* Flexible:
  * Incrementa el tamaño que necesites cuando está attached a la VM.
  * El rendimiento aumenta con el tamaño.
    * For higher perfomance, resize or add more PDs.
* Independent lifecycle from VM instance.
  * Attach/Detach de una VM a otra.
* Options: `Regional` and `Zonal`.
  * Zonal PDs replicated in single zone. Regional PDs replicated in 2 zones in same Region.
  * Los regionales son el doble de costosos que lo zonales.
* Use case: Correr una BBDD.

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
* Snapshots puntuales de sus `Persistent Disks`.
* Puede programar `Snapshots` (configure a schedule):
  * Puedes configurar que sea eliminados tras X días.
* Snapshots pueden ser `Multi-regional` y `Regional`.
* Puedes compartir `Snapshots` entre proyectos.
* Puedes crear nuevos discos o VM a partir de un `Snapshot`.
* Snapshots son incrementales:
  * Cuando elimina un snapshot solo elimina los datos que no son necesarios para otros snapshots.
* Keep similar data together on a Persistent Disk:
  * Separate your OS, volatile data and permanent data.
  * Attach multiple disks if needed.
  * This helps to better organize your snapshots and images.

### PD Recommendations
* Evite realizar snaphost más de una vez por hora.
* Disk volume is available for use but Snapshots reducen el rendimiento.
  * Programa snapshots en las horas de menor actividad.
* Crear `Snapshot` desde un disco es más rápido que crearlas desde una `Image`.
  * Sin embargo creaer discos a partir de una `Image` es más rápido que a partir de `Snapshots`.
  * Si está creando discos a partir de un Snapshot
    * Crea una image desde Snapshot y usa la imagen para crear discos.
* `Snapshots` are incremental:
  * Pero no pierde datos al eliminar Snasphots.
  * Al borrar un snapshot, solo eliminas los datos que no son necesarios para otros snapshots.
  * No dude en eliminar snapshots innecesarios.

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
* `gcloud compute disks list/create/delete/resize/snapshot`
  * `gcloud compute disks create my-disk-1 --zone=us-east1-a`
    * `--size=SIZE` (1GB or 2TB)
    * `--type=TYPE` (default pd-standard)
    * `--image` `--image-family` -`-source-disk` `--source-snapshot`
    * `--kms-key` `--kms-project`
  * `gcloud compute disks resize example-disk-1 --size=6TB`
    * Solo soporta resize incrementando el tamaño.
  * `gcloud compute disks snapshot test --zone=us-central1-a --snapshot-names=snapshot-test`

### Images
* `gcloud compute images create/delete/deprecate/describe/export/import/list/update`
  * Creating images.
    * `gcloud compute images create my-image`
      * `--source-disk` `--source-disk-zone`
      * `--source-snapshot`
      * `--source-image` `--source-image-project`
      * `--source-image-family` `--source-image-project`
  * Deprecate image.
    * `gcloud compute images deprecate IMAGE --state=DEPRECATED`
  * exports virtual disk images.
    * `gcloud compute images export --image=my-image --destination-uri=gs://my-bucket/... --export-format=vmdk --project=my-project`

## Scenarios - Persistent Disks
| Scenarios  | Solution |
|---|---|
| Quiere mejorar el rendimiento de un PD | Aumentar el tamaño del PD o añadir más PDs o incrementerla la vCPU de su VM. |
| Quire aumentar la durabilidad de sus PD | Optar por discos regionales (costo 2x) |
| Realizar backup cada hora de sus PD para Disaster Recovery | Schedule hourly snapshots. |
| Quire eliminar los snaphosts antiguos creados por el Schedule | Puede hacerlo dentro de la programación del Schedule |

## Filestore
* Almacenamiento de archivos compartidos en la nube.
  * Soporta NFSv3 protocol
  * Provisoned capacity
* Adecuado para cargas de trabajo de alto rendimiento.
  * up to 320 TB with throughput of 16 GB/s and 480K IOPS.
* Soporta HDD (general purpose) and SSD.
* Use cases: file share, media workflows and content management.

## Review
* `Global`.
  * Images.
  * Snapshots.
  * Instances templates.
* `Regional`.
  * Regional managed IG.
  * REgional PD.
* `Zonal`.
  * Zonal managed IG.
  * Instances.
  * Persistent Disks.

## Scenarios - Block and File Storage
| Scenarios  | Solution |
|---|---|
| Quiere IOPS muy altas pero su datos se pueden perder sin problema | Local SSDs |
| Sistema de intercambio de archivos de alto rendimiento que pueda adjuntarse a varias VMs. | Filestore |
| Backup de la configuración de su VM junto a los PDs adjuntos | Machine Image |
| Facilitar creación de VM con custom Software y hardening de OS | Custom Image |



# 11 - Object Storage
## Object Cloud Storage
* Servicio de almacenamiento más popular, flexible y económico.
  * Serverless: Autoscaling
* Puede almacenar grandes objetos utilizando un enfoque `key-value`.
  * Access Contol at Object level.
  * Los ficheros son llamados `Object Storage`.
* Es posible almacenar todo tipo de archivos.

## Object Cloud Objects and Buckets
* Los `Objects` son almacenados en `Buckets`.
  * El nombre de los buckets debe ser `globally unique`.
  * El nombre de los buckets se utilizará como parte de las URLs de los objetos.
  * No pueden contener `goog prefix`.
  * Objetos ilimitados.
  * Asociado a un proyecto.
* Cada object es identificado por `unique key`.
  * `key is unique` en el bucket.
* El tamaño máximo de un objeto `5 TB`.

## Object Cloud Classes
* Puede haber diferentes patrones de acceso a objetos.
* Las `Storage classes` ayudan a optimizar los costes en base al acceso necesario.
  * Diseñado con una durabilidad de __99.99999999999% (11 9's)__.
  * Baja latencia.

| Storage Class | Name | Minimun Storage duration | Typical Monthly availabilty | Use case |
|---|---|---|---|---|
| Standard | STANDARD | None | >99.99% in multi-region and dual region, 99.99% in regions | Uso frecuente |
| Nearline storage | NEARLINE | 30 días | 99.95% in multi-region and dual region, 99.9% in regions | Lectura o modificación una vez al mes |
| Coldline storage | COLDLINE | 90 días | 99.95% in multi-region and dual region, 99.9% in regions | Lectura o modificación una vez cada 3 meses. |
| Archive storage | ARCHIVE | 365 días | 99.95% in multi-region and dual region, 99.9% in regions | Menos de una vez al año |

> Las Storage Class pueden definirse tanto para buckets como para objetos (nuevos).

## Object Cloud Object Versioning
* Previene el borrado accidental y proporciona histórico.
  * Se habilita a nivel de bucket.
    * Puede ser activado o desactivado en cualquier momento.
  * `Live version` es la última version del objeto.
    * Si elimina la Live version se convierte en una versión de objeto no actual.
  * Las versiones anteriores son identificadas por `object key + generation number`.
  * Reduce costes eliminado verions anteriores.

## Object Cloud Lifecycle Management
* Se accede a los objectos con frecuencia cuando se crean.
  * Generalmente se reduce el tiempo de acceso pasado un tiempo.
* Utilizando Lifecycle podemos eliminar ficheros o versiones antiguas así como cambiar de clase el objeto.
* Se identifican los objetos con condiciones basadas en:
  * Age, CreateBefore, isLive, MatchesStorageClass, etc.
  * Puede establecer múltiples condiciones.
* Puede realizar dos acciones:
  * `SetStorageClass` - para cambiar la clase del objecto.
  * `Deletion` actions.
* Permite transiciones:
  * `Standard` or `multi-regional` or `regional` to `Nearline` or `Coldline` or `Archive`.
  * `Nearline` to `Coldline` or `Archive`.
  * `Coldline` to `Archive`.

## Object Cloud Encryption
* `Cloud Storage` siempre cifra los datos on the `server side`.
* Se cifra:
  * `Google-managed encryption key` - Default
  * `Customer-managed encryption keys` - Creadas usando `Cloud KeyManagement Service (KMS)`.
* Opcionalmente puede cifrarlo on the `client side`, cifrando el objeto previamente y posteriormente en el lado del servidor en el bucket.

## Object Cloud Scenarios
| Scenario | Description |
|---|---|
| Quiero subir un fichero grande de 100Gb | Utiliza `Parallel composite uploads` (El fichero será partido en trozos y subido) |
| Necesita almacenar registros de apps de forma permanente y no espera acceder a ellos en mucho tiempo | Archive storage |
| Almacenar archivos a los que accederá una vez cada 3 meses | Coldline storage |
| Necesita cambiar el Storage Class de un bucket | Por un lado debe cambiarlo en el bucket, y por otro en los objetos (no se cambiará en objetos existentes), podrá hacerlo de forma más sencilla con la CLI. |

## Object Cloud Commands
* Cloud Storage (__gsutil__).
  * `gsutil versioning set on/off gs://BUCKET_NAME`.
  * `gsutil uniformbucketlevelaccess set on/off gs://BUCKET_NAME`.
  * `gsutil acl ch` (Set access permission for specific object).
    * `gsutil acl ch -u AllUsers:R gs://BUCKET_NAME/OBJ:_PATH`.
    * `gsutil acl ch -u john@examle.com:WRITE gs://BUCKET_NAME/OBJ_PATH`.
    * `gsutil acl set JSON_FILE gs://BUCKET_NAME`.
  * `gsutil iam ch MBR_TYPE:MBR_NAME:IAM_ROLE gs://BUCKET_NAME`.
  * `gsutil signurl -d 10m YOUR_KEY gs://BUCKET_NAME/OBJ_PATH`.



# 12 - IAM
## IAM
* `Authentication`
* `Authorization`
* `Identities` pueden ser:
  * A GCP User
  * A Group of GCP Users
  * An App running in GCP
  * An App runing in your data center
  * Unauthenticated users
* Proporciona `very granular control`:
  * Limitación de un usuario:
    * recurso específico
    * desde una IP
    * Durante la ventana de mantenimiento
    * ...

## Roles
* `Roles` are `Permissions`.
  * Son un conjunto de aciones sobre un conjunto de recursos.
* 3 tipos de roles
  * `Basic Roles` (or `Primitive Roles`) - Owner/Editor/Viewer
    * `Viewer(roles.viewer)` - Read-only actions
    * `Editor(roles.editor)` - Viewer + Edit actions
    * `Owner(roles.owner)` - Editor + Manage Roles and Permissions + Billing
    * __NO__ recomendable su uso en producción.
  * `Predefined Roles` - Roles detallados, predefinidos y administrados por Google.
    * Diferentes roles para distintos propósitos.
    * Ejemplos: `Storage Admin`, `Storage Object Admin`, `Storage Object Viewer`, `Storage Object Creator`, ...
  * `Custom Roles` - Utilizados cuando los `Predefined Roles` __NO__ son suficientes, y necesitamos crear nuestros propios roles.

### Roles - Example permissions
* Cloud storage Roles.
  * `Storage Admin (roles/storage.admin)`.
    * storage.buckets.*
    * storage.objects.*
  * `Storage Object Admin (roles/storage.objectAdmin)`.
    * storage.objects.*
  * `Storage Object Creator (roles/storage.objectCreator)`.
    * storage.objects.create
  * `Storage Object Viewer (roles/storage.objectViewer)`.
    * storage.objects.get
    * storage.objects.list
* Los 4 roles tienen los permisos
  * resourcemanager.projects.get
  * resourcemanager.projects.list

## Members, Role and Policy
* `Member/Principal/Identity`: Who?
* `Roles`: Permission. What Actions?
* `Policy`: Assign Permissions to Members
  * Map:
    * Roles (Wath?)
    * Members (Who?)
    * Conditions (Which Resources?, When?, From Where?)
  * Recuerda que los `Permissions` __NO__ se asignan directamente a los members.
    * Los `Permissions` son representados por un `Role`.
    * Los `Members` obtienen permissos a través de un `Role`.
* Un `Role` puede tener múltiples permisos.
* Un `Role` puede ser asignado a múltiples `Members`.

### Policy
* `Roles` son asignados a los usuario a través de `IAM Policy documents`.
* Representados por `policy object`.
  * Policy object es una lista de `bindings`.
  * A binding, une un role y una lista de members.
* El tipo de member se identifica con un `prefix`.
  * user, serviceaccount, group or domain.

```json
{
  "bindings": [
    {
      "role": "roles/owner",
      "members": [
        "user:jie@example.com",
        "serviceAccount:myAppName@appspot.gserviceacount.com",
        "group:administrators@example.com",
        "domain:google.com",
      ]
    }
  ]
}
```

## Some commands
```sh
gcloud compute project-info describe
gcloud auth list
gcloud projects get-iam-policy glowing-furnace-304608
gcloud projects add-iam-policy-binding glowing-furnace-304608 --member=user:in28minutes@gmail.com --role=roles/storage.objectAdmin
gcloud projects remove-iam-policy-binding glowing-furnace-304608 --member=user:in28minutes@gmail.com --role=roles/storage.objectAdmin
gcloud iam roles describe roles/storage.objectAdmin
gcloud iam roles copy --source=roles/storage.objectAdmin --destination=my.custom.role --dest-project=glowing-furnace-304608
```

## Service Accounts
* Utilizadas para acceder a servicios sin necesidad de utilizar credenciales personales.
* Identificadas por una dirección de email. (Ex: `id-compute@developer.gserviceaccount.com`)
* No tienen password
  * Usan `public/private RSA key-pairs`.
  * No puede logarse a través de navegadores o cookies.
* Tipos de SA
  * `Default service account` - creada automaticamente cuando algunos servicios son usados.
    * __NO__ se recomienda su uso porque tienen el role `Editor` por defecto.
  * `User managed` - Creadas por usuarios.
    * Recomendables ya que hacen uso de un control más exaustivo de permisos.
  * `Google-managed service accounts` - Creadas y administrados por Google.

### Service Accounts - Scenarios
| Scenario | Description |
|---|---|
| Una App en una VM quiere comunicarse con Cloud Storage Bucket | Configure VM para usar una SA con los permisos adecuados. |
| Una App en una VM quiren hacer put de un mensaje a un Topic de Pub/Sub | Configure VM para usar una SA con los permisos adecuados. |
| Una SA es un recurso o una identity? | Ambos |
| Una VM con una SA por defecto en el proyecto A necesita acceder a un Cloud Storage Bucket del proyecto B | En el proyecto B, agregar la SA y asignar permisos de Storage Object Viewer al bucket. |

## ACLs
* Las `ACLs` definen quien tiene acceso a sus Buckets y objectos, así como el nivel de acceso que tienen.
* Que diferencia existe con IAM
  * IAM aplica de manera uniforme a todos los objetos dentro de un Bucket.
  * Las ACLs pueden ser usadas para personalizar el acceso específico a difernetes objetos dentro del mismo Bucket.
  * Recomendable utilizar `IAM`.
* Dos tipos de acceso:
  * `Uniform` - Recomendado y aplicado con IAM.
  * `Fine-grained` - Utilizado con Iam y ACLs.



# 13 - Choosing Database
## Database Categories
* Existe múltiples tipos de BBDD:
  * Relational (OLTP and OLAP), Document, Key value, Graph In memory ...
* Elegir el tipo de base de datos no es tarea facil:
  * Necesitas un `fixed schema`?
    * Necesitas flexibilidad para definir y cambiar su schema?(schemaless)
  * Que nivel de `transactions properties` necesita? (atomicity and consistency)
  * Que tipo de `latency` quiere conseguir? (seconds, milliseconds or microseconds)
  * Cuantas `transactions` espera? (cientos, miles o millones... por segundo)
  * Cuantos datos se almacenarán? (MBs, GBs, TBs or PBs)
  * ...

## Relational Database
* Más popular.
* `Predefined schema` con tablas y relaciones.
* Capacidades transacionales sólidas.
* Usadas para
  * OLTP (Procesamiento de transacciones en línea) - banca o aplicación de negociación de acciones. Las transacciones y la estructura de los datos son muy importantes.
  * OLAP (Procesamiento de análisis en linea) - muchas consultas estandar en una gran cantidad de datos.

## OLTP Relational Databases
* La gran mayoría de usuario realizan una gran cantidad de pequeñas transaciones.
  * Los datos reads, updates and deletes.
* Casos de uso:
  * Aplicaciones tradicionales, ERP, CRM, e-commerce, banking applications.
* BBDD populares
  * MySQL, Oracle, SQL Server, etc.
* Google services:
  * `Cloud SQL`: Supports PostgreSQL, MySQL and SQL Server para bases de datos relacionales `Regional`.__(algunos TBs de datos)__.
  * `Cloud Spanner`: Escala ilimitada para el almacenamiento de muchos datos ( soporta múltiples PBs) y 99.999% de disponibilidad paraca aplicaciones globales con escalado horizontal.

## OLAP Relational Databases
* Aplicaciones que permiten a los usuarios analizar PBs de datos.
  * Example: Reporting applications, Data ware houses, Business intelligence applications, Analytics systems, ...
  * Ex de app: Desea decidir las primas de seguros analizando los datos de los últimos 100 años.
  * Los datos pueden estar consolidados por múltiples (transactionals) base de datos.
* Google services:
  * `BigQuery`: almacén distribuido a `Petabyte-scale`.

## OLTP vs OLAP
* OLTP vs OLAP estructura de datos similares (tablas y relaciones).
* Pero muy difernetes en como se almacenan los datos.
* OLTP almacenamiento en filas.
  * Eficaz para procesar pequeñas transaciones.
* OLAP almacenamiento en columnas.
  * Alta compresión, puede almacenar PBs eficientemente.
  * Datos distribuidos.
  * Ejecuta una sola consulta en varias nodos

## NoSQL
* `Flexible schema`.
  * Estructura los datos como necesite tu app.
  * El schema evoluciona con el tiempo.
* Escalado horizontal a PBs con millones de transacciones por segundo.
* Google Services:
  * `Cloud Firestore` (`Datastore`).
    * Managed serverless NoSQL document database.
    * Transacciones ACID, SQL-like queries, indexes.
    * Designada para transacciones móviles y aplicaciones webs.
    * Fuerte consistencia
    * Liberías para clientes Webs y móviles.
    * Recomendada como pequeñaa y mediana base de datos (pocos TBs).
  * `Cloud Bigtable`.
    * Managed, scalable NoSQL wide column database
    * __NO__ es serverless (necesitas crear VM).
    * Recomendado para datos > 10 TBs hasta varios PBs.
    * Recomendado para una gran carga de trabjo analítica y operativa.
      * __No__ recomendada para cargas de trabajao transaccionales.

## In-Memory
* Recuperar datos de memoria es mucho más rapido que recuperarlos de disco. 
* Las bases de datos como `Redis` brindan una latencia muy baja al almacenar datos persistentes en memoria.
* Google services:
  * `Memory Store` (Redis or Memcached)
* Caso de uso: Caching, session management, gaming leader boards, geospatial applications, ...

## Summary
| Database Type | GCP Services | Desciption |
|---|---|---|
| Relational OLTP databases | `Cloud SQL`, `Cloud Spanner` | Predefined schme and very stron transactional. `Cloud SQL`: MySQL, PostgreSQL, SQL Server. `Cloud Spanner`: Unlimited sacle and 99.999% de disponibilidad aplicaciones globales |
| Relational OLAP databases | `BigQuery` | Almacenamiento columnar con predefined schema. BigData workloads |
| NoSQL Databases | `Cloud firestore (Datastore)`, `Cloud BigTable` | `Cloud Firestore`: serverless transactional document DB, Small to Medium. `Cloud BigTable`: Large databse (10 TB - PBs) Streaming, analytical and operational worklodad. Not Serverless|
| In Memory databases/caches | `Cloud Memorystore` | Aplicaciones que necesitan respuestas en microsegundos |

## Scenarios
| Scenario | Solution |
|---|---|
| Una startup con un esquema evoluciona (envolving) rápidamente (table structure) | `Cloud Datastore/Firestore`. Si sus datos están pensando en crear muy rápido entonces pondrían pensar en `Cloud Bigtable` |
| BBDD no relacional con poco almacenamiento < 10 Gb | `Cloud Datastore` |
| BBDD global transacional con schema predefinido que necesita procesar millones de transacciones por segundo | `Cloud Spanner` |
| BBDD local transacional con miles de transacciones por segundo | `Cloud SQL` |
| Datos de cache de una aplicación web | `Cloud Memorystore` |
| BBDD para el procesamiento analítico de PBs de datos | `BigQuery` |
| BBDD para almacenar grandes volúmenes de datos de flujo de dispositivos IOT | `BigTable` |
| BBDD para almacenar grandes flujos de datos time series | `BigTable` |


# 14 - Exploring Database
## CloudSQL
* Servicio relacional administrado.
* Soporta MySQL, PostgreSQL y SQL Server.
* `Regional` Service with HA 99.95%
* Utiliza SSDs o HDDs (para mejor rendimiento SSDs).
* Puede utilizar hasta 416Gb de RAM y 30TB de almacenamiento.
* Casos de uso
  * Migrar sus BBDD locales MySQL, PostgreSQL y SQL Server a la nube.
  * Reducir costes de mantenimiento de una BBDD relacional.
  * Sin embargo, se recomienda utilizar `Cloud Spanner` si:
    * Grandes volúmenes de datos en TB.
    * Necesita un escalado infinito.
    * BBDD Global que distribuya entre varias regiones.
    * Necesitas HA 99.999%.

## Commands
```sh
# Cloud SQL
gcloud sql connect my-first-cloud-sql-instance --user=root --quiet
gcloud config set project glowing-furnace-304608
gcloud sql connect my-first-cloud-sql-instance --user=root --quiet
use todos
create table user (id integer, username varchar(30) );
describe user;
insert into user values (1, 'Ranga');
select * from user;

# Cloud Spanner
CREATE TABLE Users (
  UserId   INT64 NOT NULL,
  UserName  STRING(1024)
) PRIMARY KEY(UserId);

# Cloud BigTable
bq show bigquery-public-data:samples.shakespeare
 
gcloud --version
cbt listinstances -project=glowing-furnace-304608
echo project = glowing-furnace-304608 > ~/.cbtrc
cat ~/.cbtrc
cbt listinstances
```

## CloudSQL Features
* Automatic encryption, mantenimientos y actualizaciones.
* HA y failover
  * Puede crear un `Standby` con automatic failover.
  * Pre requisites: Habilitar backups automáticos y logging.
* Puede crear `Read Replicas` sin HA.
  * Cross-zone, Cross-region and External (NON Cloud SQL DB).
  * Pre requisites: Habilitar backups automáticos y logging.
* Aumenta automáticamente el tamaño sin downtime.
* `Point-to-time` recovery, habilita logging.
* Backups (automáticos y bajo demanda).
* Soporte para migraciones desde otras fuentes
  * Utiliza `Database Migration Service` (DMS).
* Puedes exportar datos desde UI y gcloud

## Cloud Spanner
* Base de datos relacional de misión critica, administrada y globalmente distribuida con muy HA (99.999%).
  * Sólida consistencia transaccional a escala global.
  * `Escalado de PBs` con automatic sharding.
* Escala horizontalmente para lecturas y escrituras.
  * Configura número de nodos.
  * En comparación con las réplicas de `Cloud SQL`:
    * No puede escalar horizontalmente las réplicas de escritura
* `Regional` and `Multi-Regional`
* Muy cara (comparado con `Cloud SQL`), pagas por nodo y almacenamiento.
* Puedes exportar datos desde la consola.
  * Otra opción es utilizar `Dataflow` para automatizar la exportación.
  * No gcloud export option.

## Cloud Datastore and Cloud Firestore
* `Datastore` Base de datos NoSQL Document con alta escalabilidad
  * Automáticamente escala y particiona los datos a medida que crece.
  * Recomendado para unos pocos TBs, para volumenes más grandes se recomienda `BigTable`.
  * Soporta Transactions, Indexes y SQL Queries.
  * No soporta `Joins` ni `Aggregate` (sum or count) operaciones.
  * Sus casos de usos necesitasn un `flexible schema with transactions`.
    * User Profiles and Product Catalogs
  * Estructura Kind --> Entity
  * Puedes exportar los datos solo con gcloud.
* `Firestore` es igual que `Datastore` pero optimizado.
  * Optimizado para el acceso a múltiples dispositivos.
  * Proporciona liberarías del lado del cliente.
  * Offers Datastore and Native modes.

## BigTable
* Bases de datos `NoSQL wide column y PB scale`, compatible con la API de HBase.
  * Diseñada para grandes volumenes de datos analíticos y operativos (IOT Streams, Analytics, Time Series Data, etc)
  * Puede manejar millones de trasacciones read/write por segundo con una baja latencia.
  * Admite transacciones de una sola row, por eso no es un buen candidato para aplicaciones transaccionales.
* __NO__ es serverless, necesitas crear una instancia
  * Puedes escalar horizontalmente con múltiples nodos sin downtime.
* __NO__ se puede exportar datos.
* La CLI de bigTable es `cbt`.

## Memorystore
* Completamente administrado (provisioning, replication, failover and patching)
  * HA 99.9%
  * Monitorizable con `Cloud Monitoring`.
* Soporta `Redis` y `Memcached`.
  * Usa Memcached para Reference data, databse query caching, session store
  * Usa redis para baja latencia con persistencia y HA.

## BigQuery
* Exabyte scale modern `Datawarehousing`
* BBDD relacional.
* Ofrece enfoques tradicionales (Storage + Compute) y modernos (Serverlss + Realtime).
* Siempre que hablamos de Datawarehousing es muy importante la importación y exportación
  * Puede cargar datos de multitud de fuentes
  * Export to `Cloud Storage` & `Data Studio`.
* Puede configurar algunos datos de la table como Expirables.
* access database:
  * Cloud Console
  * bq
  * BigQuiery Rest API
  * HBase API
* Recuerde que las queries de BigQuery puede ser muy caras.
* Una práctica recomendable es estimar las consultas antes de realizarlas.
  * UI or bq (--dry-run)
  * Use Pricing Calculator for 1MB data.

## Commands
### Commands - gcloud sql
* `gcloud sql instances create/clone(/delete/describe/patch`
  * `gcloud sql instances create INSTANCE`
  * `gcloud sql isntances patch --backup-start-time`
* `gcloud sql databases create/delete/describe/list/patch`
  * `gcloud sql databases create DATABASE --instance=INSTANCE`
* `gcloud slq connect INSTANCE [--database=DATABASE --user=root]`
* `glcoud sql backups create/describe/list`
  * `gcloud sql backups create --async --instance INSTANCE`

### Commands - bq
* `bq show bigquery-public-data:samples.shakespeare`
* `bq query 'QUERY-STRING'`
  * `--dry-run`
* `bq extract`
* `bq load`

### Commands - cbt
* Install `gcloud components install cbt`
* Verify installation - `cbt listinstances`
* Create __.cbtrc__ file with the configuration
  * echo project=projec-id > ~/.cbtrc
    * echo instance=quickstart-instance >> ~/.cbtrc
* `cbt create instance`
* `cbt create cluster`
* `cbt createtable/deleteinstance/deletecluster/deletetable`
* `cbt listinstances/listclusters`
* `cbt ls`

## Summary
* `BigQuery`, `Datastore`, `Firebase` __NO__ necesitan VM.
  * Pero `Cloud SQL` y `BigTable` __SI__.
* Bases de datos relacionales
  * Small local databases --> `Cloud SQL`
  * Highly scalable global databases --> `Cloud Spanner`
  * Datawarehouse - `BigQuery`
* Bases de datos NoSQL
  * Transactional database para unos pocos Tbs --> `Cloud Datastore`
  * Grandes volumenes IOT o streaming analytics data --> `Cloud BigTable`

# 15 - Pub/Sub
## Pub/Sub - Summary
* Asincrono, scalable, completamente administrado.
* Para solucinoes de HA y alta escalabilidad.
  * Autoescala a billones de mensajes
  * Bajo Coste, pago por uso.
* Casos de uso
  * Cola de mensajes. Cuando se ingestan muchos eventos.
* Soporta push and pull.
* `Publisher` - Envia el mensaje a pubsub.googleapis.com
* `Subscriber` - Recibe el mensaje
  * `Pull` - Los subscriptores hacen pull del mensaje
  * `Push` - se envía directamente a los subscriptores.

## Pub/Sub - Commands
```sh
gcloud config set project glowing-furnace-304608
gcloud pubsub topics create topic-from-gcloud
gcloud pubsub subscriptions create subscription-gcloud-1 --topic=topic-from-gcloud
gcloud pubsub subscriptions create subscription-gcloud-2 --topic=topic-from-gcloud
gcloud pubsub subscriptions pull subscription-gcloud-2
gcloud pubsub subscriptions pull subscription-gcloud-1
gcloud pubsub topics publish topic-from-gcloud --message="My First Message"
gcloud pubsub topics publish topic-from-gcloud --message="My Second Message"
gcloud pubsub topics publish topic-from-gcloud --message="My Third Message"
gcloud pubsub subscriptions pull subscription-gcloud-1 --auto-ack
gcloud pubsub subscriptions pull subscription-gcloud-2 --auto-ack
gcloud pubsub topics list
gcloud pubsub topics delete topic-from-gcloud
gcloud pubsub topics list-subscriptions my-first-topic
```

# 16 - Cloud VPC
## VPC
* Por defecto cada proyecto tiene a default VPC (Auto mode).
* Puedes crear tus propias VPCs:
  * 1 - Auto mode VPC Network
    * Las subnets son creadas automáticamente en cada región.
  * 2 - Custom mode VPC Network
    * Las subnets __NO__ son creadas automáticamente.
    * Control completo sobre el rango de direcciones IPs.
* Opciones cuando creas una subnet
  * Enable `Private Google Access` - Permite que las VMs se conecte a Google API usando IPs privadas.
  * Enable `Flowlogs` - Logs sobre la VPC Network.

## Firewall Rules
* Puede controlar el tráfico de entrada y salida de su Network.
  * Stateful - Quiere decir que si se permite el tráfico entrante el saliente también se permite.
  * Cada Firewall Rule tiene una priorida asignada (0-65535), 0 max priority.
  * Existe una regla por defecto con la prioridad más baja
    * Allow all egress
    * Deny all ingress
    * __NO__ puede ser borrada
    * Puedes sobreescribir las reglas por defecto con reglas con una prioridad mayor.
  * Default VPC tiene 4 reglas adicionales con prioridad 65534.
    * Allow incoming traffic from VM instances in same network (`default-allow-internal`)
    * Allow incoming TCP traffic on port 22 (`default-allow-ssh`)
    * Allow incoming TCP traffic on port 3389 (`default allow-rdp`)
    * Allow incoming ICMP from any source on the network (`default-allow-icmp`)

## Ingress and Egress Rules
* `Ingress Rule`: Incoming traffic from outside to GCP targets.
  * `Target`: Destination. Ex: all instances with tag X:X
  * `Source`: Ex. CIDR or All instances 
* `Egress Rule`: Outgoin traffic to destination from GCP targets.
  * `Target`: Source. Ex: all instances with tag X:X
  * `Source`: Ex. CIDR or All instances
* Con cada regla también se define
  * `Priority` - Número con mayor o menor prioridad
  * `Action on match` - Allow or Deny
  * `Protocol` - TCP, UDP or ICMP
  * `Port` - Number
  * `Enforcement status` - Enable or Disable rule

## Shared VPC
* Permite la comunicación entre recursos que forman parte de proyectos de tu organización.
  * Crea una organización o shared folder level (Access Needed: Shared VPC Admin).
  * Permite que la VPC Network sea compartida entre proyectos de la misma organización

## VPC Peering
* Permite la comunicación entre VPCs en el mismo proyecto, diferentes proyecotos de la misma organización o diferentes proyectos de organizaciones distintas.
* Para la comunicación se utilizan IPs internas
  * Eficiente porque toda la comunicación ocurre dentro de Google Network.
  * Seguro porque no es accesible desde internet.
  * No hay cargos por transferencia de datos entre servicios.

## Cloud VPN, Cloud Interconnect and Direct Peering
### Cloud VPN
* Permite conectar tu Network on-premise con la Network de GCP.
* Se implemente mediante `IPSec VPN Tunnel`.
* El tráfico pasa por internet, aunque está cifrado.
* Existen dos soluciones:
  * `HA VPN` - Servicio HA 99.99% con 2 direcciones IPs.
    * Solo admite enrutamiento dinámico.
  * `Classic VPN` 99.9% con 1 dirección IP.
    * Soporta rutas estáticas y dinámicas

## Cloud Interconnect
* Conexión física directa de alta velocidad entre on-premise y VPC Networks on GCP
  * Alta disponiblidad y alto rendimiento
  * Existen dos tipos de conexiones
    * Dedicated Interconnect - 10 Gbps or 100 Gbps
    * Partner Interconnect - 50 Mbps to 10 Gbps
* Pasa a través de en una red privada, sin embargo `Cloud VPN` pasa a través de internet.
  * Comunicación con las IPs privadas.
  * Reducción de costes en el tráfico de salida.
* Puede acceder a la API de Google de forma privada desde on-premise.
* Se recomienda para necesidades de gran ancho de banda, en caso contrario lo recomendable es `Cloud VPN`.

## Direct Peering
* Se utiliza para conectar la red de cliente a la red de Google.
* __NO__ es un servicio de GCP.
* Recomendado utlizar `Cloud Interconnect` y `Cloud VPN`.



# 17 - Operations
## Cloud Monitoring
* Herramienta para monitorizar infraestructura en GCP.
* Mide aspectos importantes de los servicios (Metrics).
* Crear visualizaciones (Graphs y Dashboards).
* Configurar Alerts (when metrics are NOT healthy).
  * Define Alerting Policies
    * Condition
    * Notifications
    * Documentation

### Cloud Monitoring - Workspace
* Puede usar `Cloud Monitoring` para monitorizar uno o más proyectos de GCP y una o más cuentas de AWS.
* Permite visualizar información de múltiples proyectos.

### Cloud Monitoring - VM
* Default metrics:
  * CPU utilization
  * Disk traffic
  * Network traffic
  * Uptime information
* Install Cloud Monitoring agente para obtener más metricas de disk, CPU, network.

## Cloud Logging
* Real time log management and analysis tool
* Permite almancer, buscar, analizar y alertar sobre volúmenes de datos masivos.
* Administrado y escalable.
* Ingesta datos desde cualquier fuente.
* Features:
  * Logs Explorer.
  * Logs Dashboard.
  * Logs Metrics.
  * Logs Router.
* La mayoría de servicios de GCP envían logs a Cloud Logging.
  * GKE.
  * App Engine.
  * Cloud Run.
* La ingesta de logs desde GCE VMs, se hace instalando `Logging Agent`.

## Cloud Audit Logs
* `Access Transparency Logs` - captura las acciones realizadas por el equipo de GCP sobre tus recursos (No soportoado por todos los servicios).
  * Solo para organizaciones que tienen Gold support.
* `Cloud Audit Logs` - Quien hizo que, donde y cuando
  * `Admin Activity logs`
  * `Data Access Logs`
  * `System Event Audit Logs`
  * `Policy Denied Audit Logs`

## Cloud Routing Logs and Exports
* Puede enrutar logs desde distintas fuentes.
* Dos tipos de Log buckets
  * _Required
  * _Default
* Idealmente debería almacenar los registros en `Cloud Logging` durante un periodo de tiempo.
  * Pueden ser exportados a `Cloud Storage Bucket`.
  * Pueden ser exportados a `BigQuery dataset`.
  * Pueden ser exportados a `Cloud Pub/Sub`.

## Cloud Trace
* Permite recoger trazas de los sistemas de GCP:
  * Soporta GCP services (GCE, CKE, App Engine)

## Cloud Debugger
* Captura el estado de una aplicación
  * Inespecciona el estado directamente en el entorno de GCP
  * Puede tomar snapshots de variables y llamadas

## Cloud Profiler
* Permite identificar los cuellos de botella en producción

## Error Reporting
* Monitorización de excepciones en tiempo real

## Operations - Scenarios
| Scenario | Solution |
|---|---|
| Le gustaría almacenar todas las operaciones sobre todos los objetos de un Bucket  | Habilitar el registro de auditorías del bucket |
| Quiere rastrear una solicitud en varios microservicios | Cloud Trace |
| Desea identificar excepciones destacadas para un microservicio específico | Error Reporting |
| Desea depurar un problema en producción ejecutandolo paso a paso | Cloud Debugger |
| Desea ver los registros para una solicitud específica  | Cloud Logging |



# 18 - Organizations and IAM
## Projects, Folders and Organization
* Existe una jerarquía bien definida
  * Organization -> Folder -> Project -> Resources
* Resources, son creados en un proyecto.
* Folder, puede contener múltiples proyects.
* Organization, puede tener múltiples Folers.

### Projects, Folders and Organization - Recommendations
* Crea proyects separados para cada entorno
* Crea folders para cada departamento
* Un proyecto por aplicación

## Billing Accounts
* Billing account es obligatoria antes de crear recursos.
* Una Billing Account puede estar asociada a uno o más proyectos.
* Puede tener múltiples billing accounts en una Organización
* Hay dos tipos:
  * Self Serve
  * Invoiced

### Billing Accounts - Budget, Alerts and Exports
* Una de las recomendaciones importantes es configurar `Cloud Billing Bugdet` para evitar sorpresas.
  * Configure `Alerts`.
  * Existe alertas por defecto para cuando supere el 50%, 90% y 100% del presupuesto.
    * Opcionalmente puede enviar alertas a PubSub.
    * `Billing admins` and `Billing Account user` son alertados por e-mail.
* Billing data pueden ser exportados:
  * `BigQuery`
  * `Cloud Storage`

## IAM Best Practices
* `Principle of Least Privilege` - Asigne el mínimo privilegio
  * Basic Roles (Primitives) __NO__ son recomendados.
  * Utilice SAs con privilegios mínimos.
    * Utilice una SA para un único propósito
* Funciones separadas.
  * Tener separada el role del que despliega, del que modifica el tráfico.
* Monitorización constante.

## User Identity Management
* Federate Cloud Identity or Google Workspace with yuour IDP.
* Enable Singles Sign On

## IAM members/Identities
* Google Account - representa a una persona
* Service Account - representa una aplicación
* Google Group - Colección
  * Email único
  * Ayuda a aplicar políticas de acceso a un grupo
* Google Workspace domain - G Suite
* Cloud Identity domain - 

### IAM members/Identities - use Cases
| Scenario | Solution |
|---|---|
| Todos los miembros de tu equipo tienen cuentas en G Suite. Está creando un proyecto de produción y le gustaría dar acceso a su equipo de operaciones | Crear un grupo con todos los miembros del equipo, crear una política con los permisos necesarios y realizar la asginación al grupo |
| Todos los miembros de tu equipo tienen cuentas en G Suite. Está configurando un proyecto nuevo. Desea proporcionar un acceso rápido por única vez a un miembro del equipo | Asignar la función directamente a la dirección de correo , dado que va a ser temporal |
| Dar acceso a un auditor externo para ver los recursos de su proyecto, pero NO debería poder realizar cambios. | Aplicar role de Viewer, que aunque no esté recomendado, será algo temporal y es el único role que tiene permisos de RO sobre todos los recursos. |
| Tu aplicación se implementa en un proyecto A en una VM y necesita acceder a un Bucket de un proyecto diferente | Asignar en el proyecto B el role a la SA del proyecto A |

## Policy Service
* Puede crear políticas a nivel de organización, por ejemplo para evitar que se creen Service Accounts.
* Para modifiacr una `Organization Policy` necesita el role `Organization Policy Administrator`

## IAM Roles
### IAM Roles - Organization, Billing and Project Roles
* `Organization Administrator`
  * Puede definir la jerarquía de recursos
  * Puede definir `Access Management Policies`
  * Administrar otros `roles` y `users`
* `Billing Account Creator` - crear Billing Accounts
* `Billing Account Administrator` - Administra Billings accounts, pero __NO__ puede crear Billing Accounts.
* `Billing Account User` - Puede asociar `Projects` y `Billing Accounts`.
  * Generalmente se usa con `Project Creator`.
* `Billing Account Viewer` - Puede ver los detalles de las Billing Accounts.

### IAM Roles - GCE
* `Compute Engine Admin` - Control completo sobre compute - Instances, Images, Load Balancers, Network, Firewalls, etc
* `Compute Instance Admin` - Crear, modificar y eliminar VM y discos
* `Compute Engine Network Admin` - Acceso completo sobre Network (routes, networks, health checks, VPN, Gateways, etc) and RO to firewall rules and SSL Certificates
* `Compute Engine Security Admin` - Acceso completo a las firewall rules and SSL Certificates
* `Compute Storage Admin` - Acceso completo a disks, images y snapshots
* `Compute Engine Viewer` - RO sobre todos los recursos de compute 
* `Compute OS Admin Login` - Log in en las VM como admin user
* `Compute OS Login` - Log in en las VM como usuario standar

### IAM Roles - Google App Engine
* `App Engine Creator` - Responsable de crear aplicaciones
* `App Engine Admin` - acceso completo
* `App Engine Viewer` - acceso como RO
* `App Engine Code Viewer` - acceso para ver el código
* `App Engine Deployer` - versiones, aplicaciones
* `App Engine Service Admin` - split or migrate versions, start and stop a version

### IAM Roles - GKE
* `Kubernetes Engine Admin` - Acceso completo para administar los clusters y objetos de Kubernetes.
* `Kubernetes Engine Cluster Admin` - Administrador del cluster (sin permisos en objetos)
* `Kubernetes Engine Developer` - Puede administra algunos objetos de Kubernetes
* `Kubernetes Engine Viewer` - get/list cluster and kubernetes api objets

### IAM Roles - Google Cloud Storage
* `Storage Admin` - Administrador total
* `Storage Object Admin` - Administrador de objetos
* `Storage Object Creator` - Puede crear objetoss
* `Storage Object Viewer` - get/list
* Container Registry utiliza los mismos permisos que Cloud Storage.

### IAM Roles - Google Cloud BigQuery
* `BigQuery Admin` - administrador completo de BigQuery
* `BigQuery Data Owner` - administrador de datos, sin acceso a los Jobs
* `BigQuery Data Editor` - puede actualizar datos
* `BigQuery Data Viewer` - puede visualizar datos
* `BigQuery Job User` - Puede crear Jobs
* `BigQuery User` - 

### IAM Roles - Logging and Service Accounts
* `roles/logging.viewer` - 
* `roles/logging.privateLogViewer` - 
* `roles/logging.admin` - 
* `roles/iam.serviceAccountAdmin` - 
* `roles/iam.serviceAccountUser` - 
* `roles/iam.serviceAccountTokenCreator` - 
* `roles/iam.serviceAccountKeyAdmin` - 

### IAM Roles - Other importante IAM Roles
* `roles/iam.securityAdmin` - Obtener y modificar IAM Policy
* `roles/iam.securityReviewer` - Listar todos los recursos y IAM policies
* `roles/iam.organizationRoleAdmin` - Administrator todos los custom roles en una organización y proyectos
* `roles/iam.organizationRoleViewer` - Leer todos los roles de la organización
* `roles/iam.roleAdmin` - Acceso a los roles de un proyecto concreto
* `roles/iam.roleViewer` - Lectura sobre todos los roles de un proyecto concreto
* `roles/browser` - Acceso de lectura sobre una jerarquia.



# 20 - Other Services
## Cloud Deployment Manager
* Automatiza la implementación y modificación de recursos de Google.
* Configuración definida como YAML
* Maneja las dependencias
* Por defecto hace rollback cuando hay un error
* Su uso es gratuito, solo paga por los recursos que despliega.

```yaml
resources:
- name: vm-created-by-deployment-manager
  type: compute.v1.instance
  properties:
    zone: us-central1-a
    machineType: zones/us-central1-a/machineTypes/n1-standard-1
    disks:
    - deviceName: boot
      type: PERSISTENT
      boot: true
      autoDelete: true
      initializeParams:
        sourceImage: projects/debian-cloud/global/images/family/debian-11
    networkInterfaces:
    - network: global/networks/default
```
* Puede utilizar Python o Jinja2 para los `Templates`.

## Cloud Marketplace (Cloud Launcher)
* Repositorios con imágenes preconfigurados por ejemplo, con wordpress.

## Cloud DNS
* Global Domain Name System
* Puede manejar zonas privadas y públicas.

## Cloud Dataflow
* Se puede usar para importar y exportar de múltiples fuentes.
* Por ejemplo, datos de Pub/Sub a BigQuery.

## Cloud Dataproc
* Servicio administrado de Spark y Hadoop.


# 21 - Extras
* [GCE vs GKE vs Cloud Run vs GAE vs Cloud Functions](https://cloud.google.com/blog/topics/developers-practitioners/where-should-i-run-my-stuff-choosing-google-cloud-compute-option)
* [Database compare](https://cloud.google.com/products/databases?hl=es)
* [CheatSheet](https://cloud.google.com/sdk/docs/cheatsheet?hl=es-419)