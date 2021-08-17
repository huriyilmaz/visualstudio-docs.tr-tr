---
title: Derleme Sürecinde Kod Oluşturma
description: Metin dönüştürmenin bir çözüm oluşturma işleminin bir parçası olarak nasıl çağrıl Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: how-to
helpviewer_keywords:
- text templates, build tasks
- text templates, transforming by using msbuild
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: bb628f967f9d56f954c2c639951f9317fa8efed9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122048069"
---
# <a name="invoke-text-transformation-in-the-build-process"></a>Derleme sürecinde metin dönüştürmeyi çağırma

[Metin dönüştürme,](../modeling/code-generation-and-t4-text-templates.md) bir çözüm oluşturma [işleminin bir parçası](/azure/devops/pipelines/index) olarak Visual Studio çağrılabilir. Metin dönüştürme için özelleştirilmiş yapı görevleri vardır. T4 yapı görevleri tasarım zamanı metin şablonlarını çalıştırır ve aynı zamanda çalışma zamanı (önişlenmiş) metin şablonlarını derler.

Kullandığınız oluşturma motoruna bağlı olarak, yapı görevleri farklı işlevleri yerine getirebilirler. Visual Studio'da çözümü derlemeniz, [hostspecific="true"](../modeling/t4-template-directive.md) özniteliği ayarlanırsa Visual Studio API'sini (EnvDTE) kullanabilir. Ancak bu, çözümü komut satırdan derlemek veya bir sunucu derlemesi başlatmak için Visual Studio. Bu durumlarda, yapı MSBuild tarafından oluşturulur ve farklı bir T4 ana bilgisayar kullanılır. Başka bir ifadeyle, proje dosya adları gibi şeylere bir metin şablonu derlemek için aynı şekilde erişe MSBuild. Ancak, derleme [parametrelerini kullanarak ortam bilgilerini metin şablonlarına ve yönerge işlemcilerine geçebilirsiniz.](#parameters)

## <a name="configure-your-machines"></a><a name="buildserver"></a> Makinelerinizi yapılandırma

Geliştirme bilgisayarınızda derleme görevlerini etkinleştirmek için Visual Studio için Modelleme SDK'Visual Studio.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Derleme [sunucunuz yüklü](/azure/devops/pipelines/agents/agents) olmayan bir bilgisayarda Visual Studio aşağıdaki dosyaları geliştirme makinenizin derleme bilgisayarına kopyalayın:

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VisualStudio\v16.0\TextTemplating

  - Microsoft.VisualStudio.TextTemplating.Sdk.Host.15.0.dll
  - Microsoft.TextTemplating.Build.Tasks.dll
  - Microsoft.TextTemplating.targets

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\VSSDK\VisualStudioIntegration\Common\Assemblies\v4.0

  - Microsoft.VisualStudio.TextTemplating.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.Interfaces.15.0.dll
  - Microsoft.VisualStudio.TextTemplating.VSHost.15.0.dll

- %ProgramFiles(x86)%\Microsoft Visual Studio\2019\Community\Common7\IDE\PublicAssemblies

  - Microsoft.VisualStudio.TextTemplating.Modeling.15.0.dll

> [!TIP]
> Derleme sunucusunda TextTemplating derleme hedeflerini çalıştırmaya yönelik `MissingMethodException` bir Microsoft.CodeAnalysis yöntemi alırsanız, Roslyn derlemelerinin derleme yürütülebilir dosyasıyla aynı dizinde yer alan *Roslyn* adlı bir dizinde (örneğin,msbuild.exe) olduğundan *emin* olun.

## <a name="edit-the-project-file"></a>Proje dosyasını düzenleme

Metin dönüştürme hedeflerini içeri aktarma gibi MSBuild bazı özellikleri yapılandırmak için proje dosyanızı düzenleyin.

Bu **Çözüm Gezgini** projenizin **sağ** tıklama menüsünden Kaldır'ı seçin. Bu .csproj veya .vbproj dosyasını XML düzenleyicisinde düzenlemenize olanak tanır. Düzenlemeyi bitirdikten sonra Yeniden **Yükle'yi seçin.**

## <a name="import-the-text-transformation-targets"></a>Metin dönüştürme hedeflerini içeri aktarma

.Vbproj veya .csproj dosyasında şöyle bir satır bulun:

`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />`

\- veya -

`<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />`

Bu satırın ardından, Metin Şablon Oluşturma almayı ekleyin:

::: moniker range=">=vs-2019"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

::: moniker range="vs-2017"

```xml
<Import Project="$(MSBuildExtensionsPath)\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets" />
```

::: moniker-end

## <a name="transform-templates-in-a-build"></a>Derlemede şablonları dönüştürme

Dönüştürme görevini kontrol etmek için proje dosyanızın içine ekleyebileceğiniz bazı özellikler vardır:

- Dönüştürme görevini her yapı başlangıcında çalıştır:

    ```xml
    <PropertyGroup>
        <TransformOnBuild>true</TransformOnBuild>
    </PropertyGroup>
    ```

- Salt okunur dosyaların üzerine yaz( örneğin, kullanıma alınmış değil) :

    ```xml
    <PropertyGroup>
        <OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>
    </PropertyGroup>
    ```

- Her şablonu her zaman dönüştür:

    ```xml
    <PropertyGroup>
        <TransformOutOfDateOnly>false</TransformOutOfDateOnly>
    </PropertyGroup>
    ```

     Varsayılan olarak, T4 MSBuild görev şundan eski ise bir çıkış dosyasını yeniden oluşturur:

     - şablon dosyası
     - dahil edilen tüm dosyalar
     - daha önce şablon veya kullandığı yönerge işlemcisi tarafından okunan tüm dosyalar

     Bu, yalnızca şablon ve çıkış dosyasının  tarihlerini karşılaştıran Visual Studio Tüm Şablonları Dönüştür komutu tarafından kullanılandan daha güçlü bir bağımlılık testidir.

Projenizde yalnızca metin dönüştürmeleri gerçekleştirmek için TransformAll görevini çağırın:

`msbuild myProject.csproj /t:TransformAll`

Belirli metin şablonu dönüştürmek için:

`msbuild myProject.csproj /t:Transform /p:TransformFile="Template1.tt"`

TransformFile içinde joker karakterler kullanabilirsiniz:

`msbuild dsl.csproj /t:Transform /p:TransformFile="GeneratedCode\**\*.tt"`

## <a name="source-control"></a>Kaynak denetimi

Kaynak denetim sistemi ile yerleşik herhangi bir tümleştirme yoktur. Ancak, örneğin, oluşturulan bir dosyayı kontrol etmek ve iade etmek için kendi uzantılarınızı ekebilirsiniz. Varsayılan olarak, metin dönüştürme görevi salt okunur olarak işaretlenmiş bir dosyanın üzerine yazmaktan kaçınır. Böyle bir dosyayla karşılaşıldıysanız, Hata Listesi'ne Visual Studio hata kaydedilir ve görev başarısız olur.

Salt okunur dosyaların üzerine yazılması gerektiğini belirtmek için bu özelliği ekleyin:

`<OverwriteReadOnlyOutputFiles>true</OverwriteReadOnlyOutputFiles>`

Son işleme adımını özelleştirmedikçe, bir dosyanın üzerine yazıldığında Hata Listesi'ne bir uyarı kaydedilir.

## <a name="customize-the-build-process"></a>Derleme işlemini özelleştirme

Oluşturma işleminde diğer görevlerden önce metin dönüştürme gerçekleşir. ve özelliklerini ayarlayarak dönüştürmeden önce ve sonra çağrılan görevleri `$(BeforeTransform)` `$(AfterTransform)` tanımlayabilirsiniz:

```xml
<PropertyGroup>
    <BeforeTransform>CustomPreTransform</BeforeTransform>
    <AfterTransform>CustomPostTransform</AfterTransform>
</PropertyGroup>
<Target Name="CustomPreTransform">
    <Message Text="In CustomPreTransform..." Importance="High" />
</Target>
<Target Name="CustomPostTransform">
    <Message Text="In CustomPostTransform..." Importance="High" />
</Target>
```

içinde, `AfterTransform` dosya listelerine başvurabilirsiniz:

- GeneratedFiles - işlem tarafından yazılan dosyaların listesi. Mevcut salt okunur dosyaların üzerine yazan dosyalar `%(GeneratedFiles.ReadOnlyFileOverwritten)` için true olur. Bu dosyalar kaynak denetiminden denetlenebilir.

- NonGeneratedFiles - üzerine yazılmamış, salt okunur dosyaların listesi.

Örneğin, GeneratedFiles'ı kullanıma almak için bir görev tanımlarsınız.

## <a name="outputfilepath-and-outputfilename"></a>OutputFilePath ve OutputFileName

Bu özellikler yalnızca MSBuild tarafından kullanılır. Visual Studio'da kod üretimi etkilemez. Bunlar, oluşturulan çıktı dosyasını farklı bir klasör veya dosyaya yeniden yönlendirir. Hedef klasörün zaten bulunması gerekir.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFilePath>MyFolder</OutputFilePath>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

yeniden yönlendirilmesi yararlı bir `$(IntermediateOutputPath)` klasördür.

Bir çıkış dosya adı belirtirsiniz, şablonlarda çıkış yönergesinde belirtilen uzantıdan önceliklidir.

```xml
<ItemGroup>
  <None Include="MyTemplate.tt">
    <Generator>TextTemplatingFileGenerator</Generator>
    <OutputFileName>MyOutputFileName.cs</OutputFileName>
    <LastGenOutput>MyTemplate.cs</LastGenOutput>
  </None>
</ItemGroup>
```

Bir OutputFileName veya OutputFilePath belirtmeniz önerilmez. Ayrıca, tüm şablonları Dönüştür'Visual Studio  kullanarak veya tek dosya oluşturucusünü çalıştırarak şablonları da dönüştürebilirsiniz. Dönüşümü nasıl tetiklenize bağlı olarak farklı dosya yollarıyla karşınıza çıktı. Bu konu kafa karıştırıcı olabilir.

## <a name="add-reference-and-include-paths"></a>Başvuru ekleme ve yolları ekleme

Ana bilgisayar, şablonlarda başvurulan derlemeler için arama yaptığı varsayılan bir grup yola sahiptir. Bu gruba ekleme yapmak için:

```xml
<ItemGroup>
    <T4ReferencePath Include="$(VsIdePath)PublicAssemblies\" />
    <!-- Add more T4ReferencePath items here -->
</ItemGroup>
```

Ekleme kodu dosyalarının aranacağı klasörleri ayarlamak için, noktalı virgülle ayrılmış bir liste sağlayın. Genellikle varolan klasör listesine eklersiniz.

```xml
<PropertyGroup>
    <IncludeFolders>
$(IncludeFolders);$(MSBuildProjectDirectory)\Include;AnotherFolder;And\Another</IncludeFolders>
</PropertyGroup>
```

## <a name="pass-build-context-data-into-the-templates"></a><a name="parameters"></a> Derleme bağlamı verilerini şablonlara iletir

Proje dosyasında parametre değerlerini ayarlayabilirsiniz. Örneğin, derleme özelliklerini ve [ortam](../msbuild/msbuild-properties.md) [değişkenlerini geçebilirsiniz:](../msbuild/how-to-use-environment-variables-in-a-build.md)

```xml
<ItemGroup>
  <T4ParameterValues Include="ProjectFolder">
    <Value>$(ProjectDir)</Value>
    <Visible>false</Visible>
  </T4ParameterValues>
</ItemGroup>
```

Bir metin şablonunda, şablon `hostspecific` yönergesinde ayarlayın. Değerleri almak [için parametre](../modeling/t4-parameter-directive.md) yönergesi kullanın:

```
<#@template language="c#" hostspecific="true"#>
<#@ parameter type="System.String" name="ProjectFolder" #>
The project folder is: <#= ProjectFolder #>
```

Yönerge işlemcisinde [ITextTemplatingEngineHost.ResolveParameterValue çağrısında bulundurarak:](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))

