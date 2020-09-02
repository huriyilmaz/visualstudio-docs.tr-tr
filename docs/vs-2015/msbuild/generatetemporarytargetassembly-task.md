---
title: GenerateTemporaryTargetAssembly Görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ce412fdeb8d466708f3231cba14718d13720c69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676627"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>Bir projede en az bir [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] sayfa, bu projede yerel olarak tanımlanan bir türe başvuruyorsa, görev bir derleme oluşturur. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya yapı işlemi başarısız olursa kaldırılır.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AssemblyName`|Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir ve ayrıca geçici olarak oluşturulan hedef derlemenin adıdır. Örneğin, bir proje [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] adı **WinExeAssembly.exe**bir yürütülebilir dosya oluşturursa, **AssemblyName** parametresinin değeri **WinExeAssembly**olur.|  
|`CompileTargetName`|Gerekli **dize** parametresi.<br /><br /> [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)]Kaynak kod dosyalarından derlemeler oluşturmak için kullanılan hedefin adını belirtir. **CompileTargetName** için tipik değer **CoreCompile**' dir.|  
|`CompileTypeName`|Gerekli **dize** parametresi.<br /><br /> **CompileTargetName** parametresi tarafından belirtilen hedef tarafından gerçekleştirilen derlemenin türünü belirtir. **CoreCompile** hedefi için bu değer **derlenir**.|  
|`CurrentProject`|Gerekli **dize** parametresi.<br /><br /> [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)]Geçici bir hedef derleme gerektiren proje için proje dosyasının tam yolunu belirtir.|  
|`GeneratedCodeFiles`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) görevi tarafından oluşturulan dile özgü yönetilen kod dosyalarının listesini belirtir.|  
|`IntermediateOutputPath`|Gerekli **dize** parametresi.<br /><br /> Geçici hedef derlemenin oluşturulduğu dizini belirtir.|  
|`MSBuildBinPath`|Gerekli **dize** parametresi.<br /><br /> Geçici hedef derlemeyi derlemek için gereken **MSBuild.exe**konumunu belirtir.|  
|`ReferencePath`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Geçici hedef derlemeye derlenen türlerin başvurduğu, yola ve dosya adına göre derlemelerin bir listesini belirtir.|  
|`ReferencePathTypeName`|Gerekli **dize** parametresi.<br /><br /> Derleme başvuruları (**ReferencePath**) listesini belirten derleme hedefi (**CompileTargetName**) parametresi tarafından kullanılan parametreyi belirtir. Uygun değer **ReferencePath**' dir.|  
  
## <a name="remarks"></a>Açıklamalar  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)tarafından çalıştırılan ilk biçimlendirme derleme geçişi, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyaları ikili biçime derler. Sonuç olarak, derleyici, dosyalar tarafından kullanılan türleri içeren Başvurulmuş derlemelerin bir listesine ihtiyaç duyuyor [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] . Ancak, bir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya aynı projede tanımlı bir tür kullanıyorsa, proje derlenene kadar bu proje için karşılık gelen bir derleme oluşturulmaz. Bu nedenle, ilk biçimlendirme derleme geçişi sırasında bir derleme başvurusu sağlanamaz.  
  
 Bunun yerine, **MarkupCompilePass1** , [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)tarafından yürütülen ikinci bir biçimlendirme derleme geçişine aynı projedeki türlere başvuru içeren dosyaların dönüştürülmesini erteler. **MarkupCompilePass2** yürütülmeden önce geçici bir derleme oluşturulur. Bu derleme, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] biçimlendirme derleme geçişinin ertelenmesi gereken dosyalar tarafından kullanılan türleri içerir. Oluşturulan derlemeye bir başvuru, ertelenmiş derleme **MarkupCompilePass2** [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyalarının ikili biçime dönüştürülmesine izin vermek için çalıştırıldığında MarkupCompilePass2 olarak sağlanır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `Page1.xaml` aynı projede bulunan bir türe başvuru içerdiğinden geçici bir derleme oluşturur.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [WPF uygulaması oluşturma (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
