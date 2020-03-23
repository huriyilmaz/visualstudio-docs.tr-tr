---
title: Yapı işlemini genişletme
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
ms.openlocfilehash: f6a465a752282f4a0dc00f3fb294ade4169bb19b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093939"
---
# <a name="how-to-extend-the-visual-studio-build-process"></a>Nasıl?

Visual Studio oluşturma işlemi, proje dosyanıza aktarılan bir dizi MSBuild *.targets* dosyası yla tanımlanır. Bu içe aktarılan dosyalardan biri olan *Microsoft.Common.targets,* yapı işleminde çeşitli noktalarda özel görevleri çalıştırmanıza olanak sağlamak için genişletilebilir. Bu makalede, Visual Studio oluşturma işlemini genişletmek için kullanabileceğiniz iki yöntem açıklanmaktadır:

- Ortak hedeflerde tanımlanan belirli önceden tanımlanmış hedefleri geçersiz kılmak *(Microsoft.Common.targets* veya içe aktyaptığı dosyalar).

- Ortak hedeflerde tanımlanan "Bağımlı" özellikleri geçersiz kılma.

## <a name="override-predefined-targets"></a>Önceden tanımlanmış hedefleri geçersiz kılın

Ortak hedefler, yapı işlemindeki bazı ana hedeflerden önce ve sonra çağrılan önceden tanımlanmış boş hedefler kümesini içerir. Örneğin, `BeforeBuild` MSBuild hedefi ana `CoreBuild` hedeften önce, `AfterBuild` hedefi `CoreBuild` hedeften sonra çağırır. Varsayılan olarak, ortak hedeflerdeki boş hedefler hiçbir şey yapmaz, ancak ortak hedefleri içeri aktaran bir proje dosyasında istediğiniz hedefleri tanımlayarak varsayılan davranışlarını geçersiz kılabilirsiniz. Önceden tanımlanmış hedefleri geçersiz kılarak, yapı işlemi üzerinde daha fazla denetim sağlamak için MSBuild görevlerini kullanabilirsiniz.
Ortak hedefler, yapı işlemindeki bazı ana hedeflerden önce ve sonra çağrılan önceden tanımlanmış boş hedefler kümesini içerir. Örneğin, `BeforeBuild` MSBuild hedefi ana `CoreBuild` hedeften önce, `AfterBuild` hedefi `CoreBuild` hedeften sonra çağırır. Varsayılan olarak, ortak hedeflerdeki boş hedefler hiçbir şey yapmaz, ancak ortak hedefleri içeri aktaran bir proje dosyasında istediğiniz hedefleri tanımlayarak varsayılan davranışlarını geçersiz kılabilirsiniz. Önceden tanımlanmış hedefleri geçersiz kılarak, yapı işlemi üzerinde daha fazla denetim sağlamak için MSBuild görevlerini kullanabilirsiniz.

