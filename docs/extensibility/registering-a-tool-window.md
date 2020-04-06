---
title: Araç Penceresi Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, registering managed
- tool windows, registering
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e7971de5ae5301d99147bbfc374dda6b039662a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701594"
---
# <a name="register-a-tool-window"></a>Araç pencereni kaydetme
Araç pencerelerinizi kullanarak <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> kaydedebilirsiniz ve. <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>

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

 Yukarıdaki kodda, <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> Visual Studio `PersistedWindowPane` `DynamicWindowPane` ile ve araç pencereleri kaydeder. Kalıcı araç penceresi sabitlenir ve **Solution Explorer**ile sekmeli ve dinamik pencere varsayılan bir başlangıç konumu ve boyutu verilir. Dinamik pencere geçici olarak yapılır, bu da başlangıç üzerinde oluşturulmadığını gösterir. Bu, `DontForceCreate` sistem kayıt `ToolWindows` defterindeki anahtara bir değer yazar. Daha fazla bilgi için [Bkz. Araç penceresi görüntüleme yapılandırması.](/visualstudio/extensibility/tool-window-display-configuration?view=vs-2015)
