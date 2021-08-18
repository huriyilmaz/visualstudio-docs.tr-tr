---
title: XmlPoke Görev | Microsoft Docs
description: Bir XPath MSBuild xml dosyasına değerleri ayarlamak için XmlPoke görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPoke task [MSBuild]
- MSBuild, XmlPoke task
ms.assetid: 6ba1953c-be3b-4df8-8561-e133408f8270
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 5abe59d607ef2c80ca1451da94f9cc6cd7d08688e669178848ea7fed5da183de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443093"
---
# <a name="xmlpoke-task"></a>XmlPoke görevi

Değerleri bir XPath sorgusu tarafından belirtilen şekilde bir XML dosyasına ayarlar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `XmlPoke` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Namespaces`|İsteğe `String` bağlı parametre.<br /><br /> XPath sorgu ön ekleri için ad alanlarını belirtir. `Namespaces` , ve özniteliklerine sahip öğelerden oluşan bir XML `Namespace` kod `Prefix` `Uri` parçacığıdır. özniteliği, `Prefix` özniteliğinde belirtilen ad alanıyla ilişkilendirilen ön eki `Uri` belirtir. Boş bir `Prefix` kullanmayın.|
|`Query`|İsteğe `String` bağlı parametre.<br /><br /> XPath sorgusunu belirtir.|
|`Value`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> Belirtilen yola eklenecek değeri belirtir.|
|`XmlInputPath`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> XML girişini bir dosya yolu olarak belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Değiştirerek şunları sample.xml:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

Bu örnekte, değiştirmek için `/Package/mp:PhoneIdentity/PhoneProductId` kullanın

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Namespace>
        <Namespace Prefix="dn" Uri="http://schemas.microsoft.com/appx/manifest/foundation/windows10" />
        <Namespace Prefix="mp" Uri="http://schemas.microsoft.com/appx/2014/phone/manifest" />
        <Namespace Prefix="uap" Uri="http://schemas.microsoft.com/appx/manifest/uap/windows10" />
    </Namespace>
</PropertyGroup>

<Target Name="Poke">
  <XmlPoke
    XmlInputPath="Sample.xml"
    Value="MyId"
    Query="/dn:Package/mp:PhoneIdentity/@PhoneProductId"
    Namespaces="$(Namespace)"/>
</Target>
</Project>
```

`dn` burada varsayılan ad alanı için yapay ad alanı ön eki olarak kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
