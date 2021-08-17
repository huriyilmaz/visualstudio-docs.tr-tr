---
title: MarkupCompilePass1 Görev | Microsoft Docs
description: Yerelleştirilebilir MSBuild proje dosyalarını derlenmiş ikili biçime dönüştürmek için MarkupCompilePass1 görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: d9895158e4264cee60fb966e4435776209af2e7898ee04297ce21eec71acd5bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427671"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 görevi

Görev, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> yerelleştirilebilir olmayan XAML proje dosyalarını derlenmiş ikili biçime dönüştürür.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
| - | - |
| `AllGeneratedFiles` | İsteğe **bağlı ITaskItem[]** çıkış parametresi.<br /><br /> Görev tarafından oluşturulan dosyaların tam listesini <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> içerir. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | İsteğe **bağlı Boole parametresi.**<br /><br /> Görevin ayrı bir içinde çalıştırıp çalıştırılamay olmadığını <xref:System.AppDomain> belirtir. Bu parametre **false döndürürse,** görev aynı şekilde MSBuild <xref:System.AppDomain> ve daha hızlı çalışır. parametresi true **döndürürse,** görev bir saniye içinde çalışır ve bu değerden <xref:System.AppDomain> yalıtılmış MSBuild yavaş çalışır. |
| `ApplicationMarkup` | İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> Uygulama tanımı XAML dosyasının adını belirtir. |
| `AssembliesGeneratedDuringBuild` | İsteğe **bağlı String[]** parametresi.<br /><br /> Derleme işlemi sırasında değişen derlemelere yapılan başvuruları belirtir. Örneğin, bir Visual Studio çözümü başka bir projenin derlenmiş çıkışına başvurulan bir proje içerebilir. Bu durumda, ikinci projenin derlenmiş çıktısı **AssembliesGeneratedDuringBuild parametresine eklenebilir.**<br /><br /> Not: **AssembliesGeneratedDuringBuild** parametresi, derleme çözümü tarafından oluşturulan derlemelerin tam kümesine başvurular içermesi gerekir. |
| `AssemblyName` | Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir. Örneğin, bir proje adı Windows bir yürütülebilir dosya *WinExeAssembly.exe,* **AssemblyName** parametresi **winExeAssembly değerine sahip olur.** |
| `AssemblyPublicKeyToken` | İsteğe **bağlı Dize** parametresi.<br /><br /> Derleme için ortak anahtar belirteci belirtir. |
| `AssemblyVersion` | İsteğe **bağlı Dize** parametresi.<br /><br /> Derlemenin sürüm numarasını belirtir. |
| `ContentFiles` | İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> Gevşek içerik dosyalarının listesini belirtir. |
| `DefineConstants` | İsteğe **bağlı Dize** parametresi.<br /><br /> DefineConstants geçerli **değerinin tutul** olduğunu belirtir. hedef derleme neslini etkileyen; Bu parametre değiştirilirse, hedef derlemedeki genel API değiştirilebilir ve yerel türlere başvurulan XAML dosyalarının derlemesi etkilenebilir. |
| `ExtraBuildControlFiles` | İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> Görev yeniden çalıştırlendiğinde yeniden oluşturmanın tetiklendiğinde tetiklenen bir yeniden oluşturma olup olmadığını kontrol edecek dosyaların listesini belirtir; bu dosyalardan biri değişirse yeniden <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> oluşturma tetiklenir. |
| `GeneratedBamlFiles` | İsteğe **bağlı ITaskItem[]** çıkış parametresi.<br /><br /> XAML ikili biçiminde oluşturulan dosyaların listesini içerir. |
| `GeneratedCodeFiles` | İsteğe **bağlı ITaskItem[]** çıkış parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının listesini içerir. |
| `GeneratedLocalizationFiles` | İsteğe **bağlı ITaskItem[]** çıkış parametresi.<br /><br /> Yerelleştirilebilir her XAML dosyası için oluşturulan yerelleştirme dosyalarının listesini içerir. |
| `HostInBrowser` | İsteğe **bağlı Dize** parametresi.<br /><br /> Oluşturulan derlemenin bir XAML Tarayıcı Uygulaması (XBAP) olup olmadığını belirtir. Geçerli seçenekler true **ve** **false'tır.** True **ise,** tarayıcı barındırmayı desteklemek için kod oluşturulur. |
| `KnownReferencePaths` | İsteğe **bağlı String[]** parametresi.<br /><br /> Derleme işlemi sırasında değişmeden derlemelere yapılan başvuruları belirtir. Genel derleme önbelleğinde (GAC), bir .NET yükleme dizininde bulunan derlemeleri içerir ve bu şekilde devam eder. |
| `Language` | Gerekli **Dize** parametresi.<br /><br /> Derleyicinin desteklediği yönetilen dili belirtir. Geçerli seçenekler **C#**, **VB**, **JScript** ve **C++ seçenekleridir.** |
| `LanguageSourceExtension` | İsteğe **bağlı Dize** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyasının uzantısına eklenen uzantıyı belirtir:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> **LanguageSourceExtension** parametresi belirli bir değerle ayarlanmazsa, dil için varsayılan kaynak dosya adı uzantısı kullanılır: Visual Basic için *.vb,* C# için *.csharp.* |
| `LocalizationDirectivesToLocFile` | İsteğe **bağlı Dize** parametresi.<br /><br /> Her bir kaynak XAML dosyası için yerelleştirme bilgileri oluşturmanın nasıl olduğunu belirtir. Geçerli seçenekler Yok, **AçıklamalarOnlar ve** Tüm  **seçenekleridir.** |
| `OutputPath` | Gerekli **Dize** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının ve XAML ikili biçim dosyalarının üretil olduğu dizini belirtir. |
| `OutputType` | Gerekli **Dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derleme türünü belirtir. Geçerli **seçenekler: şarapxe**, **exe,** **kitaplık** ve **netmodule.** |
| `PageMarkup` | İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> İşlen XAML dosyalarının listesini belirtir. |
| `References` | İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> Dosyalardan XAML dosyalarında kullanılan türleri içeren derlemelere başvuru listesini belirtir. |
| `RequirePass2ForMainAssembly` | İsteğe **bağlı Boole** çıkış parametresi.<br /><br /> Projenin, ana derlemeye eklenmiş yerel türlere başvurulan yerelleştirilebilir olmayan XAML dosyaları içerdiğini gösterir. |
| `RequirePass2ForSatelliteAssembly` | İsteğe **bağlı Boole** çıkış parametresi.<br /><br /> Projenin ana derlemeye eklenmiş yerel türlere başvurulan yerelleştirilebilir XAML dosyaları içerdiğini gösterir. |
| `RootNamespace` | İsteğe **bağlı Dize** parametresi.<br /><br /> Projenin içindeki sınıfların kök ad alanını belirtir. **RootNamespace,** ilgili XAML dosyası özniteliğini içermezken, oluşturulan bir yönetilen kod dosyasının varsayılan ad alanı olarak `x:Class` da kullanılır. |
| `SourceCodeFiles` | İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> Geçerli proje için kod dosyalarının listesini belirtir. Liste, dile özgü oluşturulan yönetilen kod dosyalarını içermez. |
| `UICulture` | İsteğe **bağlı Dize** parametresi.<br /><br /> Oluşturulan XAML ikili biçim dosyalarının ekli olduğu kullanıcı arabirimi kültürü için uydu derlemeyi belirtir. **UICulture** ayarlanmazsa, oluşturulan XAML ikili biçim dosyaları ana derlemeye katıştırıldı. |
| `XAMLDebuggingInformation` | İsteğe **bağlı Boole parametresi.**<br /><br /> True **olduğunda,** hata ayıklamaya yardımcı olmak için tanılama bilgileri oluşturulur ve derlenmiş XAML'ye dahil edilir. |

