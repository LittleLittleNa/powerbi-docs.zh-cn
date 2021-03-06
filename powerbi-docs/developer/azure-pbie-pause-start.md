---
title: 在 Azure 门户中暂停和启动 Power BI Embedded 容量 | Microsoft Docs
description: 本文介绍如何在 Microsoft Azure 中暂停和启动 Power BI Embedded 容量。
services: power-bi-embedded
author: markingmyname
ms.author: maghan
manager: kfile
editor: ''
tags: ''
ms.service: power-bi-embedded
ms.topic: conceptual
ms.date: 09/28/2017
ms.openlocfilehash: 9f939c0eae4f7ea1f24eec473549dc00191f1b67
ms.sourcegitcommit: fecea174721d0eb4e1927c1116d2604a822e4090
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/31/2018
ms.locfileid: "39360146"
---
# <a name="pause-and-start-your-power-bi-embedded-capacity-in-the-azure-portal"></a>在 Azure 门户中暂停和启动 Power BI Embedded 容量

本文介绍如何在 Microsoft Azure 中暂停和启动 Power BI Embedded 容量。 这里假设你已创建 Power BI Embedded 容量。 如果还没有，请参阅[在 Azure 门户中创建 Power BI Embedded 容量](azure-pbie-create-capacity.md)开始创建。

如果没有 Azure 订阅，请在开始之前先创建一个[免费帐户](https://azure.microsoft.com/free/)。

## <a name="pause-your-capacity"></a>暂停容量

暂停容量可以避免付费。 如果在某段时间内不需要使用容量，那么暂停容量是一个不错的选择。 请使用以下步骤暂停容量。

> [!NOTE]
> 暂停容量可能会导致内容在 Power BI 中不可用。 在暂停之前，请确保从容量中取消分配工作区，以防发生中断。

1. 登录到 [Azure 门户](https://portal.azure.com/)。

2. 选择“所有服务” > “Power BI Embedded”以查看容量。

    ![Azure 门户中的所有服务](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. 选择要暂停的容量。

    ![Azure 门户中的 Power BI Embedded 容量列表](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. 在容量详细信息中选择“暂停”。

    ![暂停容量](media/azure-pbie-pause-start/azure-portal-pause-capacity.png)

5. 选择“是”，确认要暂停容量。

    ![确认暂停](media/azure-pbie-pause-start/azure-portal-confirm-pause.png)

## <a name="start-your-capacity"></a>启动容量

通过启动容量来恢复使用。 启动容量也会恢复计费。

1. 登录到 [Azure 门户](https://portal.azure.com/)。

2. 选择“所有服务” > “Power BI Embedded”以查看容量。

    ![Azure 门户中的所有服务](media/azure-pbie-pause-start/azure-portal-more-services.png)

3. 选择要启动的容量。

    ![Azure 门户中的 Power BI Embedded 容量列表](media/azure-pbie-pause-start/azure-portal-capacity-list.png)

4. 在容量详细信息中选择“启动”。

    ![启动容量](media/azure-pbie-pause-start/azure-portal-start-capacity.png)

5. 选择“是”，确认要启动容量。

    ![确认启动](media/azure-pbie-pause-start/azure-portal-confirm-start.png)

如果为此容量分配了任何内容，则启动容量后便可使用这些内容。

## <a name="next-steps"></a>后续步骤

如果要纵向扩展或减少容量，请参阅[缩放 Power BI Embedded 容量](azure-pbie-scale-capacity.md)。

若要开始在应用程序中嵌入 Power BI 内容，请参阅[如何嵌入 Power BI 仪表板、报表和磁贴](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/)。

更多问题？ [尝试咨询 Power BI 社区](http://community.powerbi.com/)