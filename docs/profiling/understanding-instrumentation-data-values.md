---
title: Ölçüm ölçümlerini anlama veri | Microsoft Docs
description: Ölçüm profil oluşturma yönteminin, profil profili yapılan uygulamada işlev çağrıları, satırlar ve yönergeler için ayrıntılı zamanlama bilgilerini nasıl kaydediyor olduğunu öğrenin.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation
- instrumentation profiling method
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 45a02deb51774a46c7d7618d912b87c49e187c852e0048108bf502fbf02f1e1a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395998"
---
# <a name="understand-instrumentation-data-values"></a>Ölçüm ölçüm verisi değerlerini anlama

Profil *oluşturma yönteminin* ölçüm Visual Studio, satırlar ve profil profili yapılan uygulama yönergeleri için ayrıntılı zamanlama bilgilerini kaydediyor

Ölçüm yöntemi, profili profili yapılan ikili dosyada hedef işlevlerin başlangıcına ve sonuna, bu işlevler tarafından yapılan her çağrının önce ve sonrasını diğer işlevlere kodlar. Yeni kod aşağıdaki bilgileri kaydeder:

- Bu koleksiyon olayı ile önceki olay arasındaki aralık.

- İşletim sisteminin aralık sırasında bir işlem gerçekleştirip gerçekleştirip gerçekleştire olmadığı. Örneğin, işletim sistemi diske okuyabilir veya yazabilir ya da başka bir işlemde hedef iş parçacığı ile başka bir iş parçacığı arasında geçiş olabilir.

Profil oluşturma analizi, her aralık için aralığın sonunda mevcut olan çağrı yığınını yeniden yapılandırıyor. Çağrı yığını, bir işlemcide zaman içinde etkin olan işlevlerin listesidir. Yalnızca bir işlev (geçerli işlev) kod yürütür; diğer işlevler, geçerli işleve (çağrı yığını) yapılan çağrıyla sonuçlandırılmış işlev çağrıları zinciridir.

Aralık kaydediken çağrı yığınında yer alan her işlev için profil oluşturma analizi, aralık işlevinin dört veri değerine bir veya daha fazla veri değeri ekler. Analiz, iki ölçüte göre bir işlevin veri değerine aralığı ekler:

- Aralığın işlevin kodunda mı yoksa bir alt *işlevde* mi (işlev tarafından çağrılan bir işlev) olup olmadığı.

- Aralıkta bir işletim sistemi olayı olup olmadığı.

Bir işlevin veya veri aralığının veri değerleri, Geçen Dahil *,* *Özel,* Uygulama Dahil ve Özel Uygulama Dahil olarak *adlandırılmıştır:*

- Bir işlevin tüm aralıkları, Geçen Kapsayıcı veri değerine eklenir.

- Aralık, bir alt işlevde değil işlevin kodunda oluştu ise, aralık işlevin Geçen Özel veri değerine eklenir.

- Aralıkta bir işletim sistemi olayı oluşmazsa, aralık Uygulama Dahil veri değerine eklenir.

- Bir işletim sistemi olayı aralık içinde oluşmadı ve aralık işlev kodunun doğrudan yürütülmesinde (yani bir alt işlevde oluşmadı) oluştu ise, aralık Uygulama Özel veri değerine eklenir.

Profil Oluşturma Araçları, profil oluşturma oturumunda işlevlerin toplam değerlerini ve oturumun işlemlerini, iş parçacıklarını ve ikili değerlerini bir araya toplar.

## <a name="elapsed-inclusive-values"></a>Geçen Kapsayıcı değerler

Bir işlevin ve alt işlevlerinin yürütülmesi için harcanan toplam süre.

Geçen Kapsayıcı değerler, işlev kodunun doğrudan yürütülmesi için harcanan aralıkları ve hedef işlevin alt işlevlerini yürütmek için harcanan aralıkları içerir. İşlevin veya işletim sisteminin beklemesini içeren alt işlevlerin aralıkları, Geçen Kapsayıcı değerlere de dahil edilir.

## <a name="elapsed-exclusive-values"></a>Geçen Özel değerler

Alt işlevlerde harcanan süre hariç olmak üzere bir işlevin yürütülmesi için harcanan süre.

Geçen Özel değerler, aralıkta bir işletim sistemi olayı olup olmadığı bağımsız olarak işlev kodunun doğrudan yürütülmesi için harcanan aralıkları içerir. Alt işlevlerde hedef işlev tarafından çağrılan tüm aralıklar, Geçen Özel değerler'e dahil değildir.

## <a name="application-inclusive-values"></a>Uygulama Dahil değerleri

İşletim sistemi olaylarında harcanan süre hariç olmak üzere, bir işlevi ve onun alt işlevlerini yürütmek için harcanan süre.

Uygulama Dahil değerleri işletim sistemi olaylarını içeren aralıklar içermez. Uygulama Dahil değerleri, aralığın işlev kodunu doğrudan yürütmeye mi yoksa hedef işlevin alt işlevlerine mi harcanıp harcanmalarına bakılmaksızın bir işlevin yürütülmesi için harcanan diğer tüm aralıkları içerir.

## <a name="application-exclusive-values"></a>Uygulamaya Özel değerler

Alt işlevlerde harcanan süre ve işletim sistemi olaylarında harcanan süre hariç olmak üzere bir işlevin yürütülmesi için harcanan süre.

Özel Uygulama değerleri, işletim sistemi olaylarını içeren aralıkları veya işlev tarafından çağrılan işlevleri yürüterek harcanan aralıkları içermez. Uygulama Özel değerleri yalnızca işlev kodunun doğrudan yürütülmesi için harcanan ve işletim sistemi olayı içermeen aralıkları içerir.

## <a name="elapsed-inclusive-percent"></a>Geçen Kapsayıcı yüzde

Profil oluşturma oturumunun işlev, modül, iş parçacığı veya işleminin Geçen Kapsayıcı değerleri olan toplam Geçen Kapsayıcı değerlerinin yüzdesi.

100 * İşlev Dahil/ Oturum Dahil Geçildi

## <a name="elapsed-exclusive-percent"></a>Geçen Özel yüzde

Profil oluşturma oturumunun işlevin, modülün, iş parçacığının veya işleme ait Özel değerler olan toplam Geçen Kapsayıcı değerlerinin yüzdesi.

100 * İşlev Özel Olarak Geçen / Oturum Dahil Edildi

## <a name="application-inclusive-percent"></a>Uygulama Dahil yüzde

Profil oluşturma oturumunun işlev, modül, iş parçacığı veya işleme yönelik Application Inclusive değerleri olan toplam Application Inclusive değerlerinin yüzdesi.

100 * İşlev Uygulaması Dahil / Oturum Uygulaması Dahil

## <a name="application-exclusive-percent"></a>Uygulamaya Özel yüzde

Profil oluşturma oturumunun işlev, modül, iş parçacığı veya işleme ait Application Exclusive aralıkları olan toplam Application Inclusive değerlerinin yüzdesi.

100 * İşlev Uygulaması Özel / Oturum Uygulaması Dahil

## <a name="see-also"></a>Ayrıca bkz.

[Performans araçları verilerini analiz etme](../profiling/analyzing-performance-tools-data.md) 
 [Nasıl yapılacaklar: Koleksiyon yöntemlerini seçme](../profiling/how-to-choose-collection-methods.md)
