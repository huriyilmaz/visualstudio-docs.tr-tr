---
title: MergeLocalizationDirectives Görev | Microsoft Docs
description: XAML ikili MSBuild dosyalarının yerelleştirme özniteliklerini ve açıklamalarını tek bir dosyada birleştirmek için MergeLocalizationDirectives görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 13d052402196126c53f327fd1cc2033f99da548b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628460"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives görevi

Görev, bir veya daha fazla XAML ikili biçim dosyasının yerelleştirme özniteliklerini ve açıklamalarını bütün derleme <xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> için tek bir dosyada birleştirilmesini sağlar.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Gerekli **ITaskItem[]** parametresi.<br /><br /> XAML ikili biçimindeki tek tek dosyalar için yerelleştirme yönergeleri dosyalarının listesini belirtir. |
| `OutputFile` | Gerekli **Dize** çıkış parametresi.<br /><br /> Derlenmiş localization-directives derlemenin çıkış yolunu belirtir. |

## <a name="remarks"></a>Açıklamalar

XAML içeriğine yerelleştirme öznitelikleri ve yorumları ekleme. Windows Presentation Foundation (WPF) yerelleştirme desteğiyle, yerelleştirme özniteliklerini ve açıklamalarını ayırarak bunları oluşturulan derlemeden ayrı *bir .loc* dosyasına koyabilirsiniz. **LocalizationPropertyStorage özniteliğini kullanarak bunu yapabiliriz.** Yerelleştirme öznitelikleri ve yorumları ve **LocalizationPropertyStorage** hakkında daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve yorumları.](/dotnet/framework/wpf/advanced/localization-attributes-and-comments)

## <a name="example"></a>Örnek

Aşağıdaki örnek, birkaç XAML ikili biçimli dosyanın yerelleştirme açıklamalarını tek bir *.loc dosyasıyla birleştirmektedir.*

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
- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [MSBuild görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
