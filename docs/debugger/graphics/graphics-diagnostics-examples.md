---
title: Grafik Tanılama örnekleri | Microsoft Docs
description: Visual Studio Grafik Tanılama kullanarak DirectX tabanlı uygulamalarda işleme sorunlarının nasıl ayıklanabileceği örneklerini görüntüleyin.
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
Bu örneklerde, Grafik Tanılama kullanarak DirectX tabanlı uygulamalarda işleme sorunlarının nasıl ayıklanacağı gösterilmektedir [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="capturing-graphics-information"></a>Graf bilgilerini yakalama
 Uygulamanızdaki işleme sorunlarını tanılamak için Grafik Tanılama kullanabilmeniz için, çalışırken uygulamadan grafik bilgilerini yakalamanız gerekir. Grafik bilgileri, yerel olarak çalışan bir uygulamadan veya uzak bir bilgisayarda ya da başka bir cihazda çalışan bir uygulamadan yakalanabilir. Bu izlenecek yollar, bir uygulamadan el ile veya program aracılığıyla grafik bilgilerini nasıl yakalayabileceğiniz göstermektedir:

- [İzlenecek yol: Grafik Bilgilerini Yakalama](walkthrough-capturing-graphics-information.md)

- [İzlenecek yol: Grafik Bilgilerini Program Aracılığıyla Yakalama](walkthrough-capturing-graphics-information-programmatically.md)

## <a name="use-graphics-diagnostics-with-an-arm-based-device"></a>ARM tabanlı bir cihazla Grafik Tanılama kullanma
 Uzaktan hata ayıklamayı kullanarak, ARM tabanlı bir cihazda Direct3D uygulamanızda hata ayıklamak için Grafik Tanılama kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ARM cihazındaki grafik tanılama kullanma](graphics-diagnostics-examples.md).

## <a name="playing-back-graphics-information"></a>Grafik bilgilerini kayıttan yürütme
 Çalışan bir uygulamadan grafik bilgilerini yakaladıktan sonra, işleme sorunlarının tanılanabilmesi için yakalanan olayları kayıttan çalabilirsiniz. Kayıttan yürütmek için geliştirme makinenizi kullanabilir veya bağlı olduğunuz uzak bir makineyi veya cihazı kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: grafik tanılama kayıttan yürütme makinesini değiştirme](how-to-change-the-graphics-diagnostics-playback-machine.md).

## <a name="debugging-missing-objects"></a>Eksik nesnelerde hata ayıklama
 Eksik bir nesne (veya nesneleri), grafik geliştiricilerin deneyen yaygın işleme sorunlarından biridir. Birçok farklı hata türü nesnenin kaybolması nedeniyle bu tür bir sorun tanınabilmesi zor olabilir. Eksik nesnelerin tipik nedenleri, yanlış yapılandırılmış cihaz durumunu, nesnenin geometrisini dönüştürmesiyle ilgili sorunları veya hatalı yapılandırılmış bir grafik işlem hattını içerir.

 Bu senaryolar, bir nesnenin neden eksik olduğunu belirleyebilmek ve sorumlu kodu bulmak için Grafik Tanılama nasıl kullanabileceğinizi gösterir.

- [İzlenecek yol: Cihaz Durumu Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-device-state.md)

- [İzlenecek yol: Köşe Gölgeleme Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-vertex-shading.md)

- [İzlenecek yol: Yanlış Yapılandırılmış Ardışık Düzen Nedeniyle Eksik Nesneler](walkthrough-missing-objects-due-to-misconfigured-pipeline.md)

## <a name="debugging-rendering-errors"></a>Hata ayıklama oluşturma hataları
 Doğru görünüme sahip olmayan bir nesne (veya nesneler), grafik geliştiricilerin deneydiklerinin yaygın bir sorundur. Bu tür bir sorun, yanlış görünüm ve nedeni çok açık olan, yanlış dokuyu bağlama (gölgelendirici kodundaki bir hata ya da gölgelendiriciler arasında beklenmeyen bir etkileşim) için çok daha belirgin bir şekilde bağlantı sağladığından, tanılanması zor olabilir. Bazı sorunlar nedeniyle hataların bir birleşimi olabilir.

 Aşağıda, küçük bir gölgelendirici hatasından kaynaklanan, olmayan, hafif bir işleme sorununu izlemek için Grafik Tanılama nasıl kullanabileceğinizi gösteren bir senaryo verilmiştir:

- [İzlenecek yol: Gölgeleme Nedeniyle Çıkan Oluşturma Hatalarını Ayıklama](walkthrough-debugging-rendering-errors-due-to-shading.md)

## <a name="debugging-compute-shaders"></a>İşlem gölgelendiricileri hatalarını ayıklama
 Hatalı sonuçlar üreten DirectCompute COMPUTE-Shader çekirdekler hatalarını ayıklamak için grafik tanılama kullanabilirsiniz. DirectCompute ile, çok sayıda veri öğesi üzerinde hesaplamalar gerçekleştirmek için GPU 'nun hesaplama gücünü kullanabilirsiniz. Belirli sorun türleri için GPU kullanımı, hatta iyi iyileştirilmiş CPU kodundan birçok kez daha hızlı çalışabilir. Ancak, geleneksel hata ayıklayıcıları GPU üzerinde çalışan kodu algılayamaz. Bu tür kodların hata ayıklaması, genellikle satıcıya özgü özelleştirilmiş araçlar gerektirir ve Visual Studio ile iyi tümleşebilir. İşlem gölgelendirici hata ayıklamasını bir dizi GPU 'da daha tutarlı hale getirmek için Grafik Tanılama, işlem gölgelendirici kodunuzda hata ayıklamak üzere tanıdık araçları kullanabilmeniz için, Direct3D işleme olaylarının yanı sıra DirectCompute dağıtım olaylarını yakalar.

 Bir işlem gölgelendirici içindeki hatanın neden olduğu simülasyon sorununun nasıl ayıklanacağını gösteren bir senaryo için bkz. [Izlenecek yol: Using grafik tanılama, Işlem gölgelendiricide hata ayıklama](walkthrough-using-graphics-diagnostics-to-debug-a-compute-shader.md).