```csharp
string value = Host.ResolveParameterValue("-", "-", "parameterName");
```

```vb
Dim value = Host.ResolveParameterValue("-", "-", "parameterName")
```

> [!NOTE]
> `ResolveParameterValue`yalnızca veri `T4ParameterValues` kaynağından veri MSBuild. Şablon dönüştürmeyi kullanarak Visual Studio parametrelerin varsayılan değerleri vardır.

## <a name="use-project-properties-in-assembly-and-include-directives"></a><a name="msbuild"></a> Derleme ve include yönergelerinde proje özelliklerini kullanma

Visual Studio **(SolutionDir) gibi** makrolar bir MSBuild. Bunun yerine, proje özelliklerini kullanabilirsiniz.

Proje özelliğini *tanımlamak için .csproj* *veya .vbproj* dosyanızı düzenleyin. Bu örnek **myLibFolder adlı bir özelliği tanımlar:**

```xml
<!-- Define a project property, myLibFolder: -->
<PropertyGroup>
    <myLibFolder>$(MSBuildProjectDirectory)\..\libs</myLibFolder>
</PropertyGroup>

<!-- Tell the MSBuild T4 task to make the property available: -->
<ItemGroup>
    <T4ParameterValues Include="myLibFolder">
      <Value>$(myLibFolder)</Value>
    </T4ParameterValues>
  </ItemGroup>
```

