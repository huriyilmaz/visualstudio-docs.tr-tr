---
title: Çalışan ASP.NET işlemini bulun | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 54aa98dd238d7a78e4ae89af05dceae0f9911478
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187662"
---
# <a name="find-the-name-of-the-aspnet-process"></a>ASP.NET işleminin adını bulma

Çalışan bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] uygulamasında hata ayıklamak için Visual Studio hata ayıklayıcının ada göre [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işlem eklemesi gerekir.

**Hangi işlemin bir ASP.NET uygulamasını çalıştırmakta olduğunu öğrenmek için:**

1. Uygulama çalışırken, Visual Studio 'da **hata ayıkla** > **işleme Ekle**' yi seçin.

1. **Işleme İliştir** iletişim kutusunda, aşağıdaki listeden işlem adının ilk harflerini yazın veya bunları arama kutusuna girin. Çalıştıran biri, ASP.NET uygulamasını çalıştırdır. Uygulamada hata ayıklamak için bu işleme iliştirin.

    - *W3wp. exe* , IIS 6,0 ve üzeri.
    - *Aspnet_wp. exe* , IIS 'nin önceki sürümleridir.
    - *ıısexpress. exe* , iisexpress.
    - *DotNet. exe* ASP.NET Core.
    - *ınetinfo. exe* , işlem içi çalışan eski ASP uygulamalardır.

>[!NOTE]
>Visual Studio 2012 ve önceki sürümlerde [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kod dosya sisteminde olabilir ve *Web dev. webserver. exe* veya *webdev. WebServer40. exe*test sunucusunda çalıştırılabilir. Bu durumda, yerel hata ayıklama için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] işlemi yerine *webdev. webserver. exe* veya *webdev. WebServer40. exe* ' ye ekleyin.

**Ayrıca bkz:**

- [Çalışan bir işleme iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Uzaktan hata ayıklama Web uygulamalarının önkoşulları](remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)
- [Sistem gereksinimleri](../debugger/aspnet-debugging-system-requirements.md)
- [ASP.NET uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)