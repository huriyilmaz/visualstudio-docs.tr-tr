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
ms.openlocfilehash: cca0c55951d4928347528814d043bb8a7c55be9a
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633856"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Nasıl yapılır: Visual Studio derleme işlemini genişletme

Visual Studio derleme işlemi, proje dosyanıza aktarılan MSBuild *. targets* dosyaları serisi tarafından tanımlanır. Bu içeri aktarılan dosyalardan biri olan *Microsoft. Common. targets*, derleme sürecinde birkaç noktada özel görevleri çalıştırmanıza olanak tanımak için genişletilebilir. Bu makalede, Visual Studio derleme işlemini genişletmek için kullanabileceğiniz iki yöntem açıklanmaktadır:

- Ortak hedeflerde tanımlanan belirli önceden tanımlanmış hedefleri geçersiz kılma (*Microsoft. Common. targets* veya içeri aktardığı dosyalar).

- Ortak hedeflerde tanımlanan "Bağımlıdson" özelliklerini geçersiz kılma.
## <a name="override-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kılma

## <a name="override-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kılma

Ortak hedefler, yapı işlemindeki ana hedeflerden önce ve sonra çağrılan bir dizi önceden tanımlanmış boş hedef kümesi içerir. Örneğin, MSBuild, ana `CoreBuild` hedeften önce `BeforeBuild` hedefini ve `CoreBuild` hedeften sonra `AfterBuild` hedefini çağırır. Varsayılan olarak, ortak hedeflerde boş hedefler hiçbir şey yapmaz, ancak ortak hedefleri içeri aktaran bir proje dosyasında istediğiniz hedefleri tanımlayarak varsayılan davranışlarını geçersiz kılabilirsiniz. Önceden tanımlanmış hedefleri geçersiz kılarak, yapı işlemi üzerinde size daha fazla denetim sağlamak için MSBuild görevlerini kullanabilirsiniz.
Ortak hedefler, yapı işlemindeki ana hedeflerden önce ve sonra çağrılan bir dizi önceden tanımlanmış boş hedef kümesi içerir. Örneğin, MSBuild, ana `CoreBuild` hedeften önce `BeforeBuild` hedefini ve `CoreBuild` hedeften sonra `AfterBuild` hedefini çağırır. Varsayılan olarak, ortak hedeflerde boş hedefler hiçbir şey yapmaz, ancak ortak hedefleri içeri aktaran bir proje dosyasında istediğiniz hedefleri tanımlayarak varsayılan davranışlarını geçersiz kılabilirsiniz. Önceden tanımlanmış hedefleri geçersiz kılarak, yapı işlemi üzerinde size daha fazla denetim sağlamak için MSBuild görevlerini kullanabilirsiniz.

> [!NOTE]
> SDK stili projelerin, *Proje dosyasının son satırından sonra*hedeflerin örtük bir şekilde içe aktarılması vardır. Diğer bir deyişle, içeri aktarmaların [nasıl yapılır: MSBuild proje SDK 'Larını kullanma](how-to-use-project-sdk.md)bölümünde açıklandığı şekilde el ile belirtmediğiniz sürece varsayılan hedefleri geçersiz kılamazsınız.

#### <a name="to-override-a-predefined-target"></a>Önceden tanımlanmış bir hedefi geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bir hedef belirler. Güvenli bir şekilde geçersiz kılabilirsiniz hedeflerin tam listesi için aşağıdaki tabloya bakın.

2. Proje dosyanızın sonundaki hedef veya hedefleri, `</Project>` etiketinden hemen önce tanımlayın. Örnek:

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
|`BeforeBuild`, `AfterBuild`|Bu hedefler birinde eklenen görevler önce veya sonra yapı diğer her şey çalışır. **Note:**  `BeforeBuild` ve `AfterBuild` hedefleri, çoğu proje dosyasının sonundaki açıklamalarda zaten tanımlanmış ve proje dosyanıza kolayca ve derleme sonrası olayları kolayca eklemenize olanak tanır.|
|`BeforeRebuild`, `AfterRebuild`|Bu hedefler önce çalıştırması biriyle eklenen veya çekirdek sonra işlevi yeniden görevleri çağrılır. *Microsoft. Common. targets* içindeki hedef yürütmenin sırası: `BeforeRebuild`, `Clean`, `Build`ve sonra `AfterRebuild`.|
|`BeforeClean`, `AfterClean`|Önce bu hedefler birinde eklenen görevleri çalıştırmak veya çekirdek sonra temiz işlevi çağrılır.|
|`BeforePublish`, `AfterPublish`|Bu hedefler önce çalıştırması biriyle eklenen veya sonra çekirdek işlevselliğini yayımlama görevleri çağrılır.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Bu hedefler birinde eklenen görevler önce ya da derleme başvurularını çözüldükten sonra çalışır.|
|`BeforeResGen`, `AfterResGen`|Bu hedefler birinde eklenen görevler önce ya da kaynak oluşturulduktan sonra çalışır.|

## <a name="override-dependson-properties"></a>DependsOn özelliklerini geçersiz kıl

Önceden tanımlanmış hedefleri geçersiz kılmak, yapı sürecini genişletmenin kolay bir yoludur, ancak MSBuild, hedefleri ardışık olarak değerlendirirken, projenizi içeri aktaran başka bir projenin zaten sahip olduğunuz hedefleri geçersiz kılmasını önlemenin bir yolu yoktur geçersiz kılınan. Bu nedenle, örneğin, proje dosyasında tanımlanan son `AfterBuild` hedefi, diğer tüm projeler içeri aktarıldıktan sonra, derleme sırasında kullanılan bir olur.

Ortak hedeflerin tamamında `DependsOnTargets` özniteliklerde kullanılan Bağımlılson özelliklerini geçersiz kılarak, hedeflerin istenmeden geçersiz kılmalara karşı koruma sağlayabilirsiniz. Örneğin, `Build` hedefi `"$(BuildDependsOn)"``DependsOnTargets` öznitelik değerini içerir. Aşağıdakileri dikkate alın:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Bu XML parçası `Build` hedefin çalıştırılabilmesi için önce `BuildDependsOn` özelliğinde belirtilen tüm hedeflerin önce çalıştırılması gerektiğini gösterir. `BuildDependsOn` özelliği şu şekilde tanımlanır:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Bu özellik değerini, proje dosyanızın sonundaki `BuildDependsOn` adlı başka bir özelliği bildirerek geçersiz kılabilirsiniz. Önceki `BuildDependsOn` özelliğini yeni özelliğe dahil ederek, hedef listenin başına ve sonuna yeni hedefler ekleyebilirsiniz. Örnek:

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

2. Özellik veya özellikleri, proje dosyasının sonunda başka bir örneğini tanımlar. Özgün özelliği, örneğin `$(BuildDependsOn)`, yeni özellikte ekleyin.

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
- [. targets dosyaları](../msbuild/msbuild-dot-targets-files.md)
