---
title: MarkupCompilePass2 görevi | Microsoft Docs
description: MSBuild, aynı projedeki türlere başvuran XAML dosyalarında ikinci geçiş biçimlendirme derlemesini gerçekleştirmek için MarkupCompilePass2 görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 823905cc21670c0b3c39178bf4feec97bd2e016a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625634"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 görevi

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>Görev, aynı projedeki türlere başvuran xaml dosyalarında ikinci geçiş biçimlendirme derlemesini gerçekleştirir.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | İsteğe bağlı **Boolean** parametresi.<br /><br /> Görevin ayrı ayrı çalıştırılıp çalıştırılmayacağını belirtir <xref:System.AppDomain> . bu parametre **false** döndürürse, görev MSBuild ile aynı şekilde çalışır <xref:System.AppDomain> ve daha hızlı çalışır. parametre **true** döndürürse, görev, <xref:System.AppDomain> MSBuild yalıtılmış ve daha yavaş çalışan bir saniye içinde çalışır. |
| `AssembliesGeneratedDuringBuild` | İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında değişen derlemelere yönelik başvuruları belirtir. örneğin, bir Visual Studio çözümü başka bir projenin derlenmiş çıktısına başvuran bir proje içerebilir. Bu durumda, ikinci projenin derlenmiş çıktısı **AssembliesGeneratedDuringBuild**' e eklenebilir.<br /><br /> Note: **AssembliesGeneratedDuringBuild** , derleme çözümü tarafından oluşturulan derlemelerin tamamına yönelik başvuruları içermelidir. |
| `AssemblyName` | Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir. Örneğin, bir proje adı *WinExeAssembly.exe* bir yürütülebilir dosya üretiyorsa, **AssemblyName** parametresinin değeri **WinExeAssembly** olur. |
| `GeneratedBaml` | İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> XAML ikili biçimindeki oluşturulan dosyaların listesini içerir. |
| `KnownReferencePaths` | İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında hiçbir değişiklik olmayan derlemeler için başvuruları belirtir. Genel derleme önbelleğinde (GAC), bir .NET yükleme dizininde bulunan derlemeler ve bu şekilde devam eder. |
| `Language` | Gerekli **dize** parametresi.<br /><br /> Derleyicinin desteklediği yönetilen dili belirtir. geçerli seçenekler **C#**, **VB**, **JScript** ve **C++**' dir. |
| `LocalizationDirectivesToLocFile` | İsteğe bağlı **dize** parametresi.<br /><br /> Her kaynak XAML dosyası için yerelleştirme bilgilerinin nasıl oluşturulacağını belirtir. Geçerli seçenekler None, **CommentsOnly** ve **All** **'tur**. |
| `OutputPath` | Gerekli **dize** parametresi.<br /><br /> Oluşturulan XAML ikili biçim dosyalarının oluşturulduğu dizini belirtir. |
| `OutputType` | Gerekli **dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derlemenin türünü belirtir. Geçerli seçenekler **winexe**, **exe**, **Library** ve **netmodule**' dir. |
| `References` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> XAML dosyalarında kullanılan türleri içeren derlemelere ait başvuruların listesini belirtir. Bir başvuru, görev tarafından oluşturulan ve <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> görevden önce çalıştırılması gereken derlemeye yönelik bir başvurudur <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> . |
| `RootNamespace` | İsteğe bağlı **dize** parametresi.<br /><br /> Projenin içindeki sınıfların kök ad alanını belirtir. **RootNamespace** , KARŞıLıK gelen xaml dosyası özniteliğini içermiyorsa oluşturulan bir yönetilen kod dosyasının varsayılan ad alanı olarak da kullanılır `x:Class` . |
| `XAMLDebuggingInformation` | İsteğe bağlı **Boolean** parametresi.<br /><br /> **Doğru** olduğunda, hata ayıklamaya yardımcı olması için tanılama bilgileri OLUŞTURULUP derlenmiş xaml 'e eklenir. |

## <a name="remarks"></a>Açıklamalar

**MarkupCompilePass2** çalıştırmadan önce, biçimlendirme derleme geçişinin ERTELENMESI olan XAML dosyaları tarafından kullanılan türleri içeren geçici bir derleme oluşturmanız gerekir. **GenerateTemporaryTargetAssembly** görevini çalıştırarak geçici derlemeyi oluşturabilirsiniz.

Oluşturulan geçici derlemeye bir başvuru <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> , çalıştırıldığında, derleme sırasında ilk biçimlendirme derleme geçişinde ERTELENMIŞ XAML dosyaları, artık ikili biçime derlenmeye sağlanır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> ikinci bir pass derlemesi gerçekleştirmek için görevinin nasıl kullanılacağını gösterir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass2Task">
    <MarkupCompilePass2
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
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
