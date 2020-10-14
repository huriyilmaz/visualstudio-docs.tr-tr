---
title: Unity için Visual Studio Araçları ve Azure ile programlama | Microsoft Docs
description: Unity için Visual Studio Araçları ve Azure ile program. Azure, telemetri ve diğer oyun verilerini bulutta depolamaya yönelik ölçeklenebilir bir çözüm sunar.
ms.custom: ''
ms.date: 12/18/2017
ms.reviewer: crdun
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 7921D4C7-5526-42F5-8E03-82D3E33A893F
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 5be430b4a59dd4aa36945555f6553f321b9d50c0
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039826"
---
# <a name="program-with-unity-and-azure"></a>Unity ve Azure ile Programlama

Azure, telemetri ve diğer oyun verilerini bulutta depolamaya yönelik ölçeklenebilir bir çözüm sunar. Unity 2017 sürümü sayesinde Unity 'nin .NET 4,6 için deneysel desteği, Azure .NET SDK 'larının kullanılmasına izin vererek Azure tümleştirmesini her zamankinden daha kolay hale getirir.

## <a name="experimental-azure-sdks"></a>Deneysel Azure SDK 'Ları

> [!NOTE]
> Bu SDK 'lar desteklenmemiştir, ancak müşterilerin Unity 'nin deneysel .NET 4,6 desteğini denemenize yardımcı olmak için sağlanır.

Unity ile aşağıdaki deneysel Azure SDK 'larını denemek için [korumalı alanı](/sandbox/) ziyaret edin:

* [Unity için Azure depolama SDK 'Sı](/sandbox/gamedev/unity/azure-storage-unity?wt.mc_id=azgamedev-sandbox-brpeek)
* [Unity için Azure Event Hubs SDK](/sandbox/gamedev/unity/azure-event-hubs-unity?WT.mc_id=azgamedev-sandbox-brpeek)
* [Unity için Azure Mobile Apps SDK](/sandbox/gamedev/unity/azure-mobile-apps-unity?WT.mc_id=azgamedev-sandbox-brpeek)

## <a name="azure-sdk-sample"></a>Azure SDK örneği

Ayrıca, Azure kolay tabloları SDK ve Unity kullanarak [basit bir örnek oyun](/sandbox/gamedev/unity/samples/azure-mobile-apps-unity-racer) de vardır. Oyun, yüksek puanı elde etmek ve oyun içi Telemetriyi izlemek için Azure kolay tabloları veri depolamayı kullanır ve [GitHub 'dan indirilebilir](https://github.com/BrianPeek/AzureSamples-Unity).

![Örnek oyun ekran görüntüsü](media/vstu_azure-test-sample-game-image2.png)
