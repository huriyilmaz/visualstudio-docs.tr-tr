---
title: Enstrümantasyon Veri Değerlerini Anlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3dace7b13816c63664ccb4dabfed52d1c5fb7523
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778082"
---
# <a name="understand-instrumentation-data-values"></a>Enstrümantasyon veri değerlerini anlama

Visual Studio'nun *enstrümantasyon* profilleme yöntemi, profilli uygulamada işlev çağrıları, çizgiler ve talimatlar için ayrıntılı zamanlama bilgilerini kaydeder

Enstrümantasyon yöntemi, profilli ikilideki hedef işlevlerin başında ve sonunda ve bu işlevler tarafından yapılan her çağrıdan önce ve sonra diğer işlevlere kod enjekte eder. Enjekte edilen kod aşağıdaki bilgileri kaydeder:

- Bu toplama olayı ile önceki olay arasındaki aralık.

- İşletim sisteminin aralık ta bir işlem gerçekleştirip gerçekleştirmediği. Örneğin, işletim sistemi diske okuma veya yazma veya başka bir işlemde hedef iş parçacığı ile başka bir iş parçacığı arasında geçiş yapabilir.

Her aralık için profil oluşturucu çözümlemesi, aralığın sonunda bulunan çağrı yığınını yeniden yapılandır. Çağrı yığını, bir anda işlemcide etkin olan işlevlerin listesidir. Yalnızca bir işlev (geçerli işlev) kodu yürüter; diğer işlevler, geçerli işleve (çağrı yığını) çağrıyla sonuçlanan işlev çağrıları zinciridir.

Aralık kaydedildiğinde çağrı yığınındaki her işlev için profil oluşturucu çözümlemesi, işlev için dört veri değerden biri veya daha fazlasına aralığı ekler. Çözümleme, iki ölçüte dayalı bir işlev için bir veri değerine aralığı ekler:

- Aralığın işlevin kodunda mı yoksa *alt işlevde* mi (işlev tarafından çağrılan bir işlev) oluşup oluşmadığı.

- Aralıkta bir işletim sistemi olayının oluşup oluşmadığı.

Bir işlev veya veri aralığının bir aralığı için veri değerleri *Elapsed Inclusive*, *Elapsed Exclusive*, *Application Inclusive*ve *Application Exclusive*adlanır :

- Bir işlevin tüm aralıkları, Geçen Kapsayıcı veri değerine eklenir.

- Aralık bir alt işlevde değil de işlevin kodunda oluştuysa, aralık işlevin Geçen Özel veri değerine eklenir.

- Aralıkta bir işletim sistemi olayı meydana gelmediyse, aralık Uygulama Kapsayıcı veri değerine eklenir.

- Aralıkta bir işletim sistemi olayı meydana gelmediyse ve işlev kodunun doğrudan yürütülmesinde oluşan aralık (diğer bir deyişle, bir alt işlevde gerçekleşmedi), aralık Uygulama Münhasır veri değerine eklenir.

Profil Oluşturma Araçları raporları, profil oluşturma oturumundaki işlevlerin toplam değerlerini ve oturumun işlemlerini, iş parçacıklarını ve ikililerini toplar.

## <a name="elapsed-inclusive-values"></a>Geçen Kapsayıcı değerler

Bir işlevi ve alt işlevleri yürütme harcanan toplam zaman.

Geçen Kapsayıcı değerler, işlev kodunun doğrudan yürütülmesi için harcanan aralıkları ve hedef işlevin alt işlevlerini yürütmek için harcanan aralıkları içerir. İşletim sistemini beklemeyi içeren işlev in veya alt işlevlerinin aralıkları da Geçen Kapsayıcı değerlere dahil edilir.

## <a name="elapsed-exclusive-values"></a>Geçen Özel değerler

Alt işlevlerde harcanan süre hariç olmak üzere, bir işlevi yürütmek için harcanan süre.

Geçen Özel değerler, bir işletim sistemi olayının aralıkta oluşup oluşmadığına bakılmaksızın işlev kodunu niçin doğrudan yürütmek için harcanan aralıkları içerir. Hedef işlev tarafından çağrılan alt işlevlerde harcanan tüm aralıklar, Geçen Özel değerlere dahil edilmez.

## <a name="application-inclusive-values"></a>Uygulama Dahil değerleri

İşletim sistemi olaylarında harcanan süre hariç olmak üzere, bir işlevi ve alt işlevleri yürütmek için harcanan süre.

Uygulama Dahil değerleri işletim sistemi olayları içeren aralıkları içermez. Uygulama Dahil değerleri, aralığın işlev kodunu niçin doğrudan çalıştırdığına veya hedef işlevin alt işlevlerinde harcanıp harcanmadığına bakılmaksızın, bir işlevi yürütmek için harcanan diğer tüm aralıkları içerir.

## <a name="application-exclusive-values"></a>Uygulama Özel değerler

Alt işlevlerde harcanan süre ve işletim sistemi olaylarında harcanan süre hariç olmak üzere bir işlevi yürütmek için harcanan süre.

Uygulama Özel değerler, işletim sistemi olayları veya işlev tarafından çağrılan işlevleri yürütme için harcanan aralıkları içeren aralıkları içermez. Uygulama Özel değerleri yalnızca işlev kodunu doğrudan yürütmeiçin harcanan ve bir işletim sistemi olayı içermeyen aralıkları içerir.

## <a name="elapsed-inclusive-percent"></a>Geçen Dahil yüzdesi

İşlev, modül, iş parçacığı veya işlemin Geçen Kapsayıcı değerleri olan profil oluşturma oturumunun toplam Geçen Kapsayıcı değerlerinin yüzdesi.

100 * Fonksiyon Geçen Dahil / Oturum Dahil Geçti

## <a name="elapsed-exclusive-percent"></a>Geçen Özel yüzde

İşlevin, modülün, iş parçacığının veya işlemin Geçen Münhasır değerleri olan profil oluşturma oturumunun toplam Geçen Kapsayıcı değerlerinin yüzdesi.

100 * Fonksiyon Geçen Özel / Oturum Dahil Geçti

## <a name="application-inclusive-percent"></a>Uygulama Dahil Yüzdesi

İşlev, modül, iş parçacığı veya işlemin Uygulama Dahil değerleri olan profil oluşturma oturumunun toplam Uygulama Dahil değerlerinin yüzdesi.

100 * Fonksiyon Uygulaması Dahil / Oturum Uygulaması Dahil

## <a name="application-exclusive-percent"></a>Uygulama Münhasır yüzde

Profil oluşturma oturumunun, işlevin, modülün, iş parçacığının veya işlemin Uygulama Münhasır aralıkları olan toplam Uygulama Dahil değerlerinin yüzdesi.

100 * Fonksiyon Uygulaması Özel / Oturum Uygulaması Dahil

## <a name="see-also"></a>Ayrıca bkz.

[Performans araçları verilerini](../profiling/analyzing-performance-tools-data.md)
analiz[etme Nasıl Yapılır: Toplama yöntemlerini seçin](../profiling/how-to-choose-collection-methods.md)
