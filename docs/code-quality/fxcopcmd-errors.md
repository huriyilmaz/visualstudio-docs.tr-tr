---
title: FxCopCmd hataları
ms.date: 10/19/2016
description: FxCopCmd komutunun döndüren hata kodları hakkında bilgi edinebilirsiniz. Her kodun hangi hata türünü temsil ettiğine bakın ve önemli hataların nasıl tanındığını bulun.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: c06c996245dfba796d4ab7e71fdbb28ad486f017
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098040"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd aracı hataları

FxCopCmd tüm hataların önemli olduğunu düşünmez. FxCopCmd kısmi analiz gerçekleştirmek için yeterli bilgiye sahipse, analizi gerçekleştirir ve oluşan hataları raporlar. 32 bit tamsayı olan hata kodu, hatalara karşılık gelen sayısal değerlerin bit olarak bir bileşimini içerir.

Aşağıdaki tabloda FxCopCmd tarafından döndürülen hata kodları açıklandı:

|Hata|Sayısal değer|
|-----------|-------------------|
|Hata yok|0x0|
|Analiz hatası|0x1|
|Kural özel durumları|0x2|
|Project hatası|0x4|
|Derleme yükleme hatası|0x8|
|Kural kitaplığı yükleme hatası|0x10|
|Raporu içeri aktarma yükleme hatası|0x20|
|Çıkış hatası|0x40|
|Komut satırı anahtarı hatası|0x80|
|Başlatma hatası|0x100|
|Derleme başvuruları hatası|0x200|
|BuildBreakingMessage|0x400|
|Bilinmeyen hata|0x1000000|

**Önemli hatalar** için analiz hatası döndürülür. Analizin tamamlanamadı olduğunu gösterir. Uygun olduğunda, hata kodu önemli hatanın temel nedenini de içerir. Aşağıdaki koşullar önemli hatalar üretir:

- Yetersiz giriş nedeniyle analiz gerçekleştirilmedi.

- Analiz FxCopCmd tarafından işlen bir özel durum oluşturdu.

- Belirtilen proje dosyası bulunamadı veya bozuk.

- Çıkış seçeneği belirtilmedi veya dosya yazılamdı.

> [!NOTE]
> FxCopCmd dönüş kodu **Derlemesi hataya** başvurur 0x200 tek başına bir hata değil uyarıdır. Bu dönüş kodu eksik dolaylı başvurular olduğunu ama FxCopCmd'nin bunları işleye olduğunu gösterir. Uyarı, bazı analiz sonuçlarının tehlikeye atılmış olma olasılığının olduğu anlamına gelir. Derleme **başvuruları hatasını,** başka bir dönüş koduyla birleştirildiklerine bir hata olarak davran.

## <a name="see-also"></a>Ayrıca bkz.

- [Code Analysis Uygulama Hataları](../code-quality/code-analysis-application-errors.md)
