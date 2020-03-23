---
title: Proje Öğesi (MSBuild) | Microsoft Dokümanlar
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df9eff3e941cc21aaa71c2779a72084e12e8e590
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632985"
---
# <a name="project-element-msbuild"></a>Proje öğesi (MSBuild)

MSBuild proje dosyasının gerekli kök öğesi.

## <a name="syntax"></a>Sözdizimi

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

| Öznitelik | Açıklama |
|------------------------| - |
| `DefaultTargets` | İsteğe bağlı öznitelik.<br /><br /> Hedef belirtilmemişse, varsayılan hedef veya hedef yapının giriş noktası olmayı hedefler. Birden fazla hedef yarı kolonlu (;) Sınırlandırılmış.<br /><br /> Öznitelik veya MSBuild komut `DefaultTargets` satırında varsayılan hedef belirtilmemişse, [akit](../msbuild/import-element-msbuild.md) öğeleri değerlendirildikten sonra motor proje dosyasındaki ilk hedefi yürütür. |
| `InitialTargets` | İsteğe bağlı öznitelik.<br /><br /> Öznitelikte veya komut satırında `DefaultTargets` belirtilen hedeflerden önce çalıştırılacak ilk hedef veya hedefler. Birden fazla hedef yarı-kolon (`;`) sınırlıdır. Birden çok içe `InitialTargets`aktarılan dosya tanımlanırsa, söz konusu tüm hedefler, içe aktarma sırasına göre çalıştırılır. |
| `Sdk` | İsteğe bağlı öznitelik. <br /><br /> .proj dosyasına eklenen örtülü Alma deyimleri oluşturmak için kullanılacak SDK adı ve isteğe bağlı sürüm. Sürüm belirtilmemişse, MSBuild varsayılan sürümü çözmeye çalışır.  Örneğin `<Project Sdk="Microsoft.NET.Sdk" />` veya `<Project Sdk="My.Custom.Sdk/1.0.0" />` olabilir. |
| `ToolsVersion` | İsteğe bağlı öznitelik.<br /><br /> MSBuild Araç Seti sürümü $(MSBuildBinPath) ve $(MSBuildToolsPath) değerlerini belirlemek için kullanır. |
| `TreatAsLocalProperty` | İsteğe bağlı öznitelik.<br /><br /> Genel olarak kabul edilmeyecek özellik adları. Bu öznitelik, belirli komut satırı özelliklerinin proje veya hedef dosyasında ve sonraki tüm içe almalarda ayarlanan özellik değerlerini geçersiz kılmasını önler. Birden fazla özellik yarı-kolon (;) Sınırlandırılmış.<br /><br /> Normalde, genel özellikler proje veya hedef dosyasında ayarlanan özellik değerlerini geçersiz kılar. Özellik `TreatAsLocalProperty` değerde listelenmişse, genel özellik değeri bu dosyada ayarlanan özellik değerlerini ve sonraki tüm içeri aktarımları geçersiz kılmaz. Daha fazla bilgi için [bkz: Farklı seçeneklerle aynı kaynak dosyaları oluşturun.](../msbuild/how-to-build-the-same-source-files-with-different-options.md) **Not:**  **-özellik** (veya **-p)** anahtarını kullanarak genel özellikleri komut isteminde ayarlarsınız. Ayrıca, MSBuild görevinin özniteliğini `Properties` kullanarak çok projeli bir yapıdaki alt projeler için genel özellikleri ayarlayabilir veya değiştirebilirsiniz. Daha fazla bilgi için [MSBuild görevine](../msbuild/msbuild-task.md)bakın. |
| `xmlns` | İsteğe bağlı öznitelik.<br /><br /> Belirtildiğinde, `xmlns` öznitelik `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Alt öğeleri

| Öğe | Açıklama |
| - | - |
| [Seçin:](../msbuild/choose-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Değerlendirilecek bir `ItemGroup` öğe ve/veya `PropertyGroup` öğe kümesi seçmek için alt öğeleri değerlendirir. |
| [İçeri Aktarma](../msbuild/import-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Proje dosyasının başka bir proje dosyasını içe aktarmasını sağlar. Bir projede sıfır `Import` veya daha fazla öğe olabilir. |
| [İthalat Grubu](../msbuild/importgroup-element.md) | İsteğe bağlı öğe.<br /><br /> İsteğe bağlı `Import` bir koşul altında gruplandırılmış öğeler topluluğu içerir. |
| [ıtemgroup](../msbuild/itemgroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Tek tek öğeler için bir gruplandırma öğesi. Öğeler [Öğe](../msbuild/item-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır `ItemGroup` veya daha fazla öğe olabilir. |
| [ıtemdefinitiongroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Varsayılan olarak, projedeki tüm öğelere uygulanan meta veri değerleri olan Madde Tanımları kümesini tanımlamanızı sağlar. ItemDefinitionGroup, görev ve görevin `CreateItem` kullanılması gereksiniminin `CreateProperty` yerini alır. |
| [Proje Uzantıları](../msbuild/projectextensions-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> MSBuild proje dosyasında MSBuild olmayan bilgileri kalıcı olarak sürdürmek için bir yol sağlar. Projede sıfır veya `ProjectExtensions` bir öğe olabilir. |
| [Propertygroup](../msbuild/propertygroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Tek tek özellikler için bir gruplandırma öğesi. Özellikler [Özellik](../msbuild/property-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır `PropertyGroup` veya daha fazla öğe olabilir. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Bir MSBuild projesi SDK'ya başvurur.  Bu öğe Sdk özniteliğine alternatif olarak kullanılabilir. |
| [Hedef](../msbuild/target-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> MSBuild'in sırayla çalıştırılaması için bir dizi görev içerir. Görevler [Görev](../msbuild/task-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır `Target` veya daha fazla öğe olabilir. |
| [Usingtask](../msbuild/usingtask-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> MSBuild'te görevleri kaydetmek için bir yol sağlar. Bir projede sıfır `UsingTask` veya daha fazla öğe olabilir. |

### <a name="parent-elements"></a>Üst öğeler

 Yok.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: İlk hangi hedefi oluşturacaklarını belirtin](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [Msbuild](../msbuild/msbuild.md)
