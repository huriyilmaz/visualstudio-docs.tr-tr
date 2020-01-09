---
title: Derleme işlemini genişletme
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, overriding predefined targets
- MSBuild, overriding DependsOn properties
- MSBuild, extending Visual Studio builds
- MSBuild, DependsOn properties
ms.assetid: cb077613-4a59-41b7-96ec-d8516689163c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 995bf368d367d51a3d38e02dbab2d6e55ff4ab13
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75575932"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Nasıl yapılır: Visual Studio derleme işlemini genişletme
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Yapı işlemi bir dizi tarafından tanımlanan [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] *.targets* proje dosyanıza aktarmış dosyaları. Dosyaları, bunlardan alınan *Microsoft.Common.targets*, yapı işleminde bazı noktalarda özel görevleri çalıştırmanıza olanak tanır şekilde genişletilebilir. Bu makalede genişletmek için kullanabileceğiniz iki yöntem anlatılmaktadır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] derleme işlemi:

- Ortak hedeflerde tanımlanan belirli önceden tanımlanmış hedefleri geçersiz kılma (*Microsoft. Common. targets* veya içeri aktardığı dosyalar).

- Ortak hedeflerde tanımlanan "Bağımlıdson" özelliklerini geçersiz kılma.

## <a name="override-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kılma
Ortak hedefler, yapı işlemindeki ana hedeflerden önce ve sonra çağrılan bir dizi önceden tanımlanmış boş hedef kümesi içerir. Örneğin, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] çağrıları `BeforeBuild` ana önce hedef `CoreBuild` hedef ve `AfterBuild` sonra hedef `CoreBuild` hedef. Varsayılan olarak, ortak hedeflerde boş hedefler hiçbir şey yapmaz, ancak ortak hedefleri içeri aktaran bir proje dosyasında istediğiniz hedefleri tanımlayarak varsayılan davranışlarını geçersiz kılabilirsiniz. Kullanabileceğiniz önceden tanımlanmış hedefleri geçersiz kılma [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] yapı işlemi hakkında daha fazla denetime size görevleri.

