---
title: XmlPeek Görev | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a76bf033fa3eb85f0626478b965285f32e5fb6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094660"
---
# <a name="xmlpeek-task"></a>XmlPeek görevi

XML dosyasından XPath Sorgusu tarafından belirtilen değerleri döndürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevparametreleri `XmlPeek` açıklanmaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Namespaces`|İsteğe bağlı `String` parametre.<br /><br /> XPath sorgu önekleri için ad alanlarını belirtir.|
|`Query`|İsteğe bağlı `String` parametre.<br /><br /> XPath sorgusunu belirtir.|
|`Result`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> `[]` çıktı parametresi.<br /><br /> Bu görev tarafından döndürülen sonuçları içerir.|
|`XmlContent`|İsteğe bağlı `String` parametre.<br /><br /> XML girişini dize olarak belirtir.|
|`XmlInputPath`|İsteğe bağlı <xref:Microsoft.Build.Framework.ITaskItem> parametre.<br /><br /> XML girişini bir dosya yolu olarak belirtir.|

## <a name="remarks"></a>Açıklamalar

 Tabloda listelenen parametrelere sahip olmanın yanı sıra, bu görev <xref:Microsoft.Build.Tasks.TaskExtension> sınıftan devralınan parametreleri de devralır. <xref:Microsoft.Build.Utilities.Task> Bu ek parametrelerin ve açıklamalarının listesi için [TaskExtension taban sınıfına](../msbuild/taskextension-base-class.md)bakın.



## <a name="example"></a>Örnek

Burada okumak için örnek `settings.config` bir XML dosyası:

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

Bu örnekte, okumak `value`istiyorsanız, aşağıdaki gibi kod kullanın:

```xml
<Target Name="BeforeBuild">
    <XmlPeek XmlInputPath="settings.config" Query="appSettings/add[@key='ProjectFolder']/@value">
        <Output TaskParameter="Result" ItemName="value" />
    </XmlPeek>
    <Message Text="Using project folder @(value)." Importance="high" />
    <PropertyGroup>
        <ProjectFolder>@(value)</ProjectFolder>
    </PropertyGroup>
    <ItemGroup>
        <Compile Include="Projects\$(ProjectFolder)\Controls\Control1.ascx.cs">
            <SubType>ASPXCodeBehind</SubType>
        </Compile>
    </ItemGroup>
</Target>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
