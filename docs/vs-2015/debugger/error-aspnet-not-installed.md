---
title: 'Hata: ASP.NET yüklü değil | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
ms.assetid: 6286dd3d-3e2b-4edd-959d-81e0ed45500b
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2198ed401f714353be2dd18846dd527cc433e695
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64823723"
---
# <a name="error-aspnet-not-installed"></a>Hata: ASP.NET Yüklü Değil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu hata, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] hata ayıklamaya çalıştığınız bilgisayarda düzgün şekilde yüklenmemişse oluşur. Bu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , hiç yüklenmemiş veya [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] önce yüklenen ve IIS 'nin daha sonra yüklendiği anlamına gelebilir.  
  
### <a name="to-reinstall-aspnet"></a>ASP.NET 'i yeniden yüklemek için  
  
1. Bir komut istemi penceresinde aşağıdaki komutu çalıştırın:  
  
    ```  
    \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i  
    ```  
  
     Burada *Sürüm* , bilgisayarınızda yüklü olan .NET Framework sürüm numarasını temsil eder, örneğin v 1.0.370. Framework sürümünü dizine bakarak belirleyebilirsiniz `\WINDOWS\Microsoft.NET\Framework` .  
  
    > [!NOTE]
    > Windows Server 2003 ile, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Denetim Masası 'Ndaki **Program Ekle veya Kaldır** 'ı kullanarak yükleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