> [!NOTE]
> SDK stili projelerin, *Proje dosyasının son satırından sonra*hedeflerin örtük bir şekilde içe aktarılması vardır. Diğer bir deyişle, içeri aktarmaların [nasıl yapılır: MSBuild proje SDK 'Larını kullanma](how-to-use-project-sdk.md)bölümünde açıklandığı şekilde el ile belirtmediğiniz sürece varsayılan hedefleri geçersiz kılamazsınız.

#### <a name="to-override-a-predefined-target"></a>Önceden tanımlanmış bir hedefi geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bir hedef belirler. Güvenli bir şekilde geçersiz kılabilirsiniz hedeflerin tam listesi için aşağıdaki tabloya bakın.

2. Hemen önce hedef veya hedefleri, proje dosyasının sonunda tanımlamak `</Project>` etiketi. Örneğin:

    ```xml
    <Project>
        ...
        <Target Name="BeforeBuild">
            <!-- Insert tasks to run before build here -->
        </Target>
        <Target Name="AfterBuild">
            <!-- Insert tasks to run after build here -->
        </Target>
    </Project>
    ```

3. Proje dosyası oluşturun.

Aşağıdaki tabloda, güvenle geçersiz kılabileceğiniz ortak hedeflerin tüm hedefleri gösterilmektedir.

|Hedef adı|Açıklama|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Bu hedefler birinde eklenen görevler önce veya çekirdek derleme tamamlandıktan sonra çalışır. Çoğu özelleştirmeleri, bu iki hedefi birinde gerçekleştirilir.|
|`BeforeBuild`, `AfterBuild`|Bu hedefler birinde eklenen görevler önce veya sonra yapı diğer her şey çalışır. **Not:** `BeforeBuild` ve `AfterBuild` hedefleri sonunda öncesi ve derleme sonrası olayları proje dosyanıza kolayca eklemenize olanak sağlayan, çoğu proje dosyaları, açıklamalar içinde zaten tanımlanmıştır.|
|`BeforeRebuild`, `AfterRebuild`|Bu hedefler önce çalıştırması biriyle eklenen veya çekirdek sonra işlevi yeniden görevleri çağrılır. Hedef yürütme sırası *Microsoft.Common.targets* olduğu: `BeforeRebuild`, `Clean`, `Build`, ardından `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Önce bu hedefler birinde eklenen görevleri çalıştırmak veya çekirdek sonra temiz işlevi çağrılır.|
|`BeforePublish`, `AfterPublish`|Bu hedefler önce çalıştırması biriyle eklenen veya sonra çekirdek işlevselliğini yayımlama görevleri çağrılır.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Bu hedefler birinde eklenen görevler önce ya da derleme başvurularını çözüldükten sonra çalışır.|
|`BeforeResGen`, `AfterResGen`|Bu hedefler birinde eklenen görevler önce ya da kaynak oluşturulduktan sonra çalışır.|

## <a name="override-dependson-properties"></a>DependsOn özelliklerini geçersiz kıl
Önceden tanımlanmış hedefleri geçersiz kılma derleme işlemini genişletme için kolay bir yol olduğunu ancak, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] hedefleri tanımını ardışık olarak değerlendirir projenizi hedefleri geçersiz kılmasını içeri aktarır. başka bir proje önlemek için bir yolu yoktur, zaten silmiş. Bunu, örneğin, son `AfterBuild` sonra diğer tüm projeleri içe aktarılmış, yapı sırasında kullanılan bir proje dosyasında tanımlanmış hedefi.

Ortak hedeflerin tamamında `DependsOnTargets` özniteliklerde kullanılan Bağımlılson özelliklerini geçersiz kılarak, hedeflerin istenmeden geçersiz kılmalara karşı koruma sağlayabilirsiniz. Örneğin, `Build` hedefi içeren bir `DependsOnTargets` öznitelik değerini `"$(BuildDependsOn)"`. Aşağıdakileri dikkate alın:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Bu XML parçası önce belirten `Build` hedef çalışma zamanı, tüm hedefler belirtilen `BuildDependsOn` özelliği ilk çalıştırmalısınız. `BuildDependsOn` Özelliği olarak tanımlanır:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Adlı başka bir özellik bildirerek bu özellik değerini geçersiz kılabilirsiniz `BuildDependsOn` , proje dosyasının sonunda. Önceki ekleyerek `BuildDependsOn` özelliği yeni özelliği, yeni hedefleri başına hem de hedef listesinin sonuna ekleyebilirsiniz. Örneğin:

```xml
<PropertyGroup>
    <BuildDependsOn>
        MyCustomTarget1;
        $(BuildDependsOn);
        MyCustomTarget2
    </BuildDependsOn>
</PropertyGroup>

<Target Name="MyCustomTarget1">
    <Message Text="Running MyCustomTarget1..."/>
</Target>
<Target Name="MyCustomTarget2">
    <Message Text="Running MyCustomTarget2..."/>
</Target>
```

Proje dosyalarını içeri aktaran projeler, yaptığınız özelleştirmelerin üzerine yazmadan bu özellikleri geçersiz kılabilirsiniz.

#### <a name="to-override-a-dependson-property"></a>DependsOn özelliği geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bir Bağımlıdson özelliğini belirler. Yaygın olarak geçersiz kılınan DependsOn özelliklerinin bir listesi için aşağıdaki tabloya bakın.

2. Özellik veya özellikleri, proje dosyasının sonunda başka bir örneğini tanımlar. Özgün özelliği, örneğin `$(BuildDependsOn)`, yeni özellik de.

3. Önce veya sonra özellik tanımı özel hedeflerinizi tanımlayın.

4. Proje dosyası oluşturun.

### <a name="commonly-overridden-dependson-properties"></a>Yaygın olarak geçersiz kılınan DependsOn özellikleri

|Özellik adı|Açıklama|
|-------------------|-----------------|
|`BuildDependsOn`|Önce veya sonra tüm derleme işlemi özel hedefleri eklemek istiyorsanız geçersiz kılmak için özellik.|
|`CleanDependsOn`|Derleme işlemi özel çıkışı Temizle istiyorsanız geçersiz kılmak için özellik.|
|`CompileDependsOn`|Özel işlemler önce veya sonra derleme adımı eklemek istiyorsanız geçersiz kılmak için özellik.|

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio tümleştirmesi](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [.targets dosyaları](../msbuild/msbuild-dot-targets-files.md)
