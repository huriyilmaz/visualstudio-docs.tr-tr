---
title: MarkupCompilePass1 Görevi | Microsoft Docs
description: MSBuild 'in, yerelleştirilemeyen XAML proje dosyalarını derlenmiş ikili biçime dönüştürmek için MarkupCompilePass1 görevini nasıl kullandığını öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 775884692963da226947a8fac524a8bd440d6c8d
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904273"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 görevi

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>Görev, YERELLEŞTIRILEMEYEN xaml proje dosyalarını derlenmiş ikili biçime dönüştürür.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
| - | - |
| `AllGeneratedFiles` | İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Görev tarafından oluşturulan dosyaların tüm listesini içerir <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> . |
| `AlwaysCompileMarkupFilesInSeparateDomain` | İsteğe bağlı **Boolean** parametresi.<br /><br /> Görevin ayrı ayrı çalıştırılıp çalıştırılmayacağını belirtir <xref:System.AppDomain> . Bu parametre **false** döndürürse, görev MSBuild ile aynı şekilde çalışır <xref:System.AppDomain> ve daha hızlı çalışır. Parametre **true** döndürürse, görev, <xref:System.AppDomain> MSBuild 'ten yalıtılmış ve daha yavaş çalışır. |
| `ApplicationMarkup` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Uygulama tanımı XAML dosyasının adını belirtir. |
| `AssembliesGeneratedDuringBuild` | İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında değişen derlemelere yönelik başvuruları belirtir. Örneğin, bir Visual Studio çözümü başka bir projenin derlenmiş çıktısına başvuran bir proje içerebilir. Bu durumda, ikinci projenin derlenmiş çıktısı **AssembliesGeneratedDuringBuild** parametresine eklenebilir.<br /><br /> Note: **AssembliesGeneratedDuringBuild** parametresi bir yapı çözümü tarafından oluşturulan derlemelerin tamamına yönelik başvurular içermelidir. |
| `AssemblyName` | Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir. Örneğin, bir proje adı *WinExeAssembly.exe* olan bir Windows yürütülebiliri üretiyorsa, **AssemblyName** parametresinin değeri **WinExeAssembly** olur. |
| `AssemblyPublicKeyToken` | İsteğe bağlı **dize** parametresi.<br /><br /> Derleme için ortak anahtar belirtecini belirtir. |
| `AssemblyVersion` | İsteğe bağlı **dize** parametresi.<br /><br /> Derlemenin sürüm numarasını belirtir. |
| `ContentFiles` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Gevşek içerik dosyalarının listesini belirtir. |
| `DefineConstants` | İsteğe bağlı **dize** parametresi.<br /><br /> **Definesabitleri** 'nin geçerli değerinin tutulduğu belirtir. hedef derleme üretimini etkiler; Bu parametre değiştirilirse, hedef derlemedeki ortak API değiştirilebilir ve yerel türlere başvuruda bulunan XAML dosyalarının derlenmesi etkilenebilir. |
| `ExtraBuildControlFiles` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Görev tekrar çalıştığında yeniden oluşturma tetiklenip tetiklenmediğini denetleyen dosyaların listesini belirtir <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> ; Bu dosyalardan biri değişirse yeniden oluşturma tetiklenir. |
| `GeneratedBamlFiles` | İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> XAML ikili biçimindeki oluşturulan dosyaların listesini içerir. |
| `GeneratedCodeFiles` | İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının listesini içerir. |
| `GeneratedLocalizationFiles` | İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Her yerelleştirilebilir XAML dosyası için oluşturulan yerelleştirme dosyalarının listesini içerir. |
| `HostInBrowser` | İsteğe bağlı **dize** parametresi.<br /><br /> Oluşturulan derlemenin bir XAML tarayıcı uygulaması (XBAP) olup olmadığını belirtir. Geçerli seçenekler **true** ve **false** şeklindedir. **True** ise tarayıcı barındırmayı desteklemek için kod üretilir. |
| `KnownReferencePaths` | İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında değiştirolmayan derlemelere yönelik başvuruları belirtir. Genel derleme önbelleğinde (GAC), bir .NET yükleme dizininde bulunan derlemeler ve bu şekilde devam eder. |
| `Language` | Gerekli **dize** parametresi.<br /><br /> Derleyicinin desteklediği yönetilen dili belirtir. Geçerli seçenekler **C#** , **vb** , **JScript** ve **C++** ' dir. |
| `LanguageSourceExtension` | İsteğe bağlı **dize** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyasının uzantısına eklenen uzantıyı belirtir:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> **LanguageSourceExtension** parametresi belirli bir değer ile ayarlanmamışsa, dil için varsayılan kaynak dosya adı uzantısı kullanılır: Visual Basic için. *vb* , C# için *. CSharp* . |
| `LocalizationDirectivesToLocFile` | İsteğe bağlı **dize** parametresi.<br /><br /> Her kaynak XAML dosyası için yerelleştirme bilgilerinin nasıl oluşturulacağını belirtir. Geçerli seçenekler None, **CommentsOnly** ve **All** **'tur** . |
| `OutputPath` | Gerekli **dize** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının ve XAML ikili biçim dosyalarının oluşturulduğu dizini belirtir. |
| `OutputType` | Gerekli **dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derlemenin türünü belirtir. Geçerli seçenekler **winexe** , **exe** , **Library** ve **netmodule** ' dir. |
| `PageMarkup` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> İşlenecek XAML dosyalarının bir listesini belirtir. |
| `References` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> XAML dosyalarında kullanılan türleri içeren derlemelere ait başvuruların listesini belirtir. |
| `RequirePass2ForMainAssembly` | İsteğe bağlı **Boole** çıkış parametresi.<br /><br /> Projenin, ana derlemeye katıştırılmış yerel türlere başvuran, yerelleştirilemeyen XAML dosyaları içerip içermediğini gösterir. |
| `RequirePass2ForSatelliteAssembly` | İsteğe bağlı **Boole** çıkış parametresi.<br /><br /> Projenin, ana derlemeye katıştırılmış yerel türlere başvuran yerelleştirilebilir XAML dosyaları içerip içermediğini gösterir. |
| `RootNamespace` | İsteğe bağlı **dize** parametresi.<br /><br /> Projenin içindeki sınıfların kök ad alanını belirtir. **RootNamespace** , KARŞıLıK gelen xaml dosyası özniteliğini içermiyorsa oluşturulan bir yönetilen kod dosyasının varsayılan ad alanı olarak da kullanılır `x:Class` . |
| `SourceCodeFiles` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Geçerli proje için kod dosyalarının listesini belirtir. Liste, dile özgü oluşturulmuş yönetilen kod dosyalarını içermez. |
| `UICulture` | İsteğe bağlı **dize** parametresi.<br /><br /> Oluşturulan XAML ikili biçimi dosyalarının gömülme Kullanıcı arabirimi kültürü için uydu derlemesini belirtir. **UICulture** ayarlanmamışsa, oluşturulan XAML ikili biçim dosyaları ana derlemeye katıştırılır. |
| `XAMLDebuggingInformation` | İsteğe bağlı **Boolean** parametresi.<br /><br /> **Doğru** olduğunda, hata ayıklamaya yardımcı olması için tanılama bilgileri OLUŞTURULUP derlenmiş xaml 'e eklenir. |

