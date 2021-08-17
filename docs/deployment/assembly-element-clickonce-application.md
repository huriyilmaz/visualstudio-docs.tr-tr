---
title: '&lt;assembly &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
description: bütünleştirilmiş kod öğesi kök öğesidir ve ClickOnce uygulamasında gereklidir. İlk kapsanan öğesi bir assemblyIdentity öğesi olmalıdır.
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
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: cc8fb424c3a6232f27737521604247cf55ebc20e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090071"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;assembly &gt; öğesi (ClickOnce uygulaması)
Uygulama bildirimi için en üst düzey öğe.

## <a name="syntax"></a>Syntax

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `assembly`Öğesi kök öğesidir ve gereklidir. İlk kapsanan öğesi bir `assemblyIdentity` öğesi olmalıdır. Bildirim öğeleri şu ad alanlarından birinde olmalıdır:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Derlemenin alt öğeleri de bu ad alanlarında, devralmayla veya etiketlemeyle olmalıdır.

 `assembly`Öğesi aşağıdaki özniteliğe sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`manifestVersion`|Gereklidir. `manifestVersion`Özniteliğin olarak ayarlanması gerekir `1.0` .|

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, `assembly` bir uygulama için uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . bu kod örneği, [ClickOnce uygulama bildiriminde](../deployment/clickonce-application-manifest.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>Ayrıca bkz.
- [uygulama bildirimini ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assembly> dosyalarında](../deployment/assembly-element-clickonce-deployment.md)
