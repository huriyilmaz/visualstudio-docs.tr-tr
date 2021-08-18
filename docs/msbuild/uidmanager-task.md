---
title: Uııdmanager görevi | Microsoft Docs
description: kaynak XAML dosyalarındaki tüm XAML öğelerini yerelleştirmek için MSBuild uımanager görevinin benzersiz tanımlayıcıları (uıd 'ler) nasıl denetleyeceğini, güncelleştirdiğini veya kaldırmadığını öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142721"
---
# <a name="uidmanager-task"></a>UidManager görevi

<xref:Microsoft.Build.Tasks.Windows.UidManager>Görev, kaynak xaml dosyalarına dahil edilen tüm XAML öğelerini yerelleştirmek için benzersiz tanımlayıcıları (UID 'ler) denetler, güncelleştirir veya kaldırır.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `IntermediateDirectory` | İsteğe bağlı **dize** parametresi.<br /><br /> **MarkupFiles** parametresi tarafından BELIRTILEN kaynak xaml dosyalarını yedeklemek için kullanılan dizini belirtir. |
| `MarkupFiles` | Gerekli **ıtaskitem []** parametresi.<br /><br /> UID denetimi, güncelleştirilmesi veya kaldırılması için dahil edilecek kaynak XAML dosyalarını belirtir. |
| `Task` | Gerekli **dize** parametresi.<br /><br /> Gerçekleştirmek istediğiniz UID yönetim görevini belirtir. Geçerli seçenekler **Check**, **Update** veya **Remove** seçenekleridir. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, <xref:Microsoft.Build.Tasks.Windows.UidManager> belirtilen kaynak xaml dosyalarının uygun UID 'leri olan xaml öğeleri içerdiğini denetlemek için görevini kullanır.

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
- [Nasıl yapılır: bir uygulamayı yerelleştirme](/dotnet/framework/wpf/advanced/how-to-localize-an-application)