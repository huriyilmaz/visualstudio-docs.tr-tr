---
title: MarkupCompilePass2 görevi | Microsoft Docs
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
ms.openlocfilehash: f239670200a75dc3494b22b9a6aa761b1736119d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592223"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 görevi

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> görevi, aynı projedeki türlere başvuran [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] dosyalarında ikinci geçiş biçimlendirme derlemesini gerçekleştirir.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | İsteğe bağlı **Boolean** parametresi.<br /><br /> Görevin ayrı bir <xref:System.AppDomain>çalıştırıp çalıştıramayacağını belirtir. Bu parametre **false**döndürürse, görev [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]ile aynı <xref:System.AppDomain> çalışır ve daha hızlı çalışır. Parametre **true**değerini döndürürse, görev [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] yalıtılmış ve daha yavaş çalışan ikinci bir <xref:System.AppDomain> çalışır. |
| `AssembliesGeneratedDuringBuild` | İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında değişen derlemelere yönelik başvuruları belirtir. Örneğin, bir Visual Studio çözümü başka bir projenin derlenmiş çıktısına başvuran bir proje içerebilir. Bu durumda, ikinci projenin derlenmiş çıktısı **AssembliesGeneratedDuringBuild**' e eklenebilir.<br /><br /> Note: **AssembliesGeneratedDuringBuild** , derleme çözümü tarafından oluşturulan derlemelerin tamamına yönelik başvuruları içermelidir. |
| `AssemblyName` | Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir. Örneğin, bir proje adı *WinExeAssembly. exe*olan [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] yürütülebilir bir dosya üretiyorsa, **AssemblyName** parametresinin değeri **WinExeAssembly**olur. |
| `GeneratedBaml` | İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçimdeki oluşturulan dosyaların listesini içerir. |
| `KnownReferencePaths` | İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında hiçbir değişiklik olmayan derlemeler için başvuruları belirtir. [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] yükleme dizininde bulunan derlemeler ve bu şekilde devam eder. |
| `Language` | Gerekli **dize** parametresi.<br /><br /> Derleyicinin desteklediği yönetilen dili belirtir. Geçerli seçenekler, **C#** **vb**, **JScript**ve **C++** ' dir. |
| `LocalizationDirectivesToLocFile` | İsteğe bağlı **dize** parametresi.<br /><br /> Her kaynak [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyası için yerelleştirme bilgilerinin nasıl oluşturulacağını belirtir. Geçerli seçenekler None, **CommentsOnly**ve **All** **'tur**. |
| `OutputPath` | Gerekli **dize** parametresi.<br /><br /> Oluşturulan [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçim dosyalarının oluşturulduğu dizini belirtir. |
| `OutputType` | Gerekli **dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derlemenin türünü belirtir. Geçerli seçenekler **winexe**, **exe**, **Library**ve **netmodule**' dir. |
| `References` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Dosya [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyalarında kullanılan türleri içeren derlemelere ait başvuruların listesini belirtir. Bir başvuru, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> görevden önce çalıştırılması gereken <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> görevi tarafından oluşturulan derlemeye yönelik bir başvurudur. |
| `RootNamespace` | İsteğe bağlı **dize** parametresi.<br /><br /> Projenin içindeki sınıfların kök ad alanını belirtir. **RootNamespace** , karşılık gelen [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyası `x:Class` özniteliğini içermiyorsa, oluşturulan bir yönetilen kod dosyasının varsayılan ad alanı olarak da kullanılır. |
| `XAMLDebuggingInformation` | İsteğe bağlı **Boolean** parametresi.<br /><br /> **Doğru**olduğunda, hata ayıklamaya yardımcı olması için tanılama bilgileri oluşturulup derlenmiş [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] eklenir. |

## <a name="remarks"></a>Açıklamalar

**MarkupCompilePass2**çalıştırmadan önce, biçimlendirme derleme geçişinin ertelenmesi olan [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyaları tarafından kullanılan türleri içeren geçici bir derleme oluşturmanız gerekir. **GenerateTemporaryTargetAssembly** görevini çalıştırarak geçici derlemeyi oluşturabilirsiniz.

Oluşturulan geçici derlemeye bir başvuru, çalıştırıldığında <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> için verilmiştir ve derleme, ilk biçimlendirme derleme geçişinde, artık ikili biçime derlenmek üzere ertelenmiş [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyalara izin verir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> görevinin ikinci bir pass derlemesini gerçekleştirmek için nasıl kullanılacağını gösterir.

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
