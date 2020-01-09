---
title: XmlPoke Görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f44ce4736900fde35716ca3ec9dabb2d55c6df51
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588388"
---
# <a name="xmlpoke-task"></a>XmlPoke görevi

Bir XPath sorgusu tarafından belirtilen değerleri bir XML dosyasına ayarlar.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda `XmlPoke` görevinin parametreleri açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Namespaces`|İsteğe bağlı `String` parametresi.<br /><br /> XPath sorgu ön ekleri için ad alanlarını belirtir. `Namespaces`, `Prefix` ve `Uri`özniteliklere sahip `Namespace` öğelerinden oluşan bir XML kod parçacıdır. Öznitelik `Prefix` `Uri` özniteliğinde belirtilen ad alanıyla ilişkilendirilecek ön eki belirtir. Boş bir `Prefix`kullanmayın.|
|`Query`|İsteğe bağlı `String` parametresi.<br /><br /> XPath sorgusunu belirtir.|
|`Value`|Gerekli <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> Belirtilen yola eklenecek değeri belirtir.|
|`XmlInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametresi.<br /><br /> XML girişini dosya yolu olarak belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere ek olarak, bu görev, kendisini <xref:Microsoft.Build.Utilities.Task> sınıfından devralan <xref:Microsoft.Build.Tasks.TaskExtension> sınıfından parametreleri devralır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Örnek

Değiştirilecek örnek bir. xml dosyası aşağıda verilmiştir:

```xml
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10" >
<Identity Name="Sample.Product " Publisher="CN=1234" Version="1.0.0.0" />
<mp:PhoneIdentity PhoneProductId="456" PhonePublisherId="0" />
</Package>
```

Bu örnekte, `/Package/mp:PhoneIdentity/PhonePublisherId`değiştirmek istiyorsanız,

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

`dn`, varsayılan ad alanı için yapay bir ad alanı öneki olarak kullanılır.

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
