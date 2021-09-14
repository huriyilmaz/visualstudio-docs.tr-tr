---
title: Derleme işlemini genişletme
description: Projenizin nasıl derlemesini kontrol etmek ve özelleştirmek için derleme işlemini değiştirmenin çeşitli yollarını öğrenin.
ms.custom: seodec18, SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: db2b813937c4966dd4acd37b6e053cbe533e993c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625701"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Nasıl Visual Studio: Visual Studio genişletme

Derleme Visual Studio, proje dosyanıza aktarılan MSBuild *.targets* dosyaları dizisi tarafından tanımlanır. Bu içe aktarılan dosyalardan biri olan *Microsoft.Common.targets,* derleme işleminin çeşitli noktalarında özel görevler çalıştırmanızı sağlayacak şekilde genişletilmiş olabilir. Bu makalede derleme işlemini genişletmek için kullanabileceğiniz iki yöntem Visual Studio açıklanmıştır:

- Ortak hedeflerde tanımlanan önceden tanımlanmış belirli hedefleri geçersiz kılma *(Microsoft.Common.targets* veya içeri aktarmış olduğu dosyalar).

- Ortak hedeflerde tanımlanan "DependsOn" özelliklerini geçersiz kılma.

## <a name="override-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kılma

Ortak hedefler, derleme sürecindeki bazı ana hedeflerden önce ve sonra çağrılmış önceden tanımlanmış boş hedefler içerir. Örneğin, MSBuild önce hedefi, sonra da `BeforeBuild` `CoreBuild` hedefi `AfterBuild` çağıran bir hedef `CoreBuild` olabilir. Varsayılan olarak, ortak hedeflerde boş hedefler hiçbir şey yapmasa da, ortak hedefleri içeri aktaran bir proje dosyasında istediğiniz hedefleri tanımlayarak varsayılan davranışlarını geçersiz kılabilirsiniz. Önceden tanımlanmış hedefleri geçersiz karak, derleme MSBuild daha fazla denetim vermek için görevleri kullanabilirsiniz.

> [!NOTE]
> SDK stili projelerin, proje dosyasının son satırı sonrasında *hedeflerin örtülü bir içeri aktarması vardır.* Bu, içeri aktarmalarınızı Nasıl yapılır: Proje SDK'larını kullanma konusunda açıklandığı gibi el ile [MSBuild geçersiz kılamazsınız.](how-to-use-project-sdk.md)

#### <a name="to-override-a-predefined-target"></a>Önceden tanımlanmış bir hedefi geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bir hedef belirleme. Güvenli bir şekilde geçersiz kılabilirsiniz hedeflerin tam listesi için aşağıdaki tabloya bakın.

2. Proje dosyanın sonunda etiketin hemen öncesinde hedefi veya hedefleri `</Project>` tanımlayın. Örnek:

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

3. Proje dosyasını derleme.

Aşağıdaki tabloda ortak hedeflerde yer alan ve güvenli bir şekilde geçersiz kılabilirsiniz.

|Hedef ad|Description|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Bu hedeflerden birinin içine eklenen görevler, çekirdek derleme yapılmadan önce veya sonra çalıştırıldığında. Özelleştirmelerin çoğu bu iki hedefte yapılır.|
|`BeforeBuild`, `AfterBuild`|Bu hedeflerden birinin içine eklenen görevler, derlemenin diğer her şeyden önce veya sonra çalıştırıldığında. **Not:**  ve hedefleri, çoğu proje dosyasının sonundaki açıklamalarda zaten tanımlanmıştır ve proje dosyanıza kolayca derleme öncesi ve sonrası `BeforeBuild` `AfterBuild` olaylar eklemenize olanak sağlar.|
|`BeforeRebuild`, `AfterRebuild`|Bu hedeflerden birinin içine eklenen görevler, çekirdek yeniden oluşturma işlevi çağrılmadan önce veya sonra çalıştırıldığında. *Microsoft.Common.targets'ta* hedef yürütme sırası şu şekildedir: `BeforeRebuild` , , ve ardından `Clean` `Build` `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Bu hedeflerden birinin içine eklenen görevler, temel temiz işlevsellik çağrılmadan önce veya sonra çalıştırıldığında.|
|`BeforePublish`, `AfterPublish`|Bu hedeflerden birinin içine eklenen görevler, çekirdek yayımlama işlevi çağrılmadan önce veya sonra çalıştırıldığında.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Bu hedeflerden biri içine eklenen görevler, derleme başvuruları çözümlendikten önce veya sonra çalıştırıldığında.|
|`BeforeResGen`, `AfterResGen`|Bu hedeflerden birinin içine eklenen görevler, kaynaklar oluşturulmadan önce veya sonra çalıştırıldığında.|

