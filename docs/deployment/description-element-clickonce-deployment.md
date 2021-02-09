---
title: '&lt;Description &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
description: Description öğesi, Denetim Masası 'ndaki bir kabuk varlığı ve Program Ekle/Kaldır öğesi oluşturmak için kullanılan uygulama bilgilerini tanımlar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#description
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <description> element [ClickOnce deployment manifest]
ms.assetid: 18f6919e-a3ab-4942-a57d-167fabfac44e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dee33fca027ce47ede8315f7956479ee2394382
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893093"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;Description &gt; öğesi (ClickOnce dağıtımı)
Denetim Masası 'ndaki bir kabuk varlığı ve **Program Ekle/Kaldır** öğesi oluşturmak için kullanılan uygulama bilgilerini tanımlar.

## <a name="syntax"></a>Syntax

```xml

      <description 
   publisher 
   product
   suiteName
   supportUrl
/>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `description`Öğesi gereklidir ve `urn:schemas-microsoft-com:asm.v1` ad alanında bulunur. Alt öğesi içermez ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`publisher`|Gereklidir. Dağıtım yüklenmek üzere yapılandırıldığında, Windows **Başlat** menüsünde simge yerleştirme için kullanılan şirket adını ve Denetim Masası 'Ndaki **Program Ekle/Kaldır** öğesini tanımlar.|
|`product`|Gereklidir. Tam ürün adını tanımlar. Windows **Başlat** menüsünde yüklü simgenin başlığı olarak kullanılır.|
|`suiteName`|İsteğe bağlı. `publisher`Windows **Başlat** menüsündeki klasör içindeki bir alt klasörü tanımlar.|
|`supportUrl`|İsteğe bağlı. Denetim Masası 'ndaki **Program Ekle veya Kaldır** öğesinde gösterilen bir destek URL 'sini belirtir. Dağıtım yüklenmek üzere yapılandırıldığında, Windows **Başlat** menüsündeki uygulama desteği için de bu URL 'nin bir kısayolu oluşturulur.|

## <a name="remarks"></a>Açıklamalar
 Tüm dağıtım yapılandırmalarında Description öğesi gereklidir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde bir `description` dağıtım bildiriminde bir öğe gösterilmektedir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu kod örneği, [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md) konusu için sağlanmış daha büyük bir örneğin bir parçasıdır.

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)