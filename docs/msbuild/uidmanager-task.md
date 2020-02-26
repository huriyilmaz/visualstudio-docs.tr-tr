---
title: Uııdmanager görevi | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 312e174b1bbe0a21d155e4e6b5050e6f41dd8352
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579553"
---
# <a name="uidmanager-task"></a>Uıdmanager görevi
<xref:Microsoft.Build.Tasks.Windows.UidManager> görevi, kaynak [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyalarına dahil edilen tüm [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] öğelerini yerelleştirmek için benzersiz tanımlayıcıları (UID 'ler) denetler, güncelleştirir veya kaldırır.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `IntermediateDirectory` | İsteğe bağlı **dize** parametresi.<br /><br /> **MarkupFiles** parametresi tarafından belirtilen kaynak [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyalarını yedeklemek için kullanılan dizini belirtir. |
| `MarkupFiles` | Gerekli **ıtaskitem []** parametresi.<br /><br /> UID denetimi, güncelleştirilmesi veya kaldırılması için içerilecek kaynak [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyalarını belirtir. |
| `Task` | Gerekli **dize** parametresi.<br /><br /> Gerçekleştirmek istediğiniz UID yönetim görevini belirtir. Geçerli seçenekler **Check**, **Update**veya **Remove**seçenekleridir. |

## <a name="example"></a>Örnek
 Aşağıdaki örnek, belirtilen kaynak [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dosyalarının uygun UID 'leri olan [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] öğeler içerdiğini denetlemek için <xref:Microsoft.Build.Tasks.Windows.UidManager> görevini kullanır.

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