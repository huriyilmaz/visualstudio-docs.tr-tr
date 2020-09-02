---
title: MarkupCompilePass1 Görevi | Microsoft Docs
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
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd5a6edc2f89470b4aacf05ef0a416c060cf23df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703532"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>Görev, yerelleştirilemeyen [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] Proje dosyalarını derlenmiş ikili biçime dönüştürür.  
  
## <a name="task-parameters"></a>Görev parametreleri  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`AllGeneratedFiles`|İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Görev tarafından oluşturulan dosyaların tüm listesini içerir <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> .|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|İsteğe bağlı **Boolean** parametresi.<br /><br /> Görevin ayrı ayrı çalıştırılıp çalıştırılmayacağını belirtir <xref:System.AppDomain> . Bu parametre **false**döndürürse, görev aynı <xref:System.AppDomain> şekilde çalışır [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] ve daha hızlı çalışır. Parametresi **true**değerini döndürürse, görev bir saniye içinde <xref:System.AppDomain> yalıtılmış [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] ve daha yavaş çalışır.|  
|`ApplicationMarkup`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Uygulama tanımı dosyasının adını belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] .|  
|`AssembliesGeneratedDuringBuild`|İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında değişen derlemelere yönelik başvuruları belirtir. Örneğin, bir [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] çözüm başka bir projenin derlenmiş çıktısına başvuran bir proje içerebilir. Bu durumda, ikinci projenin derlenmiş çıktısı **AssembliesGeneratedDuringBuild** parametresine eklenebilir.<br /><br /> Note: **AssembliesGeneratedDuringBuild** parametresi bir yapı çözümü tarafından oluşturulan derlemelerin tamamına yönelik başvurular içermelidir.|  
|`AssemblyName`|Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir. Örneğin, bir proje [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] adı **WinExeAssembly.exe**bir yürütülebilir dosya üretiyorsa, **AssemblyName** parametresinin değeri **WinExeAssembly**olur.|  
|`AssemblyPublicKeyToken`|İsteğe bağlı **dize** parametresi.<br /><br /> Derleme için ortak anahtar belirtecini belirtir.|  
|`AssemblyVersion`|İsteğe bağlı **dize** parametresi.<br /><br /> Derlemenin sürüm numarasını belirtir.|  
|`ContentFiles`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Gevşek içerik dosyalarının listesini belirtir.|  
|`DefineConstants`|İsteğe bağlı **dize** parametresi.<br /><br /> **Definesabitleri**'nin geçerli değerinin tutulduğu belirtir. hedef derleme üretimini etkiler; Bu parametre değiştirilirse, hedef derlemedeki ortak API değiştirilebilir ve [!INCLUDE[TLA2#tla_titlexaml](../includes/tla2sharptla-titlexaml-md.md)] Yerel türlere başvuruda bulunan dosyaların derlenmesi etkilenebilir.|  
|`ExtraBuildControlFiles`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Görev tekrar çalıştığında yeniden oluşturma tetiklenip tetiklenmediğini denetleyen dosyaların listesini belirtir <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> ; Bu dosyalardan biri değişirse yeniden oluşturma tetiklenir.|  
|`GeneratedBamlFiles`|İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Oluşturulan dosyaların listesini [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimde içerir.|  
|`GeneratedCodeFiles`|İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının listesini içerir.|  
|`GeneratedLocalizationFiles`|İsteğe bağlı **ıtaskitem []** çıkış parametresi.<br /><br /> Her yerelleştirilebilir dosya için oluşturulan yerelleştirme dosyalarının listesini içerir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] .|  
|`HostInBrowser`|İsteğe bağlı **dize** parametresi.<br /><br /> Oluşturulan derlemenin a olup olmadığını belirtir [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] . Geçerli seçenekler **true** ve **false**şeklindedir. **True**ise tarayıcı barındırmayı desteklemek için kod üretilir.|  
|`KnownReferencePaths`|İsteğe bağlı **dize []** parametresi.<br /><br /> Yapı işlemi sırasında değiştirolmayan derlemelere yönelik başvuruları belirtir. İçinde, [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)] bir [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] yükleme dizininde bulunan derlemeleri ve bu şekilde devam eder.|  
|`Language`|Gerekli **dize** parametresi.<br /><br /> Derleyicinin desteklediği yönetilen dili belirtir. Geçerli seçenekler **C#**, **vb**, **JScript**ve **C++**' dir.|  
|`LanguageSourceExtension`|İsteğe bağlı **dize** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyasının uzantısına eklenen uzantıyı belirtir:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> **LanguageSourceExtension** parametresi belirli bir değerle ayarlanmamışsa, dilin varsayılan kaynak dosya adı uzantısı kullanılır: **. vb** for [!INCLUDE[TLA#tla_visualb](../includes/tlasharptla-visualb-md.md)] , **. CSharp** [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] .|  
|`LocalizationDirectivesToLocFile`|İsteğe bağlı **dize** parametresi.<br /><br /> Her kaynak dosya için yerelleştirme bilgilerinin nasıl oluşturulacağını belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] . Geçerli seçenekler None, **CommentsOnly**ve **All** **'tur**.|  
|`OutputPath`|Gerekli **dize** parametresi.<br /><br /> Oluşturulan yönetilen kod dosyalarının ve [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçim dosyalarının oluşturulduğu dizini belirtir.|  
|`OutputType`|Gerekli **dize** parametresi.<br /><br /> Bir proje tarafından oluşturulan derlemenin türünü belirtir. Geçerli seçenekler **winexe**, **exe**, **Library**ve **netmodule**' dir.|  
|`PageMarkup`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> İşlenecek dosyaların bir listesini belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] .|  
|`References`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Dosyalarda kullanılan türleri içeren derlemelere ait başvuruların listesini belirtir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] .|  
|`RequirePass2ForMainAssembly`|İsteğe bağlı **Boole** çıkış parametresi.<br /><br /> Projenin, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ana derlemeye katıştırılmış yerel türlere başvuran yerelleştirilebilir olmayan dosyalar içerip içermediğini gösterir.|  
|`RequirePass2ForSatelliteAssembly`|İsteğe bağlı **Boole** çıkış parametresi.<br /><br /> Projenin, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ana derlemeye katıştırılmış yerel türlere başvuran yerelleştirilebilir dosyalar içerip içermediğini gösterir.|  
|`RootNamespace`|İsteğe bağlı **dize** parametresi.<br /><br /> Projenin içindeki sınıfların kök ad alanını belirtir. **RootNamespace** , karşılık gelen [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya özniteliğini içermediği zaman oluşturulan bir yönetilen kod dosyasının varsayılan ad alanı olarak da kullanılır `x:Class` .|  
|`SourceCodeFiles`|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Geçerli proje için kod dosyalarının listesini belirtir. Liste, dile özgü oluşturulmuş yönetilen kod dosyalarını içermez.|  
|`UICulture`|İsteğe bağlı **dize** parametresi.<br /><br /> Oluşturulan [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçim dosyalarının gömülme Kullanıcı arabirimi kültürü için uydu derlemesini belirtir. **UICulture** ayarlanmamışsa, oluşturulan [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçim dosyaları ana derlemeye katıştırılır.|  
|`XAMLDebuggingInformation`|İsteğe bağlı **Boolean** parametresi.<br /><br /> **Doğru**olduğunda, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] hata ayıklamaya yardımcı olması için tanılama bilgileri oluşturulur ve derlenmeye dahil edilir.|  
  
## <a name="remarks"></a>Açıklamalar  
 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>Görev genellikle [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimde derlenir ve kod dosyaları oluşturur. Bir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosya aynı projede tanımlı türlere başvurular içeriyorsa, derleme ikili biçime, **MarkupCompilePass1** tarafından ikinci bir biçimlendirme derleme geçişine (**MarkupCompilePass2**) ertelenir. Başvurulan yerel olarak tanımlanan türler derlenene kadar beklememeleri gerektiğinden, bu tür dosyaların derlenmesi ertelenmelidir. Ancak, bir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyanın `x:Class` özniteliği varsa, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> bunun için dile özgü kod dosyası oluşturur.  
  
 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]Özniteliği kullanan öğeler içeriyorsa bir dosya yerelleştirilebilir `x:Uid` :  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 Bir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] Dosya [!INCLUDE[TLA#tla_xml](../includes/tlasharptla-xml-md.md)] , `clr-namespace` geçerli projedeki bir ad alanına başvurmak için değeri kullanan bir ad alanı algıladığında yerel olarak tanımlanan bir türe başvurur:  
  
```  
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
  
 Herhangi bir [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] Dosya yerelleştirilebilir veya yerel olarak tanımlanmış bir türe başvuruyorsa, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) ve ardından [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)çalıştırılmasını gerektiren ikinci bir biçimlendirme derleme geçişi gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç `Page` [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] dosyanın ikili biçim dosyalarına nasıl dönüştürüleceğini gösterir. `Page1` projenin kök ad alanında olan bir türe başvuru içerir `Class1` ve bu nedenle, bu biçimlendirme derleme geçişinde ikili biçim dosyalarına dönüştürülmez. Bunun yerine, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) yürütülür ve ardından [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)tarafından izlenir.  
  
```  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)   
 [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild başvurusu](../msbuild/msbuild-reference.md)   
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)   
 [WPF uygulaması oluşturma (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [WPF XAML Tarayıcı Uygulamalarına Genel Bakış](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