## <a name="remarks"></a>Açıklamalar

Görev <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> genellikle XAML'i ikili biçimde derler ve kod dosyaları üretir. Bir XAML dosyası aynı projede tanımlanan türlere başvurular içeriyorsa, ikili biçimde derlemesi **MarkupCompilePass1** tarafından ikinci bir işaretleme derleme geçişini (**MarkupCompilePass2**) erteler. Bu tür dosyaların, başvurulan yerel olarak tanımlanmış türler derlenmesine kadar beklemeleri gereken derlemeleri ertelenmiş olması gerekir. Ancak, bir XAML dosyası bir `x:Class` özniteliğine <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> sahipse, bunun için dile özgü kod dosyasını üretir.

Bir XAML dosyası, özniteliğini kullanan öğeler içeriyorsa `x:Uid` yerelleştirilebilir:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

XAML dosyası, geçerli projedeki bir ad alanına başvurmak için değerini kullanan bir XML ad alanı bildirerek yerel olarak tanımlanmış `clr-namespace` bir türe başvurur:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Herhangi bir XAML dosyası yerelleştirilebilirse veya yerel olarak tanımlanmış bir türe başvurursa, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) ve [ardından MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)çalıştırmayı gerektiren ikinci bir işaretleme derleme geçişi gereklidir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, üç Sayfa XAML *dosyası ikili* biçim dosyalarına nasıl dönüştürülecek? *Page1,* projenin kök ad alanı içinde olan ve bu nedenle bu işaretleme derleme geçişinin ikili biçim dosyalarına dönüştürülen bir türüne başvuru `Class1` içerir. Bunun yerine [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) yürütülür ve ardından [MarkupCompilePass2 gelir.](../msbuild/markupcompilepass2-task.md)

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)