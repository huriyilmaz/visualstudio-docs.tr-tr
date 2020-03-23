---
title: Alma Öğesi (MSBuild) | Microsoft Dokümanlar
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
ms.openlocfilehash: 7d9e66934015c7c4a57c7d7c6911b9ebe02ac536
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094491"
---
# <a name="import-element-msbuild"></a>Alma öğesi (MSBuild)

Bir proje dosyasının içeriğini başka bir proje dosyasına aktarın.

\<Proje \<> İthalat>

## <a name="syntax"></a>Sözdizimi

```xml
<Import Project="ProjectPath"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|`Project`|Gerekli öznitelik.<br /><br /> Proje dosyasının içe aktarılasonraki yolu. Yol joker karakterler içerebilir. Eşleşen dosyalar sırayla alınır. Bu özelliği kullanarak, yalnızca kod dosyasını bir dizine ekleyerek projeye kod ekleyebilirsiniz.|
|`Condition`|İsteğe bağlı öznitelik.<br /><br /> Değerlendirilecek bir durum. Daha fazla bilgi için [Koşullar'a](../msbuild/msbuild-conditions.md)bakın.|
|`Sdk`| İsteğe bağlı öznitelik.<br /><br /> Bir proje SDK'ya başvurur.|

### <a name="child-elements"></a>Alt öğeleri

 None

### <a name="parent-elements"></a>Üst öğeler

| Öğe | Açıklama |
| - | - |
| [Proje](../msbuild/project-element-msbuild.md) | MSBuild proje dosyasının gerekli kök öğesi. |
| [İthalat Grubu](../msbuild/importgroup-element.md) | İsteğe bağlı `Import` bir koşul altında gruplandırılmış öğeler topluluğu içerir. |

## <a name="remarks"></a>Açıklamalar

 Öğeyi `Import` kullanarak, birçok proje dosyasında ortak olan kodu yeniden kullanabilirsiniz. Paylaşılan kodda yaptığınız tüm güncelleştirmeler, kodu içe aktaran tüm projelere yayıldığı için kodun korunmasını kolaylaştırır.

 Kuralına göre, paylaşılan içe aktarılan proje dosyaları *.hedef* dosyaları olarak kaydedilir, ancak bunlar standart MSBuild proje dosyalarıdır. MSBuild, farklı bir dosya adı uzantısı olan bir projeyi almanızı engellemez, ancak tutarlılık için *.targets* uzantısını kullanmanızı öneririz.

 İçe aktarılan projelerdeki göreli yollar, içe aktarılan projenin dizinine göre yorumlanır (bu paragrafta daha sonra açıklanan birkaç istisna dışında). Bu nedenle, bir proje dosyası farklı konumlarda birden çok proje dosyasına aktarılırsa, alınan proje dosyasındaki göreli yollar içe aktarılan her proje için farklı şekilde yorumlanır. İki istisna vardır. Bir istisna, `Import` öğelerde, yolun her zaman `Import` öğeyi içeren projeye göre yorumlanmasıdır. Başka bir özel `UsingTask` durum, her zaman `AssemblyFile` `UsingTask` öğeiçeren dosyaya göre öznitelik için göreli yolu yorumlar.

 Örneğin, proje dosyasıyla ilgili `MSBuildProjectDirectory` tüm MSBuild ayrılmış `MSBuildProjectFile`özellikleri ve içe aktarılan projede başvurulan tüm MSBuild ayrılmış özellikleri, içe aktarılan proje dosyasına göre değerler atanır.

 Alınan projenin bir `DefaultTargets` özniteliği yoksa, alınan projeler içe aktarıldıkları sırada denetlenir ve keşfedilen `DefaultTargets` ilk özniteliğin değeri kullanılır. Örneğin, ProjectA ProjectB ve ProjectC'i (bu sırada) içeri alırsa ve ProjectB ProjectD'i içeri alırsa, MSBuild önce `DefaultTargets` ProjectA'da, sonra ProjectB'de, sonra ProjectB'de ve son olarak ProjectC'de belirtilir.

 İthal edilen bir projenin şeması standart bir projenin şemasıyla aynıdır. MSBuild içe aktarılan bir proje yi oluşturabilse de, içe aktarılan bir proje genellikle hangi özelliklerin ayarlanabileceği veya hedefleri çalıştırılma sırası hakkında bilgi içermediğinden olası değildir. İçe aktarılan proje, bu bilgileri sağlamak için içe aktarıldığı projeye bağlıdır.

## <a name="wildcards"></a>Joker karakterler

 .NET Framework 4'te, MSBuild Proje özniteliğindeki joker karakterlere izin verir. Joker karakterler olduğunda, bulunan tüm eşleşmeler sıralanır (tekrarlanabilirlik için) ve sıra açıkça ayarlanmış gibi bu sırada alınır.

 Bu, dosya adını açıkça içe aktarma dosyasına eklemenize gerek kalmadan bir başkasının dosyayı içe aktarabilmesi için bir genişletilebilirlik noktası sunmak istiyorsanız yararlıdır. Bu amaçla, *Microsoft.Common.Targets* dosyanın üst kısmında aşağıdaki satırı içerir.

```xml
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>
```

## <a name="example"></a>Örnek

 Aşağıdaki örnek, birkaç öğe ve özelliği olan ve genel bir proje dosyası içe aktaran bir projeyi gösterir.

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
- [Nasıl kullanılır: Birden çok proje dosyasında aynı hedefi kullanma](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
