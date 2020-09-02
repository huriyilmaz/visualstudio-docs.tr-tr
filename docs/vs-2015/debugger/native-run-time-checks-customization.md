---
title: Yerel çalışma zamanı denetimleri özelleştirmesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 434f2425b1eeefd82b954e47a8ced55491a7ec11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697815"
---
# <a name="native-run-time-checks-customization"></a>Yerel Çalışma Zamanı Denetimlerini Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**/RTC** (çalışma zamanı denetimleri) ile derlerken veya `runtime_checks` pragma kullandığınızda C çalışma zamanı kitaplığı yerel çalışma zamanı denetimleri sağlar. Bazı durumlarda, çalışma zamanı denetimini özelleştirmek isteyebilirsiniz:  
  
- Çalışma zamanı denetim iletilerini varsayılan dışında bir dosya veya hedefe yönlendirmek için.  
  
- Üçüncü taraf bir hata ayıklayıcı altındaki çalışma zamanı denetimi iletileri için çıkış hedefi belirtmek için.  
  
- C çalışma zamanı kitaplığının yayın sürümü ile derlenen bir programdan çalışma zamanı denetim iletilerini raporlamak için. Kitaplığın yayın sürümleri, `_CrtDbgReportW` çalışma zamanı hatalarını raporlamak için kullanmaz. Bunun yerine, her bir çalışma zamanı hatası için bir onay **iletişim kutusu görüntüler** .  
  
  Çalışma zamanı hata denetimini özelleştirmek için şunları yapabilirsiniz:  
  
- Çalışma zamanı hata raporlama işlevi yazın. Daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanı hata raporlama Işlevi yazma](../debugger/how-to-write-a-run-time-error-reporting-function.md).  
  
- Hata iletisi hedefini özelleştirin.  
  
- Çalışma zamanı denetimi hataları hakkında bilgi sorgula.  
  
## <a name="customize-the-error-message-destination"></a>Hata Iletisi hedefini özelleştirme  
 `_CrtDbgReportW`Hataları raporlamak için kullanırsanız, `_CrtSetReportMode` hata iletilerinin hedefini belirtmek için kullanabilirsiniz.  
  
 Özel bir raporlama işlevi kullanıyorsanız, bir `_RTC_SetErrorType` hatayı rapor türüyle ilişkilendirmek için kullanın.  
  
## <a name="query-for-information-about-run-time-checks"></a>Çalışma zamanı denetimleri hakkında bilgi sorgula  
 `_RTC_NumErrors` çalışma zamanı hata denetimleri tarafından algılanan hata türlerinin sayısını döndürür. Her bir hatanın kısa bir açıklamasını almak için, 0 ' dan dönüş değerine döngü yapabilirsiniz `_RTC_NumErrors` , yineleme değeri `_RTC_GetErrDesc` Her döngüde öğesine geçer. Daha fazla bilgi için bkz. [_RTC_NumErrors](https://msdn.microsoft.com/library/7e82adae-38e2-4f8b-bc0b-37bda8109fd1) ve [_RTC_GetErrDesc](https://msdn.microsoft.com/library/7994ec2b-5488-4fd4-806d-a166c9a9f927).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma](../debugger/how-to-use-native-run-time-checks.md)   
 [runtime_checks](https://msdn.microsoft.com/library/ae50b43f-f88d-47ad-a2db-3389e9e7df5b)   
 [_CrtDbgReport, _CrtDbgReportW](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc)