## <a name="remarks"></a>Açıklamalar

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>Görev genellıkle xaml 'yi ikili biçimde derler ve kod dosyaları oluşturur. Bir XAML dosyası aynı projede tanımlı türlere başvurular içeriyorsa, derleme ikili biçime, **MarkupCompilePass1** tarafından ikinci bir biçimlendirme derleme geçişine ( **MarkupCompilePass2** ) ertelenir. Başvurulan yerel olarak tanımlanan türler derlenene kadar beklememeleri gerektiğinden, bu tür dosyaların derlenmesi ertelenmelidir. Ancak, bir XAML dosyasında bir öznitelik varsa `x:Class` , <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> dile özgü kod dosyasını oluşturur.

XAML dosyası özniteliği kullanan öğeler içeriyorsa yerelleştirilebilir `x:Uid` :

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

XAML dosyası, `clr-namespace` geçerli projedeki bir ad alanına başvurmak için değeri kullanan BIR XML ad alanı algıladığında yerel olarak tanımlanan bir türe başvurur:

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

Herhangi bir XAML dosyası yerelleştirilebilir veya yerel olarak tanımlanmış bir türe başvuruyorsa, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) ve ardından [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)çalıştırılmasını gerektiren ikinci bir biçimlendirme derleme geçişi gerekir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, üç *sayfalı* xaml dosyasının ikili biçim dosyalarına nasıl dönüştürüleceğini gösterir. *Sayfa1* , `Class1` projenin kök ad alanındaki bir türe başvuru içerir ve bu nedenle, bu biçimlendirme derleme geçişinde ikili biçim dosyalarına dönüştürülmez. Bunun yerine, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) yürütülür ve ardından [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)tarafından izlenir.

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