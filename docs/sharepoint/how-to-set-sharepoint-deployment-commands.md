---
title: 'Nasıl SharePoint: Dağıtım Komutlarını | Microsoft Docs'
description: Dağıtım öncesi ve dağıtım sonrası komutlarını SharePoint dağıtım işlemini özelleştirmeyi anlama.
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
ms.openlocfilehash: 2b97317d0fcc186cd457fcbe696bb5bfc73413316f522302bdb9d98f8ed83506
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121332019"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Nasıl yapabilirsiniz: SharePoint komutlarını ayarlama
  Dağıtım öncesi ve dağıtım sonrası komutlarını ayarerek dağıtım işlemini özelleştirebilirsiniz. Bu komutlar, çözümlerde hata ayıklarken diğer dağıtım eylemlerinden önce SharePoint sonra Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Dağıtım öncesi komutu eklemek için

1. Menü çubuğunda Özellikler'i **Project**  >  **\<*ProjectName*> seçin.**

2. İlke **sekmesini SharePoint** seçin.

3. Dağıtım Öncesi **Komut Satırı metin kutusuna** MS-DOS veya MSBuild komutları girerek bu adımı özelleştirin.

     Örneğin, dağıtım tamamlanmadan önce dizin içeriğini listeley için **dir girin.**

### <a name="to-add-a-post-deployment-command"></a>Dağıtım sonrası komutu eklemek için

1. Menü çubuğunda Özellikler'i **Project**  >  **\<*ProjectName*> seçin.**

2. İlke **sekmesini SharePoint** seçin.

3. Dağıtım Sonrası **Komut Satırı metin kutusuna** MS-DOS veya MSBuild komutları girerek bu adımı özelleştirin.

     Örneğin, dağıtım tamamlandıktan sonra dizin içeriğini listeledikten sonra **dir girin.** Derleme dizininden derlemeyi kopyalamak MSBuild değişkenini kullanmak için **copy $(TargetPath) c:\DeploymentDirectory girin.**

## <a name="see-also"></a>Ayrıca bkz.
- [Dağıtım çözümlerini SharePoint dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
