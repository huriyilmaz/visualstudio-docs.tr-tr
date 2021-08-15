---
title: Yerel Run-Time Özelleştirme Denetimlerini | Microsoft Docs
description: 'Çalışma zamanı denetimlerini özelleştirmenin yollarını öğrenin. Örneğin: ileti hedefi belirtme, hata raporlama işlevi yazma ve hata bilgilerini sorgulama.'
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 534e2d8616fb70ca0089cc2efa90c19ac97c62b7860723f64784549620111a85
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121239616"
---
# <a name="native-run-time-checks-customization"></a>Yerel Çalışma Zamanı Denetimlerini Özelleştirme
**/RTC** ile derle (çalışma zamanı denetimleri) veya pragma kullanırken, C çalışma zamanı kitaplığı yerel `runtime_checks` çalışma zamanı denetimleri sağlar. Bazı durumlarda, çalışma zamanı denetimlerini özelleştirmek istiyor olabilir:

- Çalışma zamanı denetim iletilerini varsayılandan farklı bir dosyaya veya hedefe yönlendirme.

- Bir üçüncü taraf hata ayıklayıcısı altında çalışma zamanı denetim iletileri için bir çıkış hedefi belirtmek için.

- C çalışma zamanı kitaplığının yayın sürümüyle derlenmiş bir programdan çalışma zamanı denetim iletilerini rapor etmek için. Kitaplığın sürüm sürümleri çalışma zamanı `_CrtDbgReportW` hatalarını rapor etmek için kullanmaz. Bunun yerine, her çalışma **zamanı** hatası için bir Onay iletişim kutusu görüntüler.

  Çalışma zamanı hata denetimlerini özelleştirmek için şunları sebilirsiniz:

- Çalışma zamanı hata raporlama işlevi yazın. Daha fazla bilgi için, [bkz. How to: Write a Run-Time Error Reporting Function](../debugger/how-to-write-a-run-time-error-reporting-function.md).

- Hata iletisi hedeflerini özelleştirin.

- Çalışma zamanı denetim hataları hakkında bilgi için sorgu.

## <a name="customize-the-error-message-destination"></a>Hata İletisi Hedeflerini Özelleştirme
 Hataları rapor `_CrtDbgReportW` etmek için kullanırsanız, hata `_CrtSetReportMode` iletilerinin hedeflerini belirtmek için kullanabilirsiniz.

 Özel raporlama işlevi kullanıyorsanız, bir hatayı `_RTC_SetErrorType` bir rapor türüyle ilişkilendirmek için kullanın.

## <a name="query-for-information-about-run-time-checks"></a>Denetimler Hakkında Bilgi Run-Time Sorgulama
 `_RTC_NumErrors` , çalışma zamanı hata denetimleri tarafından algılanan hata türlerinin sayısını döndürür. Her hatanın kısa bir açıklamasını almak için, her döngüde yineleme değerini değerine geçerek 0'dan dönüş `_RTC_NumErrors` değerine `_RTC_GetErrDesc` döngüye geçebilirsiniz. Daha fazla bilgi için [bkz. _RTC_NumErrors](/cpp/c-runtime-library/reference/rtc-numerrors) ve [_RTC_GetErrDesc.](/cpp/c-runtime-library/reference/rtc-geterrdesc)

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıllı: Yerel Denetimler Run-Time Kullanma](../debugger/how-to-use-native-run-time-checks.md)
- [runtime_checks](/cpp/preprocessor/runtime-checks)
- [_CrtDbgReport, _CrtDbgReportW](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw)