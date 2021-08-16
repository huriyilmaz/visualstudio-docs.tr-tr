---
title: Çalışan işlem ASP.NET bulma | Microsoft Docs
description: Çalışan bir uygulamanın hata ASP.NET öğrenin. Hata ayıklayıcısını Visual Studio adıyla ASP.NET işleme iliştirin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: ea5a2c954f031139c66616f80c4dc5b44d2efb5d8b0aa0329c5e043d4a75d909
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379132"
---
# <a name="find-the-name-of-the-aspnet-process"></a>ASP.NET işleminin adını bulma

Çalışan bir uygulamada hata [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ayıklamak için Visual Studio hata ayıklayıcısının işleme adıyla [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] eklemesi gerekir.

**Bir uygulamanın hangi işlemi ASP.NET için:**

1. Uygulama çalışıyorken, uygulamanın Visual Studio İşleme **Eklemede Hata**  >  **Ayıkla'ya seçin.**

1. İşleme **Ekle iletişim** kutusunda, aşağıdaki listeden işlem adlarının ilk harflerini yazın veya arama kutusuna girin. Bu, ASP.NET uygulamasını çalıştıran ASP.NET. Uygulamanın hata ayıklaması için bu işleme ekleme.

    - *w3wp.exe* IIS 6.0 ve sonrasıdır.
    - *aspnet_wp.exe* IIS'nin önceki sürümleridir.
    - *iisexpress.exe* IISExpress'tir.
    - *dotnet.exe* bir ASP.NET Core.
    - *inetinfo.exe,* işlemde çalışan eski ASP uygulamalarıdır.

>[!NOTE]
>Visual Studio 2012 ve önceki kodlar dosya sisteminde olabilir ve test sunucusundaWebDev.WebServer.exe[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] veya *WebDev.WebServer40.exe.* ** Bu durumda, yerel hata ayıklama için işlem *yerineWebDev.WebServer.exe* *veyaWebDev.WebServer40.exe'ye* [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] iliştirin.

**Ayrıca bkz:**

- [Çalışan bir işleme ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Web uygulamalarında uzaktan hata ayıklama önkoşulları](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
- [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)