---
title: 'Nasıl yapılır: SharePoint dağıtım komutlarını ayarlama | Microsoft Docs'
description: SharePoint dağıtım öncesi ve dağıtım sonrası komutlarını ayarlayarak dağıtım sürecini özelleştirmeyi anlayın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 72938f316be22cd9b2eab2d7dab893c9370fb0ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965856"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Nasıl yapılır: SharePoint dağıtım komutlarını ayarlama
  Dağıtım sürecini, dağıtım öncesi ve dağıtım sonrası komutları ayarlayarak özelleştirebilirsiniz. Bu komutlar, Visual Studio 'dan SharePoint Çözümlerinde hata ayıklarken diğer dağıtım eylemlerinden önce ve sonra çalışır.

### <a name="to-add-a-pre-deployment-command"></a>Dağıtım öncesi komutu eklemek için

1. Menü çubuğunda, **Proje**  >  **\<*ProjectName*> özellikleri**' ni seçin.

2. **SharePoint** sekmesini seçin.

3. **Dağıtım öncesi komut satırı** metin kutusuna bu adımı özelleştirmek için MS-DOS veya MSBuild komutları girin.

     Örneğin, dağıtım tamamlanmadan önce dizin içeriğini listelemek için **dir** girin.

### <a name="to-add-a-post-deployment-command"></a>Dağıtım sonrası komutu eklemek için

1. Menü çubuğunda, **Proje**  >  **\<*ProjectName*> özellikleri**' ni seçin.

2. **SharePoint** sekmesini seçin.

3. **Dağıtım sonrası komut satırı** metin kutusuna bu adımı özelleştirmek için MS-DOS veya MSBuild komutları girin.

     Örneğin, dağıtım tamamlandığında dizin içeriğini listelemek için **dir** girin. Yapı dizininden derlemeyi kopyalamak üzere bir MSBuild değişkeni kullanmak için, **Copy $ (TargetPath) c:\DeploymentDirectory** yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
