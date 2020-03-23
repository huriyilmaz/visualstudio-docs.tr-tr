---
title: 'DA0505: Profillenen İşlem için ayrılan Ortalama Özel Bayt | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b905b0de69110f5f7cd684deb6fe6c5955bb4b0c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777409"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: İşlem için izin verilen Ortalama Özel Bayt Sayısının profili oluşturuluyor

|||
|-|-|
|Kural Id|DA0505|
|Kategori|Kaynak Yönetimi|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmış. İşlem Özel Bayt karşı tevkici, profil oluşturma işlemi tarafından ayrılan sanal belleği ölçer. Bildirilen değer, tüm ölçüm aralıkları üzerinden hesaplanan ortalamadır.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemin şu anda bayt (Özel bayt) olarak ayırdığı ortalama sanal bellek miktarını bildirir. Özel baytlar, yalnızca işlem içinde çalışan iş parçacıkları tarafından erişilebilen işlem tarafından ayrılan sanal bellek konumlarını temsil eder.

 32 bit makinede çalışan 32 bit işlemler için, işlem adres alanının özel bölümünün üst sınırı 2 GB'dır. [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini anahtarını kullanarak 32 bit işlemleri 3 GB'a kadar sanal bellek elde edebilir. 64 bit makinede çalışan 32 bit işlem, 4 GB'a kadar özel sanal bellek elde edebilir.

 64 bit makinede çalışan 64 bit işlem, 8 TB'a kadar özel sanal bellek elde edebilir.

 Bildirilen değer, profillenen işlemin etkin olduğu tüm ölçüm aralıklarının ortalamasıdır.

 İşlem adres alanları hakkında daha fazla bilgi için Windows Bellek Yönetimi belgelerinde [Sanal Adres Alanı'na](/windows/win32/memory/virtual-address-space) bakın.

## <a name="how-to-use-rule-data"></a>Kural verileri nasıl kullanılır?
 Farklı sürümlerin veya programın yapılarının performansını karşılaştırmak veya farklı profil oluşturma senaryoları altında uygulamanın performansını anlamak için bildirilen değeri kullanın.
