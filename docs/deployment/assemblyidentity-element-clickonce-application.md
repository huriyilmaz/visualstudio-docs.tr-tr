---
title: '&lt;AssemblyIdentity &gt; öğesi (ClickOnce uygulaması) | Microsoft Docs'
description: Öğe, ClickOnce uygulamasında gereklidir. Alt öğesi içermez ve bu makalede açıklanan özniteliklere sahiptir.
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
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92b5c1d323634bbb242cdccb54890908d5668803
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911387"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;AssemblyIdentity &gt; öğesi (ClickOnce uygulaması)
Bir dağıtımda dağıtılan uygulamayı tanımlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

## <a name="syntax"></a>Syntax

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler
 `assemblyIdentity`Öğe gereklidir. Alt öğesi içermez ve aşağıdaki özniteliklere sahiptir.

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Name`|Gereklidir. Uygulamanın adını tanımlar.<br /><br /> `Name`Tek veya çift tırnak gibi özel karakterler içeriyorsa, uygulama etkinleştiremeyebilir.|
|`Version`|Gereklidir. Uygulamanın sürüm numarasını aşağıdaki biçimde belirtir: `major.minor.build.revision`|
|`publicKeyToken`|İsteğe bağlı. `SHA-1`Uygulamanın veya derlemenin imzalandığı ortak anahtarın karma değerinin son 8 baytını temsil eden 16 karakterlik bir onaltılık dize belirtir. Kataloğu imzalamak için kullanılan ortak anahtar 2048 bit veya daha büyük olmalıdır.<br /><br /> Bir derlemeyi imzalamak önerilse ancak isteğe bağlı olsa da, bu öznitelik gereklidir. Bir bütünleştirilmiş kod imzasız ise, kendinden imzalı bir derlemeden bir değer kopyalamanız veya tümü sıfırlardan oluşan bir "kukla" değeri kullanmanız gerekir.|
|`processorArchitecture`|Gereklidir. İşlemciyi belirtir. Geçerli değerler `msil` tüm işlemciler için `x86` 32 bit windows, `IA64` 64 bit Windows için ve `Itanium` Intel 64 bit Itanium işlemcilere yöneliktir.|
|`language`|Gereklidir. Derlemenin iki bölümden oluşan dil kodlarını tanımlar (örneğin, `en-US` ). Bu öğe `asmv2` ad alanıdır. Belirtilmemişse, varsayılan olur `neutral` .|

## <a name="examples"></a>Örnekler

### <a name="description"></a>Açıklama
 Aşağıdaki kod örneği `assemblyIdentity` bir uygulama bildiriminde bir öğe gösterir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Bu kod örneği, [ClickOnce uygulama bildiriminde](../deployment/clickonce-application-manifest.md)sağlanmış daha büyük bir örneğin bir parçasıdır.

### <a name="code"></a>Kod

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulama bildirimi](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> dosyalarında](../deployment/assemblyidentity-element-clickonce-deployment.md)