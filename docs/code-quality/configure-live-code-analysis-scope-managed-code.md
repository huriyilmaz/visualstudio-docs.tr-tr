---
title: .NET için canlı kod analizi kapsamını yapılandırma
ms.date: 09/01/2020
description: Visual Studio 'da arka plan analizi hakkında bilgi edinin. Bkz. analizi, görünür belge, tüm açık belgeler veya tüm dosya ve projeler ile sınırlama.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 7a6a7253d4104fbcde09b96b86f5f83a864677cf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860405"
---
# <a name="configure-live-code-analysis-for-net"></a>.NET için Canlı Kod analizini yapılandırma

Visual Studio, düzenleyicide kaynak dosyaları düzenlediğinizde *arka plan Analizi* olarak da adlandırılan, bir dizi Canlı Kod analizini yürütür. Bir kısmı, kabul edilebilir bir Visual Studio IDE düzenlemesi deneyimi için en az analiz gerektirir. Bazıları IDE özellikleri için iyileştirilmiş yanıt verme içindir. Bu bir nedenle, Roslyn çözümleyicilerinin tanılama ve kod düzeltmeleri gibi ek IDE işlevlerini etkinleştirmektir. İşlevlere bağlı olarak, bu çözümlemeler aşağıdaki gibi gruplandırılabilir:

- **Tanılama arka plan hesaplama**: kaynak dosyalardaki hataları, uyarıları ve önerileri hesaplamak için analiz. Bu Tanılamalar, hata listesinde ve düzenleyicide dalgalı çizgiler olarak giriş gösterir. Bunlar iki kategoride sınıflandırılabilirler:
  - C# ve Visual Basic derleyici tanılaması
  - Şunları içeren Roslyn Çözümleyicisi tanılaması:

    - Kod stili önerileri için yerleşik IDE Çözümleyicileri
    - Kod kalitesi önerileri için yerleşik CA Çözümleyicileri
    - Geçerli çözümdeki projeler için [yüklenen](./install-roslyn-analyzers.md) üçüncü taraf çözümleyici paketleri.

- **Diğer arka plan analizleri**: IDE özelliklerine yönelik yanıt verme ve Visual Studio etkileşimini artırmaya yönelik analiz. Bu analizler için bazı örnekler şunlardır:
  - Açık dosyaları arka planda ayrıştırma.
  - Belirli IDE özelliklerinde iyileştirilmiş yanıt verme için sembolleri gerçekleştirmek üzere açık dosyaları olan projelerin arka plan derlenmesi.
  - Sözdizimi ve sembol önbellekleri oluşturma.
  - Formlar, denetimler vb. kaynak dosyaları için tasarımcı ilişkilendirmesi algılanıyor.

## <a name="default-analysis-scope"></a>Varsayılan analiz kapsamı

Varsayılan olarak, Visual Studio 'da _açılan_ tüm dosyalar için tanılama 'nın arka plan hesaplama için canlı kod analizi yürütülür. Yukarıda belirtilen _diğer arka plan analizlerinin_ birkaçı, en az bir açık dosya içeren tüm projeler için yürütülür. Tüm çözüm için birkaç arka plan analizleri yürütüyoruz.

## <a name="custom-analysis-scope"></a>Özel analiz kapsamı

Her bir arka plan analizinin varsayılan kapsamı, çoğu müşteri senaryosu ve çözümü için en iyi kullanıcı deneyimi, işlevselliği ve performansı için ayarlanmıştır. Ancak, müşterilerin arka plan analizini azaltmak veya artırmak üzere bu kapsamı özelleştirmek isteyebileceğiniz durumlar vardır. Örneğin:

- Güç tasarrufu modu: kullanıcılar dizüstü pille çalışıyorsa, daha uzun pil ömrü için güç tüketimini en aza indirmek isteyebilir. Bu senaryoda, arka plan analizini en aza indirmek istiyoruz.
- İsteğe bağlı kod analizi: kullanıcılar gerçek zamanlı çözümleyici yürütmeyi kapatmayı ve isteğe bağlı kod analizini el ile çalıştırmayı tercih ediyorsanız, arka plan analizini en aza indirmek istedikleri olur. Bkz. [nasıl yapılır: isteğe bağlı kod analizini el ile çalıştırma](./how-to-run-code-analysis-manually-for-managed-code.md).
- Tam çözüm Analizi: kullanıcılar, düzenleyicide açık olup olmadıkları bağımsız olarak, Çözümdeki tüm dosyalardaki tüm tanılamayı her zaman görmek istiyorlarsa. Bu senaryoda, tüm çözüme arka plan Analizi kapsamını en üst düzeye çıkarmak istiyoruz.

Visual Studio 2019 sürüm 16,5 ' den başlayarak, kullanıcılar C# ve Visual Basic projeleri için tanılama hesaplaması dahil olmak üzere tüm canlı kod analizinin kapsamını açıkça özelleştirebilir. Kullanılabilir analiz kapsamları şunlardır:

- **Geçerli belge**: yalnızca düzenleyicideki geçerli veya görünür dosya için yürütmek üzere canlı kod analizi kapsamını en aza indirir.
- **Açık belgeler**: Yukarıdaki bölümde açıklandığı gibi, varsayılan canlı kod analizi kapsamı.
- Tüm **çözüm**: tüm çözüm içindeki tüm dosyalar ve projeler için yürütülecek canlı kod analizi kapsamını en üst düzeye çıkarır.

Aşağıdaki adımları izleyerek, Araçlar Seçenekler iletişim kutusunda Yukarıdaki özel analiz kapsamları arasından birini seçebilirsiniz:

1. **Seçenekler** iletişim kutusunu açmak için, Visual Studio 'daki menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Seçenekler** iletişim kutusunda **metin düzenleyici**  >  **C#** veya **temel**  >  **Gelişmiş**' i seçin.

3. Analiz kapsamını özelleştirmek için istenen **arka plan Analizi kapsamını** seçin. İşiniz bittiğinde **Tamam ' ı** seçin.

![Analiz kapsamı.](./media/background-analysis-scope.png)

> [!NOTE]
> Kullanıcılar, Visual Studio 2019 sürüm 16,5 ' den önce, **Araçlar** Seçenekler metin Düzenleyicisi   >    >    >  **C#** veya **temel**  >  **Gelişmiş** sekmesinden tam çözüm analizini etkinleştir onay kutusunu kullanarak tüm çözüme tanılama hesaplaması için analiz kapsamını özelleştirebilir. Önceki Visual Studio sürümlerindeki arka plan Analizi kapsamını en aza indirme desteği yoktur.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Canlı Kod Analizi kapsamını otomatik olarak Küçült

Visual Studio 200 MB veya daha az sistem belleği olduğunu algılarsa, canlı kod analizi kapsamını "geçerli belge" olarak en aza indirir. Bu gerçekleşirse, Visual Studio 'Nun bazı özellikleri devre dışı bırakıldığını bildiren bir uyarı görüntülenir. Bir düğme isterseniz, önceki Analiz kapsamına geri geçiş yapmanızı sağlar.

![Uyarı metni simge durumuna küçültme analiz kapsamı](./media/fsa_alert.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik özelliği askıya alma](./automatic-feature-suspension.md)
- [Güç tasarrufu modu özellik isteği](https://github.com/dotnet/roslyn/issues/38429)
