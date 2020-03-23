---
title: MarkupCompilePass2 Görev | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d18bc3638454e2a6b034cd2e35c3a158361a033e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633531"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 görevi

Görev, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> aynı projede başvuru türlerine başvuran XAML dosyalarında ikinci geçiş biçimlendirme derlemesi gerçekleştirir.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | İsteğe bağlı **Boolean** parametresi.<br /><br /> Görevin ayrı <xref:System.AppDomain>bir şekilde çalıştırılıp çalıştırılmayacağını belirtir. Bu parametre **yanlış**dönerse, görev MSBuild ile aynı <xref:System.AppDomain> şekilde çalışır ve daha hızlı çalışır. Parametre **doğru**döndürürse, görev <xref:System.AppDomain> MSBuild'ten yalıtılmış bir saniyede çalışır ve daha yavaş çalışır. |
| `AssembliesGeneratedDuringBuild` | İsteğe bağlı **String[]** parametresi.<br /><br /> Yapı işlemi sırasında değişen derlemelere yapılan başvuruları belirtir. Örneğin, Visual Studio çözümü, başka bir projenin derlenmiş çıktısını başvuran bir proje içerebilir. Bu durumda, ikinci projenin derlenmiş **çıktısı AssembliesGeneratedDuringBuild**eklenebilir.<br /><br /> Not: **DerlemelerGeneratedDuringBuild,** bir yapı çözümü tarafından oluşturulan tüm derlemeler kümesine başvurular içermelidir. |
| `AssemblyName` | Gerekli **String** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir. Örneğin, bir proje *winexeAssembly.exe*olan bir yürütülebilir oluşturuyorsa, **AssemblyName** parametresi **WinExeAssembly**değerine sahiptir. |
| `GeneratedBaml` | İsteğe bağlı **ITaskItem[]** çıktı parametresi.<br /><br /> XAML ikili biçiminde oluşturulan dosyaların listesini içerir. |
| `KnownReferencePaths` | İsteğe bağlı **String[]** parametresi.<br /><br /> Yapı işlemi sırasında hiç değişmeyen derlemelere yapılan başvuruları belirtir. Genel montaj önbelleğinde (GAC) bulunan derlemeleri, bir .NET yükleme dizininde vb. içerir. |
| `Language` | Gerekli **String** parametresi.<br /><br /> Derleyicinin desteklediği yönetilen dili belirtir. Geçerli seçenekler **C#**, **VB**, **JScript**ve **C++**'dır. |
| `LocalizationDirectivesToLocFile` | İsteğe bağlı **String** parametresi.<br /><br /> Her kaynak XAML dosyası için yerelleştirme bilgilerinin nasıl üretileceklerini belirtir. Geçerli seçenekler **Yok**, **CommentsOnly**, ve **Tüm**. |
| `OutputPath` | Gerekli **String** parametresi.<br /><br /> Oluşturulan XAML ikili biçim dosyalarının oluşturulduğu dizini belirtir. |
| `OutputType` | Gerekli **String** parametresi.<br /><br /> Bir proje tarafından oluşturulan derleme türünü belirtir. Geçerli seçenekler **winexe**, **exe**, **kütüphane**ve **netmodule**vardır. |
| `References` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> Dosyalardan XAML dosyalarında kullanılan türleri içeren derlemelere yapılan başvuruların listesini belirtir. Başvurulardan biri, <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> görevden önce çalıştırılması gereken görev tarafından <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> oluşturulan derlemedir. |
| `RootNamespace` | İsteğe bağlı **String** parametresi.<br /><br /> Projenin içinde olan sınıflar için kök ad alanını belirtir. **RootNamespace,** ilgili XAML dosyası özniteliği içermiyorsa, `x:Class` yönetilen kod dosyasının varsayılan ad alanı olarak da kullanılır. |
| `XAMLDebuggingInformation` | İsteğe bağlı **Boolean** parametresi.<br /><br /> **Doğru**olduğunda, tanılama bilgileri oluşturulur ve hata ayıklama yardımcı olmak için derlenmiş XAML dahil. |

## <a name="remarks"></a>Açıklamalar

**MarkupCompilePass2'yi**çalıştırmadan önce, biçimlendirme derleme geçişi ertelenmiş olan XAML dosyaları tarafından kullanılan türleri içeren geçici bir derleme oluşturmanız gerekir. **GenerateTemporaryTargetAssembly** görevini çalıştırarak geçici derlemeyi oluşturursunuz.

Oluşturulan geçici derlemeye <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> bir başvuru, ilk biçimlendirme derleme geçişinde derlemesi ertelenen XAML dosyalarının artık ikili biçime derlenmesine izin vererek çalıştığında sağlanır.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, ikinci <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> bir geçiş derlemesi gerçekleştirmek için görevin nasıl kullanılacağı gösterilmektedir.

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
- [WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
