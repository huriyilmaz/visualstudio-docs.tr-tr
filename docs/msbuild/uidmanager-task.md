---
title: UidManager Görev | Microsoft Docs
description: UidManager MSBuild kaynak XAML dosyalarında tüm XAML öğelerini yerelleştirmek için benzersiz tanımlayıcıları (UID) nasıl denetler, ler veya kaldırır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UidManager task [WPF MSBuild]
- UidManager task [WPF MSBuild], parameters
- managing UIDs when localizing XAML elements [WPF MSBuild]
- localizing XAML elements [WPF MSBuild], managing UIDs
- checking UIDs when localizing XAML elements [WPF MSBuild]
ms.assetid: 4fc7b5a5-11b0-46ca-9656-8c2a0b08d1fe
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 323756067e8c553eb13729e305cb76677ccf3a3b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625455"
---
# <a name="uidmanager-task"></a>UidManager görevi

Görev, kaynak XAML dosyalarına dahil edilen tüm XAML öğelerini yerelleştirmek için benzersiz tanımlayıcıları <xref:Microsoft.Build.Tasks.Windows.UidManager> (UID) denetler, günceller veya kaldırır.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `IntermediateDirectory` | İsteğe **bağlı Dize** parametresi.<br /><br /> **MarkupFiles** parametresi tarafından belirtilen kaynak XAML dosyalarını back up için kullanılan dizini belirtir. |
| `MarkupFiles` | Gerekli **ITaskItem[]** parametresi.<br /><br /> UID denetleme, güncelleştirme veya kaldırma için eklenecek kaynak XAML dosyalarını belirtir. |
| `Task` | Gerekli **Dize** parametresi.<br /><br /> Gerçekleştirmek istediğiniz UID yönetim görevini belirtir. Geçerli seçenekler **Denetim,** Güncelleştirme **veya** Kaldır **seçenekleridir.** |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, belirtilen kaynak XAML dosyalarının uygun UID'lere sahip XAML öğeleri içerdiğini <xref:Microsoft.Build.Tasks.Windows.UidManager> kontrol etmek için görevini kullanır.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UidManager"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UidManagerTask">
    <UidManager
      Task="Check"
      MarkupFiles="Page1.xaml;Page2.xaml"
      IntermediateDirectory="c:\UidManagerIntermediateDirectory" />
  </Target>
</Project>
```

## <a name="see-also"></a>Ayrıca bkz.

- [WPF MSBuild başvurusu](../msbuild/wpf-msbuild-reference.md)
- [Görev başvurusu](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild başvurusu](../msbuild/msbuild-reference.md)
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
- [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Nasıl: Uygulamayı yerelleştirme](/dotnet/framework/wpf/advanced/how-to-localize-an-application)