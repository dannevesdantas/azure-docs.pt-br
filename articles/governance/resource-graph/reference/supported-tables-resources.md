---
title: Tipos de recursos de Azure Resource Manager com suporte
description: Forneça uma lista dos tipos de recursos de Azure Resource Manager com suporte pelo grafo de recursos do Azure e pelo histórico de alterações.
ms.date: 03/10/2021
ms.topic: reference
ms.custom: generated
ms.openlocfilehash: d7b4be0b35fdfebd2f680a299bc7b90375e36afc
ms.sourcegitcommit: b572ce40f979ebfb75e1039b95cea7fce1a83452
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/11/2021
ms.locfileid: "102633760"
---
# <a name="azure-resource-graph-table-and-resource-type-reference"></a>Tabela e referência de tipo de recursos do Azure Resource Graph

O Azure Resource Graph oferece suporte aos seguintes **tipos de recursos** do [Azure Resource Manager](../../../azure-resource-manager/management/overview.md). Cada **tipo de recurso** faz parte de uma **tabela** no Resource Graph.

## <a name="advisorresources"></a>advisorresources

- microsoft.advisor/configurations
- microsoft.advisor/recommendations
- Microsoft. Advisor/Recommendations/supressões
- microsoft.advisor/suppressions

## <a name="alertsmanagementresources"></a>alertsmanagementresources

- microsoft.alertsmanagement/alerts

## <a name="extendedlocationresources"></a>extendedlocationresources

- Microsoft. extendedlocation/customlocations/enabledresourcetypes

## <a name="guestconfigurationresources"></a>guestconfigurationresources

- Microsoft. guestconfiguration/guestconfigurationassignments

## <a name="kubernetesconfigurationresources"></a>kubernetesconfigurationresources

- Microsoft. kubernetesconfiguration/Extensions
- Microsoft. kubernetesconfiguration/sourcecontrolconfigurations

## <a name="maintenanceresources"></a>maintenanceresources

- microsoft.maintenance/configurationassignments
- microsoft.maintenance/updates

## <a name="patchassessmentresources"></a>patchassessmentresources

- Microsoft. Compute/VirtualMachines/patchassessmentresults
- Microsoft. Compute/VirtualMachines/patchassessmentresults/softwarepatches
- Microsoft. hybridcompute/Machines/patchassessmentresults
- Microsoft. hybridcompute/Machines/patchassessmentresults/softwarepatches

## <a name="patchinstallationresources"></a>patchinstallationresources

- Microsoft. Compute/VirtualMachines/patchinstallationresults
- Microsoft. Compute/VirtualMachines/patchinstallationresults/softwarepatches
- Microsoft. hybridcompute/Machines/patchinstallationresults
- Microsoft. hybridcompute/Machines/patchinstallationresults/softwarepatches

## <a name="policyresources"></a>policyresources

- Microsoft. policyinsights/policystates

## <a name="recoveryservicesresources"></a>recoveryservicesresources

- Microsoft. dataprotection/backupvaults/backupinstances
- Microsoft. dataprotection/backupvaults/backupjobs
- Microsoft. dataprotection/backupvaults/backuppolicies
- Microsoft. recoveryservices/cofres/alertas
- Microsoft. Recoveryservices/Vaults/backupFabrics/protectionContainers/protectedItems (itens de backup)
- Microsoft. recoveryservices/Vaults/backupjobs
- Microsoft. recoveryservices/Vaults/backuppolicies

## <a name="resourcecontainers"></a>resourcecontainers

- Microsoft. Resources/subscriptions (assinaturas)
- Microsoft. Resources/subscriptions/resourceGroups (grupos de recursos)

## <a name="resources"></a>recursos

