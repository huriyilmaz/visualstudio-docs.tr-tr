---
title: Hata-ASP.NET yüklü değil | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.http_not_supported
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Web applications, errors
- debugger, Web application errors
- error messages, ASP.NET
- ASP.NET, installation error messages
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 3a768a1a3a0295190701cacc9bbf017baee507b7
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460911"
---
# <a name="error-aspnet-not-installed"></a>Hata: ASP.NET Yüklü Değil
Bu hata, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hata ayıklamaya çalıştığınız bilgisayarda düzgün şekilde yüklenmemişse oluşur. Bu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , hiç yüklenmemiş veya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] önce yüklenen ve IIS 'nin daha sonra yüklendiği anlamına gelebilir.

### <a name="to-reinstall-aspnet"></a>ASP.NET 'i yeniden yüklemek için

1. Bir komut istemi penceresinde aşağıdaki komutu çalıştırın:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    Burada *Sürüm* , bilgisayarınızda yüklü olan .NET Framework sürüm numarasını temsil eder, örneğin v 1.0.370. Framework sürümünü dizine bakarak belirleyebilirsiniz `\WINDOWS\Microsoft.NET\Framework` .

   > [!NOTE]
   > Windows Server 2003 ile, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Denetim Masası 'Ndaki **Program Ekle veya Kaldır** 'ı kullanarak yükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
