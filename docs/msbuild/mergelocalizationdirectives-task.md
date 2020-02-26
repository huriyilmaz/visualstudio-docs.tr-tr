---
title: Mergelocalizationyönergeleri görevi | Microsoft Docs
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
ms.openlocfilehash: 86c689122ac0ddfd9441122fdead64ecd8049e72
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579631"
---
# <a name="mergelocalizationdirectives-task"></a>Mergelocalizationyönergeleri görevi
<xref:Microsoft.Build.Tasks.Windows.MergeLocalizationDirectives> görevi, bir veya daha fazla [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçim dosyasının tüm derleme için tek bir dosyada yerelleştirme özniteliklerini ve açıklamalarını birleştirir.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|------------------------------| - |
| `GeneratedLocalizationFiles` | Gerekli **ıtaskitem []** parametresi.<br /><br /> [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçiminde tek tek dosyalar için yerelleştirme yönergeleri dosyalarının listesini belirtir. |
| `OutputFile` | **Dize** çıkış parametresi gerekli.<br /><br /> Derlenmiş yerelleştirme-yönergeleri derlemesinin çıkış yolunu belirtir. |

## <a name="remarks"></a>Açıklamalar
[!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] içeriğine yerelleştirme öznitelikleri ve yorumlar ekleyebilirsiniz. [!INCLUDE[TLA#tla_wpf](../msbuild/includes/tlasharptla_wpf_md.md)] yerelleştirme desteğiyle, yerelleştirme özniteliklerini ve açıklamalarını açabilir ve bunları oluşturulan derlemeden ayrı bir *. loc* dosyasına yerleştirebilirsiniz. Bunu **LocalizationPropertyStorage** özniteliğini kullanarak yapabilirsiniz. Yerelleştirme öznitelikleri ve açıklamalar ve **LocalizationPropertyStorage**hakkında daha fazla bilgi için bkz. [Yerelleştirme öznitelikleri ve açıklamaları](/dotnet/framework/wpf/advanced/localization-attributes-and-comments).

## <a name="example"></a>Örnek
Aşağıdaki örnek, birkaç [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] ikili biçim dosyasının yerelleştirme açıklamalarını tek bir *. loc* dosyasında birleştirir.

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
