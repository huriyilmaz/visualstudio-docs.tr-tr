---
title: GenerateTemporaryTargetAssembly Görevi | Microsoft Docs
description: Bir proje yerel olarak tanımlanan bir türe başvuruyorsa bir derleme oluşturmak için MSBuild GenerateTemporaryTargetAssembly görevini kullanın.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 0a100ad8a3be57288e49a858d6f87851269df303
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436762"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly görevi

<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>Bir projede en az BIR XAML sayfası bu projede yerel olarak tanımlanan bir türe başvuruyorsa, görev bir derleme oluşturur. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya yapı işlemi başarısız olursa kaldırılır.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|--------------------------| - |
| `AssemblyName` | Gerekli **dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir ve ayrıca geçici olarak oluşturulan hedef derlemenin adıdır. Örneğin, bir proje adı *WinExeAssembly.exe*olan bir Windows yürütülebiliri oluşturursa, **AssemblyName** parametresinin değeri **WinExeAssembly**olur. |
| `CompileTargetName` | Gerekli **dize** parametresi.<br /><br /> Kaynak kod dosyalarından derlemeler oluşturmak için kullanılan MSBuild hedefinin adını belirtir. **CompileTargetName** için tipik değer **CoreCompile**' dir. |
| `CompileTypeName` | Gerekli **dize** parametresi.<br /><br /> **CompileTargetName** parametresi tarafından belirtilen hedef tarafından gerçekleştirilen derlemenin türünü belirtir. **CoreCompile** hedefi için bu değer **derlenir**. |
| `CurrentProject` | Gerekli **dize** parametresi.<br /><br /> Proje için geçici bir hedef derleme gerektiren MSBuild proje dosyasının tam yolunu belirtir. |
| `GeneratedCodeFiles` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) görevi tarafından oluşturulan dile özgü yönetilen kod dosyalarının listesini belirtir. |
| `IntermediateOutputPath` | Gerekli **dize** parametresi.<br /><br /> Geçici hedef derlemenin oluşturulduğu dizini belirtir. |
| `MSBuildBinPath` | Gerekli **dize** parametresi.<br /><br /> Geçici hedef derlemeyi derlemek için gereken *MSBuild.exe*konumunu belirtir. |
| `ReferencePath` | İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Geçici hedef derlemeye derlenen türlerin başvurduğu, yola ve dosya adına göre derlemelerin bir listesini belirtir. |
| `ReferencePathTypeName` | Gerekli **dize** parametresi.<br /><br /> Derleme başvuruları (**ReferencePath**) listesini belirten derleme hedefi (**CompileTargetName**) parametresi tarafından kullanılan parametreyi belirtir. Uygun değer **ReferencePath**' dir. |

## <a name="remarks"></a>Açıklamalar

[MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)tarafından çalıştırılan ilk biçimlendirme derleme geçişi xaml dosyalarını ikili biçime derler. Sonuç olarak, derleyicinin XAML dosyaları tarafından kullanılan türleri içeren Başvurulmuş derlemelerin bir listesine ihtiyacı vardır. Ancak, bir XAML dosyası aynı projede tanımlı bir tür kullanıyorsa, proje derlenene kadar bu proje için karşılık gelen bir derleme oluşturulmaz. Bu nedenle, ilk biçimlendirme derleme geçişi sırasında bir derleme başvurusu sağlanamaz.

Bunun yerine **MarkupCompilePass1** , [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)tarafından yürütülen ikinci bir biçimlendirme derleme geçişine aynı PROJEDEKI türlere başvuruları içeren xaml dosyalarının dönüştürülmesini erteler. **MarkupCompilePass2** yürütülmeden önce geçici bir derleme oluşturulur. Bu derleme, biçimlendirme derleme geçişinin ertelenmesi olan XAML dosyaları tarafından kullanılan türleri içerir. Oluşturulan derlemeye bir başvuru, ertelenmiş derleme XAML dosyalarının ikili biçime dönüştürülmesine izin vermek için çalıştırıldığında **MarkupCompilePass2** olarak sağlanır.

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
