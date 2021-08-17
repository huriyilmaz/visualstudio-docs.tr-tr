---
title: '&lt;description &gt; Öğesi (ClickOnce Dağıtımı) | Microsoft Docs'
description: Description öğesi, kabuk varlığı oluşturmak için kullanılan uygulama bilgilerini ve programlarda Program Ekle veya Kaldır öğesini Denetim Masası.
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
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: fabce5e8d6f7b6bf59f1a62346c8d9b5927e2cae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080656"
---
# <a name="ltdescriptiongt-element-clickonce-deployment"></a>&lt;description &gt; öğesi (ClickOnce dağıtım)
Kabuk varlığı oluşturmak için kullanılan uygulama bilgilerini ve programlarda **Program Ekle veya** Kaldır öğesini Denetim Masası.

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
 öğesi `description` gereklidir ve ad alanı `urn:schemas-microsoft-com:asm.v1` içindedir. Alt öğe içerir ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`publisher`|Gereklidir. Windows Başlat menüsünde simge yerleşimi için  kullanılan şirket  adını ve dağıtım yükleme için yapılandırıldığında Denetim Masası'daki Program Ekle veya Kaldır öğesini tanımlar.|
|`product`|Gereklidir. Tam ürün adını tanımlar. Başlat menüsünde yüklü olan simgenin başlığı olarak Windows **kullanılır.**|
|`suiteName`|İsteğe bağlı. Başlat menüsünde klasör içinde `publisher` bir alt klasör Windows **tanımlar.**|
|`supportUrl`|İsteğe bağlı. Program Ekle veya Kaldır öğesinde gösterilen destek **URL'sini** Denetim Masası. Dağıtım yükleme için yapılandırıldığında, bu URL'nin Windows  başlat menüsünde uygulama desteği için de bir kısayol oluşturulur.|

## <a name="remarks"></a>Açıklamalar
 Açıklama öğesi tüm dağıtım yapılandırmalarında gereklidir.

## <a name="example"></a>Örnek
 Aşağıdaki kod örneği, dağıtım `description` bildiriminde bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] öğeyi gösterir. Bu kod örneği, dağıtım bildirimi konusu için sağlanan daha [büyük ClickOnce bir parçasıdır.](../deployment/clickonce-deployment-manifest.md)

```xml
<description
  asmv2:publisher="My Company Name"
  asmv2:product="My Application"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)