---
title: 为 Power BI 报表服务器创建 Power BI 报表
description: 了解如何通过执行简单几步为 Power BI 报表服务器创建 Power BI 报表。
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-report-server
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: maggies
ms.openlocfilehash: 64757d6cbd82b666bf18f1ee87d8e51954872990
ms.sourcegitcommit: 67336b077668ab332e04fa670b0e9afd0a0c6489
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "44726722"
---
# <a name="create-a-power-bi-report-for-power-bi-report-server"></a>为 Power BI 报表服务器创建 Power BI 报表
可以在 Power BI 报表服务器 Web 门户中在本地存储和管理 Power BI 报表，就像在 Power BI 服务 (https://powerbi.com)) 中的云中存储 Power BI 报表一样。 可以在 Power BI Desktop 中创建和编辑报表，并将其发布到 Web 门户中。 接下来，组织中的报表读取器可以在浏览器或移动设备上的 Power BI 移动应用中查看报表。

![Web 门户中的 Power BI 报表](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

可以遵循以下四个步骤入门。

## <a name="step-1-install-power-bi-desktop-optimized-for-power-bi-report-server"></a>步骤 1：安装已针对 Power BI 报表服务器进行优化的 Power BI Desktop

如果已在 Power BI Desktop 中创建 Power BI 报表，便可以开始为 Power BI 报表服务器创建 Power BI 报表。 建议安装更适合 Power BI 报表服务器的 Power BI Desktop 版本，这样就能确定服务器和应用始终同步。可以在同一台计算机上安装两个版本的 Power BI Desktop。

1. 在报表服务器 Web 门户中，选择“下载”箭头 >“Power BI Desktop”。

    ![从 Web 门户下载 Power BI Desktop](media/quickstart-create-powerbi-report/report-server-download-web-portal.png)

    或者，在 Microsoft 下载中心直接转到 [Microsoft Power BI Desktop](https://www.microsoft.com/download/details.aspx?id=56723)（已针对 Power BI 报表服务器进行优化 - 2018 年 3 月版）。

2. 在“下载中心”页中，选择“下载”。

3. 根据所用的计算机选择：

    - **PBIDesktopRS.msi**（32 位版本）或

    - **PBIDesktopRS_x64.msi**（64 位版本）。

4. 下载安装程序后，运行 Power BI Desktop（2018 年 3 月版）安装向导。

2. 安装结束时，请选中“立即启动 Power BI Desktop”。
   
    此时，它会自动启动，可以开始使用了。 根据标题栏中显示的“Power BI Desktop（2018 年 3 月版）”，便知道使用了正确的版本。

    ![Power BI Desktop 2018 年 3 月版](media/quickstart-create-powerbi-report/report-server-desktop-march-2018.png)

3. 如果不熟悉 Power BI Desktop，请考虑观看欢迎屏幕上的视频。
   
    ![Power BI Desktop 开始屏幕](media/quickstart-create-powerbi-report/report-server-powerbi-desktop-start.png)

## <a name="step-2-select-a-data-source"></a>第 2 步：选择数据源
可以连接到各种数据源。 详细了解如何[连接数据源](connect-data-sources.md)。

1. 在欢迎屏幕上，选择“获取数据”。
   
    在“开始”选项卡上，选择“获取数据”。
2. 选择你的数据源 - 本例中为 Analysis Services。
   
    ![选择数据源](media/quickstart-create-powerbi-report/report-server-get-data-ssas.png)
3. 填写“服务器”，并视需要填写“数据库”。 务必选中“实时连接”，然后单击“确定”。
   
    ![服务器名称](media/quickstart-create-powerbi-report/report-server-ssas-server-name.png)
4. 选择将要保存你的报表的报表服务器。
   
    ![报表服务器选择](media/quickstart-create-powerbi-report/report-server-select-server.png)

## <a name="step-3-design-your-report"></a>第 3 步：设计报表
有意思的是，可以创建视觉对象来显示数据。

例如，可以创建按年收入显示客户和组值的漏斗图。

![设计报表](media/quickstart-create-powerbi-report/report-server-create-funnel.png)

1. 在“可视化效果”中，选择“漏斗图”。
2. 将要计入的字段拖到“值”井中。 如果不是数值字段，Power BI Desktop 会自动将其转换成值计数。
3. 将要分组的字段拖到“组”井中。

请阅读有关[设计 Power BI 报表](../desktop-report-view.md)的详细信息。

## <a name="step-4-save-your-report-to-the-report-server"></a>第 4 步：将报表保存到报表服务器
创建并设计完报表后，可以将其保存到步骤 2 中所选的 Power BI 报表服务器。

1. 在“文件”菜单上，依次选择“另存为” > “Power BI 报表服务器”。
   
    ![保存到报表服务器](media/quickstart-create-powerbi-report/report-server-save-as-powerbi-report-server.png)
2. 现在可以在 Web 门户中查看报表。
   
    ![在 Web 门户中查看报表](media/quickstart-create-powerbi-report/report-server-powerbi-report.png)

## <a name="considerations-and-limitations"></a>注意事项和限制
Power BI 报表服务器和 Power BI 服务 (http://powerbi.com)) 中报表的行为几乎完全相同，但有一些功能不同。

### <a name="in-a-browser"></a>在浏览器中
Power BI 报表服务器报表支持所有可视化效果，包括：

* 自定义视觉对象

Power BI 报表服务器报表不支持：

* R 视觉对象
* ArcGIS 地图
* 痕迹导航栏
* Power BI Desktop 预览功能

### <a name="in-the-power-bi-mobile-apps"></a>在 Power BI 移动应用中
Power BI 报表服务器报表支持 [Power BI 移动应用](../consumer/mobile/mobile-apps-for-mobile-devices.md)中的所有基本功能，其中包括：

* [手机报表布局](../desktop-create-phone-report.md)：可以优化 Power BI 移动应用的报表。 在你的移动手机上，已优化的报表都具有一个特殊的图标 ![手机报表布局图标](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-icon.png) 和布局。
  
    ![针对手机优化后的报表](media/quickstart-create-powerbi-report/power-bi-rs-mobile-optimized-report.png)

Power BI 报表服务器报表不支持 Power BI 移动应用中的如下功能：

* R 视觉对象
* ArcGIS 地图
* 自定义视觉对象
* 痕迹导航栏
* 地理位置筛选或条码

## <a name="next-steps"></a>后续步骤
### <a name="power-bi-desktop"></a>Power BI Desktop
若要了解如何在 Power BI Desktop 中创建报表，可以参阅许多有价值的资源。 此链接是一个良好的开端。

* [Power BI Desktop 入门](../desktop-getting-started.md)
* 引导式学习：[Power BI Desktop 入门](../guided-learning/gettingdata.yml?tutorial-step=2)

### <a name="power-bi-report-server"></a>Power BI 报表服务器
* [安装更适合 Power BI 报表服务器的 Power BI Desktop](install-powerbi-desktop.md)  
* [什么是 Power BI 报表服务器？](get-started.md)  

更多问题？ [尝试咨询 Power BI 社区](https://community.powerbi.com/)
