---
title: İçeri aktarma öğesi (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 13ffaff052e672eb900d5ed3a1ce5ae7c2a370df
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75573999"
---
# <a name="import-element-msbuild"></a>İçeri aktarma öğesi (MSBuild)
Bir proje dosyasının içeriğini başka bir proje dosyasına aktarır.

\<Proje > \<Içeri aktarma >

## <a name="syntax"></a>Sözdizimi

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Project`|Gerekli öznitelik.<br /><br /> İçeri aktarılacak proje dosyasının yolu. Yol joker karakterler içerebilir. Eşleşen dosyalar sıralanmış sırada içeri aktarılır. Bu özelliği kullanarak, kod dosyasını bir dizine ekleyerek bir projeye kod ekleyebilirsiniz.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek koşul. Daha fazla bilgi için bkz. [koşullar](../msbuild/msbuild-conditions.md).|
|`Sdk`| İsteğe bağlı öznitelik.<br /><br /> Proje SDK 'sına başvurur.|

### <a name="child-elements"></a>Alt öğeleri
 Yok.

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasının gerekli kök öğesi. |
| [ImportGroup](../msbuild/importgroup-element.md) | İsteğe bağlı bir koşul altında gruplanmış bir `Import` öğeleri koleksiyonu içerir. |

## <a name="remarks"></a>Açıklamalar
 `Import` öğesini kullanarak, birçok proje dosyası için ortak olan kodu yeniden kullanabilirsiniz. Bu, paylaşılan kodda yaptığınız tüm güncelleştirmeler tarafından içeri aktarılan tüm projelere yayıldığından, kodun korunmasını kolaylaştırır.

 Kurala göre, paylaşılan içe aktarılan proje dosyaları *. targets* dosyaları olarak kaydedilir, ancak bunlar standart [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyalarıdır. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], farklı bir dosya adı uzantısına sahip bir projeyi içeri aktarmamalarını engellemez, ancak *. targets* uzantısını tutarlılık için kullanmanızı öneririz.

 İçeri aktarılan projelerdeki göreli yollar, içeri aktarılan projenin dizinine göre yorumlanır. Bu nedenle, bir proje dosyası farklı konumlarda birkaç proje dosyasına aktarılmışsa, içeri aktarılan proje dosyasındaki göreli yollar, içeri aktarılan her proje için farklı şekilde yorumlanacak.

 Proje dosyası ile ilgili tüm [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ayrılmış özellikler, örneğin, içeri aktarılan bir projede başvurulan `MSBuildProjectDirectory` ve `MSBuildProjectFile`, içeri aktarma projesi dosyasına göre değerler atanır.

 İçeri aktarılan projenin bir `DefaultTargets` özniteliği yoksa, içeri aktarılan projeler içeri aktarıldıkları sırada incelenir ve ilk keşfedilen `DefaultTargets` özniteliğinin değeri kullanılır. Örneğin, ProjectA, ProjectB ve ProjectC 'yi (Bu sırada) içeri aktardığında ve ProjectB, ProjectD 'yi içeri aktardığında, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] önce ProjectA, sonra ProjectB, sonra ProjectD ve finally ProjectC üzerinde belirtilen `DefaultTargets` bakar.

 İçeri aktarılan projenin şeması, standart bir proje ile aynıdır. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] içeri aktarılan bir proje oluşturabiliyor olsa da, içeri aktarılan bir proje genellikle hangi özelliklerin ayarlanacağı veya hedeflerin çalıştırılacağı sıra hakkında bilgi içermediği için olası bir olasılıktır. İçeri aktarılan proje, bu bilgileri sağlamak için içeri aktarıldığı projeye bağlıdır.

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
