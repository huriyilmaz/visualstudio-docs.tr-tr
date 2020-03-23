---
title: 'DA0030: Veritabanı projeleri için Katman Etkileşimölçümleri Toplama | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0030
- vs.performance.rules.DA0030
- vs.performance.30
ms.assetid: 42b2f69d-0cfa-4854-82c4-589c3d8b4557
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 26b0905882ef8ec2e3fcddc4cf699ecae7dbe7a4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777482"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: Veritabanı projeleri için katman etkileşim ölçümleri toplama

|||
|-|-|
|Kural Id|DA0030|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|Çok katmanlı uygulamalar için etkileşim ölçümleri toplamak, veritabanı kullanım modellerini ve önemli veri erişim gecikmelerini anlamanıza yardımcı olur. Katman Etkileşimi Profil oluşturma seçeneği etkinken uygulamayı yeniden profil oluşturmayı deneyin.|
|Kural türü|Bilgi|

## <a name="cause"></a>Nedeni
 Yöntemlere <xref:System.Data> yapılan çağrılar profil oluşturma verilerinin önemli bir kısmıdır ve profil oluşturma çalışmasında katman etkileşim verileri toplamadınız. Yeniden profil oluşturmayı ve katman etkileşim verileri eklemeyi düşünün.

## <a name="rule-description"></a>Kural açıklaması
 System.Data ad alanlarında bulunan işlevlerde önemli bir etkinlik olduğunda bu kural <xref:System.Data.Linq> <xref:System.Data.Linq>yanar.

 Çok katmanlı uygulamalar, sunumları ve veri katmanları için katmanlı hizmetler kullanır. Genellikle veri katmanı, Microsoft SQL Server gibi bir veritabanı yönetim sistemini çalıştıran ayrı bir işlemdir. Veri katmanı, uygulamanın geri kalanından ayrı bir makinede çalışıyor olabilir. Örnekleme profilleri, işlem dışı veya uzaktan çalışan işlevler ve hizmetler hakkında çok az bilgi sağlar.

 Profil oluşturma araçları, ADO.NET hizmetlerine asynchronous çağrıları kullanarak Microsoft SQL Server veri katmanıyla etkileşimde bulunan çok katmanlı uygulamalar için zamanlama bilgileri toplayabilir. Katman Etkileşimi Profil oluşturmayı açıkça etkinleştirmelisiniz. Varsayılan olarak açık değil.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 Bu kural yalnızca bilgi içindir ve düzeltici eylem gerektirmeyebilir.

 Visual Studio IDE'deki profil oluşturma verilerine katman etkileşim verilerinin nasıl eklendirilen [Collect tier interaction data](../profiling/collecting-tier-interaction-data.md)hakkında bilgi için bkz. Komut satırından katman etkileşim verilerinin nasıl ekleyebileceği hakkında bilgi [için](../profiling/adding-tier-interaction-data-from-the-command-line.md)bkz.
