---
description: vstov4 ad alanının formRegions öğesi, Microsoft Office Outlook eklenti ile ilişkili form bölgelerini VSTO içerir.
title: '&lt;formRegions &gt; öğesi (Office geliştirme Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e1a4439f5c1dab78ce32c553a4bee98db6fa7da4f072152c3a046ba819222128
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121440870"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions &gt; öğesi (Office geliştirme Visual Studio)
  Ad `formRegions` alanının `vstov4` öğesi, Microsoft Office Outlook eklenti ile ilişkili form bölgelerini VSTO içerir.

## <a name="syntax"></a>Syntax

```xml
<formRegions>
  <formRegion>
  </formRegion>
</formRegions>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 Ad `formRegions` alanının `vstov4` öğesi, bir `formRegion` eklentinin tüm öğelerini Outlook VSTO içerir. Yalnızca form bölgelerini Outlook VSTO eklentileri oluşturmak için gereklidir.

 Bir uygulama bildiriminde `formRegions` tanımlanan yalnızca bir öğe olabilir.

 öğesinin `formRegions` özniteliği yoktur.

 öğesi `formRegions` aşağıdaki öğeye sahip.

### <a name="formregion"></a>Formregion
 Form Outlook VSTO içeren eklentiler oluşturmak için gereklidir. öğesi `formRegion` [formRegion&#60;öğesinde&#62; geliştirme &#40;Office öğesinde Visual Studio&#41;. ](../vsto/formregion-element-office-development-in-visual-studio.md)

## <a name="vsto-add-in-example"></a>VSTO Eklenti örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak `formRegions` dağıtılan bir uygulama düzeyi uygulama Office öğesi [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir Office bir bölümüdur.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstov4:formRegions>
  <vstov4:formRegion
      name="OutlookAddIn1.FormRegion1">
    <vstov4:messageClass name="IPM.Note" />
    <vstov4:messageClass name="IPM.Contact" />
    <vstov4:messageClass name="IPM.Appointment" />
  </vstov4:formRegion>
</vstov4:formRegions>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
