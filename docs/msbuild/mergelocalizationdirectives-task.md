---
title: BirleştirmeYerelleştirme Yönergeleri Görev | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- localizing XAML [WPF MSBuild], moving comments and attributes to a separate file
- MergeLocalizationDirectives task [WPF MSBuild], parameters
- MergeLocalizationDirectives task [WPF MSBuild]
- moving localization comments and attributes to a separate file [WPF MSBuild]
ms.assetid: 9095b4f1-88da-4194-914b-ee1456826830
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9c7699afeb09604a437aad091f9aaf9ce624d33e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633505"
---
# <a name="mergelocalizationdirectives-task"></a>BirleştirmeYerelleştirme Yönergeleri görev

Görev, <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> bir veya daha fazla XAML ikili biçim dosyasının yerelleştirme özniteliklerini ve açıklamalarını tüm derleme için tek bir dosyada birleştirir.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Gerekli **ITaskItem[]** parametresi.<br /><br /> XAML ikili biçiminde tek tek dosyalar için yerelleştirme yönergeleri dosyalarının listesini belirtir. |
| `OutputFile` | Gerekli **String** çıkış parametresi.<br /><br /> Derlenen yerelleştirme yönergeleri derlemesinin çıkış yolunu belirtir. |

## <a name="remarks"></a>Açıklamalar

XAML içeriğine yerelleştirme öznitelikleri ve açıklamalar ekleyebilirsiniz. Windows Sunu Temeli (WPF) yerelleştirme desteğiyle, yerelleştirme özniteliklerini ve açıklamalarını silebilir ve bunları oluşturulan derlemeden ayrı bir *.loc* dosyasına koyabilirsiniz. Bunu **YerelleştirmeÖzellik Depolama** özniteliğini kullanarak yapabilirsiniz. Yerelleştirme öznitelikleri ve açıklamaları ve **YerelleştirmeÖzellik Depolama**hakkında daha fazla bilgi için [bkz.](/dotnet/framework/wpf/advanced/localization-attributes-and-comments)

## <a name="example"></a>Örnek

Aşağıdaki örnek, birkaç XAML ikili biçimli dosyanın yerelleştirme yorumlarını tek bir *.loc* dosyasında birleştirir.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MergeLocalizationDirectivesTask">
    <MergeLocalizationDirectives
      GeneratedLocalizationFiles="obj\debug\page1.loc;obj\debug\page2.loc;obj\debug\page3.loc"
      OutputFile="obj\debug\WPFMSBuildSample.loc" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [WPF MSBuild görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
