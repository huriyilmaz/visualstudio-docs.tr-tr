---
title: DA0503-profili oluşturulan Işlem için bayt cinsinden ortalama çalışma kümesi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: b6717f524f6a2d3f9f09290ac9bfbd8f02fc23fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544553"
---
# <a name="da0503-average-working-set-in-bytes-for-the-process-being-profiled"></a>DA0503: işlemin profili oluşturulan ortalama çalışma kümesi bayt cinsinden

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0503|
|Kategori|Kaynak Izleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmıştı. Işlem çalışma kümesi sayacı, profil oluşturduğunuz işlem tarafından fiziksel bellek kullanımını ölçer. Bildirilen değer tüm ölçüm aralıklarında hesaplanan ortalama değerdir.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemin Şu anda kullandığı ortalama fiziksel bellek miktarını bayt (çalışma kümesi) olarak bildirir. İşlem çalışma kümesi, şu anda fiziksel bellekte bulunan işlem adres alanından sayfaları temsil eder.

 Raporlanan değer, paylaşılan bellek segmentlerinden işleme başvurduğu yerleşik sayfaları içerir. İşlemin başvurduğu paylaşılan DLL 'Ler, sayılan paylaşılan bellek kesimlerine dahil edilir. İşlem çalışma kümesinin değeri, paylaşılan bellek kesimleri nedeniyle işlemin ayırdığı sanal bellek miktarından daha yüksek olabilir.

 Bildirilen değer, işlem yapılan işlemin etkin olduğu tüm ölçüm aralıklarının ortalaması olarak belirlenir.

 İşlem çalışma kümesinin boyutu, işlemin etkin bir şekilde ne kadar sanal bellek kullandığını yansıtır. Ayrıca, uygulamayı çalıştırmak için kullanılabilir fiziksel bellek miktarı (veya RAM) ve diğer çalışan işlemlerden bu fiziksel bellek için çekişmeden da etkilenir. Fiziksel bellek kısıtlandığından, işlem çalışma kümesinin değeri, işlem çalışma kümelerinden oldukça etkin olmayan sayfaları düzenli olarak kırparak, işletim sistemleri, etkin süreçler genelinde bellek kullanımını dengelemeye çalıştığı için apt ' dir.

 İşlem çalışma kümeleri hakkında daha fazla bilgi için bkz. MSDN 'nin Windows bellek yönetimi belgelerindeki [çalışma kümesi](/windows/win32/memory/working-set) .

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için kural değerini kullanın.

 Profil oluşturma verilerinin [Işaretler görünümü](../profiling/marks-view.md) görünümüne gitmek Için hatalar Listesi penceresinde iletiye çift tıklayın. **Process\working kümesini** ve **bellek \ Sayfa/sn** sütunlarını bulun. İki sütunu karşılaştırın ve daha fazla sayfalama GÇ etkinliğiyle ilişkili olarak görünen program yürütmesinin belirli aşamaları olup olmadığını saptayın.
