---
title: DA0030 - Veritabanı projeleri için Katman Etkileşimi ölçümlerini | Microsoft Docs
description: System.Data yöntemlerine yapılan çağrılar, profil oluşturma verilerinin önemli bir oranıdır ve profil oluşturma çalıştırması içinde katman etkileşim verileri toplamaz. Yeniden profil oluşturmayı ve katman etkileşim verileri eklemeyi göz önünde bulundurabilirsiniz.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: de0de156ecd959671394679a30912f24a5aaaaf5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635785"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Veritabanı projeleri için katman etkileşim ölçümlerini toplama

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0030|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|Çok katmanlı uygulamalar için etkileşim ölçümleri toplamak, veritabanı kullanım düzenlerini ve önemli veri erişim gecikmelerini anlamanıza yardımcı olur. Katman Etkileşim Profili Oluşturma seçeneği etkinken uygulamanın profilini oluşturmayı yeniden deneyin.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Yöntemlere yapılan çağrılar profil oluşturma verilerinin önemli bir oranıdır ve profil oluşturma çalıştırması içinde katman <xref:System.Data> etkileşim verilerini toplamaz. Yeniden profil oluşturmayı ve katman etkileşim verileri eklemeyi göz önünde bulundurabilirsiniz.

## <a name="rule-description"></a>Kural açıklaması
 Bu kural, dahil olmak üzere System.Data ad alanlarında bulunan işlevlerde önemli bir etkinlik olduğunda <xref:System.Data.Linq> <xref:System.Data.Linq> oluşur.

 Çok katmanlı uygulamalar, sunum ve veri katmanları için katmanlı hizmetler kullanır. Veri katmanı genellikle veri katmanı gibi bir veritabanı yönetim sistemi çalıştıran ayrı bir Microsoft SQL Server. Veri katmanı, uygulamanın geri kalanından ayrı bir makinede bile çalışıyor olabilir. Örnekleme profilleri, işlem yetersiz veya uzaktan çalışan işlevler ve hizmetler hakkında çok az içgörü sağlar.

 Profil oluşturma araçları, bir Microsoft SQL Server veri katmanıyla etkileşime Microsoft SQL Server hizmetleri için zaman uyumsuz çağrılar kullanarak çok katmanlı uygulamalar için zamanlama ADO.NET toplar. Katman Etkileşim Profili Oluşturmayı açıkça etkinleştirmeniz gerekir. Varsayılan olarak açık değildir.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Bu kural yalnızca bilgi içindir ve düzeltici eylem gerektirmeyebilirsiniz.

 IDE'den profil oluşturma verilerine katman etkileşim verileri ekleme hakkında Visual Studio için [bkz. Katman etkileşim verilerini toplama.](../profiling/collecting-tier-interaction-data.md) Komut satırına katman etkileşim verileri ekleme hakkında bilgi için [bkz. Katman etkileşim verilerini toplama.](../profiling/adding-tier-interaction-data-from-the-command-line.md)
