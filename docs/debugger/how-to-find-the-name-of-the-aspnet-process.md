---
title: Çalışan ASP.NET işlemini bulun | Microsoft Docs
description: Çalışan bir ASP.NET uygulamasında hata ayıklamayı öğrenin. Visual Studio debugger 'ı ada göre ASP.NET işlemine iliştirebilirsiniz.
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
ms.workload:
- aspnet
ms.openlocfilehash: 11526639975924fd9984dce33a08e54c9a5405b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877661"
---
# <a name="find-the-name-of-the-aspnet-process"></a>ASP.NET işleminin adını bulma

Çalışan bir uygulamada hata ayıklamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Visual Studio hata ayıklayıcı, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işleme adına göre bağlanmalıdır.

**Hangi işlemin bir ASP.NET uygulamasını çalıştırmakta olduğunu öğrenmek için:**

1. Uygulama çalışırken, Visual Studio 'da,   >  **işleme Ekle** Hata Ayıkla ' yı seçin.

1. **Işleme İliştir** iletişim kutusunda, aşağıdaki listeden işlem adının ilk harflerini yazın veya bunları arama kutusuna girin. Çalıştıran biri, ASP.NET uygulamasını çalıştırdır. Uygulamada hata ayıklamak için bu işleme iliştirin.

    - *w3wp.exe* IIS 6,0 ve üzeri.
    - *aspnet_wp.exe* , IIS 'nin önceki sürümleridir.
    - *iisexpress.exe* IISExpress.
    - *dotnet.exe* ASP.NET Core.
    - *inetinfo.exe* , işlem içi çalışan eski ASP uygulamalardır.

>[!NOTE]
>Visual Studio 2012 ve önceki bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod dosya sisteminde olabilir ve *WebDev.WebServer.exe* veya *WebDev.WebServer40.exe* test sunucusunda çalıştırılabilir. Bu durumda, yerel hata ayıklama için işlem yerine *WebDev.WebServer.exe* veya *WebDev.WebServer40.exe* ekleyin [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] .

**Ayrıca bkz:**

- [Çalışan bir işleme iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Uzaktan hata ayıklama Web uygulamalarının önkoşulları](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
- [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)