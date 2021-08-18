---
title: Yapı işlemini uzat
description: Projenizin yapısını denetlemek ve özelleştirmek için yapı sürecini değiştirmek için çeşitli yollar edinin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122136943"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>nasıl yapılır: Visual Studio derleme işlemini genişletme

Visual Studio yapı işlemi, proje dosyanıza aktarılan MSBuild *. targets* dosyaları serisi tarafından tanımlanır. Bu içeri aktarılan dosyalardan biri olan *Microsoft. Common. targets*, derleme sürecinde birkaç noktada özel görevleri çalıştırmanıza olanak tanımak için genişletilebilir. bu makalede Visual Studio yapı işlemini genişletmek için kullanabileceğiniz iki yöntem açıklanmaktadır:

- Ortak hedeflerde tanımlanan belirli önceden tanımlanmış hedefleri geçersiz kılma (*Microsoft. Common. targets* veya içeri aktardığı dosyalar).

- Ortak hedeflerde tanımlanan "Bağımlıdson" özelliklerini geçersiz kılma.

## <a name="override-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kıl

Ortak hedefler, yapı işlemindeki ana hedeflerden önce ve sonra çağrılan bir dizi önceden tanımlanmış boş hedef kümesi içerir. örneğin, MSBuild hedeften `BeforeBuild` sonra ana hedeften önce hedefi `CoreBuild` ve `AfterBuild` hedefi çağırır `CoreBuild` . Varsayılan olarak, ortak hedeflerde boş hedefler hiçbir şey yapmaz, ancak ortak hedefleri içeri aktaran bir proje dosyasında istediğiniz hedefleri tanımlayarak varsayılan davranışlarını geçersiz kılabilirsiniz. önceden tanımlanmış hedefleri geçersiz kılarak, yapı işlemi üzerinde daha fazla denetim sağlamak için MSBuild görevleri kullanabilirsiniz.

