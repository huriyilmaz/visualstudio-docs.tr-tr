---
title: Grafik Tanılama Örnekleri | Microsoft Docs
description: DirectX tabanlı uygulamalarda, Visual Studio Grafik Tanılama kullanarak işleme sorunlarının hata ayıklama örneklerini Visual Studio Grafik Tanılama.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45dd86b2-801e-4b07-a8c4-7bd25641d7f8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 412f8dcae25b0cefda9a96695f418306c1d66bb8741963a4215d0f27a4d3a0c7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121454261"
---
# <a name="graphics-diagnostics-examples"></a>Grafik Tanılama Örnekleri
Bu örnekler, DirectX tabanlı uygulamalarda veri işleme sorunlarının hata ayıklamak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Grafik Tanılama.

## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama
 Uygulamanıza işleme Grafik Tanılama tanılamak için Grafik Tanılama'ı kullanamadan önce, çalışırken uygulamanın grafik bilgilerini yakalamanız gerekir. Grafik bilgileri yerel olarak çalışan bir uygulama veya uzak bir bilgisayarda veya başka bir cihazda çalışan bir uygulamadan yakalanabiliyor. Bu izlenecek yollar, bir uygulamanın grafik bilgilerini el ile veya program aracılığıyla nasıl yakalayabilirsiniz?

- [İzlenecek yol: Grafik Bilgilerini Yakalama](walkthrough-capturing-graphics-information.md)

- [İzlenecek yol: Grafik Bilgilerini Program Aracılığıyla Yakalama](walkthrough-capturing-graphics-information-programmatically.md)

## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>ARM Grafik Tanılama cihazla cihaz kullanma
 Uzaktan hata Grafik Tanılama kullanarak ARM tabanlı bir cihazda Direct3D uygulamanıza hata ayıklamak için Grafik Tanılama'ı kullanabilirsiniz. Daha fazla bilgi [için bkz. Nasıl Grafik Tanılama ARM Cihazı ile Birlikte Kullanma.](graphics-diagnostics-examples.md)

## <a name="playing-back-graphics-information"></a>Grafik bilgilerini yeniden çalma
 Çalışan bir uygulamanın grafik bilgilerini yakaladikten sonra, işleme sorunlarını tanılamak için yakalanan olayları geri oynatabilirsiniz. Geri oynatmak için geliştirme makinenizi veya bağlı olduğunuz uzak bir makineyi veya cihazı kullanabilirsiniz. Daha fazla bilgi için, [bkz. How to: Change the Grafik Tanılama Playback Machine](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="debugging-missing-objects"></a>Eksik nesnelerde hata ayıklama
 Eksik nesne (veya nesneler), grafik geliştiricilerin en sık karşılaşılan işleme sorunlarından biri. Bir nesnenin kaybolmasına neden olan birkaç farklı hata türü nedeniyle bu tür bir sorunu tanılamak zor olabilir. Eksik nesnelerin tipik nedenleri arasında yanlış yapılandırılmış cihaz durumu, nesnenin geometrisini dönüştürme sorunları veya yanlış yapılandırılmış grafik işlem hattı yer almaktadır.

 Bu senaryolar, bir nesnenin Grafik Tanılama nedenini belirlemek ve sorumlu kodu bulmak için Grafik Tanılama'ı nasıl kullanabileceğiniz gösterir.

- [İzlenecek yol: Cihaz Durumu Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-device-state.md)

- [İzlenecek yol: Köşe Gölgeleme Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-vertex-shading.md)

- [İzlenecek yol: Yanlış Yapılandırılmış Ardışık Düzen Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)

## <a name="debugging-rendering-errors"></a>Hata ayıklama işleme hataları
 Bir nesnenin (veya nesnelerin) doğru görünüme sahip olması, grafik geliştiricilerin sık karşılaşılan bir diğer sorunudur. Bu tür bir sorunu tanılamak zor olabilir çünkü yanlış görünüm ve nedeni çok belirginden (yanlış dokuyu bağlamadan çok inceye kadar) gölgelendirici kodundaki bir hata veya gölgelendiriciler arasındaki beklenmeyen bir etkileşim arasında olabilir. Bazı sorunlara bir hata bileşimi neden olabilir.

 Küçük gölgelendirici hatasının neden olduğu çok ince olmayan Grafik Tanılama bir işleme sorununu izlemek için Grafik Tanılama'i nasıl kullanabileceğinizi gösteren bir senaryo aşağıda ve açık ve açık bir şekilde açık bir şekilde açık ve açık bir şekilde açık bir şekilde açık ve açık bir şekilde açık ve açık bir şekilde açık bir şekilde ve dolayısıyla aşağıdaki senaryoyu inceleyebildi:

- [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)

## <a name="debugging-compute-shaders"></a>İşlem gölgelendiricilerde hata ayıklama
 Hatalı sonuçlar Grafik Tanılama DirectCompute işlem gölgelendiricisi çekirdekleri hata ayıklamak için Grafik Tanılama kullanabilirsiniz. DirectCompute ile GPU'nun işlem gücünü kullanarak paralel olarak çok sayıda veri öğeleri üzerinde hesaplamalar gerçekleştirebilirsiniz. Belirli türlerde sorunlar için GPU'yu kullanmak, iyileştirilmiş CPU kodundan bile çok daha hızlı bir şekilde işlem gerçekleştirebilirsiniz. Ancak geleneksel hata ayıklayıcıları GPU üzerinde çalışan kodu algılayamaz. Bu tür kodlarda hata ayıklamak için genellikle satıcıya özgü özel araçlar gerekir ve bu araçlarla iyi tümleştirilene Visual Studio. İşlem gölgelendiricisi hata ayıklamasını farklı GPU'larda daha tutarlı hale Grafik Tanılama, Direct3D işleme olaylarının yanı sıra DirectCompute Dispatch olaylarını yakalar; böylece işlem gölgelendiricisi kodundaki sorunları ayıklamak için tanıdık araçları kullanabilirsiniz.

 İşlem gölgelendiricideki bir hatadan kaynaklanan bir simülasyon sorununun hata ayıklaması gösteren bir senaryo için bkz. Adım [adım:](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md)İşlem Gölgelendiricisinde Hata Ayıklamak için Grafik Tanılama Kullanma.