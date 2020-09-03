---
title: FxCopCmd hataları
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b72f419331b2a02c55d885a2b8855070698879a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "78167617"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd aracı hataları

FxCopCmd tüm hataları önemli olarak kabul etmez. FxCopCmd ' nin kısmi analiz gerçekleştirmek için yeterli bilgileri varsa, Analizi gerçekleştirir ve oluşan hataları raporlar. 32 bitlik bir tamsayı olan hata kodu, hatalara karşılık gelen sayısal değerlerin bit düzeyinde birleşimini içerir.

Aşağıdaki tabloda, FxCopCmd tarafından döndürülen hata kodları açıklanmaktadır:

|Hata|Sayısal değer|
|-----------|-------------------|
|Hata yok|'dır|
|Analiz hatası|0x1|
|Kural özel durumları|0x2|
|Proje yükleme hatası|4,|
|Derleme yükleme hatası|0x8|
|Kural kitaplığı yükleme hatası|0x10|
|Rapor yükleme hatasını içeri aktar|0x20|
|Çıkış hatası|0x40|
|Komut satırı anahtar hatası|0x80|
|Başlatma hatası|0x100|
|Derleme başvuruları hatası|0x200|
|BuildBreakingMessage|0x400|
|Bilinmeyen hata|0x1000000|

Önemli hatalar için **çözümleme hatası** döndürüldü. Çözümlemenin tamamlanamayacağını gösterir. Uygun olduğunda, hata kodu önemli hatanın temel nedenini de içerir. Aşağıdaki koşullar önemli hatalar üretir:

- Yetersiz giriş nedeniyle analiz gerçekleştirilemedi.

- Analiz, FxCopCmd tarafından işlenmeyen bir özel durum oluşturdu.

- Belirtilen proje dosyası bulunamadı veya bozuk.

- Çıkış seçeneği belirtilmemiş veya dosya yazılamadı.

> [!NOTE]
> FxCopCmd dönüş kodu **derleme** hatası 0x200 bir hata yerine bir uyarı. Bu dönüş kodu, dolaylı başvuruların eksik olduğunu, ancak FxCopCmd 'nin bunları işleyebildiğini gösterir. Uyarı, bazı analiz sonuçlarının tehlikeye girmiş olabileceğini belirten bir olasılık anlamına gelir. **Derleme başvuruları hatasını** , başka bir dönüş koduyla birleştirildiğinde hata olarak değerlendirin.

## <a name="see-also"></a>Ayrıca bkz.

- [Kod Analizi uygulama hataları](../code-quality/code-analysis-application-errors.md)
