# **VPN**

### ****

### **VPN概述**

VPN连接利用公网架设专用网络，通过加密通道实现外部用户内网访问、跨地域内网互通等。例如可通过VPN专用网络连接企业数据中心和京东云私有网络，提供安全可靠的混合云部署。

### **VPN产品功能**

1. 
安全可靠的专用通道

京东云VPN使用IPSEC、IKE、预共享密钥方式对数据进行加密，基于公网提供安全可靠的通信隧道。

2. 灵活的组网方式，支持多隧道共享网关

支持VPN网关下组建多条隧道（需不同的对端网关），提供相对灵活的组网方式，应对不同业务场景需求。

3. 隧道连通性检测，保证隧道可用性

VPN默认提供隧道连通性自动检测，定时检测隧道的连通状况，并实时更新当前隧道的可用状态。

### **VPN产品优势**

对比昂贵的专线和自建VPN服务，京东云VPN具有明显的优势：

1. 
操作简单

京东云VPN通过控制台操作，流程简单，可按需购买，即买即用，方便管理；自建VPN需单独购买镜像、配置复杂，需专业人员操作。

2. 高安全性

京东云VPN使用IPSEC、IKE协议进行加密通信，数据传输安全可靠；自建VPN达到同样的安全级别需单独购买 VPN License。

3. 低成本

可根据具体业务需求创建、删除VPN隧道和网关，提供灵活的计费方式（配置计费/包年包月）；自建VPN需单独采购相关配件、专配备业的运维人员。

## **VPN应用场景**

企业数据中心+京东云混合云部署

通过VPN可实现企业数据中心+京东云混合云部署，例如可将应用部署在京东云私有网络，而将数据库部署在企业数据中心，双方通过VPN加密隧道进行通信，可保证数据在公网安全、可靠传输。

![](https://img1.jcloudcs.com/cms/287db89e-22db-4690-8c0e-b1a76349492e20170329161731.png)

## **操作指南**

****

## **创建VPN网关**

1. 
通过菜单-网络-VPN进入VPN列表页；
1. 
点击“创建”新建一个VPN网关；
1. 
选择地域，注意和需要选择的路由器（子网）所在地域保持一致；
1. 
输入VPN名称；
1. 
选择已有的路由器或新建路由器，与VPN网关进行绑定；
1. 
选择公网IP线路（BGP或非BGP）、对应带宽上限，会自动新建公网IP，与VPN网关进行绑定；
1. 
通过右侧“计费类型”可切换购买方式：按配置、包年/包月；
1. 
点击“立即支付”并确认支付成功，完成VPN网关创建；因资源创建需一定时间（通常为几秒），可手动刷新列表页查看状态。
![](https://img1.jcloudcs.com/cms/f9b77e5e-a498-4e79-8631-fe96787a5cd720170329162434.png)

### **创建对端网关**

1. 
输入对端网关的名称；
1. 
输入对端网关的公网地址，对端网关公网IP地址不能重复。
![](https://img1.jcloudcs.com/cms/7a4212ec-6ee9-4412-8ad9-ce15473ba41220170329162502.png)

### **创建VPN隧道**

1. 
选择VPN隧道地域；
1. 
输入VPN隧道名称；
1. 
本端配置：选择该地域下的VPN网关及对应路由器下的子网，最多允许选择10个本端子网；
1. 
对端配置：选择对端网关，输入对端子网的CIDR，最多允许输入10个对端子网；
1. 
本端子网和对端子网不允许存在重复的网络，对端网络之间不允许出现重复的网络，即网络地址不能重复；
1. 
输入预共享密钥；
1. 
配置隧道的IPSec属性：认证算法、加密算法、PFS、 IPSec-SA-LifeTime(秒)；
1. 
配置隧道的IKE属性：IKE版本、认证算法、加密算法、协商模式、PFS、IKE-SA-LifeTime(秒)；
1. 
确定后，VPN隧道处于创建中状态，隧道创建完成后，状态变为“可用”或“不可用”，若对端的VPN网关之前已进行过同样配置，则可直接建立连接。

![](https://img1.jcloudcs.com/cms/0fecf3ba-82d3-475f-b922-360faa07cf4e20170329162611.png)![](https://img1.jcloudcs.com/cms/484866e0-428f-45c3-b6ce-4faa04b7962220170329162641.png)![](https://img1.jcloudcs.com/cms/7520958b-744b-473e-9155-c1ebcfdb265c20170329162646.png)![](https://img1.jcloudcs.com/cms/b07ab81f-b059-418d-9aed-4f3dcf3494a220170329162658.png)

### **下载配置文件**

1. 
若对端的VPN网关之前未进行过配置，可在VPN隧道列表页-操作栏下载创建的VPN隧道的配置文件，在对端导入该配置并重置VPN隧道后即可建立VPN连接；
1. 
配置文件下载说明：支持cisco（厂商）-IOS（操作系统）-12.3(11)T（版本），华为（厂商）-vrp（操作系统）-V100R001（版本）。
![](https://img1.jcloudcs.com/cms/d4a5c65a-736a-477e-89ad-4d6ed5ec302720170329162738.png)![](https://img1.jcloudcs.com/cms/98fe30fb-07b3-4b94-a20b-be831b84cde020170329162743.png)

### **重置VPN隧道**

1. 
通过VPN隧道列表页-操作栏，可进行VPN隧道重置，更新网关配置信息；
1. 
重置隧道时，会终止现有VPN隧道并重新建立连接，故请您提前做好VPN断开的准备。
![](https://img1.jcloudcs.com/cms/7695b483-f1bb-47e6-b549-638dc0d5c62c20170329162810.png)

### **删除VPN隧道**

通过VPN隧道列表页-操作栏，可删除VPN隧道。

### **删除VPN网关**

通过VPN网关列表-操作栏，可删除VPN网关。注意：如该VPN网关下有关联的隧道，则需要先删除隧道后才能删除VPN网关；同理对端网关需同样处理。

### **配置IPSEC**

1. 
已创建的VPN隧道支持修改IPSec配置；
1. 
IPSec配置项同创建隧道时的选项；
1. 
修改配置后，需下载该VPN隧道的配置文件，在对端导入新配置并重置VPN隧道后才能建立VPN隧道连接。
![](https://img1.jcloudcs.com/cms/d1b027f1-b63d-41e4-8108-b261ae2d2bbf20170329162833.png)

### **配置IKE**

1. 
已创建的VPN隧道支持修改IKE配置；
1. 
IKE配置项同创建隧道时的选项；
1. 
修改配置后，需下载该VPN隧道的配置文件，在对端导入新配置并重置VPN隧道后才能建立VPN隧道连接。
![](https://img1.jcloudcs.com/cms/bf8a9221-1e62-40d7-a09e-0cf7ed94802920170329162848.png)