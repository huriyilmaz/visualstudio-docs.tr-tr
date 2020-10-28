---
title: Mergelocalizationyönergeleri görevi | Microsoft Docs
description: MSBuild 'in, XAML ikili biçim dosyalarının yerelleştirme özniteliklerini ve açıklamalarını tek bir dosyada birleştirmek için Mergelocalizationyönergeleri görevini nasıl kullandığını öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97d04978a2809a4744f62f27c375efdec1e43dcc
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903879"
---
# <a name="mergelocalizationdirectives-task"></a>MergeLocalizationDirectives görevi

<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives>Görev, bir veya daha fazla XAML ikili biçim dosyasının yerelleştirme özniteliklerini ve açıklamalarını tüm derleme için tek bir dosyada birleştirir.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Gerekli **ıtaskitem []** parametresi.<br /><br /> XAML ikili biçimindeki tek dosyalar için yerelleştirme yönergeleri dosyalarının listesini belirtir. |
| `OutputFile` | **Dize** çıkış parametresi gerekli.<br /><br /> Derlenmiş yerelleştirme-yönergeleri derlemesinin çıkış yolunu belirtir. |

## <a name="remarks"></a>Açıklamalar

XAML içeriğine yerelleştirme öznitelikleri ve yorumlar ekleyebilirsiniz. Windows Presentation Foundation (WPF) yerelleştirme desteğiyle, yerelleştirme özniteliklerini ve açıklamalarını açabilir ve bunları oluşturulan derlemeden ayrı bir *. loc* dosyasına yerleştirebilirsiniz. Bunu **LocalizationPropertyStorage** özniteliğini kullanarak yapabilirsiniz. Yerelleştirme öznitelikleri ve açıklamalar ve **LocalizationPropertyStorage** hakkında daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve açıklamaları](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Örnek

Aşağıdaki örnek, birkaç XAML ikili biçim dosyasının yerelleştirme açıklamalarını tek bir *. loc* dosyasında birleştirir.

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
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