> [!NOTE]
> SDK stili projelerin, *Proje dosyasının son satırından sonra* hedeflerin örtük bir şekilde içe aktarılması vardır. diğer bir deyişle, içeri aktarmaların [nasıl yapılır: MSBuild projesi sdk 'larını kullanma](how-to-use-project-sdk.md)bölümünde açıklandığı şekilde el ile belirtmediğiniz sürece varsayılan hedefleri geçersiz kılamazsınız.

#### <a name="to-override-a-predefined-target"></a>Önceden tanımlanmış bir hedefi geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bir hedef belirler. Güvenli şekilde geçersiz kılabileceğiniz hedeflerin tamamı listesi için aşağıdaki tabloya bakın.

2. Doğrudan etiketinden önce, proje dosyanızın sonundaki hedef veya hedefleri tanımlayın `</Project>` . Örnek:

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

3. Proje dosyasını derleyin.

Aşağıdaki tabloda, güvenle geçersiz kılabileceğiniz ortak hedeflerin tüm hedefleri gösterilmektedir.

|Hedef adı|Açıklama|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Bu hedeflerden birine eklenen görevler, temel derlemeden önce veya sonra çalışır. Çoğu özelleştirme, bu iki hedefin birinde yapılır.|
|`BeforeBuild`, `AfterBuild`|Bu hedeflerden birine eklenen görevler, derlemede bulunan her şeyin öncesinde veya sonrasında çalışır. **Note:**  `BeforeBuild` Ve `AfterBuild` hedefleri çoğu proje dosyasının sonundaki açıklamalarda zaten tanımlanmıştır. Bu, proje dosyanıza kolayca ve oluşturma sonrası olayları kolayca eklemenize olanak tanır.|
|`BeforeRebuild`, `AfterRebuild`|Bu hedeflerden birine eklenen görevler, çekirdek yeniden oluşturma işlevselliği çağrılmadan önce veya sonra çalışır. *Microsoft. Common. targets* içindeki hedef yürütmenin sırası: `BeforeRebuild` , `Clean` , `Build` , ve sonra `AfterRebuild` .|
|`BeforeClean`, `AfterClean`|Bu hedeflerden birine eklenen görevler, çekirdek Temizleme işlevselliği çağrılmadan önce veya sonra çalışır.|
|`BeforePublish`, `AfterPublish`|Bu hedeflerden birine eklenen görevler, çekirdek yayımlama işlevselliği çağrılmadan önce veya sonra çalışır.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Bu hedeflerden birine eklenen görevler, derleme başvuruları çözümlenmeden önce veya sonra çalıştırılır.|
|`BeforeResGen`, `AfterResGen`|Bu hedeflerden birine eklenen görevler, kaynaklar oluşturulmadan önce veya sonra çalışır.|

## <a name="example-aftertargets-and-beforetargets"></a>Örnek: AfterTargets ve BeforeTargets

Aşağıdaki örnek, `AfterTargets` Çıkış dosyalarıyla bir şeyi yapan özel bir hedef eklemek için özniteliğinin nasıl kullanılacağını gösterir. Bu durumda, çıktı dosyalarını *Customoutput* yeni bir klasöre kopyalar.  Örnek ayrıca bir özniteliği kullanarak bir hedefle birlikte özel yapı işlemi tarafından oluşturulan dosyaların nasıl temizleyeceğini `CustomClean` `BeforeTargets` ve özel temizleme işleminin hedeften önce çalıştığını belirtmektir `CoreClean` .

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
> Önceki bölümde bulunan tabloda listelenen önceden tanımlanmış hedeften farklı adlar kullandığınızdan emin olun (örneğin, burada, özel derleme hedefini burada olarak adlandırdık `CustomAfterBuild` `AfterBuild` ), bu ön TANıMLı hedefler SDK içeri aktarması tarafından da tanımlananlar tarafından geçersiz kılınır. Bu hedefleri geçersiz kılan hedef dosyanın içeri aktarımını görmezsiniz, ancak `Sdk` BIR SDK 'ya başvurmak için öznitelik yöntemini kullandığınızda proje dosyasının sonuna örtük olarak eklenir.

## <a name="override-dependson-properties"></a>Bağımlıdson özelliklerini geçersiz kıl

önceden tanımlanmış hedefleri geçersiz kılmak, yapı sürecini genişletmenin kolay bir yoludur, ancak MSBuild, hedeflerin tanımını ardışık olarak değerlendirirken, projenizi içeri aktaran başka bir projenin zaten geçersiz kılmış olduğunuz hedefleri geçersiz kılmasını önlemenin bir yolu yoktur. Bu nedenle, örneğin, `AfterBuild` diğer tüm projeler içeri aktarıldıktan sonra proje dosyasında tanımlanan son hedef, derleme sırasında kullanılan bir tane olur.

Ortak hedeflerin tamamında özniteliklerde kullanılan Bağımlılson özelliklerini geçersiz kılarak, hedefe yönelik istenmeyen geçersiz kılmalara karşı koruma sağlayabilirsiniz `DependsOnTargets` . Örneğin, hedef, `Build` `DependsOnTargets` öğesinin bir öznitelik değerini içerir `"$(BuildDependsOn)"` . Aşağıdakileri dikkate alın:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

Bu XML parçası, hedefin çalıştırılabilmesi için önce `Build` özellikte belirtilen tüm hedeflerin `BuildDependsOn` önce çalıştırılması gerektiğini gösterir. `BuildDependsOn`Özelliği şu şekilde tanımlanır:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Proje dosyanızın sonunda adlı başka bir özelliği bildirerek, bu özellik değerini geçersiz kılabilirsiniz `BuildDependsOn` . Önceki `BuildDependsOn` özelliği yeni özelliğe dahil ederek, hedef listenin başına ve sonuna yeni hedefler ekleyebilirsiniz. Örnek:

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

Proje dosyalarınızı içeri aktarma projeleri, yaptığınız özelleştirmelerin üzerine yazmadan bu özellikleri geçersiz kılabilir.

#### <a name="to-override-a-dependson-property"></a>Bir Bağımlıdson özelliğini geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bir Bağımlıdson özelliğini belirler. Yaygın olarak geçersiz kılınan Bağımlıdson özelliklerinin listesi için aşağıdaki tabloya bakın.

2. Proje dosyanızın sonundaki özelliğin veya özelliklerin başka bir örneğini tanımlayın. Yeni özellikte, örneğin, özgün özelliğini ekleyin `$(BuildDependsOn)` .

3. Özellik tanımından önce veya sonra özel hedeflerinizi tanımlayın.

4. Proje dosyasını derleyin.

### <a name="commonly-overridden-dependson-properties"></a>Yaygın olarak geçersiz kılınan Bağımlıdson özellikleri

|Özellik adı|Açıklama|
|-------------------|-----------------|
|`BuildDependsOn`|Tüm derleme işleminden önce veya sonra özel hedefler eklemek istiyorsanız geçersiz kılınacak özellik.|
|`CleanDependsOn`|Özel yapı sürecinizden çıktıyı temizlemek istiyorsanız geçersiz kılınacak özellik.|
|`CompileDependsOn`|Derleme adımından önce veya sonra özel süreçler eklemek istiyorsanız geçersiz kılınacak özellik.|

## <a name="example-builddependson-and-cleandependson"></a>Örnek: Buildbağımlıdson ve Cleanbağımlıdson

Aşağıdaki örnek, `BeforeTargets` ve `AfterTargets` örneğine benzerdir, ancak benzer işlevlere nasıl ulaşmanız gerektiğini gösterir. Derleme `BuildDependsOn` sonrasında çıktı dosyalarını kopyalayan kendi görevinizi eklemek için kullanarak derlemeyi genişletir `CustomAfterBuild` ve ayrıca kullanarak buna karşılık gelen `CustomClean` görevi ekler `CleanDependsOn` .  

Bu örnekte, bu bir SDK stili projem. bu makalenin önceki kısımlarında yer alan SDK stili projelerle ilgili notta `Sdk` bahsedildiği gibi, proje dosyalarını oluşturduğunda Visual Studio kullanılan özniteliği yerine el ile içeri aktarma yöntemini kullanmanız gerekir.

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

Öğelerin sırası önemlidir. `BuildDependsOn`Ve `CleanDependsOn` öğeleri, standart SDK hedefi dosyası içe aktarıldıktan sonra görünmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio tümleştirmesi](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [. targets dosyaları](../msbuild/msbuild-dot-targets-files.md)
