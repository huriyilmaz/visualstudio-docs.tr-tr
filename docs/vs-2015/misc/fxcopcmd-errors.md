---
title: FxCopCmd hataları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3e0770654f564c57cf576666dcd9575f47d9ce1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787280"
---
# <a name="fxcopcmd-errors"></a>FxCopCmd Hataları
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
  
 Çözümleme hatası, önemli hatalar için döndürülür. Çözümlemenin tamamlanamayacağını gösterir. Uygun olduğunda, hata kodu önemli hatanın temel nedenini de içerir. Aşağıdaki koşullar önemli hatalar üretir:  
  
- Analiz, yetersiz giriş nedeniyle gerçekleştirilemedi.  
  
- Analiz, FxCopCmd tarafından işlenmeyen bir özel durum oluşturdu.  
  
- Belirtilen proje dosyası bulunamadı veya bozuk.  
  
- Çıkış seçeneği belirtilmemiş veya dosya yazılamadı.  
  
    > [!NOTE]
    > FxCopCmd dönüş kodu "derleme başvuruları hatası" 0x200 tek başına bir hata değil uyarısı. Bu dönüş kodu eksik dolaylı başvuruların bulunduğunu, ancak FxCopCmd 'nin bunları işleyebileceğini gösterir. Bazı analiz sonuçlarının riskli olabileceğini bildiren bir uyarıdır. "Derleme başvuruları hatası" nı, başka bir dönüş koduyla birleştirildiğinde hata olarak döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kod Analizi uygulama hataları](../code-quality/code-analysis-application-errors.md)