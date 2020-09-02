---
title: MarkupCompilePass2 görevi | Microsoft Docs
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
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47e27dbfa221a9476488d563ae2a48235a08f769
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703503"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>Görev [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] , aynı projedeki türlere başvuran dosyalarda ikinci geçiş biçimlendirme derlemesini gerçekleştirir.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|İsteğe bağlı **Boolean** parametresi.<br /><br /> Görevin ayrı ayrı çalıştırılıp çalıştırılmayacağını belirtir <xref:System.AppDomain> . Bu parametre **false**döndürürse, görev aynı <xref:System.AppDomain> şekilde çalışır [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] ve daha hızlı çalışır. Parametresi **true**değerini döndürürse, görev bir saniye içinde <xref:System.AppDomain> yalıtılmış [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] ve daha yavaş çalışır.|  
|`AssembliesGeneratedDuringBuild`|İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında değişen derlemelere yönelik başvuruları belirtir. Örneğin, bir [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] çözüm başka bir projenin derlenmiş çıktısına başvuran bir proje içerebilir. Bu durumda, ikinci projenin derlenmiş çıktısı **AssembliesGeneratedDuringBuild**' e eklenebilir.<br /><br /> Note: **AssembliesGeneratedDuringBuild** , derleme çözümü tarafından oluşturulan derlemelerin tamamına yönelik başvuruları içermelidir.|  
|`AssemblyName`|Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir. Örneğin, bir proje [!INCLUDE[TLA#tla_win](../includes/tlasharptla-win-md.md)] adı **WinExeAssembly.exe**bir yürütülebilir dosya üretiyorsa, **AssemblyName** parametresinin değeri **WinExeAssembly**olur.|  
|`GeneratedBaml`|İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Oluşturulan dosyaların listesini [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimde içerir.|  
|`KnownReferencePaths`|İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında hiçbir değişiklik olmayan derlemeler için başvuruları belirtir. İçinde, [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)] bir [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] yükleme dizininde bulunan derlemeleri ve bu şekilde devam eder.|  
|`Language`|Gerekli **dize** parametresi.<br /><br /> Derleyicinin desteklediği yönetilen dili belirtir. Geçerli seçenekler **C#**, **vb**, **JScript**ve **C++**' dir.|  
|`LocalizationDirectivesToLocFile`|İsteğe bağlı **dize** parametresi.<br /><br /> Her kaynak dosya için yerelleştirme bilgilerinin nasıl oluşturulacağını belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] . Geçerli seçenekler None, **CommentsOnly**ve **All** **'tur**.|  
|`OutputPath`|Gerekli **dize** parametresi.<br /><br /> Oluşturulan [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçim dosyalarının oluşturulduğu dizini belirtir.|  
|`OutputType`|Gerekli **dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derlemenin türünü belirtir. Geçerli seçenekler **winexe**, **exe**, **Library**ve **netmodule**' dir.|  
|`References`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Dosyalarda kullanılan türleri içeren derlemelere ait başvuruların listesini belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] . Bir başvuru, görev tarafından oluşturulan ve <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> görevden önce çalıştırılması gereken derlemeye yönelik bir başvurudur <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> .|  
|`RootNamespace`|İsteğe bağlı **dize** parametresi.<br /><br /> Projenin içindeki sınıfların kök ad alanını belirtir. **RootNamespace** , karşılık gelen [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya özniteliğini içermediği zaman oluşturulan bir yönetilen kod dosyasının varsayılan ad alanı olarak da kullanılır `x:Class` .|  
|`XAMLDebuggingInformation`|İsteğe bağlı **Boolean** parametresi.<br /><br /> **Doğru**olduğunda, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] hata ayıklamaya yardımcı olması için tanılama bilgileri oluşturulur ve derlenmeye dahil edilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 **MarkupCompilePass2**çalıştırmadan önce, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] biçimlendirme derleme geçişinin ertelenmesi olan dosyalar tarafından kullanılan türleri içeren geçici bir derleme oluşturmanız gerekir. **GenerateTemporaryTargetAssembly** görevini çalıştırarak geçici derlemeyi oluşturabilirsiniz.  
  
 Oluşturulan geçici derlemeye bir başvuru <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> çalıştırıldığında, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] derleme sırasında ilk biçimlendirme derleme geçişinde ertelenmiş olan dosyaların artık ikili biçime derlenmesine izin verir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> ikinci bir pass derlemesi gerçekleştirmek için görevinin nasıl kullanılacağını gösterir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [WPF uygulaması oluşturma (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