## <a name="example-aftertargets-and-beforetargets"></a>Örnek: AfterTargets ve BeforeTargets

Aşağıdaki örnek, çıkış dosyalarıyla `AfterTargets` bir şey yapmak üzere özel bir hedef eklemek için özniteliğinin nasıl kullanılageldi. Bu durumda, çıktı dosyalarını *CustomOutput* klasörüne kopyalar.  Örnek ayrıca öznitelik kullanarak ve özel temizleme işlemi hedeften önce çalıştırılan belirterek özel derleme işlemi tarafından oluşturulan dosyaların nasıl `CustomClean` `BeforeTargets` temizlenir? `CoreClean`

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
     <TargetFramework>netcoreapp3.1</TargetFramework>
     <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

  <Target Name="CustomAfterBuild" AfterTargets="Build">
    <ItemGroup>
      <_FilesToCopy Include="$(OutputPath)**\*"/>
    </ItemGroup>
    <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

    <Message Text="DestFiles:
        @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles=
          "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean" BeforeTargets="CoreClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

> [!WARNING]
> Önceki bölümde tabloda listelenen önceden tanımlanmış hedeflerden farklı adlar (örneğin, özel derleme hedefine burada değil adını verdik) emin olun çünkü önceden tanımlanmış hedefler de bunları tanımlayan SDK içeri aktarması tarafından geçersiz `CustomAfterBuild` `AfterBuild` kılınır. Bu hedefleri geçersiz kılmaya yönelik hedef dosyanın içeri aktarını görmüyorsanız, ancak SDK'ya başvurmak için öznitelik yöntemini kullanırsanız proje dosyasının sonuna örtülü olarak `Sdk` eklenir.

## <a name="override-dependson-properties"></a>DependsOn özelliklerini geçersiz kılma

Önceden tanımlanmış hedefleri geçersiz kılma, derleme işlemini genişletmek için kolay bir yol sağlar, ancak MSBuild hedef tanımını sırayla değerlendirene için, projenizi içeri aktaran başka bir projenin zaten geçersiz kmış olduğu hedefleri geçersiz kılmasını önlemenin bir yolu yoktur. Bu nedenle, örneğin, proje dosyasında tanımlanan son hedef, diğer tüm projeler içe aktarıldıktan sonra `AfterBuild` derleme sırasında kullanılan hedef olur.

Ortak hedefler genelinde özniteliklerde kullanılan DependsOn özelliklerini geçersiz kılarak hedeflerin unintended geçersiz kılmalarına `DependsOnTargets` karşı koruma sabilirsiniz. Örneğin, hedef `Build` bir öznitelik değeri `DependsOnTargets` `"$(BuildDependsOn)"` içerir. Aşağıdakileri dikkate alın:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Bu XML parçası, hedef `Build` çalıştırılamadan önce özelliğinde belirtilen tüm hedeflerin önce `BuildDependsOn` çalışması gerektiğini gösterir. özelliği `BuildDependsOn` şu şekilde tanımlanır:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Proje dosyanın sonunda adlı başka bir özellik `BuildDependsOn` bildirerek bu özellik değerini geçersiz kılabilirsiniz. Önceki özelliği `BuildDependsOn` yeni özelliğine dahil etmekle, hedef listesinin başına ve sonuna yeni hedefler ekleyebilirsiniz. Örnek:

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

