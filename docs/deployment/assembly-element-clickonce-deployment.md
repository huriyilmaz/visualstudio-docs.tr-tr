---
title: '&lt;Assembly &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
description: Bütünleştirilmiş kod öğesi kök öğesidir ve ClickOnce dağıtımında gereklidir. İlk kapsanan öğesi bir assemblyIdentity öğesi olmalıdır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b7838e0a212bbc1e743783255106bb44561fbe62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837768"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;Assembly &gt; öğesi (ClickOnce dağıtımı)
Dağıtım bildirimi için en üst düzey öğe.

## <a name="syntax"></a>Syntax

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `assembly`Öğesi kök öğesidir ve gereklidir. İlk kapsanan öğesi bir `assemblyIdentity` öğesi olmalıdır. Bildirim öğeleri şu ad alanlarında olmalıdır: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` , ve `http://www.w3.org/2000/09/xmldsig#` . Derlemenin alt öğeleri de bu ad alanlarında, devralmayla veya etiketlemeyle olmalıdır.

 `assembly`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`manifestVersion`|Gereklidir. Bu özniteliğin olarak ayarlanması gerekir `1.0` .|

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `assembly` kullanılarak dağıtılan bir uygulama için dağıtım bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu kod örneği, [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md) konusu için sağlanmış daha büyük bir örneğin bir parçasıdır.

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> dosyalarında](../deployment/assembly-element-clickonce-application.md)