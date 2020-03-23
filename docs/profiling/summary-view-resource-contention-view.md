---
title: Özet Görünüm - Kaynak Çekişme Görünümü | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 6da57b83-7b42-4d7c-9aea-8e0a830faf6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 185345c13134f4d2ec6086e6a66183e044c577ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74771454"
---
# <a name="summary-view---resource-contention-view"></a>Özet Görünümü - Kaynak Çakışması Görünümü
Özet görünümü, bir kaynağa erişim beklerken bir iş parçacığının veya işlemin askıya alındığını uygulamanızdaki olaylarla ilgili bilgileri görüntüler.

 Bildirim Bağlantıları ve Rapor listelerinin açıklaması da dahil olmak üzere daha fazla bilgi için [Özet Görünüm](../profiling/summary-view.md)bölümüne bakın.

## <a name="timeline-graph"></a>Zaman Çizelgesi Grafiği
 Özet görünümündeki zaman çizelgesi grafiği, profil oluşturmanın gerçekleştiği süre içinde profiluygulamasının çekişme olaylarının sayısını gösterir. Görünümü seçili bir zaman aralığına filtrelemek için zaman çizelgesi grafiğini kullanabilirsiniz. Daha fazla bilgi için [bkz: Özet Zaman Çizelgesinden Rapor Görünümlerini Filtreleyin.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)

## <a name="most-contended-resources"></a>En Çok Kullanılan Kaynaklar
 **Çoğu Zamanlanmış Kaynaklar,** uygulamada en çok çekişme olaylarına neden olan kaynakları listeler. Çekişmeler görünümünü görüntülemek için bir kaynak adını tıklatabilirsiniz. Çekişmeler görünümü, iş parçacığına göre kaynak çekişmelerinin ayrıntılı bir zaman çizelgesini sağlar.

 **Çoğu Zamanlanmış Kaynak,** her kaynak için aşağıdaki verileri içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Adı**|Kaynağın adı.|
|**Çekişmeler %**|Profil oluşturma verilerindeki tüm çekişme olaylarının yüzdesi, bu kaynak üzerinde çekişmeler vardı.|

## <a name="most-contended-thread"></a>En Çok Contended Thread
 **En Çok Contended Threads** çekişme olayları en çok sayıda olan uygulamada iş parçacıkları listeler. İş parçacığı tarafından kaynak çekişmeleri ayrıntılı bir zaman çizelgesi sağlayan Çekişmeler görünümünü görüntülemek için bir iş parçacığı adını tıklatabilirsiniz.

 **Çoğu Contended Threads** her iş parçacığı için aşağıdaki verileri içerir.

|Sütun|Açıklama|
|------------|-----------------|
|**Kimliği**|İş parçacığı tanımlayıcısı.|
|**Adı**|İş parçacığının sahibi olan işlemin adı.|
|**Çekişmeler %**|Profil oluşturma verilerindeki tüm çekişme olaylarının yüzdesi, bu kaynak üzerinde çekişmeler vardı.|
