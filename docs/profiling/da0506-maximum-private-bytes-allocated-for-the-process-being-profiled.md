---
title: 'DA0506: Profillendirilmek tesime ayrılan Maksimum Özel Bayt | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7600e65beb3035fac6d5ea58b25f6965d681f83a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779317"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: İşlem için izin verilen Maksimum Özel Bayt Sayısının profili oluşturuluyor

|||
|-|-|
|Kural Id|DA0506|
|Kategori|Kaynak İzleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmış. İşlem Özel Bayt karşı tevkici, profil oluşturma işlemi tarafından ayrılan sanal belleği ölçer. Bildirilen değer, tüm ölçüm aralıklarında gözlenen maksimum değerdir.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemin şu anda bayt (Özel bayt) olarak ayırdığı maksimum sanal bellek miktarını bildirir. Özel baytlar, yalnızca işlem içinde çalışan iş parçacıkları tarafından erişilebilen işlem tarafından ayrılan sanal bellek konumlarını temsil eder.

 32 bit makinede çalışan 32 bit işlemler için, işlem adres alanının özel bölümünün üst sınırı 2 GB'dır. [/3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini anahtarını kullanarak, 32 bit işlemler 3 GB'a kadar sanal bellek elde edebilir. 64 bit makinede çalışan 32 bit işlem, 4 GB'a kadar özel sanal bellek elde edebilir.

 64 bit makinede çalışan 64 bit işlem, 8 TB'a kadar özel sanal bellek elde edebilir.

 Bildirilen değer, profillenen işlemin etkin olduğu tüm ölçüm aralıkları üzerindeki maksimum değerdir.

 İşlem adres alanları hakkında daha fazla bilgi için Windows Bellek Yönetimi belgelerinde [Sanal Adres Alanı'na](/windows/win32/memory/virtual-address-space) bakın.

## <a name="how-to-use-rule-data"></a>Kural verileri nasıl kullanılır?
 Farklı sürümlerin veya programın yapılarının performansını karşılaştırmak veya farklı profil oluşturma senaryoları altında uygulamanın performansını anlamak için bildirilen değeri kullanın.

 Bir işlem adresi alanının ne kadar büyük büyüyebileceği mimari sınırına yaklaşan işlem özel baytlarının maksimum değeri bellek dışında özel durumlara yol açabilir. Daha fazla bilgi için MSDN Dergisi'ndeki [Bellek Sorunlarını Araştırma](https://msdn.microsoft.com/magazine/cc163528.aspx) konusuna bakın.
