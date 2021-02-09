---
title: '&lt;AssemblyIdentity &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
description: Öğe, ClickOnce dağıtımında gereklidir. Alt öğesi içermez ve bu makalede açıklanan özniteliklere sahiptir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bc689c80d033c6b92178f020c0d3273f6ec86ca7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911345"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;AssemblyIdentity &gt; öğesi (ClickOnce dağıtımı)
Uygulamanın birincil derlemesini tanımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `assemblyIdentity`Öğe gereklidir. Alt öğesi içermez ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`name`|Gereklidir. Bilgilendirici amaçlar için dağıtımın okunabilir adını tanımlar.<br /><br /> `name`Tek veya çift tırnak gibi özel karakterler içeriyorsa, uygulama etkinleştiremeyebilir.|
|`version`|Gereklidir. Derlemenin sürüm numarasını şu biçimde belirtir: `major.minor.build.revision` .<br /><br /> Bu değer, bir uygulama güncelleştirmesinin tetiklenmesi için güncelleştirilmiş bir bildirimde arttırılmalıdır.|
|`publicKeyToken`|Gereklidir. Dağıtım bildiriminin imzalandığı, ortak anahtarın SHA-1 karma değerinin son 8 baytını temsil eden 16 karakterlik bir onaltılık dize belirtir. İmzalamak için kullanılan ortak anahtar 2048 bit veya daha büyük olmalıdır.<br /><br /> Bir derlemeyi imzalamak önerilse ancak isteğe bağlı olsa da, bu öznitelik gereklidir. Bir bütünleştirilmiş kod imzasız ise, kendinden imzalı bir derlemeden bir değer kopyalamanız veya tümü sıfırlardan oluşan bir "kukla" değeri kullanmanız gerekir.|
|`processorArchitecture`|Gereklidir. İşlemciyi belirtir. Geçerli değerler `msil` tüm işlemciler için `x86` 32 bit windows, `IA64` 64 bit Windows için ve `Itanium` Intel 64 bit Itanium işlemcilere yöneliktir.|
|`type`|Gereklidir. Windows yan yana yükleme teknolojisiyle uyumluluk için. İzin verilen tek değer `win32` .|

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Aşağıdaki kod örneğinde bir `assemblyIdentity` dağıtım bildiriminde bir öğe gösterilmektedir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu kod örneği, [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md) konusu için sağlanmış daha büyük bir örneğin bir parçasıdır.

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> dosyalarında](../deployment/assemblyidentity-element-clickonce-application.md)