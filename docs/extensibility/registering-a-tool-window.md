---
title: Araç Penceresi Kaydı | Microsoft Docs
description: ProvideToolWindowAttribute ve ProvideToolWindowVisibilityAttribute kullanarak araç pencerelerinizi Visual Studio ile kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fb0163c9c28f1ceb51a2685b92d081b3012757b1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028702"
---
# <a name="register-a-tool-window"></a>Araç penceresi kaydetme
ve kullanarak araç pencerelerinizi <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute>  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> kaydedebilirsiniz.

## <a name="example"></a>Örnek

```csharp

[ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")]
[ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)]
[ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]
[ProvideMenuResource(1000, 1)]
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]
public class PackageToolWindow : Package
{
```

 Yukarıdaki kodda, ve <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> araç `PersistedWindowPane` pencerelerini `DynamicWindowPane` Visual Studio. Kalıcı araç penceresi Çözüm Gezgini ile **yerleştirildi** ve sekmeye alındı. Dinamik pencereye varsayılan başlangıç konumu ve boyutu verilir. Dinamik pencere, başlangıçta oluşturulmamış olduğunu gösteren geçici olarak yapılır. Bu, `DontForceCreate` sistem kayıt `ToolWindows` defterindeki anahtara bir değer yazar. Daha fazla bilgi için [bkz. Araç penceresi görüntüleme yapılandırması.](/previous-versions/visualstudio/visual-studio-2015/extensibility/tool-window-display-configuration?preserve-view=true&view=vs-2015)