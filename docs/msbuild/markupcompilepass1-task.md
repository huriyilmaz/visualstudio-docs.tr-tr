---
title: MarkupCompilePass1 Görev | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a847f096edf5e42623cb2cb32cf4fd871a89aad7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633518"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 görevi

Görev, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> yerelleştirilebilir olmayan XAML proje dosyalarını derlenmiş ikili biçime dönüştürür.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
| - | - |
| `AllGeneratedFiles` | İsteğe bağlı **ITaskItem[]** çıktı parametresi.<br /><br /> <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Görev tarafından oluşturulan dosyaların tam listesini içerir. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | İsteğe bağlı **Boolean** parametresi.<br /><br /> Görevin ayrı <xref:System.AppDomain>bir şekilde çalıştırılıp çalıştırılmayacağını belirtir. Bu parametre **yanlış**dönerse, görev MSBuild ile aynı <xref:System.AppDomain> şekilde çalışır ve daha hızlı çalışır. Parametre **doğru**döndürürse, görev <xref:System.AppDomain> MSBuild'ten yalıtılmış bir saniyede çalışır ve daha yavaş çalışır. |
| `ApplicationMarkup` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> Uygulama tanımı XAML dosyasının adını belirtir. |
| `AssembliesGeneratedDuringBuild` | İsteğe bağlı **String[]** parametresi.<br /><br /> Yapı işlemi sırasında değişen derlemelere yapılan başvuruları belirtir. Örneğin, Visual Studio çözümü, başka bir projenin derlenmiş çıktısını başvuran bir proje içerebilir. Bu durumda, ikinci projenin derlenmiş **çıktısı AssembliesGeneratedDuringBuild** parametresine eklenebilir.<br /><br /> Not: **DerlemelerGeneratedDuringBuild** parametresi, bir yapı çözümü tarafından oluşturulan tüm derlemeler kümesine başvurular içermelidir. |
| `AssemblyName` | Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir. Örneğin, bir proje *winexeAssembly.exe*olan bir Windows çalıştırılabilir oluşturuyorsa, **AssemblyName** parametresi **WinExeAssembly**değerine sahiptir. |
| `AssemblyPublicKeyToken` | İsteğe bağlı **String** parametresi.<br /><br /> Derleme için ortak anahtar belirteci belirtir. |
| `AssemblyVersion` | İsteğe bağlı **String** parametresi.<br /><br /> Derlemenin sürüm numarasını belirtir. |
| `ContentFiles` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> Gevşek içerik dosyalarının listesini belirtir. |
| `DefineConstants` | İsteğe bağlı **String** parametresi.<br /><br /> **DefineConstants'ın**geçerli değerinin tutulduğunu belirtir. hedef montaj üretimini etkileyen; Bu parametre değiştirilirse, hedef derlemedeki genel API değiştirilebilir ve yerel türlere başvuran XAML dosyalarının derlenebilir. |
| `ExtraBuildControlFiles` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Görev yeniden çalıştırıldığında yeniden oluşturulup tetiklenmediğini denetleyen dosyaların listesini belirtir; bu dosyalardan biri değişirse yeniden tetiklenir. |
| `GeneratedBamlFiles` | İsteğe bağlı **ITaskItem[]** çıktı parametresi.<br /><br /> XAML ikili biçiminde oluşturulan dosyaların listesini içerir. |
| `GeneratedCodeFiles` | İsteğe bağlı **ITaskItem[]** çıktı parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının listesini içerir. |
| `GeneratedLocalizationFiles` | İsteğe bağlı **ITaskItem[]** çıktı parametresi.<br /><br /> Her yerelleştirilebilir XAML dosyası için oluşturulan yerelleştirme dosyalarının listesini içerir. |
| `HostInBrowser` | İsteğe bağlı **String** parametresi.<br /><br /> Oluşturulan derlemenin XAML Tarayıcı Uygulaması (XBAP) olup olmadığını belirtir. Geçerli seçenekler **doğru** ve **yanlıştır.** **Doğruysa,** kod tarayıcı barındırma desteklemek için oluşturulur. |
| `KnownReferencePaths` | İsteğe bağlı **String[]** parametresi.<br /><br /> Yapı işlemi sırasında değişmeyan derlemelere yapılan başvuruları belirtir. Genel montaj önbelleğinde (GAC) bulunan derlemeleri, bir .NET yükleme dizininde vb. içerir. |
| `Language` | Gerekli **String** parametresi.<br /><br /> Derleyicinin desteklediği yönetilen dili belirtir. Geçerli seçenekler **C#**, **VB**, **JScript**ve **C++**'dır. |
| `LanguageSourceExtension` | İsteğe bağlı **String** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyasının uzantısına eklenen uzantıyı belirtir:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> **LanguageSourceExtension** parametresi belirli bir değerle ayarlanmazsa, bir diliçin varsayılan kaynak dosya adı uzantısı kullanılır: *.vb* Visual Basic için, *.csharp* for C#. |
| `LocalizationDirectivesToLocFile` | İsteğe bağlı **String** parametresi.<br /><br /> Her kaynak XAML dosyası için yerelleştirme bilgilerinin nasıl üretileceklerini belirtir. Geçerli seçenekler **Yok**, **CommentsOnly**, ve **Tüm**. |
| `OutputPath` | Gerekli **String** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının ve XAML ikili biçim dosyalarının oluşturulduğu dizini belirtir. |
| `OutputType` | Gerekli **String** parametresi.<br /><br /> Bir proje tarafından oluşturulan derleme türünü belirtir. Geçerli seçenekler **winexe**, **exe**, **kütüphane**ve **netmodule**vardır. |
| `PageMarkup` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> İşlenmesi gereken XAML dosyalarının listesini belirtir. |
| `References` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> Dosyalardan XAML dosyalarında kullanılan türleri içeren derlemelere yapılan başvuruların listesini belirtir. |
| `RequirePass2ForMainAssembly` | İsteğe bağlı **Boolean** çıkış parametresi.<br /><br /> Projenin, ana derlemeye katıştırılmış yerel türlere başvuran yerelleştirilebilir olmayan XAML dosyaları bulunup olmadığını gösterir. |
| `RequirePass2ForSatelliteAssembly` | İsteğe bağlı **Boolean** çıkış parametresi.<br /><br /> Projenin ana derlemede katıştırılmış yerel türlere başvuran yerelleştirilebilir XAML dosyaları içerip içermediğini gösterir. |
| `RootNamespace` | İsteğe bağlı **String** parametresi.<br /><br /> Projenin içinde olan sınıflar için kök ad alanını belirtir. **RootNamespace,** ilgili XAML dosyası özniteliği içermiyorsa, `x:Class` yönetilen kod dosyasının varsayılan ad alanı olarak da kullanılır. |
| `SourceCodeFiles` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> Geçerli proje için kod dosyaları listesini belirtir. Liste, oluşturulan dile özgü yönetilen kod dosyalarını içermez. |
| `UICulture` | İsteğe bağlı **String** parametresi.<br /><br /> Oluşturulan XAML ikili biçimli dosyaların gömülü olduğu UI kültürü için uydu derlemesini belirtir. **UICulture** ayarlanmazsa, oluşturulan XAML ikili biçim dosyaları ana derlemeye eklenir. |
| `XAMLDebuggingInformation` | İsteğe bağlı **Boolean** parametresi.<br /><br /> **Doğru**olduğunda, tanılama bilgileri oluşturulur ve hata ayıklama yardımcı olmak için derlenmiş XAML dahil. |