Artık derlemede ve ekleme yönergelerinde proje özelliklerini kullanabilirsiniz:

```
<#@ assembly name="$(myLibFolder)\MyLib.dll" #>
<#@ include file="$(myLibFolder)\MyIncludeFile.t4" #>
```

Bu yönergeler, hem MSBuild içinde hem de Visual Studio ana bilgisayarlarında T4parameterValues değerlerini alır.

## <a name="q--a"></a>Soru-Cevap

**Neden derleme sunucusunda şablonları dönüştürmek istiyorum? Koduma giriş Visual Studio önce Visual Studio şablonları zaten dönüştürdüm.**

Dahil edilen bir dosyayı veya şablon tarafından okunan başka bir dosyayı Visual Studio, dosyayı otomatik olarak dönüştürmez. Şablonları derlemenin bir parçası olarak dönüştürmek, her şeyin güncel olduğundan emin olun.

**Metin şablonlarını dönüştürmek için başka hangi seçenekler vardır?**

- [TextTransform yardımcı programı](../modeling/generating-files-with-the-texttransform-utility.md) komut betikleri içinde kullanılabilir. Çoğu durumda MSBuild kullanmak daha kolaydır.

- [Visual Studio uzantısında metin dönüştürmeyi çağır](../modeling/invoking-text-transformation-in-a-vs-extension.md).

- [Tasarım zamanı metin şablonları](../modeling/design-time-code-generation-by-using-t4-text-templates.md) Visual Studio tarafından dönüştürülür.

- [Çalışma zamanı metin şablonları](../modeling/run-time-text-generation-with-t4-text-templates.md) uygulamanızdaki çalışma zamanında dönüştürülür.

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="vs-2017"

- Şu adreste T4 MSbuild şablonunda iyi bir kılavuzluk vardır: `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\msbuild\Microsoft\VisualStudio\v15.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

::: moniker range=">=vs-2019"

- Şu adreste T4 MSbuild şablonunda iyi bir kılavuzluk vardır: `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\msbuild\Microsoft\VisualStudio\v16.0\TextTemplating\Microsoft.TextTemplating.targets`

::: moniker-end

- [T4 metin şablonu yazma](../modeling/writing-a-t4-text-template.md)
