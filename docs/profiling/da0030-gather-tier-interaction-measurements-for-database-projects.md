---
title: 'DA0030: veritabanı projeleri için katman etkileşim ölçümleri toplayın | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74777482"
---
# <a name="da0030-gather-tier-interaction-measurements-for-database-projects"></a>DA0030: veritabanı projeleri için katman etkileşim ölçümleri toplayın

|||
|-|-|
|Kural Kimliği|DA0030|
|Kategori|Profil Oluşturma Araçları kullanımı|
|Profil oluşturma yöntemi|Aşağıdakine|
|İleti|Çok katmanlı uygulamalar için etkileşim ölçümleri toplanması, veritabanı kullanım düzenlerini ve önemli veri erişimi gecikmelerini anlamanıza yardımcı olur. Katman etkileşimi profili oluşturma seçeneği etkinken uygulamayı yeniden oluşturmayı deneyin.|
|Kural türü|Bilgisi|

## <a name="cause"></a>Sebep
 <xref:System.Data> yöntemlere yapılan çağrılar, profil oluşturma verilerinin önemli bir oranlarından oluşur ve profil oluşturma çalıştırmasında katman etkileşim verilerini toplamamış olursunuz. Profil oluşturmayı yeniden deneyin ve katman etkileşim verileri ekleyin.

## <a name="rule-description"></a>Kural açıklaması
 Bu kural, <xref:System.Data.Linq><xref:System.Data.Linq>dahil olmak üzere System. Data ad alanlarında bulunan işlevlerde önemli etkinlik olduğunda ateşlenir.

 Çok katmanlı uygulamalar, sunum ve veri katmanları için katmanlı Hizmetleri kullanır. Veri katmanı genellikle Microsoft SQL Server gibi bir veritabanı yönetim sistemi çalıştıran ayrı bir işlemdir. Veri katmanı, uygulamanın geri kalanından ayrı bir makinede bile çalışıyor olabilir. Örnekleme profilleri, işlev ve hizmetlerin işlem dışı veya uzaktan çalışmasını çok daha fazla anlayış sağlar.

 Profil oluşturma araçları, ADO.NET hizmetlerine yönelik zaman uyumsuz çağrılar kullanılarak Microsoft SQL Server bir veri katmanıyla etkileşim kuran çok katmanlı uygulamalar için zamanlama bilgileri toplayabilir. Katman etkileşimi profili oluşturmayı açıkça etkinleştirmeniz gerekir. Varsayılan olarak açık değildir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 Bu kural yalnızca bilgi amaçlıdır ve düzeltici eylem gerektirmeyebilir.

 Visual Studio IDE 'den profil oluşturma verilerine katman etkileşim verileri ekleme hakkında daha fazla bilgi için bkz. [Katman etkileşimi verilerini toplama](../profiling/collecting-tier-interaction-data.md). Komut satırından katman etkileşim verileri ekleme hakkında daha fazla bilgi için bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).
