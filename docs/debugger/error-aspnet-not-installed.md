---
title: 'Hata: ASP.NET yüklü değil | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
ms.openlocfilehash: 7d754cc2bb7931cdcbdb42abeddd554390ba320c
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737913"
---
# <a name="error-aspnet-not-installed"></a>Hata: ASP.NET Yüklü Değil
Bu hata, hata ayıklamaya çalıştığınız bilgisayarda [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] düzgün şekilde yüklenmemişse oluşur. Bu, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] hiç yüklenmediği veya [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] önce yüklendiği ve IIS 'in daha sonra yüklendiği anlamına gelebilir.

### <a name="to-reinstall-aspnet"></a>ASP.NET 'i yeniden yüklemek için

1. Bir komut istemi penceresinde aşağıdaki komutu çalıştırın:

   ```cmd
   \WINDOWS\Microsoft.NET\Framework\version\aspnet_regiis -i
   ```

    Burada *Sürüm* , bilgisayarınızda yüklü olan .NET Framework sürüm numarasını temsil eder, örneğin v 1.0.370. Framework sürümünü `\WINDOWS\Microsoft.NET\Framework` dizinine bakarak belirleyebilirsiniz.

   > [!NOTE]
   > Windows Server 2003 ile, Denetim Masası 'ndaki **Program Ekle veya Kaldır** 'ı kullanarak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] yükleyebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [Web Uygulamalarında Hata Ayıklama: Hatalar ve Sorun Giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
