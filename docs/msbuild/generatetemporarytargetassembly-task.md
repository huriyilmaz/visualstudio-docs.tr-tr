---
title: GenerateTemporaryTargetAssembly Görev | Microsoft Docs
description: Proje yerel olarak MSBuild bir türe başvurursa derleme oluşturmak için GenerateTemporaryTargetAssembly görevini kullanın.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 513aa3ae1f14cff7958da1492819cd6321558694
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093846"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly görevi

Bir projedeki en az bir XAML sayfası, bu projede yerel olarak bildirilen bir türe başvurursa görev <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> bir derleme üretir. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya derleme işlemi başarısız olursa kaldırılır.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|--------------------------| - |
| `AssemblyName` | Gerekli **Dize** parametresi.<br /><br /> Bir proje için oluşturulan derlemenin kısa adını ve ayrıca geçici olarak oluşturulan hedef derlemenin adını belirtir. Örneğin, bir proje adı Windows bir yürütülebilir dosya *WinExeAssembly.exe,* **AssemblyName** parametresi **winExeAssembly değerine sahip olur.** |
| `CompileTargetName` | Gerekli **Dize** parametresi.<br /><br /> Kaynak kod dosyalarından derlemeler MSBuild hedef hedef adını belirtir. **CompileTargetName için tipik değer** **CoreCompile değeridir.** |
| `CompileTypeName` | Gerekli **Dize** parametresi.<br /><br /> **CompileTargetName** parametresi tarafından belirtilen hedef tarafından gerçekleştirilen derleme türünü belirtir. **CoreCompile hedefi için** bu değer Compile (Derle) **değeridir.** |
| `CurrentProject` | Gerekli **Dize** parametresi.<br /><br /> Geçici bir hedef derleme gerektiren MSBuild proje dosyasının tam yolunu belirtir. |
| `GeneratedCodeFiles` | İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) görevi tarafından oluşturulan dile özgü yönetilen kod dosyalarının listesini belirtir. |
| `IntermediateOutputPath` | Gerekli **Dize** parametresi.<br /><br /> Geçici hedef derlemenin üret olduğu dizini belirtir. |
| `MSBuildBinPath` | Gerekli **Dize** parametresi.<br /><br /> Geçici hedef *derlemeyi derlemekMSBuild.exe* için gerekli olanMSBuild.exekonumunu belirtir. |
| `ReferencePath` | İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> Geçici hedef derlemede derlenmiş türler tarafından başvurulan yol ve dosya adına göre derlemelerin listesini belirtir. |
| `ReferencePathTypeName` | Gerekli **Dize** parametresi.<br /><br /> Derleme başvurularının listesini ( ReferencePath ) belirten derleme hedefi (**CompileTargetName**) parametresi tarafından kullanılan **parametreyi belirtir.** Uygun değer **ReferencePath değeridir.** |

## <a name="remarks"></a>Açıklamalar

[MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)tarafından çalıştır edilen ilk işaretleme derleme geçişi, XAML dosyalarını ikili biçime derler. Sonuç olarak, derleyicinin XAML dosyaları tarafından kullanılan türleri içeren başvurulan derlemelerin bir listesine ihtiyacı vardır. Ancak, bir XAML dosyası aynı projede tanımlanan bir tür kullanıyorsa, proje oluşturulana kadar bu proje için karşılık gelen bir derleme oluşturulmaz. Bu nedenle, bir derleme başvurusu ilk işaretleme derleme geçişi sırasında sağlanamıyor.

Bunun yerine **MarkupCompilePass1,** aynı projedeki türlere başvurular içeren XAML dosyalarının [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)tarafından yürütülen ikinci bir işaretleme derleme geçişini dönüştürmesini karşılar. **MarkupCompilePass2** yürütülmeden önce geçici bir derleme oluşturulur. Bu derleme, işaretleme derlemesi geçişi ertelenmiş XAML dosyaları tarafından kullanılan türleri içerir. Ertelenen derleme XAML dosyalarının ikili biçime dönüştürülmesi için çalıştırıldıklarında **MarkupCompilePass2'ye** oluşturulan derlemeye bir başvuru sağlanır.

## <a name="example"></a>Örnek

*Page1.xaml* aynı projede olan bir türe başvuru içerdiği için aşağıdaki örnek geçici bir derleme üretir.

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
