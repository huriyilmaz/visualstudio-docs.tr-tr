---
title: GenerateTemporaryTargetAssembly Görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 634cf365c0cd42e3eb146b74a137a66f742a8730
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594818"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly Görevi
Bir projede en az bir [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] sayfası bu projede yerel olarak tanımlanan bir türe başvuruyorsa <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> görevi bir derleme oluşturur. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya yapı işlemi başarısız olursa kaldırılır.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|--------------------------| - |
| `AssemblyName` | Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir ve ayrıca geçici olarak oluşturulan hedef derlemenin adıdır. Örneğin, bir proje adı *WinExeAssembly. exe*olan bir [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] yürütülebilir dosyası oluşturursa, **AssemblyName** parametresinin değeri **WinExeAssembly**olur. |
| `CompileTargetName` | Gerekli **dize** parametresi.<br /><br /> Kaynak kod dosyalarından derlemeler oluşturmak için kullanılan [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] hedefinin adını belirtir. **CompileTargetName** için tipik değer **CoreCompile**' dir. |
| `CompileTypeName` | Gerekli **dize** parametresi.<br /><br /> **CompileTargetName** parametresi tarafından belirtilen hedef tarafından gerçekleştirilen derlemenin türünü belirtir. **CoreCompile** hedefi için bu değer **derlenir**. |
| `CurrentProject` | Gerekli **dize** parametresi.<br /><br /> Geçici bir hedef derleme gerektiren proje için [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] proje dosyasının tam yolunu belirtir. |
| `GeneratedCodeFiles` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) görevi tarafından oluşturulan dile özgü yönetilen kod dosyalarının listesini belirtir. |
| `IntermediateOutputPath` | Gerekli **dize** parametresi.<br /><br /> Geçici hedef derlemenin oluşturulduğu dizini belirtir. |
| `MSBuildBinPath` | Gerekli **dize** parametresi.<br /><br /> Geçici hedef derlemeyi derlemek için gerekli olan *MSBuild. exe*dosyasının konumunu belirtir. |
| `ReferencePath` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Geçici hedef derlemeye derlenen türlerin başvurduğu, yola ve dosya adına göre derlemelerin bir listesini belirtir. |
| `ReferencePathTypeName` | Gerekli **dize** parametresi.<br /><br /> Derleme başvuruları (**ReferencePath**) listesini belirten derleme hedefi (**CompileTargetName**) parametresi tarafından kullanılan parametreyi belirtir. Uygun değer **ReferencePath**' dir. |

## <a name="remarks"></a>Açıklamalar
[MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)tarafından çalıştırılan ilk biçimlendirme derleme geçişi [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyaları ikili biçime derler. Sonuç olarak, derleyicinin [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyaları tarafından kullanılan türleri içeren Başvurulmuş derlemelerin bir listesine ihtiyacı vardır. Ancak, bir [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyası aynı projede tanımlı bir tür kullanıyorsa, proje derlenene kadar bu proje için karşılık gelen bir derleme oluşturulmaz. Bu nedenle, ilk biçimlendirme derleme geçişi sırasında bir derleme başvurusu sağlanamaz.

Bunun yerine **MarkupCompilePass1** , [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)tarafından yürütülen ikinci bir biçimlendirme derleme geçişinde aynı projedeki türlere başvuruları içeren [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyalarının dönüştürülmesini erteler. **MarkupCompilePass2** yürütülmeden önce geçici bir derleme oluşturulur. Bu derleme, biçimlendirme derleme geçişinin ertelenmesi olan [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyaları tarafından kullanılan türleri içerir. Oluşturulan derlemeye bir başvuru, ertelenmiş derleme [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyalarının ikili biçime dönüştürülmesine izin vermek için çalıştırıldığında **MarkupCompilePass2** 'e sağlanır.

## <a name="example"></a>Örnek
Aşağıdaki örnek, bir geçici derleme oluşturur çünkü *Sayfa1. xaml* aynı projede bulunan bir türe başvuru içeriyor.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="GenerateTemporaryTargetAssemblyTask">
    <GenerateTemporaryTargetAssembly
      AssemblyName="WPFMSBuildSample"
      CompileTargetName="CoreCompile"
      CompileTypeName="Compile"
      CurrentProject="FullBuild.proj"
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"
      IntermediateOutputPath=".\obj\debug\"
      MSBuildBinPath="$(MSBuildBinPath)"
      ReferencePathTypeName="ReferencePath"/>
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.
- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
