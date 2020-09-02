---
title: Windows Workflow Foundation için hata ayıklayıcıyı devre dışı bırakma (eski) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656779"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Windows Workflow Foundation için Visual Studio Hata Ayıklayıcısını Devre Dışı Bırakma (Eski)
Bu konuda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[wf](../includes/wf-md.md)] , eski sürümünde uygulamalar oluşturulurken yapılandırma dosyası kullanılarak hata ayıklayıcının devre dışı bırakılması açıklanmaktadır [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Ya da ' i hedefliyorsanız, eski kullanın [!INCLUDE[wfd2](../includes/wfd2-md.md)] [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] .

 Varsayılan olarak, [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] için hata ayıklayıcı [!INCLUDE[wf](../includes/wf-md.md)] bir konak işlemi için etkinleştirilmiştir. İş akışı hata ayıklamasını devre dışı bırakmak için, **\<switches>** **\<system.diagnostics>** ana bilgisayar yapılandırma dosyasının bölümüne bir "DisableWorkflowDebugging" girdi öğesi ekleyerek açık olarak kapatmanız gerekir.

 Aşağıdaki örnek, iş akışı hata ayıklamasını devre dışı bırakmak için konak yapılandırma dosyasının nasıl değiştirileceğini gösterir.

```
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <system.diagnostics>
      <switches>
         <add name="DisableWorkflowDebugging" value="true"/>
      </switches>
   </system.diagnostics>
</configuration>
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Windows Workflow Foundation (eski) Için Visual Studio hata ayıklayıcısını çağırarak](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [eski iş akışlarının hatalarını ayıklama](../workflow-designer/debugging-legacy-workflows.md)