Proje dosyalarınızı içeri aktaran projeler, yapmış olduğunu özelleştirmelerin üzerine yazmadan bu özellikleri geçersiz kılabilir.

#### <a name="to-override-a-dependson-property"></a>DependsOn özelliğini geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bir DependsOn özelliğini belirleme. Yaygın olarak geçersiz kılınan DependsOn özelliklerinin listesi için aşağıdaki tabloya bakın.

2. Proje dosyanız sonunda özelliğin veya özelliklerin başka bir örneğini tanımlayın. Yeni özelliğine özgün özelliği `$(BuildDependsOn)` (örneğin) dahil etmek.

3. Özellik tanımı öncesinde veya sonrasında özel hedeflerinizi tanımlayın.

4. Proje dosyasını derleme.

### <a name="commonly-overridden-dependson-properties"></a>Yaygın olarak DependsOn özelliklerini geçersiz kılma

|Özellik adı|Description|
|-------------------|-----------------|
|`BuildDependsOn`|Derleme işleminin tamamdan önce veya sonra özel hedefler eklemek için geçersiz kılınan özelliği.|
|`CleanDependsOn`|Özel derleme işleminizin çıktısını temizlemek için geçersiz kılınacak özellik.|
|`CompileDependsOn`|Derleme adımı öncesinde veya sonrasında özel işlemler eklemek için geçersiz kılınan özellik.|

## <a name="example-builddependson-and-cleandependson"></a>Örnek: BuildDependsOn ve CleanDependsOn

Aşağıdaki örnek ve örneğine `BeforeTargets` `AfterTargets` benzer, ancak benzer işlevlerin nasıl elde etmek için olduğunu gösterir. kullanarak derlemeyi genişleterek, derlemeden sonra çıkış dosyalarını kopyaleyen kendi görevinizi ekler ve ayrıca kullanarak ilgili `BuildDependsOn` `CustomAfterBuild` görevi `CustomClean` `CleanDependsOn` ekler.  

Bu örnekte, bu bir SDK stili projedir. Bu makalenin önceki sürümlerindeki SDK stili projelere yönelik notta belirtildiği gibi, proje dosyaları oluşturulurken Visual Studio özniteliği yerine el ile içeri aktarma `Sdk` yöntemini kullanabilirsiniz.

```xml
<Project>
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk"/>

  <PropertyGroup>
    <BuildDependsOn>
      $(BuildDependsOn);CustomAfterBuild
    </BuildDependsOn>

    <CleanDependsOn>
      $(CleanDependsOn);CustomClean
    </CleanDependsOn>

    <_OutputCopyLocation>$(OutputPath)..\..\CustomOutput\</_OutputCopyLocation>
  </PropertyGroup>

  <Target Name="CustomAfterBuild">
    <ItemGroup>
      <_FilesToCopy Include="$(OutputPath)**\*"/>
    </ItemGroup>
    <Message Importance="high" Text="_FilesToCopy: @(_FilesToCopy)"/>

    <Message Text="DestFiles:
      @(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

    <Copy SourceFiles="@(_FilesToCopy)"
          DestinationFiles="@(_FilesToCopy-&gt;'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Importance="high" Text="Inside Custom Clean"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files="@(_CustomFilesToDelete)"/>
  </Target>
</Project>
```

Öğelerin sırası önemlidir. Standart `BuildDependsOn` `CleanDependsOn` SDK hedefleri dosyası içeri aktar edildikten sonra ve öğeleri görüntü gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio tümleştirmesi](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [.targets dosyaları](../msbuild/msbuild-dot-targets-files.md)
