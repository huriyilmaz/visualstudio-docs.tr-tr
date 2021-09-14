---
title: DA0503 - İşlem için Profili | Microsoft Docs
description: Bu ileti, işlemi şu anda bayt cinsinden (çalışma kümesi) kullanan ortalama fiziksel bellek miktarını raporlar.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: dbfee079945441f41069d34d1bc3cd36e4b9896a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635742"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Profili yapılan işlem için bayt cinsinden ortalama çalışma kümesi

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0503|
|Kategori|Kaynak İzleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmış. İşlem Çalışma Kümesi sayacı, profil oluşturma işleminin fiziksel bellek kullanımını ölçür. Bildirilen değer, tüm ölçüm aralıklarında hesaplanan ortalama değerdir.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 7'niz olduğunda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemi şu anda bayt cinsinden (çalışma kümesi) kullanan ortalama fiziksel bellek miktarını raporlar. İşlem çalışma kümesi, şu anda fiziksel bellekte bulunan işlem adres alanı sayfalarını temsil eder.

 Bildirilen değer, işlemde başvurulan paylaşılan bellek segmentlerinden yerleşik sayfaları içerir. İşlem başvurularını içeren paylaşılan URL'ler, sayılacak paylaşılan bellek segmentlerine dahil edilir. İşlem çalışma kümesi değeri, paylaşılan bellek kesimleri nedeniyle işlem tarafından ayrılan sanal bellek miktarından daha yüksek olabilir.

 Bildirilen değer, profili yapılan sürecin etkin olduğu tüm ölçüm aralıklarının ortalamasıdır.

 İşlem çalışma kümesi boyutu, sürecin etkin olarak ne kadar sanal bellek kullandığını yansıtıyor. Ayrıca, uygulamayı çalıştırmak için kullanılabilen fiziksel bellek (veya RAM) miktarından ve bu fiziksel bellek için diğer çalışan işlemlerden gelen bir sorundan etkilenir. Fiziksel bellek kısıtlanmışsa, işletim sistemleri işlem çalışma kümelerinden düzenli aralıklarla etkin olmayan sayfaları kırparak bellek kullanımını dengelemeye çalıştığından işlem çalışma kümesi değeri önemli ölçüde farklılık gösterebilir.

 İşlem çalışma kümeleri hakkında daha fazla bilgi için [MSDN'nin](/windows/win32/memory/working-set) Windows Bellek Yönetimi belgelerinde Çalışma Kümesi'ne bakın.

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Programın farklı sürümlerinin veya derlemelerinin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için kural değerini kullanın.

 Profil oluşturma verileri için İşaretler Görünümü görünümüne gitmek için Hatalar [Listesi penceresindeki](../profiling/marks-view.md) iletiyi çift tıklatın. **İşlem\Çalışma Kümesi ve** **Memory\Pages/sec sütunlarını** bulun. İki sütunu karşılaştırın ve artan disk belleği IO etkinliğiyle ilişkili gibi görünen belirli program yürütme aşamaları olup olmadığını belirler.
