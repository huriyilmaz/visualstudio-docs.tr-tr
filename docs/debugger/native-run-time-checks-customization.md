---
title: Yerel çalışma zamanı denetimleri özelleştirmesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.crt
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- runtime_checks pragma
- debugger, native run-time checks
- /RTC compiler option [C++], native run-time checks
- customizing CRT error checking
- native run-time checks, customizing
ms.assetid: 76a365fe-6439-49db-8603-34058b78e5a8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: db7cc513c4c96a8b60cc6471280bb837a7b9a248
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72730897"
---
# <a name="native-run-time-checks-customization"></a>Yerel Çalışma Zamanı Denetimlerini Özelleştirme
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
 `_RTC_NumErrors` çalışma zamanı hata denetimleri tarafından algılanan hata türlerinin sayısını döndürür. Her bir hatanın kısa bir açıklamasını almak için, 0 ' dan dönüş değerine döngü yapabilirsiniz `_RTC_NumErrors` , yineleme değeri `_RTC_GetErrDesc` Her döngüde öğesine geçer. Daha fazla bilgi için bkz. [_RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) ve [_RTC_GetErrDesc](/cpp/c-runtime-library/reference/rtc-geterrdesc).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma](../debugger/how-to-use-native-run-time-checks.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)