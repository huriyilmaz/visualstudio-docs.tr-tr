---
title: '&lt;postActionData &gt; öğesi (Office geliştirme)'
description: vstav3 ad alanının postActionData öğesi, herhangi bir dağıtım sonrası eylemle ilişkili olan ve Office sonra çalışan verileri belirtir.
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 4196c3061372d46a2fad4c2b46ff8c1fe4ee2b39
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025894"
---
# <a name="ltpostactiondatagt-element-office-development"></a>&lt;postActionData &gt; öğesi (Office geliştirme)
  Ad `postActionData` alanının öğesi, dağıtım sonrası eylemle ilişkili olan ve çözüm yüklendikten sonra `vstav3` Office verileri belirtir.

## <a name="syntax"></a>Syntax

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 öğesi `postActionData` isteğe bağlıdır ve ad alanı `vstav3` içindedir. Her dağıtım sonrası `postActionData` eylem için bir uygulama bildiriminde tanımlanan bir öğe vardır.

 öğesinin `postActions` özniteliği yoktur.

 `postActions` alt öğeye sahip değil.

## <a name="post-deployment-action-example"></a>Dağıtım sonrası eylem örneği

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği, kullanılarak `postAction` dağıtılan bir uygulama çözümü için uygulama Office öğesini [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gösterir. Bu kod örneği, uygulama çözümleri için Uygulama bildirimleri [bölümünde sağlanan daha büyük bir Office örneğidir.](../vsto/application-manifests-for-office-solutions.md)

### <a name="code"></a>Kod

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama çözümleri için Office bildirimleri](../vsto/application-manifests-for-office-solutions.md)
- [Dağıtım çözümleri için Office bildirimleri](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
