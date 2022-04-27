# training_gcp_cloud_engineer_associate

# Table of Contents
1. [Certification Introduction](#1-certification-introduction)



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

### Links
* [Regions-zones](https://cloud.google.com/compute/docs/regions-zones)
* [Global/Regional/Zonal Resources](https://cloud.google.com/compute/docs/regions-zones/global-regional-zonal-resources)
* [Virtualization](https://cloud.google.com/compute/docs/regions-zones/zone-virtualization)
