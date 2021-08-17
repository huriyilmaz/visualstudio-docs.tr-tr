---
description: Bu ileti, işlemin Şu anda ayırdığı en fazla sanal bellek miktarını bayt (özel bayt) olarak bildirir.
title: DA0506-profili oluşturulan Işlem için ayrılan en fazla özel bayt sayısı | Microsoft Docs
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
ms.openlocfilehash: cb34ae103713df9867a633cdb2ac7e7c2985ef1c26e4c56057fdf673d13daade
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121333190"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Profili oluşturulan İşlem için ayırılmış En Yüksek Sayıda Özel Bayt

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0506|
|Kategori|Kaynak Izleme|
|Profil oluşturma yöntemi|Tümü|
|İleti|Bu bilgiler yalnızca bilgi için toplanmıştı. Işlem özel baytları sayacı, profil oluşturduğunuz işlem tarafından ayrılan sanal belleği ölçer. Bildirilen değer tüm ölçüm aralıklarında gözlemlenen en yüksek değerdir.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="rule-description"></a>Kural açıklaması
 Bu ileti, işlemin Şu anda ayırdığı en fazla sanal bellek miktarını bayt (özel bayt) olarak bildirir. Özel baytlar, işlem tarafından yalnızca işlem içinde çalışan iş parçacıklarının erişebileceği sanal bellek konumlarını temsil eder.

 32 bit makinede çalışan 32 bitlik işlemler için, işlem adres alanının özel bölümünün üst sınırı 2 GB 'dir. 32 bit işlem, [/3 gb](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) Boot.ini anahtarını kullanarak 3 GB 'a kadar sanal bellek alabilir. 64 bit makinede çalışan 32 bitlik bir işlem, 4 GB 'a kadar özel sanal bellek elde edebilir.

 64 bit makinede çalışan 64 bitlik bir işlem, 8 TB 'a kadar özel sanal belleği elde edebilir.

 Bildirilen değer, tüm ölçüm aralıklarının üzerinde profili oluşturulan işlemin etkin olduğu en fazla değerdir.

 işlem adres alanları hakkında daha fazla bilgi için, Windows bellek yönetimi belgelerindeki [sanal adres alanı](/windows/win32/memory/virtual-address-space) ' na bakın.

## <a name="how-to-use-rule-data"></a>Kural verilerini kullanma
 Bildirilen değeri, programın farklı sürümlerinin veya derlemelerin performansını karşılaştırmak veya farklı profil oluşturma senaryolarında uygulamanın performansını anlamak için kullanın.

 İşlem adres alanının büyük bir bölümünü büyümeye yönelik mimari sınırına yaklaştığı en yüksek işlem özel bayt değeri, bellek dışı özel durumlara neden olabilir. Daha fazla bilgi için bkz. MSDN Magazine 'te [bellek sorunlarını araştırma](/archive/msdn-magazine/2006/november/clr-inside-out-investigating-memory-issues) .
