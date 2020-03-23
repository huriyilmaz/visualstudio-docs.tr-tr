---
title: 'DA0504: Profilde Tutulan Süreç Için Baytlarda Maksimum Çalışma Seti | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0504
- vs.performance.504
- vs.performance.rules.DA0504
ms.assetid: 36e71603-ece7-4000-85fc-9da4eed61bf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a181ecb66c3735eb34ab3c866c3c68b2397781f6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779330"
---
# <a name="da0504-maximum-working-set-in-bytes-for-the-process-being-profiled"></a>DA0504: İşlem için izin verilen Bayt Cinsinden En Büyük Çalışma Kümesinin profili oluşturuluyor

|||
|-|-|
|Kural Id|DA0504|
|Kategori|Kaynak Yönetimi|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmış. İşlem Çalışma Kümesi karşı, profil oluşturma işleminize göre fiziksel bellek kullanımını ölçer. Bildirilen değer, tüm ölçüm aralıklarında gözlenen maksimum değerdir.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemin şu anda kullanmakta olduğu en büyük fiziksel bellek miktarını baytolarak bildirir. İşlem çalışma kümesi, şu anda fiziksel bellekte bulunan işlem adresi alanından sayfaları temsil eder. Bu kural, profil oluşturma etkinken işlem çalışması kümesi için en büyük değeri bildirir.

 Bildirilen değer, işlemin başlettiği paylaşılan bellek bölümlerinden yerleşik sayfaları içerir. İşlem başvurularının sayılan paylaşılan bellek segmentlerine dahil edildiği paylaşılan DL'ler. Çalışma Kümesi'nin değeri, paylaşılan bellek bölümleri nedeniyle işlemin ayırdığı sanal bellek miktarından daha yüksek olabilir.

 İşlem çalışma kümesinin boyutu, işlemin etkin olarak ne kadar sanal bellek kullandığını yansıtır. Ayrıca, diğer çalışan işlemlerden bu fiziksel bellek için uygulama ve çekişme çalıştırmak için kullanılabilir fiziksel bellek (veya RAM) miktarı etkilenir. İşlem çalışma kümeleri hakkında daha fazla bilgi için, MSDN'nin Windows Bellek Yönetimi belgelerinde [Çalışma Kümesi'ne](/windows/win32/memory/working-set) bakın.

## <a name="how-to-use-rule-data"></a>Kural Verileri Nasıl Kullanılır?
 Kural, bu ölçüm verilerini Windows performans izleme tesisinden toplar ve yalnızca bilgi için raporlar. Farklı sürümleriveya programın yapılarını karşılaştırmak veya farklı test senaryoları altında uygulamanın performansını anlamak için kullanın.

 Profil oluşturma verilerinin [İşaretler Görünümü'ne](../profiling/marks-view.md) gitmek için Hata Listesi penceresindeki iletiyi çift tıklatın. **İşlem\Çalışma Kümesi** ve **Bellek\Sayfalar/sn** sayacı sütunlarını bulun. Ardından **İşlem\Çalışma Kümesi'nin** maksimum değerini bulun ve **Bellek\Sayfalar/sn** değeriyle karşılaştırın. Sık sık, çalışma kümesi maksimum, özellikle makine bellek kısıtlı ise, azalan sayfalama IO etkinliği olduğu bir aralık ile ilişkilidir.