- 84codes. CloudAMQP/servidores (CloudAMQP)
- Citrix. Services/XenAppEssentials (Citrix virtual apps Essentials)
- Citrix. Services/XenDesktopEssentials (Citrix virtual desktops Essentials)
- Conexlink. MyCloudIt/contas (MyCloudIT – Hospedagem de área de trabalho do Azure)
- Crypteron. DataSecurity/apps (Crypteron)
- gridpro.evops/accounts
- gridpro.evops/accounts/eventrules
- gridpro.evops/accounts/requesttemplates
- gridpro.evops/accounts/views
- Hive. streaming/serviços (streaming do hive)
- incapsula.waf/accounts
- LiveArena. Broadcast/Services (difusão LiveArena)
- Mailjet. email/serviços (serviço de email Mailjet)
- Microsoft. AAD/DomainServices (Azure AD Domain Services)
- Microsoft. aadiam/azureadmetrics
- Microsoft. aadiam/privateLinkForAzureAD (link privado para o Azure AD)
- microsoft.aadiam/tenants
- Microsoft. agfoodplatform/farmbeats
- microsoft.aisupercomputer/accounts
- microsoft.aisupercomputer/accounts/jobgroups
- microsoft.aisupercomputer/accounts/jobgroups/jobs
- microsoft.alertsmanagement/actionrules
- Microsoft. alertsmanagement/resourcehealthalertrules
- microsoft.alertsmanagement/smartdetectoralertrules
- Microsoft. AnalysisServices/Servers (Analysis Services)
- Microsoft. anybuild/clusters
- Microsoft. ApiManagement/Service (serviços de gerenciamento de API)
- Microsoft. appassessment/migrateprojects
- Microsoft. AppConfiguration/configurationStores (configuração de aplicativo)
- Microsoft. AppPlatform/Spring (Azure Spring Cloud)
- microsoft.archive/collections
- Microsoft. atestation/attestationProviders (provedores de atestado)
- Microsoft. Authorization/resourceManagementPrivateLinks (links privados de gerenciamento de recursos)
- Microsoft. autogerenci/accounts
- Microsoft. automanage/configurationprofilepreferences
- Microsoft. Automation/AutomationAccounts (contas de automação)
- microsoft.automation/automationaccounts/configurations
- Microsoft. Automation/automationAccounts/runbooks (runbook)
- Microsoft. autonomousdevelopmentplatform/accounts
- Microsoft. AutonomousSystems/Workspaces (bonsai)
- Microsoft. AVS/privateClouds (nuvens privadas da AVS)
- microsoft.azconfig/configurationstores
- Microsoft. AzureActiveDirectory/b2cDirectories (locatários B2C)
- Microsoft. AzureActiveDirectory/guestUsages (usos de convidado)
- Microsoft. AzureArcData/datacontrollers (controladores de dados de arco do Azure)
- Microsoft. AzureArcData/postgresInstances (banco de dados do Azure para grupos de servidores PostgreSQL – Arc do Azure)
- Microsoft. AzureArcData/sqlManagedInstances (instâncias gerenciadas do SQL-Arc do Azure)
- Microsoft. AzureArcData/sqlServerInstances (SQL Server – arco do Azure)
- Microsoft. azurecis/autopilotenvironments
- microsoft.azuredata/datacontrollers
- microsoft.azuredata/hybriddatamanagers
- microsoft.azuredata/postgresinstances
- microsoft.azuredata/sqlbigdataclusters
- microsoft.azuredata/sqlinstances
- microsoft.azuredata/sqlmanagedinstances
- microsoft.azuredata/sqlserverinstances
- Microsoft. AzureData/sqlServerRegistrations (registros de SQL Server)
- Microsoft. azurestack/edgesubscriptions
- Microsoft. azurestack/linkedsubscriptions
- Microsoft. Azurestack/registros (hubs de Azure Stack)
- Microsoft. AzureStackHCI/clusters (Azure Stack HCI)
- Microsoft. azurestackhci/galleryimages
- Microsoft. azurestackhci/NetworkInterfaces
- Microsoft. AzureStackHCI/VirtualMachines (Azure Stack máquina virtual do HCI-Azure ARC)
- Microsoft. azurestackhci/virtualnetworks
- microsoft.baremetal/consoleconnections
- Microsoft. BareMetal/crayServers (servidores Cray)
- Microsoft. BareMetal/monitoringServers (servidores de monitoramento)
- Microsoft. BareMetalInfrastructure/bareMetalInstances (instâncias BareMetal)
- Microsoft.Batch/batchAccounts (contas do lote)
- microsoft.batchai/clusters
- microsoft.batchai/fileservers
- microsoft.batchai/jobs
- microsoft.batchai/workspaces
- Microsoft. Bing/contas (recursos do Bing)
- Microsoft. BingMaps/mapApis (API do Bing Maps para empresas)
- microsoft.biztalkservices/biztalk
- Microsoft. Blockchain/blockchainMembers (serviço Blockchain do Azure)
- Microsoft. Blockchain/cordaMembers (corda)
- Microsoft. Blockchain/inspetores (Blockchain Gerenciador de Dados)
- Microsoft. BotService/botServices (serviços de bot)
- Microsoft. cache/Redis (cache do Azure para Redis)
- Microsoft. cache/RedisEnterprise (Redis Enterprise)
- Microsoft. Cascade/sites
- Microsoft. CDN/CdnWebApplicationFirewallPolicies (políticas de firewall do aplicativo Web (WAF))
- Microsoft. CDN/Profiles (front Doors Standard/Premium (visualização))
- Microsoft. CDN/Profiles/afdendpoints
- Microsoft. CDN/perfis/pontos de extremidade (pontos de extremidade)
- Microsoft. CertificateRegistration/certificateOrders (certificados do serviço de aplicativo)
- Microsoft. caos/chaosexperiments (experimentos de caos)
- Microsoft. classicCompute/nome_do_domínio (serviços de nuvem (clássico))
- Microsoft. ClassicCompute/VirtualMachines (máquinas virtuais (clássicas))
- Microsoft. ClassicNetwork/networkSecurityGroups (grupos de segurança de rede (clássico))
- Microsoft. ClassicNetwork/reservedIps (endereços de IP Reservado (clássico))
- Microsoft. ClassicNetwork/virtualNetworks (redes virtuais (clássicas))
- Microsoft. ClassicStorage/StorageAccounts (contas de armazenamento (clássicas))
- microsoft.cloudes/accounts
- microsoft.cloudsearch/indexes
- Microsoft. CloudTest/accounts (contas do CloudTest)
- Microsoft. CloudTest/hostedpools (pools hospedados do 1ES)
- Microsoft. CloudTest/images (imagens do CloudTest)
- Microsoft. CloudTest/pools (pools de CloudTest)
- Microsoft. ClusterStor/Nodes (ClusterStors)
- Microsoft. codespaces/Plans
- Microsoft. cognição/syntheticsAccounts (contas sintéticas)
- Microsoft. Cognitivaservices/contas (serviços cognitivas)
- Microsoft. Compute/availabilitySets (conjuntos de disponibilidade)
- Microsoft. Compute/capacityreservationgroups
- Microsoft. Compute/capacityreservationgroups/capacityreservations
- Microsoft. Compute/capacityreservations
- Microsoft. Compute/cloudservices (serviços de nuvem (suporte estendido))
- Microsoft. Compute/diskAccesses (acessos a disco)
- Microsoft. Compute/diskEncryptionSets (conjuntos de criptografia de disco)
- Microsoft. Compute/disks (discos)
- Microsoft. Compute/galerias (galerias de imagens compartilhadas)
- microsoft.compute/galleries/applications
- microsoft.compute/galleries/applications/versions
- Microsoft. Compute/galerias/imagens (definições de imagem)
- Microsoft. Compute/galerias/imagens/versões (versões de imagem)
- Microsoft. Compute/hosts (grupos de hosts)
- Microsoft. Compute/hosts/hosts (hosts)
- Microsoft. Compute/images (imagens)
- Microsoft. Compute/ProximityPlacementGroups (grupos de posicionamento de proximidade)
- microsoft.compute/restorepointcollections
- microsoft.compute/sharedvmextensions
- microsoft.compute/sharedvmextensions/versions
- microsoft.compute/sharedvmimages
- microsoft.compute/sharedvmimages/versions
- Microsoft. Compute/Snapshots (instantâneos)
- Microsoft. Compute/sshPublicKeys (chaves SSH)
- microsoft.compute/swiftlets
- Microsoft. Compute/VirtualMachines (máquinas virtuais)
- microsoft.compute/virtualmachines/extensions
- microsoft.compute/virtualmachines/runcommands
- Microsoft. Compute/virtualMachineScaleSets (conjuntos de dimensionamento de máquinas virtuais)
- Microsoft. confluente/organizações (organizações confluentes)
- Microsoft. ConnectedCache/cacheNodes (recursos de cache conectados)
- Microsoft. connectedvehicle/platformaccounts
- Microsoft. connectedvmwarevsphere/ResourcePools
- Microsoft. connectedvmwarevsphere/vcenters
- Microsoft. connectedvmwarevsphere/VirtualMachines
- Microsoft. connectedvmwarevsphere/virtualmachinetemplates
- Microsoft. connectedvmwarevsphere/virtualnetworks
- Microsoft. ContainerInstance/containerGroups (instâncias de contêiner)
- Microsoft. ContainerRegistry/registros (registros de contêiner)
- microsoft.containerregistry/registries/agentpools
- microsoft.containerregistry/registries/buildtasks
- Microsoft. ContainerRegistry/registros/replicações (replicações de registro de contêiner)
- microsoft.containerregistry/registries/taskruns
- microsoft.containerregistry/registries/tasks
- Microsoft. ContainerRegistry/registros/WebHooks (datahooks do registro de contêiner)
- Microsoft. ContainerService/contêinerservices (serviços de contêiner (preterido))
- Microsoft. ContainerService/managedClusters (serviços Kubernetess)
- microsoft.containerservice/openshiftmanagedclusters
- Microsoft. contoso/clusters
- microsoft.contoso/employees
- Microsoft. contoso/Towers
- microsoft.costmanagement/connectors
- microsoft.customproviders/resourceproviders
- Microsoft. d365customerinsights/instâncias
- Microsoft. Data Box/Jobs (Data Box)
- Microsoft. DataBoxEdge/dataBoxEdgeDevices (Azure Stack Edge/Gateway do Data Box)
- Microsoft. databricks/espaços de trabalho (serviços Azure Databrickss)
- Microsoft. datacatalog/catálogos (catálogo de dados)
- microsoft.datacatalog/datacatalogs
- Microsoft. datacollaboration/Workspaces (CI do projeto)
- Microsoft. Datadog/monitores (Datadog)
- Microsoft. datafactory/datafactorings (fábricas de dados)
- Microsoft. datafactory/fábricas (data Factories (v2))
- Microsoft. DataLakeAnalytics/accounts (Data Lake Analytics)
- Microsoft. DataLakeStore/accounts (Data Lake Storage Gen1)
- Microsoft. datamigration/controladores
- Microsoft. datamigration/Services (serviços de migração de banco de dados do Azure)
- Microsoft. datamigration/serviços/projetos (projetos de migração de banco de dados do Azure)
- microsoft.datamigration/slots
- Microsoft. dataprotection/BackupVaults (cofres de backup)
- Microsoft. dataprotection/resourceoperationgatekeepers
- Microsoft. DataShare/accounts (compartilhamentos de dados)
- Microsoft. DBforMariaDB/servidores (banco de dados do Azure para servidores MariaDB)
- Microsoft. DBforMySQL/flexibleServers (banco de dados do Azure para servidores de MySQL flexíveis)
- Microsoft. DBforMySQL/servidores (banco de dados do Azure para servidores MySQL)
- Microsoft. DBforPostgreSQL/flexibleServers (banco de dados do Azure para PostgreSQL servidores flexíveis)
- Microsoft. DBforPostgreSQL/serverGroups (banco de dados do Azure para grupos de servidores PostgreSQL)
- Microsoft. dbforpostgresql/servergroupsv2
- Microsoft. DBforPostgreSQL/servidores (banco de dados do Azure para servidores PostgreSQL)
- Microsoft. DBforPostgreSQL/serversv2 (banco de dados do Azure para servidores PostgreSQL v2)
- microsoft.dbforpostgresql/singleservers
- Microsoft. delegatednetwork/Controller
- Microsoft. delegatednetwork/delegatedsubnets
- Microsoft. delegatednetwork/orchestratorinstances
- microsoft.deploymentmanager/artifactsources
- Microsoft. DeploymentManager/distribuições (distribuições)
- microsoft.deploymentmanager/servicetopologies
- microsoft.deploymentmanager/servicetopologies/services
- microsoft.deploymentmanager/servicetopologies/services/serviceunits
- microsoft.deploymentmanager/steps
- Microsoft. DesktopVirtualization/ApplicationGroups (grupos de aplicativos)
- Microsoft. DesktopVirtualization/HostPools (pools de hosts)
- Microsoft. DesktopVirtualization/ScalingPlans (planos de dimensionamento)
- Microsoft. DesktopVirtualization/Workspaces (espaços de trabalho)
- microsoft.devices/elasticpools
- microsoft.devices/elasticpools/iothubtenants
- Microsoft. Devices/IotHubs (Hub IoT)
- Microsoft. Devices/ProvisioningServices (serviços de provisionamento de dispositivos)
- Microsoft. DeviceUpdate/accounts (atualização de dispositivo para hubs IoT)
- Microsoft. deviceupdate/contas/instâncias
- Microsoft. DevOps/pipelines (iniciador DevOps)
- microsoft.devspaces/controllers
- microsoft.devtestlab/labcenters
- Microsoft. DevTestLab/Labs (DevTest Labs)
- microsoft.devtestlab/labs/servicerunners
- Microsoft. DevTestLab/Labs/virtualMachines (máquinas virtuais)
- microsoft.devtestlab/schedules
- Microsoft. DigitalTwins/digitalTwinsInstances (Azure digital gêmeos)
- Microsoft.DocumentDB/cassandraClusters (Azure Instância Gerenciada para Apache Cassandra)
- Microsoft.DocumentDb/databaseAccounts (contas de Azure Cosmos DB)
- Microsoft. DomainRegistration/Domains (domínios do serviço de aplicativo)
- Microsoft. edgeorder/endereços
- Microsoft. edgeorder/ordercollections
- Microsoft. edgeorder/Orders
- Microsoft. elástico/monitores (Elasticsearch)
- microsoft.enterpriseknowledgegraph/services
- Microsoft. EventGrid/Domains (domínios de grade de eventos)
- Microsoft. EventGrid/partnerNamespaces (namespaces de parceiro de grade de eventos)
- Microsoft. EventGrid/partnerRegistrations (registros de parceiros de grade de eventos)
- Microsoft. EventGrid/partnerTopics (tópicos de parceiro de grade de eventos)
- Microsoft. EventGrid/systemTopics (tópicos do sistema de grade de eventos)
- Microsoft. EventGrid/topics (tópicos de grade de eventos)
- Microsoft. EventHub/clusters (clusters de hubs de eventos)
- Microsoft. EventHub/namespaces (namespaces de hubs de eventos)
- Microsoft. Experimentation/experimentWorkspaces (espaços de trabalho de experimento)
- Microsoft. ExtendedLocation/CustomLocations (locais personalizados)
- microsoft.falcon/namespaces
- Microsoft. footprintmonitoring/perfis
- microsoft.gaming/titles
- Microsoft. genomas/contas (contas de genoma)
- microsoft.guestconfiguration/automanagedaccounts
- Microsoft. HanaOnAzure/hanaInstances (SAP HANA no Azure)
- Microsoft. HanaOnAzure/sapMonitors (monitores do Azure para soluções SAP)
- microsoft.hardwaresecuritymodules/dedicatedhsms
- Microsoft. HDInsight/clusters (clusters HDInsight)
- Microsoft. HealthBot/healthBots (bot de integridade do Azure)
- Microsoft. HealthcareApis/Services (API do Azure para FHIR)
- microsoft.healthcareapis/services/privateendpointconnections
- Microsoft. healthcareapis/Workspaces
- Microsoft. healthcareapis/Workspaces/dicomservices
- Microsoft. HybridCompute/computadores (servidores-Azure ARC)
- microsoft.hybridcompute/machines/extensions
- Microsoft. HybridCompute/privateLinkScopes (escopos de link privado do arco do Azure)
- Microsoft. HybridData/datamanagers (Gerenciador de dados do StorSimple)
- Microsoft. HybridNetwork/dispositivos (Gerenciador de funções de rede do Azure – dispositivos (visualização))
- Microsoft. HybridNetwork/networkFunctions (Gerenciador de funções de rede do Azure – funções de rede (visualização))
- Microsoft. hybridnetwork/virtualnetworkfunctions
- Microsoft. ImportExport/Jobs (trabalhos de importação/exportação)
- Microsoft. industrydatalifecycle/basemodels
- Microsoft. industrydatalifecycle/custodiancollaboratives
- microsoft.industrydatalifecycle/derivedmodels
- Microsoft. industrydatalifecycle/membercollaboratives
- Microsoft. industrydatalifecycle/modelmappings
- Microsoft. industrydatalifecycle/pipelinesets
- microsoft.insights/actiongroups
- microsoft.insights/activitylogalerts
- microsoft.insights/alertrules
- microsoft.insights/autoscalesettings
- Microsoft. insights/Components (Application Insights)
- Microsoft. insights/datacollectionrules (regras de coleta de dados)
- microsoft.insights/guestdiagnosticsettings
- microsoft.insights/metricalerts
- microsoft.insights/notificationgroups
- microsoft.insights/notificationrules
- Microsoft. insights/privateLinkScopes (escopos de link privado Azure Monitor)
- Microsoft. insights/querypacks
- microsoft.insights/scheduledqueryrules
- Microsoft. insights/webtestes (testes de disponibilidade)
- Microsoft. insights/pastas de trabalho (pastas de trabalho do Azure)
- Microsoft. insights/workbooktemplates (modelos de pasta de trabalho do Azure)
- Microsoft. IntelligentITDigitalTwin/digitalTwins (minervas)
- Microsoft. IntelligentITDigitalTwin/digitalTwins/ativos (ativos)
- Microsoft. IntelligentITDigitalTwin/digitalTwins/executionPlans (implantações)
- Microsoft. IntelligentITDigitalTwin/digitalTwins/testPlans (Suites)
- Microsoft. IntelligentITDigitalTwin/digitalTwins/Tests (scripts)
- Microsoft. IoTCentral/IoTApps (aplicativos IoT Central)
- Microsoft. IoTSpaces/Graph (digital gêmeos (preterido))
- microsoft.keyvault/hsmpools
- Microsoft. keyvault/managedhsms
- Microsoft. keyvault/cofres (cofres de chaves)
- Microsoft. kubernetes/connectedClusters (kubernetes-Azure ARC)
- Microsoft. Kusto/clusters (clusters do Azure Data Explorer)
- Microsoft. Kusto/clusters/bancos de dados (bancos de dados do Azure Data Explorer)
- Microsoft. LabServices/labAccounts (serviços de laboratório)
- Microsoft. LoadTestService/Load testes (testes de carga nativos de nuvem)
- Microsoft. Logic/integrationAccounts (contas de integração)
- Microsoft. Logic/integrationServiceEnvironments (ambientes de serviço de integração)
- Microsoft. Logic/integrationServiceEnvironments/managedApis (conector gerenciado)
- Microsoft. Logic/workflows (aplicativos lógicos)
- Microsoft. LOGZ/Monitors (conta principal do LOGZ)
- Microsoft. LOGZ/monitores/contas (subconta LOGZ)
- Planos de serviço Web Microsoft. MachineLearning/commitmentPlans (Machine Learning Studio (clássico))
- Microsoft. MachineLearning/WebServices (Machine Learning Studio (clássico) serviços Web)
- Espaços de trabalho Microsoft. MachineLearning/Workspaces (Machine Learning Studio (clássico))
- microsoft.machinelearningcompute/operationalizationclusters
- Microsoft. machinelearningservices/modelinventories
- Microsoft. machinelearningservices/modelinventory
- Microsoft. machinelearningservices/virtualclusters
- Microsoft. MachineLearningServices/Workspaces (aprendizado de máquina)
- Microsoft. machinelearningservices/Workspaces/batchendpoints
- Microsoft. machinelearningservices/Workspaces/batchendpoints/implantações
- Microsoft. machinelearningservices/Workspaces/inferenceendpoints
- Microsoft. machinelearningservices/Workspaces/inferenceendpoints/implantações
- Microsoft. MachineLearningServices/Workspaces/onlineEndpoints (aplicativos ML)
- Microsoft. MachineLearningServices/Workspaces/onlineEndpoints/Implantations (implantações de aplicativo ML)
- Microsoft. Maintenance/maintenanceConfigurations (configurações de manutenção)
- microsoft.maintenance/maintenancepolicies
- microsoft.managedidentity/groups
- Microsoft. ManagedIdentity/userAssignedIdentities (identidades gerenciadas)
- microsoft.managednetwork/managednetworkgroups
- microsoft.managednetwork/managednetworkpeeringpolicies
- microsoft.managednetwork/managednetworks
- microsoft.managednetwork/managednetworks/managednetworkgroups
- microsoft.managednetwork/managednetworks/managednetworkpeeringpolicies
- Microsoft. Maps/contas (contas do Azure Maps)
- Microsoft. Maps/contas/criadores
- Microsoft. Maps/accounts/privateAtlases (recursos do Azure Maps Creator)
- Microsoft. MarketplaceApps/classicDevServices (serviços de desenvolvimento clássicos)
- Microsoft. Media/mediaservices (serviços de mídia)
- Microsoft. Media/mediaservices/liveevents (eventos ao vivo)
- Microsoft. Media/mediaservices/streamingEndpoints (pontos de extremidade de streaming)
- microsoft.media/mediaservices/transforms
- Microsoft. Media/videoanalyzers
- microsoft.microservices4spring/appclusters
- microsoft.migrate/assessmentprojects
- microsoft.migrate/migrateprojects
- microsoft.migrate/movecollections
- Microsoft. migrar/Projects (projetos de migração)
- Microsoft. MixedReality/holographicsBroadcastAccounts (contas de difusão holographics)
- Microsoft. MixedReality/objectAnchorsAccounts (contas de âncoras de objeto)
- Microsoft. MixedReality/objectUnderstandingAccounts (contas de compreensão de objeto)
- Microsoft. MixedReality/remoteRenderingAccounts (contas de renderização remota)
- Microsoft. MixedReality/spatialAnchorsAccounts (contas de âncoras espaciais)
- microsoft.mixedreality/surfacereconstructionaccounts
- Microsoft. mobilenetwork/Networks
- Microsoft. mobilenetwork/redes/sites
- Microsoft. mobilenetwork/Sims
- Microsoft. mobilenetwork/Sims/simprofiles
- Microsoft. NetApp/netAppAccounts (contas do NetApp)
- microsoft.netapp/netappaccounts/backuppolicies
- Microsoft. NetApp/netAppAccounts/capacityPools (pools de capacidade)
- Microsoft. NetApp/netAppAccounts/capacityPools/volumes (volumes)
- microsoft.netapp/netappaccounts/capacitypools/volumes/mounttargets
- Microsoft. NetApp/netAppAccounts/capacityPools/volumes/instantâneos (instantâneos)
- Microsoft. Network/applicationGateways (gateways de aplicativo)
- Microsoft. Network/ApplicationGatewayWebApplicationFirewallPolicies (políticas de firewall do aplicativo Web (WAF))
- Microsoft. Network/applicationSecurityGroups (grupos de segurança de aplicativo)
- Microsoft. Network/azureFirewalls (firewalls)
- Microsoft. Network/bastionHosts (bastiões)
- Microsoft. Network/Connections (conexões)
- Microsoft. Network/customipprefixes
- microsoft.network/ddoscustompolicies
- Microsoft. Network/ddosProtectionPlans (planos de proteção contra DDoS)
- Microsoft. Network/dnsZones (zonas DNS)
- Microsoft. Network/dscpconfigurations
- Microsoft. Network/expressRouteCircuits (circuitos de ExpressRoute)
- microsoft.network/expressroutecrossconnections
- microsoft.network/expressroutegateways
- Microsoft. Network/expressRoutePorts (ExpressRoute Direct)
- Microsoft. Network/firewallPolicies (políticas de firewall)
- Microsoft. Network/frontdoors (portas frontais)
- Microsoft. Network/FrontDoorWebApplicationFirewallPolicies (políticas de firewall do aplicativo Web (WAF))
- microsoft.network/ipallocations
- Microsoft. Network/ipGroups (grupos de IP)
- Microsoft. Network/Load balancers (balanceadores de carga)
- Microsoft. Network/localnetworkgateways (gateways de rede local)
- Microsoft. Network/mastercustomipprefixes
- Microsoft. Network/natGateways (gateways NAT)
- Microsoft. Network/NetworkExperimentProfiles (perfis do Internet Analyzer)
- microsoft.network/networkintentpolicies
- Microsoft. Network/NetworkInterfaces (interfaces de rede)
- Microsoft. Network/networkManagers (gerenciadores de rede)
- microsoft.network/networkprofiles
- Microsoft. Network/NetworkSecurityGroups (grupos de segurança de rede)
- microsoft.network/networkvirtualappliances
- Microsoft. Network/networkwatchers (observadores de rede)
- microsoft.network/networkwatchers/connectionmonitors
- Microsoft. Network/networkwatchers/flowlogs (logs de fluxo de NSG)
- microsoft.network/networkwatchers/lenses
- microsoft.network/networkwatchers/pingmeshes
- microsoft.network/p2svpngateways
- Microsoft. Network/privateDnsZones (zonas de DNS privado)
- microsoft.network/privatednszones/virtualnetworklinks
- microsoft.network/privateendpointredirectmaps
- Microsoft. Network/privateEndpoints (pontos de extremidade privados)
- Microsoft. Network/privateLinkServices (Private link Services)
- Microsoft. Network/PublicIpAddresses (endereços IP públicos)
- Microsoft. Network/publicIpPrefixes (prefixos de IP público)
- Microsoft. Network/routeFilters (filtros de rota)
- Microsoft. Network/routeTables (tabelas de rotas)
- microsoft.network/sampleresources
- microsoft.network/securitypartnerproviders
- Microsoft. Network/serviceEndpointPolicies (políticas de ponto de extremidade de serviço)
- Microsoft. Network/trafficmanagerprofiles (perfis do Gerenciador de tráfego)
- microsoft.network/virtualhubs
- Microsoft. Network/virtualhubs/bgpconnections
- Microsoft. Network/virtualhubs/ipconfigurations
- Microsoft. Network/virtualNetworkGateways (gateways de rede virtual)
- Microsoft. Network/virtualNetworks (redes virtuais)
- microsoft.network/virtualnetworktaps
- microsoft.network/virtualrouters
- Microsoft. Network/virtualWans (WANs virtuais)
- microsoft.network/vpngateways
- microsoft.network/vpnserverconfigurations
- microsoft.network/vpnsites
- Microsoft. NotificationHubs/namespaces (namespaces do hub de notificação)
- Microsoft. NotificationHubs/namespaces/notificationHubs (hubs de notificação)
- Microsoft. nutanix/interfaces
- Microsoft. nutanix/nós
- microsoft.objectstore/osnamespaces
- microsoft.offazure/hypervsites
- microsoft.offazure/importsites
- Microsoft. offazure/mastersites
- microsoft.offazure/serversites
- microsoft.offazure/vmwaresites
- Microsoft. OpenLogisticsPlatform/Workspaces (plataforma de cadeia de suprimentos aberta)
- microsoft.operationalinsights/clusters
- Microsoft. OperationalInsights/querypacks (pacotes de consulta Log Analytics)
- Microsoft. OperationalInsights/Workspaces (espaços de trabalho do Log Analytics)
- Microsoft. OperationsManagement/Solutions (soluções)
- microsoft.operationsmanagement/views
- Microsoft. orbital/contactprofiles
- Microsoft. orbital/spacecrafts
- Microsoft. emparelhamento/emparelhamentos (emparelhamentos)
- Microsoft. emparelhamento/peeringServices (serviços de emparelhamento)
- Microsoft. Portal/dashboards (painéis compartilhados)
- microsoft.portalsdk/rootresources
- Microsoft. powerbi/privatelinkservicesforpowerbi
- Microsoft. powerbi/locatários
- microsoft.powerbi/workspacecollections
- Microsoft. powerbidedicated/autoscalevcores
- Microsoft. PowerBIDedicated/capacidades (Power BI Embedded)
- Microsoft. ProjectBabylon/accounts (contas do Babylon)
- Microsoft. alcance/accounts (contas do alcance)
- Microsoft. Quantum/Workspaces (espaços de trabalho do Quantum)
- Microsoft. Recoveryservices/cofres (cofres dos serviços de recuperação)
- Microsoft. RedHatOpenShift/openShiftClusters (clusters OpenShift)
- Microsoft. Relay/namespaces (retransmissões)
- microsoft.remoteapp/collections
- Microsoft. resiliência/chaosexperiments
- Microsoft. ResourceConnector/Appliances (dispositivos)
- Microsoft. resourcegraph/Queries (consultas de grafo de recursos)
- Microsoft. Resources/deploymentScripts (scripts de implantação)
- Microsoft. Resources/templateSpecs (especificações do modelo)
- microsoft.resources/templatespecs/versions
- Microsoft. SaaS/Applications (software como serviço (clássico))
- Microsoft. SaaS/Resources (SaaS)
- Microsoft. Scheduler/gratuitas (coleções de trabalhos do Agendador)
- Microsoft. SCVMM/nuvens
- Microsoft. SCVMM/virtualMachines (máquina virtual do SCVMM – arco do Azure)
- Microsoft. SCVMM/virtualmachinetemplates
- Microsoft. SCVMM/virtualnetworks
- Microsoft. SCVMM/vmmservers
- Microsoft. Search/SearchServices (serviços de pesquisa)
- microsoft.security/automations
- microsoft.security/iotsecuritysolutions
- Microsoft. SecurityDetonation/limpar (segurança denotação limpar)
- Microsoft. ServiceBus/namespaces (namespaces do barramento de serviço)
- Microsoft. infabric/clusters (clusters de Service Fabric)
- microsoft.servicefabric/containergroupsets
- Microsoft. infabric/managedclusters (Service Fabric clusters gerenciados)
- Microsoft. ServiceFabricMesh/Applications (aplicativos de malha)
- microsoft.servicefabricmesh/gateways
- microsoft.servicefabricmesh/networks
- microsoft.servicefabricmesh/secrets
- microsoft.servicefabricmesh/volumes
- Microsoft. ServicesHub/Connectors (conectores de Hub de serviços)
- Microsoft. SignalRService/Signalr (Signalr)
- Microsoft. singularidades/contas
- microsoft.solutions/appliancedefinitions
- microsoft.solutions/appliances
- Microsoft. Solutions/applicationDefinitions (definições de aplicativo gerenciado pelo catálogo de serviços)
- Microsoft. Solutions/Applications (aplicativos gerenciados)
- microsoft.solutions/jitrequests
- microsoft.spoolservice/spools
- Microsoft. SQL/instancePools (pools de instância)
- Microsoft. SQL/managedInstances (instâncias gerenciadas do SQL)
- Microsoft. SQL/managedInstances/bancos de dados (bancos de dados gerenciados)
- Microsoft. SQL/Servers (SQL Servers)
- Microsoft. SQL/servidores/bancos de dados (bancos de dados SQL)
- Microsoft. SQL/Servers/elasticpools (pools elásticos do SQL)
- microsoft.sql/servers/jobaccounts
- Microsoft. SQL/Servers/jobAgents (agentes de trabalho elástico)
- Microsoft. SQL/virtualClusters (clusters virtuais)
- microsoft.sqlvirtualmachine/sqlvirtualmachinegroups
- Microsoft. SqlVirtualMachine/SqlVirtualMachines (máquinas virtuais do SQL)
- microsoft.sqlvm/dwvm
- Microsoft. Storage/StorageAccounts (contas de armazenamento)
- Microsoft. storagecache/amlfilesystems
- Microsoft. StorageCache/caches (caches HPC)
- Microsoft. storagepool/diskpools
- Microsoft. StorageSync/storageSyncServices (serviços de sincronização de armazenamento)
- Microsoft. StorageSyncDev/storageSyncServices (serviços de sincronização de armazenamento)
- Microsoft. StorageSyncInt/storageSyncServices (serviços de sincronização de armazenamento)
- Microsoft. StorSimple/Managers (gerenciadores de dispositivos StorSimple)
- Microsoft. StreamAnalytics/clusters (clusters de Stream Analytics)
- Microsoft. StreamAnalytics/StreamingJobs (trabalhos de Stream Analytics)
- Microsoft. swiftlet/VirtualMachines
- Microsoft. swiftlet/virtualmachinesnapshots
- Microsoft. Synapse/privateLinkHubs (Azure Synapse Analytics (hubs de link privado))
- Microsoft. Synapse/Workspaces (análise de Synapse do Azure)
- Microsoft. Synapse/Workspaces/bigDataPools (pools de Apache Spark)
- Microsoft. Synapse/Workspaces/sqldatabases
- Microsoft. Synapse/espaços de trabalho/sqlpools (pools SQL dedicados)
- microsoft.terraformoss/providerregistrations
- Microsoft. testararquitetura/testbases
- Microsoft. TimeSeriesInsights/ambientes (ambientes de Time Series Insights)
- Microsoft. TimeSeriesInsights/ambientes/EventSources (Time Series Insights fontes de eventos)
- Microsoft. TimeSeriesInsights/Environments/referenceDataSets (Time Series Insights conjuntos de dados de referência)
- microsoft.token/stores
- microsoft.tokenvault/vaults
- Microsoft. VirtualMachineImages/imageTemplates (modelos de imagem)
- Microsoft. VisualStudio/Account (organizações do Azure DevOps)
- microsoft.visualstudio/account/extension
- Microsoft. VisualStudio/Account/Project (iniciante DevOps)
- microsoft.vmware/arczones
- microsoft.vmware/resourcepools
- microsoft.vmware/vcenters
- Microsoft. VMware/VirtualMachines (máquinas virtuais da AVS)
- microsoft.vmware/virtualmachinetemplates
- microsoft.vmware/virtualnetworks
- Microsoft. VMwareCloudSimple/dedicatedCloudNodes (nós CloudSimple)
- Microsoft. VMwareCloudSimple/dedicatedCloudServices (serviços CloudSimples)
- Microsoft. VMwareCloudSimple/virtualMachines (máquinas virtuais CloudSimple)
- microsoft.vmwareonazure/privateclouds
- microsoft.vmwarevirtustream/privateclouds
- microsoft.vsonline/accounts
- Microsoft. VSOnline/Plans (planos do Visual Studio online)
- Microsoft. Web/apimanagementaccounts
- microsoft.web/apimanagementaccounts/apis
- microsoft.web/certificates
- Microsoft. Web/connectionGateways (gateways de dados locais)
- Microsoft. Web/Connections (conexões de API)
- Microsoft. Web/customApis (conector personalizado de aplicativos lógicos)
- Microsoft. Web/HostingEnvironments (ambientes de serviço de aplicativo)
- Microsoft. Web/KubeEnvironments (ambientes de kubernetes do serviço de aplicativo)
- Microsoft. Web/serverFarms (planos do serviço de aplicativo)
- Microsoft. Web/sites (serviços de aplicativos)
- microsoft.web/sites/premieraddons
- Microsoft. Web/sites/slots (serviço de aplicativo (slots))
- Microsoft. Web/StaticSites (aplicativos Web estáticos (visualização))
- Microsoft. WindowsESU/multipleActivationKeys (chaves de ativação múltipla do Windows)
- Microsoft. WindowsIoT/deviceservices (serviços do Windows 10 IoT Core)
- Microsoft. workloadbuilder/migrationagents
- Microsoft. workloadbuilder/cargas de trabalho
- MyGet. PackageManagement/Services (NuGet hospedado MyGet, NPM, Bower e VSIX)
- Paraleap. CloudMonix/Services (CloudMonix)
- Pokitdok. plataforma/serviços (plataforma PokitDok)
- Providers. Test/statefulIbizaEngines (avaliações do aplicativo)
- providers.test/statefulresources
- providers.test/statefulresources/nestedresources
- providers.test/statelessresources
- RavenHq. DB/bancos de dados (RavenHQ)
- O Raygun. CrashReporting/apps (O Raygun)
- Sendgrid. email/contas (contas de SendGrid)
- Sparkpost. Basic/Services (SparkPost)
- stackify. retrace/Services (Stackify)
- test.shoebox/testresources
- test.shoebox/testresources2
- TrendMicro. DeepSecurity/contas (SaaS de segurança profunda)
- U2uconsult. TheIdentityHub/Services (o Hub de identidade)
- Wandisco. Fusion/fusionGroups (planos de LiveData)
- Wandisco. Fusion/fusionGroups/azureZones (zonas do Azure)
- Wandisco. Fusion/fusionGroups/azureZones/plugins (plugins)
- Wandisco. Fusion/fusionGroups/hiveReplicationRules (regras de replicação do hive)
- Wandisco. Fusion/fusionGroups/managedOnPremZones (zonas locais)
- wandisco.fusion/fusiongroups/onpremzones
- Wandisco. Fusion/fusionGroups/replicationRules (regras de replicação)
- Wandisco. Fusion/migrators (LiveData migrators)
- Wandisco. Fusion/migrators/liveDataMigrations (migrações)
- Wandisco. Fusion/migrators/targets (destinos)

## <a name="securityresources"></a>securityresources

- microsoft.security/assessments
- microsoft.security/assessments/subassessments
- Microsoft. Security/iotalerts
- Microsoft. Security/Locations/Alerts (alertas de segurança)
- microsoft.security/pricings
- microsoft.security/regulatorycompliancestandards
- microsoft.security/regulatorycompliancestandards/regulatorycompliancecontrols
- microsoft.security/regulatorycompliancestandards/regulatorycompliancecontrols/regulatorycomplianceassessments
- Microsoft. Security/securescores
- Microsoft. Security/securescores/securescorecontrols

## <a name="servicehealthresources"></a>servicehealthresources

- microsoft.resourcehealth/events

## <a name="workloadmonitorresources"></a>workloadmonitorresources

- Microsoft. workloadmonitor/monitores

## <a name="next-steps"></a>Próximas etapas

- Saiba mais sobre a [linguagem de consulta](../concepts/query-language.md).
- Saiba mais sobre como [explorar recursos](../concepts/explore-resources.md).
- Veja exemplos de [Consultas iniciais](../samples/starter.md).
