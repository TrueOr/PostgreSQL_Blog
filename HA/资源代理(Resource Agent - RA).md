### Resource Agent集群资源代理
* 在 Pacemaker集群中，每一个原始资源都有一个资源代理(Resource Agent, RA), RA是一个与资源相关的外部脚本程序，该程序抽象了资源本身所提供的服务并向集群呈现一致的视图以供集群对该资源进行操作控制。通过 RA,几乎任何应用程序都可以成为 Pacemaker集群的资源从而被集群资源管理器和控制。RA的存在，使得集群资源管理器可以对其所管理的资源“不求甚解"，即集群资源管理器无需知道资源具体的工作逻辑和原理（ RA已将其封装），资源管理器只需向 RA发出 start、 stop、Monitor等命令， RA便会执行相应的操作。从资源管理器对资源的控制过程来看，集群对资源的管理完全依赖于该资源所提供的，即资源的 RA脚本功能直接决定了资源管理器可以对该资源进行何种控制，因此一个功能完善的 RA在发行之前必须经过充分的功能测试。在多数情况下，资源 RA以 shell脚本的形式提供，当然也可以使用其他比较流行的如 c、 python、 perl等语言来实现 RA。
	
Pacemaker 支持三种类型的 RA：<br>
* [LSB Resource Agents](http://www.linux-ha.org/wiki/LSB_Resource_Agents)<br>
* [OCF Resource Agents](http://www.linux-ha.org/wiki/OCF_Resource_Agents)<br>
* [legacy Heartbeat Resource Agents](http://www.linux-ha.org/wiki/Heartbeat_Resource_Agents)<br>

主流的 RA 都是 OCF 类型的。RA 支持的主要操作包括： <br>
* start: enable or start the given resource	<br>
* stop: disable or stop the given resource	<br>
* monitor: check whether the given resource is running (and/or doing useful work), return status as running or not running<br>
* validate-all: validate the resource's configuration<br>
* meta-data: return information about the resource agent itself (used by GUIs and other management utilities, and documentation tools)<br>
* some more, see  [OCF Resource Agents](http://www.linux-ha.org/wiki/OCF_Resource_Agents) and the [Pacemaker documentation](http://clusterlabs.org/doc/) for details. <br>
更多RA脚本请转https://github.com/ClusterLabs/resource-agents

### RA 的配置


