---
title: Geçici Hedef Montaj Görevi Oluşturma | Microsoft Dokümanlar
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
ms.openlocfilehash: 69333b87720513244e90c131f052d11099b62e35
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634051"
---
# <a name="generatetemporarytargetassembly-task"></a>Geçici HedefMontaj görev oluşturma

Projedeki en az bir XAML sayfası, bu projede yerel olarak bildirilen bir türe başvuruyorsa, <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> görev bir derleme oluşturur. Oluşturulan derleme, yapı işlemi tamamlandıktan sonra veya yapı işlemi başarısız olursa kaldırılır.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|--------------------------| - |
| `AssemblyName` | Gerekli **String** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını belirtir ve aynı zamanda geçici olarak oluşturulan hedef derlemenin adını belirtir. Örneğin, bir proje, adı *WinExeAssembly.exe*olan bir Windows çalıştırılabilir oluşturursa, **AssemblyName** parametresi **WinExeAssembly**değerine sahiptir. |
| `CompileTargetName` | Gerekli **String** parametresi.<br /><br /> Kaynak kod dosyalarından derlemeler oluşturmak için kullanılan MSBuild hedefinin adını belirtir. **CompileTargetName** için tipik değeri **CoreCompile**olduğunu. |
| `CompileTypeName` | Gerekli **String** parametresi.<br /><br /> **DerleHedef Adı** parametresi tarafından belirtilen hedef tarafından gerçekleştirilen derleme türünü belirtir. **CoreCompile** hedefi için bu değer **Derleme'dir.** |
| `CurrentProject` | Gerekli **String** parametresi.<br /><br /> Geçici hedef derleme gerektiren proje için MSBuild proje dosyasının tam yolunu belirtir. |
| `GeneratedCodeFiles` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) görevi tarafından oluşturulan dile özgü yönetilen kod dosyalarının listesini belirtir. |
| `IntermediateOutputPath` | Gerekli **String** parametresi.<br /><br /> Geçici hedef derlemenin oluşturulduğu dizini belirtir. |
| `MSBuildBinPath` | Gerekli **String** parametresi.<br /><br /> Geçici hedef montajını derlemek için gereken *MSBuild.exe'nin*konumunu belirtir. |
| `ReferencePath` | İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> Geçici hedef derlemeye derlenen türler tarafından başvurulan, yol ve dosya adına göre derlemelerin listesini belirtir. |
| `ReferencePathTypeName` | Gerekli **String** parametresi.<br /><br /> Derleme hedefi **(CompileTargetName**) parametresi tarafından kullanılan ve derleme başvuruları **(ReferencePath)** listesini belirten parametreyi belirtir. Uygun değer **ReferencePath'tir.** |

## <a name="remarks"></a>Açıklamalar

[MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)tarafından işletilen ilk biçimlendirme derleme kartı, XAML dosyalarını ikili biçimde derler. Sonuç olarak, derleyici, XAML dosyaları tarafından kullanılan türleri içeren başvurulan derlemelerin bir listesine ihtiyaç duyar. Ancak, bir XAML dosyası aynı projede tanımlanan bir tür kullanıyorsa, proje oluşturulana kadar bu proje için karşılık gelen bir derleme oluşturulmaz. Bu nedenle, ilk biçimlendirme derleme geçişi sırasında bir derleme başvurusu sağlanamaz.

Bunun yerine, **MarkupCompilePass1,** aynı projedeki türlere atıfta bulunan XAML dosyalarının [dönüşümunu, MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)tarafından yürütülen ikinci bir biçimlendirme derleme geçişine erteler. **MarkupCompilePass2** yürütülmeden önce geçici bir derleme oluşturulur. Bu derleme, biçimlendirme derleme geçişi ertelenmiş olan XAML dosyaları tarafından kullanılan türleri içerir. Ertelenmiş derleme XAML dosyalarının ikili biçime dönüştürülmesine izin vermek için çalıştığında, oluşturulan derlemeye bir başvuru **MarkupCompilePass2'ye** verilir.

## <a name="example"></a>Örnek

*Sayfa1.xaml* aynı projede bulunan bir türe başvuru içerdiğinden, aşağıdaki örnek geçici bir derleme oluşturur.

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
- [WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [WPF XAML tarayıcı uygulamalarına genel bakış](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
