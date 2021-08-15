---
title: XmlPeek Görev | Microsoft Docs
description: Xml MSBuild xml dosyasından XPath Sorgusu tarafından belirtilen değerleri geri dönmek için xmlpeek görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: cace2a1ac5ecca3a209e242e2341bd6201f4996e785402dd6178ec14ddf90f19
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121257452"
---
# <a name="xmlpeek-task"></a>XmlPeek görevi

Xml dosyasından XPath Sorgusu tarafından belirtilen değerleri döndürür.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda görevin parametreleri açık `XmlPeek` almaktadır.

|Parametre|Açıklama|
|---------------|-----------------|
|`Namespaces`|İsteğe `String` bağlı parametre.<br /><br /> XPath sorgu ön ekleri için ad alanlarını belirtir.|
|`Query`|İsteğe `String` bağlı parametre.<br /><br /> XPath sorgusunu belirtir.|
|`Result`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> `[]` bağlı çıkış parametresi.<br /><br /> Bu görev tarafından döndürülen sonuçları içerir.|
|`XmlContent`|İsteğe `String` bağlı parametre.<br /><br /> XML girişini dize olarak belirtir.|
|`XmlInputPath`|İsteğe <xref:Microsoft.Build.Framework.ITaskItem> bağlı parametre.<br /><br /> XML girişini bir dosya yolu olarak belirtir.|

## <a name="remarks"></a>Açıklamalar

 Bu görev, tabloda listelenen parametrelerin yanı sıra sınıfından devralınan parametreleri de sınıfından <xref:Microsoft.Build.Tasks.TaskExtension> <xref:Microsoft.Build.Utilities.Task> devralınır. Bu ek parametrelerin ve açıklamalarının listesi için bkz. [TaskExtension temel sınıfı.](../msbuild/taskextension-base-class.md)

## <a name="example"></a>Örnek

Okunabilecek örnek bir XML `settings.config` dosyası şu şekildedir:

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

Bu örnekte, okumak için aşağıdaki `value` gibi bir kod kullanın:

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

XML ad alanlarıyla, aşağıdaki `Namespaces` örnekte olduğu gibi parametresini kullanırsınız. Giriş XML dosyası `XMLFile1.xml` ile:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<class AccessModifier='public' Name='test' xmlns:s='http://nsurl'>
  <s:variable Type='String' Name='a'>This</s:variable>
  <s:variable Type='String' Name='b'>is</s:variable>
  <s:variable Type='String' Name='c'>Sparta!</s:variable>
  <method AccessModifier='public static' Name='GetVal' />
</class>
```

Bir proje `Target` dosyasında aşağıdakiler tanımlanmıştır:

```xml
  <Target Name="TestPeek" BeforeTargets="Build">
    <!-- Find the Name attributes -->
    <XmlPeek XmlInputPath="XMLFile1.xml"
             Query="//s:variable/@Name"
             Namespaces="&lt;Namespace Prefix='s' Uri='http://nsurl' /&gt;">
      <Output TaskParameter="Result" ItemName="value1" />
    </XmlPeek>
    <Message Text="@(value1)"/>
    <!-- Find 'variable' nodes (XPath query includes ".") -->
    <XmlPeek XmlInputPath="XMLFile1.xml"
             Query="//s:variable/."
             Namespaces="&lt;Namespace Prefix='s' Uri='http://nsurl' /&gt;">
      <Output TaskParameter="Result" ItemName="value2" />
    </XmlPeek>
    <Message Text="@(value2)"/>
  </Target>
```

Çıkış, hedeften şunları `TestPeek` içerir:

```output
  TestPeek output:
  a;b;c
  <s:variable Type="String" Name="a" xmlns:s="http://nsurl">This</s:variable>;<s:variable Type="String" Name="b" xmlns:s="http://nsurl">is</s:variable>;<s:variable Type="String" Name="c" xmlns:s="http://nsurl">Sparta!</s:variable>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görevler](../msbuild/msbuild-tasks.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [XPath sorgu söz dizimi](https://wikipedia.org/wiki/XPath)