## <a name="remarks"></a>Açıklamalar

Görev <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> genellikle XAML'yi ikili biçimde derler ve kod dosyaları oluşturur. Bir XAML dosyası aynı projede tanımlanan türlere başvurular içeriyorsa, ikili biçime derlemesi **MarkupCompilePass1** tarafından ikinci bir biçimlendirme derleme geçişine ertelenir **(MarkupCompilePass2).** Başvurulan yerel olarak tanımlanan türler derlenene kadar beklemeleri gerektiğinden, bu tür dosyaların derlemelerinin ertelenmesi gerekir. Ancak, bir XAML dosyasının `x:Class` bir <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> özniteliği varsa, bunun için dile özgü kod dosyası oluşturur.

Bir XAML dosyası, özniteliği kullanan `x:Uid` öğeler içeriyorsa yerelleştirilebilir:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Bir XAML dosyası, geçerli projedeki bir ad alanına başvurmak için `clr-namespace` değeri kullanan bir XML ad alanı beyan ettiğinde yerel olarak tanımlanmış bir türe başvurur:

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

Herhangi bir XAML dosyası yerelleştirilebilirse veya yerel olarak tanımlanmış bir türe başvuruyorsa, [GenerateTemporaryTargetAssembly'i](../msbuild/generatetemporarytargetassembly-task.md) ve ardından [MarkupCompilePass2'yi](../msbuild/markupcompilepass2-task.md)çalıştırmayı gerektiren ikinci bir biçimlendirme derleme geçişi gereklidir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, üç *Sayfa* XAML dosyasını ikili biçimdosyalarına nasıl dönüştüreceklerini gösterir. *Sayfa1,* `Class1`projenin kök ad alanında olan bir türe başvuru içerir ve bu nedenle, bu biçimlendirme derleme geçişinde ikili biçim dosyalarına dönüştürülmez. Bunun yerine, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) yürütülür ve [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)tarafından takip edilir.

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
- [WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)