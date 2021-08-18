---
description: Bu ileti, işlem tarafından şu anda bayt cinsinden ayrılan en fazla sanal bellek miktarını (Özel bayt) raporlar.
title: DA0506 - İşlem için ayrılan en fazla Özel Bayt profili | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5daf5ad6b727014d63e77da848a94d31b36c3c4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142097"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Profili oluşturulan İşlem için ayırılmış En Yüksek Sayıda Özel Bayt

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0506|
|Kategori|Kaynak İzleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmış. İşlem Özel Bayt sayacı, profil oluşturmakta olan işlem tarafından ayrılan sanal belleği ölçür. Bildirilen değer, tüm ölçüm aralıklarında gözlemlenen en yüksek değerdir.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 10 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlem tarafından şu anda bayt cinsinden ayrılan en fazla sanal bellek miktarını (Özel bayt) raporlar. Özel baytlar, işlem tarafından yalnızca işlem içinde çalışan iş parçacıkları tarafından erişilebilen sanal bellek konumlarını temsil eder.

 32 bit makinede çalışan 32 bit işlemler için, işlem adres alanı özel bölümünün üst sınırı 2 GB'tır. [/3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini anahtarı kullanılarak, 32 bit işlemler 3 GB'a kadar sanal bellek edinebiliyor. 64 bit makinede çalışan 32 bit işlem, 4 GB'a kadar özel sanal bellek edinebiliyor.

 64 bit makinede çalışan 64 bit işlem, 8 TB'a kadar özel sanal bellek elde ediyor olabilir.

 Bildirilen değer, profili yapılan sürecin etkin olduğu tüm ölçüm aralıklarında en yüksek değerdir.

 İşlem adres alanları hakkında daha fazla bilgi için Bellek [Yönetimi belgelerinde](/windows/win32/memory/virtual-address-space) Windows Alanı'ne bakın.

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Programın farklı sürümlerinin veya derlemelerinin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için bildirilen değeri kullanın.

 Bir işlem adres alanı büyüyebilirsiniz mimari sınırına yaklaşan işlem özel bayt maksimum değeri yetersiz bellek özel durumlarına yol açabilirsiniz. Daha fazla bilgi için MSDN [Dergisi'nin Bellek](/archive/msdn-magazine/2006/november/clr-inside-out-investigating-memory-issues) Sorunlarını Araştırma makalesine bakın.
