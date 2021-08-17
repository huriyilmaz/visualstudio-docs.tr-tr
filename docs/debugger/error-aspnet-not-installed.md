---
description: Hata ayıklamaya ASP.NET bilgisayara doğru yüklenmemiş bir hata oluştuğunda bu hata oluşur.
title: ASP.NET yüklü değil
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- aspnet
ms.openlocfilehash: dc6575622ac03f8404b838959428ce30190cd5091b50450645f03cac38c61aaa
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362884"
---
# <a name="error-aspnet-not-installed"></a>Hata: ASP.NET Yüklü Değil
Hata ayıklamaya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalıştığınız bilgisayara doğru yüklenmemiş olduğunda bu hata oluşur. Bu, hiçbir zaman [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yüklenmemiş veya ilk olarak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yüklenmiş ve IIS'nin daha sonra yüklenmiş olduğu anlamına geliyor olabilir.

### <a name="to-reinstall-aspnet"></a>Yeniden yüklemek ASP.NET

1. Komut istemi penceresinde aşağıdaki komutu çalıştırın:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    burada *sürüm,* bilgisayarınızda yüklü .NET Framework sürüm numarasını (v1.0.370 gibi) temsil eder. Dizinine bakarak çerçeve sürümünü tespit `\WINDOWS\Microsoft.NET\Framework` edin.

   > [!NOTE]
   > Windows Server 2003 ile, yükleme için Program [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Ekle **veya** Kaldır'ı Denetim Masası.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
