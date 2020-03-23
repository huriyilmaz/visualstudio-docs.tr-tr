---
title: 'DA0503: Profilde Tutulan İşlem için Baytlarda Ortalama Çalışma Seti | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.503
- vs.performance.DA0503
- vs.performance.rules.DA0503
ms.assetid: 9047a494-eaaf-4679-b422-c64e8bde77a4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 8c9d309d7bf10cee07cc30c4568d2dfa59d1be56
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777456"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: Profillenenekadar baytlarda ayarlanan ortalama çalışma

|||
|-|-|
|Kural Id|DA0503|
|Kategori|Kaynak İzleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmış. İşlem Çalışma Kümesi karşı, profil oluşturma işleminize göre fiziksel bellek kullanımını ölçer. Bildirilen değer, tüm ölçüm aralıkları üzerinden hesaplanan ortalamadır.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemin şu anda baytlarda (çalışma kümesi) kullanmakta olduğu ortalama fiziksel bellek miktarını bildirir. İşlem çalışma kümesi, şu anda fiziksel bellekte bulunan işlem adresi alanından sayfaları temsil eder.

 Bildirilen değer, işlemin başlettiği paylaşılan bellek bölümlerinden yerleşik sayfaları içerir. İşlem başvurularının sayılan paylaşılan bellek segmentlerine dahil edildiği paylaşılan DL'ler. İşlem çalışma kümesinin değeri, paylaşılan bellek bölümleri nedeniyle işlemin ayırdığı sanal bellek miktarından daha yüksek olabilir.

 Bildirilen değer, profillenen işlemin etkin olduğu tüm ölçüm aralıklarının ortalamasıdır.

 İşlem çalışma kümesinin boyutu, işlemin etkin olarak ne kadar sanal bellek kullandığını yansıtır. Ayrıca, diğer çalışan işlemlerden bu fiziksel bellek için uygulama ve çekişme çalıştırmak için kullanılabilir fiziksel bellek (veya RAM) miktarı etkilenir. Fiziksel bellek kısıtlanmışsa, işletim sistemleri, işlem çalışma kümelerinden oldukça etkin olmayan sayfaları düzenli aralıklarla kırparak bellek kullanımını etkin süreçler arasında dengelemeye çalıştığından, işlem çalışma kümesinin değeri önemli ölçüde değişir.

 İşlem çalışma kümeleri hakkında daha fazla bilgi için, MSDN'nin Windows Bellek Yönetimi belgelerinde [Çalışma Kümesi'ne](/windows/win32/memory/working-set) bakın.

## <a name="how-to-use-rule-data"></a>Kural verileri nasıl kullanılır?
 Farklı sürümlerin veya programın yapılarının performansını karşılaştırmak veya farklı profil oluşturma senaryoları altında uygulamanın performansını anlamak için kural değerini kullanın.

 Profil oluşturma verilerinin [İşaretler Görünümü](../profiling/marks-view.md) görünümüne gitmek için Hatalar Listesi penceresindeki iletiyi çift tıklatın. **İşlem\Çalışma Kümesini** ve **Bellek\Sayfalar/sn** sütunlarını bulun. İki sütunu karşılaştırın ve artan sayfalama IO etkinliğiyle ilişkili görünen program yürütmesinin belirli aşamaları olup olmadığını belirleyin.