> [!NOTE]
> SDK tarzı *projeler, proje dosyasının son satırından sonra hedeflerin*örtülü bir içe aktarımı na sahiptir. Bu, nasıl açıklandığı gibi içeri almanızı el ile belirtmediğiniz sürece varsayılan hedefleri geçersiz kılamayacağınız anlamına [gelir: MSBuild proje SDK'larını kullanın.](how-to-use-project-sdk.md)

#### <a name="to-override-a-predefined-target"></a>Önceden tanımlanmış bir hedefi geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bir hedef tanımlayın. Güvenli bir şekilde geçersiz kılabileceğiniz hedeflerin tam listesi için aşağıdaki tabloya bakın.

2. Etiketten hemen önce proje dosyanızın sonundaki hedefi `</Project>` veya hedefleri tanımlayın. Örnek:

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

3. Proje dosyasını oluşturun.

Aşağıdaki tablo, güvenli bir şekilde geçersiz kılabileceğiniz ortak hedeflerdeki tüm hedefleri gösterir.

|Hedef adı|Açıklama|
|-----------------|-----------------|
|`BeforeCompile`, `AfterCompile`|Bu hedeflerden birine eklenen görevler, çekirdek derlemeden önce veya sonra çalıştırılır. Özelleştirmelerin çoğu bu iki hedefin birinde yapılır.|
|`BeforeBuild`, `AfterBuild`|Bu hedeflerden birine eklenen görevler, yapıdaki diğer her şeyden önce veya sonra çalışır. **Not:**  Ve `BeforeBuild` `AfterBuild` hedefler, çoğu proje dosyasının sonundaki yorumlarda zaten tanımlanır ve proje dosyanıza yapı öncesi ve sonrası olayları kolayca eklemenize olanak sağlar.|
|`BeforeRebuild`, `AfterRebuild`|Bu hedeflerden birine eklenen görevler, çekirdek yeniden oluşturma işlevi çağrılmadan önce veya sonra çalıştırılır. *Microsoft.Common.targets* hedef `BeforeRebuild`yürütme sırası: , `Clean` `Build`, , `AfterRebuild`ve sonra .|
|`BeforeClean`, `AfterClean`|Bu hedeflerden birine eklenen görevler, çekirdek temiz işlevselliği çağrılmadan önce veya sonra çalıştırılır.|
|`BeforePublish`, `AfterPublish`|Bu hedeflerden birine eklenen görevler, temel yayımlama işlevi çağrılmadan önce veya sonra çalıştırılır.|
|`BeforeResolveReferences`, `AfterResolveReferences`|Bu hedeflerden birine eklenen görevler, derleme başvurularından önce veya sonra çalıştırılır.|
|`BeforeResGen`, `AfterResGen`|Bu hedeflerden birine eklenen görevler, kaynaklar oluşturulmadan önce veya sonra çalıştırılır.|

## <a name="example-aftertargets-and-beforetargets"></a>Örnek: AfterTargets ve BeforeTargets

Aşağıdaki örnek, çıktı dosyalarıyla bir şeyler yapan özel bir hedef eklemek için `AfterTargets` özniteliğin nasıl kullanılacağını gösterir. Bu durumda, çıktı dosyalarını yeni bir klasöre kopyalar *Özel Çıktı.*  Örnek, özel yapı işlemi tarafından oluşturulan dosyaların bir `CustomClean` `BeforeTargets` öznitelik kullanarak ve özel temiz işlemin hedeften `CoreClean` önce çalıştığını belirterek hedefle nasıl temizleyileştirilebildiğini de gösterir.

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
> Önceki bölümde tabloda listelenen önceden tanımlanmış hedeflerden farklı adlar kullandığınızdan emin olun (örneğin, `CustomAfterBuild` `AfterBuild`burada özel yapı hedefi ne adlandırılmış , değil ), bu önceden tanımlanmış hedefler de onları tanımlayan SDK alma tarafından geçersiz kılınmıştır. Hedef dosyanın bu hedefleri geçersiz kılan içe aktarımını görmezsiniz, ancak Bir SDK'ya başvurma `Sdk` öznitelik yöntemini kullandığınızda proje dosyasının sonuna dolaylı olarak eklenir.

## <a name="override-dependson-properties"></a>Geçersiz Kılma Özelliklerine Bağlı

Önceden tanımlanmış hedefleri geçersiz kılmak yapı işlemini genişletmenin kolay bir yoludur, ancak MSBuild hedeflerin tanımını sırayla değerlendirdiği için, projenizi zaten sahip olduğunuz hedefleri geçersiz kılan başka bir projeyi önlemenin bir yolu yoktur Geçersiz kılın -mış. Örneğin, proje dosyasında `AfterBuild` tanımlanan son hedef, diğer tüm projeler alındıktan sonra, yapı sırasında kullanılan hedef olacaktır.

Ortak hedefler boyunca özniteliklerde `DependsOnTargets` kullanılan DependsOn özelliklerini geçersiz kılarak hedeflerin istenmeyen geçersiz kılmalarına karşı koruyabilirsiniz. Örneğin, `Build` hedef bir `DependsOnTargets` öznitelik değeri `"$(BuildDependsOn)"`içerir. Aşağıdakileri dikkate alın:

```xml
<Target Name="Build" DependsOnTargets="$(BuildDependsOn)"/>
```

XML'nin bu parçası, `Build` hedefin çalıştırılamadan önce, özellikte belirtilen tüm hedeflerin `BuildDependsOn` önce çalışması gerektiğini gösterir. Özellik `BuildDependsOn` olarak tanımlanır:

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Proje dosyanızın sonunda adı geçen `BuildDependsOn` başka bir özelliği beyan ederek bu özellik değerini geçersiz kılabilirsiniz. Önceki `BuildDependsOn` özelliği yeni özelliğe ekleyerek, hedef listenin başına ve sonuna yeni hedefler ekleyebilirsiniz. Örnek:

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

Proje dosyalarınızı içe aktaran projeler, yaptığınız özelleştirmelerin üzerine yazmadan bu özellikleri geçersiz kılabilir.

#### <a name="to-override-a-dependson-property"></a>Bağlı özelliği geçersiz kılmak için

1. Geçersiz kılmak istediğiniz ortak hedeflerde önceden tanımlanmış bağlı özelliği tanımlayın. Sık kullanılan geçersiz kılınan DependsOn özelliklerinin listesi için aşağıdaki tabloya bakın.

2. Proje dosyanızın sonundaki özellik veya özelliklerin başka bir örneğini tanımlayın. Orijinal özelliği, örneğin, `$(BuildDependsOn)`yeni özellik ekleyin.

3. Özel hedeflerinizi özellik tanımından önce veya sonra tanımlayın.

4. Proje dosyasını oluşturun.

### <a name="commonly-overridden-dependson-properties"></a>Genellikle geçersiz kılınan Bağlı özellikleri

|Özellik adı|Açıklama|
|-------------------|-----------------|
|`BuildDependsOn`|Tüm yapı işleminden önce veya sonra özel hedefler eklemek istiyorsanız geçersiz kılacak özellik.|
|`CleanDependsOn`|Özel yapı işleminizden çıktıtemizlemek istiyorsanız geçersiz kılacak özellik.|
|`CompileDependsOn`|Derleme adımından önce veya sonra özel işlemler eklemek istiyorsanız geçersiz kılacak özellik.|

## <a name="example-builddependson-and-cleandependson"></a>Örnek: BuildDependsOn ve CleanDependsOn

Aşağıdaki örnek, ve `BeforeTargets` `AfterTargets` örneğe benzer, ancak benzer işlevselliğin nasıl elde edilebildiğini gösterir. Çıktı dosyalarını oluşturmadan `BuildDependsOn` sonra kopyalayan `CustomAfterBuild` kendi görevinizi eklemek için kullanarak yapıyı `CustomClean` genişletir `CleanDependsOn`ve aynı zamanda ilgili görevi kullanarak da ekler.  

Bu örnekte, bu bir SDK tarzı projedir. Bu makalede daha önce SDK tarzı projelerle ilgili notta belirtildiği gibi, Visual `Sdk` Studio'nun proje dosyaları oluştururken kullandığı öznitelik yerine el ile alma yöntemini kullanmanız gerekir.

```xml
<Project>
<Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

<PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>

<Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />

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
  <Message Text="_FilesToCopy: @(_FilesToCopy)" Importance="high"/>

  <Message Text="DestFiles:
      @(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>

  <Copy SourceFiles="@(_FilesToCopy)"
        DestinationFiles=
        "@(_FilesToCopy->'$(_OutputCopyLocation)%(RecursiveDir)%(Filename)%(Extension)')"/>
  </Target>

  <Target Name="CustomClean">
    <Message Text="Inside Custom Clean" Importance="high"/>
    <ItemGroup>
      <_CustomFilesToDelete Include="$(_OutputCopyLocation)**\*"/>
    </ItemGroup>
    <Delete Files='@(_CustomFilesToDelete)'/>
  </Target>
</Project>
```

Elementlerin sırası önemlidir. Ve `BuildDependsOn` `CleanDependsOn` öğeleri standart SDK hedefleri dosyası aldıktan sonra görünmelidir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile tümleştirme](../msbuild/visual-studio-integration-msbuild.md)
- [MSBuild kavramları](../msbuild/msbuild-concepts.md)
- [.hedefleri dosyaları](../msbuild/msbuild-dot-targets-files.md)
