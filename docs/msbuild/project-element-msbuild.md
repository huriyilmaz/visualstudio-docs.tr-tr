---
title: Proje öğesi (MSBuild) | Microsoft Docs
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
ms.openlocfilehash: 1bb7c49e4f3dc86594c8a3211bacb538d3f10c4f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75597444"
---
# <a name="project-element-msbuild"></a>Proje öğesi (MSBuild)
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasının gerekli kök öğesi.

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

### <a name="attributes"></a>{1&gt;{2&gt;Öznitelikler&lt;2}&lt;1}

| Öznitelik | Açıklama |
|------------------------| - |
| `DefaultTargets` | İsteğe bağlı öznitelik.<br /><br /> Hedef belirtilmemişse, varsayılan hedef veya hedefler, yapı giriş noktası olarak kullanılır. Birden çok hedef noktalı virgül (;) Ted.<br /><br /> `DefaultTargets` özniteliğinde veya [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] komut satırında hiçbir varsayılan hedef belirtilmemişse, [Içe aktarma](../msbuild/import-element-msbuild.md) öğeleri değerlendirildikten sonra motor proje dosyasındaki ilk hedefi yürütür. |
| `InitialTargets` | İsteğe bağlı öznitelik.<br /><br /> `DefaultTargets` özniteliğinde veya komut satırında belirtilen hedeflerden önce çalıştırılacak başlangıç hedefi veya hedefleri. Birden çok hedef noktalı virgül (`;`) ile ayrılır. Birden fazla içeri aktarılan dosya `InitialTargets`tanımladıysa, belirtilen tüm hedefler içeri aktarmaların karşılaştığı sırada çalıştırılır. |
| `Sdk` | İsteğe bağlı öznitelik. <br /><br /> . Proj dosyasına eklenen örtük Içeri aktarma deyimleri oluşturmak için kullanılacak SDK adı ve isteğe bağlı sürüm. Sürüm belirtilmemişse, MSBuild varsayılan bir sürümü çözümlemeye çalışır.  Örneğin, `<Project Sdk="Microsoft.NET.Sdk" />` veya `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | İsteğe bağlı öznitelik.<br /><br /> Araç kümesi MSBuild 'in sürümü, $ (MSBuildBinPath) ve $ (Msbuildaraçları yolu) değerlerini belirlemede kullanır. |
| `TreatAsLocalProperty` | İsteğe bağlı öznitelik.<br /><br /> Genel olarak değerlendirilmeyecek Özellik adları. Bu öznitelik, belirli komut satırı özelliklerinin bir proje veya hedefler dosyasında ve sonraki tüm içeri aktarmalarda ayarlanan özellik değerlerini geçersiz kılmasını önler. Birden çok özellik noktalı virgül (;) Ted.<br /><br /> Normal olarak, genel özellikler proje veya hedefler dosyasında ayarlanan özellik değerlerini geçersiz kılar. Özellik `TreatAsLocalProperty` değerinde listeleniyorsa, genel özellik değeri bu dosyada ve sonraki tüm içeri aktarmalarda ayarlanan özellik değerlerini geçersiz kılmaz. Daha fazla bilgi için bkz. [nasıl yapılır: farklı seçeneklerle aynı kaynak dosyaları oluşturma](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Note:**  **-Property** (veya **-p**) anahtarını kullanarak bir komut isteminde genel özellikleri ayarlarsınız. Ayrıca, MSBuild görevinin `Properties` özniteliğini kullanarak, çok projeli bir derlemede alt projeler için genel özellikleri ayarlayabilir veya değiştirebilirsiniz. Daha fazla bilgi için bkz. [MSBuild görevi](../msbuild/msbuild-task.md). |
| `xmlns` | İsteğe bağlı öznitelik.<br /><br /> Belirtildiğinde `xmlns` özniteliği `http://schemas.microsoft.com/developer/msbuild/2003`değerine sahip olmalıdır. |

### <a name="child-elements"></a>Alt öğeleri

| Öğe | Açıklama |
| - | - |
| ['Yu](../msbuild/choose-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> , Değerlendirmek için bir `ItemGroup` öğe ve/veya `PropertyGroup` öğeleri kümesi seçmek üzere alt öğeleri değerlendirir. |
| [İçeri Aktar](../msbuild/import-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Proje dosyasının başka bir proje dosyasını içeri aktarmasını sağlar. Bir projede sıfır veya daha fazla öğe `Import` olabilir. |
| [ImportGroup](../msbuild/importgroup-element.md) | İsteğe bağlı öğe.<br /><br /> İsteğe bağlı bir koşul altında gruplanan `Import` öğelerinden oluşan bir koleksiyon içerir. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Ayrı öğeler için bir gruplandırma öğesi. Öğeler [Item](../msbuild/item-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla öğe `ItemGroup` olabilir. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Varsayılan olarak, projedeki tüm öğelere uygulanan meta veri değerleri olan öğe tanımları kümesini tanımlamanızı sağlar. ItemDefinitionGroup, `CreateItem` görevi ve `CreateProperty` görevini kullanma gereksinimizin yerini alır. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje dosyasında[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] olmayan bilgilerin kalıcı hale getirilmesi için bir yol sağlar. Bir projede sıfır veya bir `ProjectExtensions` öğe olabilir. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> Ayrı özellikler için bir gruplandırma öğesi. Özellikler, [özellik](../msbuild/property-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla öğe `PropertyGroup` olabilir. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] proje SDK 'sına başvurur.  Bu öğe SDK özniteliğine alternatif olarak kullanılabilir. |
| [Hedef](../msbuild/target-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] sırayla yürütülecek bir görev kümesi içerir. Görevler, [görev](../msbuild/task-element-msbuild.md) öğesi kullanılarak belirtilir. Bir projede sıfır veya daha fazla öğe `Target` olabilir. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | İsteğe bağlı öğe.<br /><br /> [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]görevleri kaydetmek için bir yol sağlar. Bir projede sıfır veya daha fazla öğe `UsingTask` olabilir. |

### <a name="parent-elements"></a>Üst öğeler
 Yok.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: önce hangi hedefin oluşturulacağını belirtme](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Komut satırı başvurusu](../msbuild/msbuild-command-line-reference.md)
- [Proje dosyası şema başvurusu](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)
