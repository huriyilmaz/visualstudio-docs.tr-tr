---
title: DA0505 - İşlem için ayrılan ortalama Özel Bayt sayısı | Microsoft Docs
description: Bu ileti, işlem tarafından şu anda bayt cinsinden ayrılan ortalama sanal bellek miktarını (Özel bayt) raporlar.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0505
- vs.performance.rules.DA0505
- vs.performance.505
ms.assetid: 32c612ea-d077-44ba-8e6f-3a96333bad00
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7c7eb5e36b511448e891c2ae38a960815d9875cb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142110"
---
# <a name="da0505-average-private-bytes-allocated-for-the-process-being-profiled"></a>DA0505: Profili oluşturulan İşlem için ayırılmış Ortalama Özel Baytlar

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0505|
|Kategori|Kaynak Yönetimi|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmış. İşlem Özel Bayt sayacı, profil oluşturmakta olan işlem tarafından ayrılan sanal belleği ölçür. Bildirilen değer, tüm ölçüm aralıklarında hesaplanan ortalama değerdir.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 10 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlem tarafından şu anda bayt cinsinden ayrılan ortalama sanal bellek miktarını (Özel bayt) raporlar. Özel baytlar, işlem tarafından yalnızca işlem içinde çalışan iş parçacıkları tarafından erişilebilen sanal bellek konumlarını temsil eder.

 32 bit makinede çalışan 32 bit işlemler için, işlem adres alanı özel bölümünün üst sınırı 2 GB'tır. [/3GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini anahtarı kullanılarak, 32 bit işlemler 3 GB'a kadar sanal bellek edinebiliyor. 64 bit makinede çalışan 32 bit işlem, 4 GB'a kadar özel sanal bellek edinebiliyor.

 64 bit makinede çalışan 64 bit işlem, 8 TB'a kadar özel sanal bellek elde ediyor olabilir.

 Bildirilen değer, profili yapılan sürecin etkin olduğu tüm ölçüm aralıklarının ortalamasıdır.

 İşlem adres alanları hakkında daha fazla bilgi için Bellek [Yönetimi belgelerinde](/windows/win32/memory/virtual-address-space) Windows Alanı'ne bakın.

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Programın farklı sürümlerinin veya derlemelerinin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için bildirilen değeri kullanın.
