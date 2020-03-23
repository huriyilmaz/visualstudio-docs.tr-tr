---
title: UidManager Görev | Microsoft Dokümanlar
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
ms.openlocfilehash: 37692c541fb2a6e9b2ccf61083dd383e56a79766
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631529"
---
# <a name="uidmanager-task"></a>UidManager görevi

Görev, <xref:Microsoft.Build.Tasks.Windows.UidManager> kaynak XAML dosyalarında bulunan tüm XAML öğelerini yerelleştirmek için benzersiz tanımlayıcıları (UID'leri) denetler, güncelleştirir veya kaldırır.

## <a name="task-parameters"></a>Görev parametreleri

| Parametre | Açıklama |
|-------------------------| - |
| `IntermediateDirectory` | İsteğe bağlı **String** parametresi.<br /><br /> **Biçimlendirme Dosyaları** parametresi tarafından belirtilen kaynak XAML dosyalarını yedeklemek için kullanılan dizini belirtir. |
| `MarkupFiles` | Gerekli **ITaskItem[]** parametresi.<br /><br /> UID denetimi, güncellenmesi veya kaldırılması için kaynak XAML dosyalarını belirtir. |
| `Task` | Gerekli **String** parametresi.<br /><br /> Gerçekleştirmek istediğiniz UID yönetim görevini belirtir. Geçerli seçenekler **Denetle,** **Güncelleştir**veya **Kaldır'** dır. |

## <a name="example"></a>Örnek

 Aşağıdaki örnek, <xref:Microsoft.Build.Tasks.Windows.UidManager> belirtilen kaynak XAML dosyalarının uygun uid'lere sahip XAML öğeleri ni içermediğini denetlemek için görevi kullanır.

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
- [WPF uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Nasıl yapilir: Uygulamayı yerelleştirme](/dotnet/framework/wpf/advanced/how-to-localize-an-application)