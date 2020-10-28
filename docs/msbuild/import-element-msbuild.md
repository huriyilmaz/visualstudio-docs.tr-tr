---
title: İçeri aktarma öğesi (MSBuild) | Microsoft Docs
description: MSBuild 'in bir proje dosyasının içeriğini başka bir proje dosyasına aktarmak için Içeri aktarma öğesini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d5a5650402655f4a5a2a0388ac0e57a0b903bc2e
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903954"
---
# <a name="import-element-msbuild"></a>İçeri aktarma öğesi (MSBuild)

Bir proje dosyasının içeriğini başka bir proje dosyasına aktarır.

\<Project>
\<Import>

## <a name="syntax"></a>Syntax

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Project`|Gerekli öznitelik.<br /><br /> İçeri aktarılacak proje dosyasının yolu. Yol joker karakterler içerebilir. Eşleşen dosyalar sıralanmış sırada içeri aktarılır. Bu özelliği kullanarak, kod dosyasını bir dizine ekleyerek bir projeye kod ekleyebilirsiniz.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`Sdk`| İsteğe bağlı öznitelik.<br /><br /> Proje SDK 'sına başvurur.|

### <a name="child-elements"></a>Alt öğeleri

 Yok

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |
| [ImportGroup](../msbuild/importgroup-element.md) | `Import`İsteğe bağlı bir koşul altında gruplanmış bir öğe koleksiyonu içerir. |

## <a name="remarks"></a>Açıklamalar

 `Import`Öğesini kullanarak, birçok proje dosyası için ortak olan kodu yeniden kullanabilirsiniz. Bu, paylaşılan kodda yaptığınız tüm güncelleştirmeler tarafından içeri aktarılan tüm projelere yayıldığından, kodun korunmasını kolaylaştırır.

 Kurala göre, paylaşılan içe aktarılan proje dosyaları *. targets* dosyaları olarak kaydedilir, ancak standart MSBuild proje dosyalarıdır. MSBuild, farklı bir dosya adı uzantısına sahip bir projeyi içeri aktarmaya engel olmaz, ancak *. targets* uzantısını tutarlılık için kullanmanızı öneririz.

 İçeri aktarılan projelerdeki göreli yollar, içeri aktarılan projenin dizinine göre yorumlanır. (bu paragrafın ilerleyen kısımlarında açıklanan bazı özel durumlarla birlikte). Bu nedenle, bir proje dosyası farklı konumlarda birkaç proje dosyasına aktarılmışsa, içeri aktarılan proje dosyasındaki göreli yollar, içeri aktarılan her proje için farklı şekilde yorumlanacak. İki özel durum vardır. Tek bir özel durum `Import` , öğelerinde her zaman öğesi içeren projeye göre yorumlanan yoldur `Import` . Başka bir özel durum, `UsingTask` her zaman `AssemblyFile` öğesi içeren dosyaya göreli olarak özniteliğin göreli yolunu yorumladığı durumdur `UsingTask` .

 İçeri aktarılan bir projede başvurulan, ve gibi proje dosyası ile ilgili tüm MSBuild ayrılmış özelliklerine, `MSBuildProjectDirectory` `MSBuildProjectFile` içeri aktarma projesi dosyasına göre değerler atanır.

 İçeri aktarılan projenin bir `DefaultTargets` özniteliği yoksa, içeri aktarılan projeler içeri aktarıldıkları sırada incelenir ve ilk keşfedilen `DefaultTargets` özniteliğin değeri kullanılır. Örneğin, ProjectA, ProjectB ve ProjectC 'yi (Bu sırada) içeri aktardığında ve ProjectB, ProjectD içeri aktardığında, MSBuild öncelikle `DefaultTargets` ProjectA, sonra ProjectB, sonra ProjectD ve finally ProjectC ' de belirtilen şekilde görünür.

 İçeri aktarılan projenin şeması, standart bir proje ile aynıdır. MSBuild içeri aktarılan bir proje oluşturabiliyor olsa da, içeri aktarılan bir proje genellikle hangi özelliklerin ayarlanacağı veya hedeflerin çalıştırılacağı sıra hakkında bilgi içermediği için olası bir olasılıktır. İçeri aktarılan proje, bu bilgileri sağlamak için içeri aktarıldığı projeye bağlıdır.

## <a name="wildcards"></a>Joker karakterler

 .NET Framework 4 ' te, MSBuild proje özniteliğinde Joker karakterlere izin verir. Joker karakterler olduğunda, bulunan tüm eşleşmeler sıralanır (reproducibility için) ve ardından sipariş açıkça ayarlanmış gibi bu sırayla içeri aktarılır.

 Bu, başka birinin dosya adını içeri aktarma dosyasına açıkça eklemenize gerek kalmadan bir dosyayı içeri aktarabilmesi için bir genişletilebilirlik noktası sunmak istiyorsanız yararlıdır. Bu amaçla, *Microsoft. Common. targets* dosyanın en üstünde aşağıdaki satırı içerir.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Örnek

 Aşağıdaki örnek, birkaç öğe ve özellik içeren ve genel bir proje dosyasını içeri aktaran bir projeyi gösterir.

```xml
<Project DefaultTargets="Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <resourcefile>Strings.resx</resourcefile>

        <compiledresources>
            $(O)\$(MSBuildProjectName).Strings.resources
        </compiledresources>
    </PropertyGroup>

    <ItemGroup>
        <CSFile Include="*.cs" />

        <Reference Include="System" />
        <Reference Include="System.Data" />
    </ItemGroup>

    <Import Project="$(CommonLocation)\General.targets" />
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Nasıl yapılır: birden çok proje dosyasında aynı hedefi kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
