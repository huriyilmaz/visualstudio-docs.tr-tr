---
title: Izleme veri değerlerini anlama | Microsoft Docs
description: İzleme profili oluşturma yönteminin, profili oluşturulmuş uygulamadaki işlev çağrıları, satırlar ve yönergeler için ayrıntılı zamanlama bilgilerini nasıl kaydettiği hakkında bilgi edinin.
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
ms.openlocfilehash: 751d990a7b7e3623311fd7487e0303100ec7300a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122140823"
---
# <a name="understand-instrumentation-data-values"></a>İzleme veri değerlerini anlama

Visual Studio *izleme* profili oluşturma yöntemi, işlev çağrıları, satırlar ve profili oluşturulmuş uygulamadaki yönergeler için ayrıntılı zamanlama bilgilerini kaydeder

İzleme yöntemi, profili oluşturulan ikilide hedef işlevlerin başlangıcında ve sonunda kodu çıkartır ve bu işlevler tarafından, diğer işlevlere yapılan her çağrıdan önce ve sonra. Eklenen kod aşağıdaki bilgileri kaydeder:

- Bu koleksiyon olayı ile bir önceki arasındaki Aralık.

- İşletim sisteminin Aralık süresince bir işlem gerçekleştirip gerçekleştirmediğini belirtir. Örneğin, işletim sistemi disk okuyabilir veya diske yazabilir ya da başka bir işlemdeki hedef iş parçacığı ile başka bir iş parçacığı arasında geçiş yapar.

Her Aralık için, profil oluşturucu Analizi aralığın sonunda mevcut olan çağrı yığınını yeniden oluşturur. Çağrı yığını, bir zaman noktasında bir işlemcide etkin olan işlevlerin listesidir. Yalnızca bir işlev (geçerli işlev) kodu yürütüyor; diğer işlevler, geçerli işleve (çağrı yığını) çağrı ile sonuçlanan işlev çağrılarının zinciridir.

Aralık kaydedildiğinde, çağrı yığınında her bir işlev için, profil oluşturucu analizi, işlev için bir veya daha fazla dört veri değerine aralığı ekler. Analiz, aralığı iki ölçüte göre bir işlev için bir veri değerine ekler:

- Aralığın, işlevin kodunda mi yoksa bir *alt işlevde* mi (işlev tarafından çağrılan bir işlev) mi gerçekleştiği.

- Aralıkta bir işletim sistemi olayının oluşup oluşmadığını belirtir.

Bir işlev veya veri aralığı için veri değerleri, *geçen kapsamlı*, *geçen dışlamalı*, *uygulama kapsamlı* ve *uygulama dışlamalı* olarak adlandırılır:

- Bir işlevin tüm aralıkları, geçen kapsamlı veri değerine eklenir.

- Aralık bir alt işlevde değil işlevin kodunda oluştuysa, Aralık işlevin geçen dışlayıcı veri değerine eklenir.

- Aralıkta bir işletim sistemi olayı gerçekleşmediyse, Aralık uygulama kapsamlı veri değerine eklenir.

- Bir işletim sistemi olayı, Aralık içinde gerçekleşmediyse ve işlev kodunun doğrudan yürütümesinde (yani, bir alt işlevde gerçekleşmediyse), Aralık uygulama dışlamalı veri değerine eklenir.

Profil Oluşturma Araçları raporlar, profil oluşturma oturumunun kendisindeki işlevlerin toplam değerini ve oturumun işlem, iş parçacığı ve ikili dosyalarını toplar.

## <a name="elapsed-inclusive-values"></a>Geçen kapsamlı değerler

Bir işlevi ve onun alt işlevlerini yürütmek için harcanan toplam süre.

Geçen kapsamlı değerler, işlev kodunu doğrudan yürüten ve hedef işlevin alt işlevlerini yürütmek için harcanan aralıkları içerir. İşlevin veya işletim sisteminin beklemeyi içeren alt işlevlerinin aralıkları, geçen kapsamlı değerlere de dahildir.

## <a name="elapsed-exclusive-values"></a>Geçen dışlamalı değerler

Alt işlevlerde harcanan zamanı hariç bir işlevi yürütmek için harcanan zaman.

Geçen dışlamalı değerler, Aralık içinde bir işletim sistemi olayının oluşup oluşmadığını bağımsız olarak, işlev kodunu doğrudan yürütmek için harcanan aralıkları içerir. Hedef işlev tarafından çağrılan alt işlevlerde harcanan tüm aralıklar, geçen özel değerlere dahil değildir.

## <a name="application-inclusive-values"></a>Uygulama kapsamlı değerler

İşletim sistemi olaylarında harcanan zamanı dışlayarak bir işlevi ve onun alt işlevlerini yürütmek için harcanan zaman.

Uygulama kapsamlı değerleri, işletim sistemi olaylarını içeren aralıklar içermez. Uygulama kapsamlı değerler, aralığın işlev kodunu doğrudan yürütme veya hedef işlevin alt işlevlerinde harcanmasından bağımsız olarak, bir işlevi yürütmek için harcanan tüm diğer aralıkları içerir.

## <a name="application-exclusive-values"></a>Uygulamanın dışlamalı değerleri

Alt işlevlerde harcanan zamanı ve işletim sistemi olaylarında harcanan zamanı hariç bir işlevi yürütmek için harcanan süre.

Uygulama dışlamalı değerleri, işlev tarafından çağrılan işlevleri yürütmeye harcanan işletim sistemi olaylarını veya aralıklarını içeren aralıklar içermez. Uygulamaya dışlamalı değerler yalnızca, işlev kodunu doğrudan yürüten ve bir işletim sistemi olayı içermeyen aralıkları içerir.

## <a name="elapsed-inclusive-percent"></a>Geçen kapsamlı yüzde

Profil oluşturma oturumunun, işlevin, modülün, iş parçacığının veya işlemin kapsamlı değerleriyle geçen toplam geçen dahil edilen değerlerinin yüzdesi.

100 * işlev geçen kapsayıcı/oturum süresi dahil geçti

## <a name="elapsed-exclusive-percent"></a>Geçen dışlamalı yüzde

Profil oluşturma oturumunun, işlev, modül, iş parçacığı veya işlemin dışlamalı değerleri ile geçen toplam geçen kapsamlı değer yüzdesi.

100 * işlev hariç geçen özel/oturum geçti

## <a name="application-inclusive-percent"></a>Uygulama kapsamlı yüzdesi

İşlev, modül, iş parçacığı veya işlemin uygulama kapsamlı değerleri olan profil oluşturma oturumunun Toplam uygulama kapsamlı değerlerinin yüzdesi.

100 * işlev uygulaması dahil/oturum uygulaması kapsamlı

## <a name="application-exclusive-percent"></a>Uygulama dışlamalı yüzdesi

Profil oluşturma oturumunun, işlev, modül, iş parçacığı veya işlemin özel kullanım aralıkları olan toplam uygulama dahil değerlerinin yüzdesi.

100 * işlev uygulaması dışlamalı/oturum uygulaması kapsamlı

## <a name="see-also"></a>Ayrıca bkz.

[Performans araçları verilerini çözümleme](../profiling/analyzing-performance-tools-data.md) 
 [Nasıl yapılır: koleksiyon Yöntemleri Seçme](../profiling/how-to-choose-collection-methods.md)
