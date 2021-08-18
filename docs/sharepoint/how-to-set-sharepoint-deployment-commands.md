---
title: 'nasıl yapılır: SharePoint dağıtım komutlarını ayarlama | Microsoft Docs'
description: dağıtım sürecini özelleştirmeyi SharePoint dağıtım öncesi ve dağıtım sonrası komutları ayarlayarak anlayın.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: dc3ad57702b7063edd0c03f305a8ffc3722eebd6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130955"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>nasıl yapılır: SharePoint dağıtım komutlarını ayarlama
  Dağıtım sürecini, dağıtım öncesi ve dağıtım sonrası komutları ayarlayarak özelleştirebilirsiniz. bu komutlar, Visual Studio SharePoint çözümlerinde hata ayıkladığınızda, diğer dağıtım eylemlerinden önce ve sonra çalışır.

### <a name="to-add-a-pre-deployment-command"></a>Dağıtım öncesi komutu eklemek için

1. menü çubuğunda **Project**  >  **\<*ProjectName*> özellikler**' i seçin.

2. **SharePoint** sekmesini seçin.

3. **dağıtım öncesi komut satırı** metin kutusuna bu adımı özelleştirmek için MS-DOS veya MSBuild komutları girin.

     Örneğin, dağıtım tamamlanmadan önce dizin içeriğini listelemek için **dir** girin.

### <a name="to-add-a-post-deployment-command"></a>Dağıtım sonrası komutu eklemek için

1. menü çubuğunda **Project**  >  **\<*ProjectName*> özellikler**' i seçin.

2. **SharePoint** sekmesini seçin.

3. **dağıtım sonrası komut satırı** metin kutusuna bu adımı özelleştirmek için MS-DOS veya MSBuild komutları girin.

     Örneğin, dağıtım tamamlandığında dizin içeriğini listelemek için **dir** girin. derlemeyi yapı dizininden kopyalamak üzere bir MSBuild değişkeni kullanmak için, **copy $ (TargetPath) c:\deploymentdirectory** yazın.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
