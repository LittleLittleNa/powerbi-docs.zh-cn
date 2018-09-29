---
title: 在 Power BI Desktop 中连接到 PDF 文件（预览）
description: 在 Power BI Desktop 中轻松连接并使用 PDF 文件中的数据
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/10/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: fe13e5776648342aa4f7e86dce657e6ffcca11b9
ms.sourcegitcommit: c51461690e8faa121a1325957ca79b7a3975e8b8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "44512579"
---
# <a name="connect-to-a-pdf-file-in-power-bi-desktop-preview"></a>在 Power BI Desktop 中连接到 PDF 文件（预览）
在 Power BI Desktop 中，可以连接到 PDF 文件并使用文件中包含的数据，就像在 Power BI Desktop 中使用任何其他数据源一样。

![连接到 PDF 文件中的数据](media/desktop-connect-pdf/connect-pdf_04.png)

以下部分介绍如何连接到 PDF 文件，选择数据并将该数据添加到 Power BI Desktop。

## <a name="enable-the-pdf-connector"></a>启用 PDF 连接器
在 Power BI Desktop 中，PDF 连接器处于预览阶段，必须启用。 要启用 PDF 连接器，请依次选择“文件”、“选项和设置”、“选项”和“预览功能”，再选择“从 PDF 文件获取数据”旁的复选框。 

![通过“选项”>“预览功能”启用 PDF 连接器](media/desktop-connect-pdf/connect-pdf_01.png)

选中此复选框后，需要重启 **Power BI Desktop**。

首次使用 PDF (beta) 连接器时，系统将发出警告，告知 PDF 连接器仍处于开发阶段，将来可能会发生更改。 选择“继续”以使用连接器。

始终建议升级到最新版 Power BI Desktop，可通过[获取 Power BI Desktop](desktop-get-the-desktop.md) 中的链接获取最新版。 

## <a name="connect-to-a-pdf-file"></a>连接到 PDF 文件
若要连接到 PDF 文件，请从 Power BI Desktop 中的“主页”功能区选择“获取数据”。 在左侧的类别中选择“文件”，然后将看到“PDF (beta)”。

![选择从 PDF 获取数据](media/desktop-connect-pdf/connect-pdf_01.png)

系统会提示你提供要使用的 PDF 文件的位置。 提供文件位置并加载 PDF 文件后，将会出现“导航器”窗口，并显示文件中可用的数据。可从这些数据中选择要在 Power BI Desktop 中导入和使用的一个或多个元素。

![连接到 PDF 文件中的数据](media/desktop-connect-pdf/connect-pdf_04.png)

选择 PDF 文件中已发现元素旁边的复选框，将其显示在右侧窗格中。 如果已准备好导入，请选择“加载”按钮，将数据添加到 Power BI Desktop 中。


## <a name="next-steps"></a>后续步骤
你可以使用 Power BI Desktop 连接到各种数据。 有关数据源的详细信息，请参阅下列资源：

* [什么是 Power BI Desktop？](desktop-what-is-desktop.md)
* [Power BI Desktop 中的数据源](desktop-data-sources.md)
* [使用 Power BI Desktop 调整和合并数据](desktop-shape-and-combine-data.md)
* [通过 Power BI Desktop 连接到 Excel 工作簿](desktop-connect-excel.md)   
* [直接将数据输入到 Power BI Desktop 中](desktop-enter-data-directly-into-desktop.md)   

