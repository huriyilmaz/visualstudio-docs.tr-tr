---
title: Yönetilen kod için canlı kod analizi kapsamını yapılandırma
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 300e3f276a45cfe2115311c7d27eedce365616cf
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432240"
---
# <a name="how-to-configure-live-code-analysis-scope-for-managed-code"></a>Nasıl yapilir: Yönetilen kod için canlı kod çözümleme kapsamını yapılandırma

## <a name="what-is-live-code-analysis-for-managed-code"></a>Yönetilen kod için "Canlı kod analizi" nedir?
Visual Studio, editörde kaynak dosyaları düzenlerken *arka plan çözümlemesi*olarak da adlandırılan bir dizi canlı kod analizini yürütür. Bazıları kabul edilebilir bir Visual Studio IDE düzenleme deneyimi için minimal analiz gereklidir. Bazıları IDE özellikleri için geliştirilmiş yanıt içindir. Bazıları Roslyn çözümleyicilerinden tanılama ve kod düzeltmeleri gibi ek IDE işlevselliği etkinleştirmek için olsa da. İşlevsellik durumuna bağlı olarak, bu analizler aşağıdaki gibi gruplandırılabilir:

- **Tanılamanın arka plan hesaplaması**: Kaynak dosyalardaki hataları, uyarıları ve önerileri hesaplamak için analiz. Bu tanılama, hata listesindeki girişler ve düzenleyicide dalgalı olarak gösteriş. Bunlar iki kategoriye ayırılabilir:
    - C# ve Visual Basic derleyici tanılama
    - Roslyn analizör tanılama, içerir:

        - Kod stili önerileri için yerleşik IDE çözümleyicileri ve
        - Geçerli çözümdeki projeler için [yüklenen](./install-roslyn-analyzers.md) üçüncü taraf çözümleyici paketleri.

- **Diğer arka plan analizleri**: IDE özellikleriiçin duyarlılık ve Visual Studio etkileşimini geliştirmek için analiz. Bu tür analizlere örnek olarak şunlar verilebilir:
    - Açık dosyaların arka plan ayrıştisi.
    - Belirli IDE özelliklerinin daha iyi yanıt verme özelliği ne kadar önemli simgeler gerçekleştirmek için açık dosyalara sahip projelerin arka plan derlemesi.
    - Sözdizimi ve sembol önbellekleri oluşturma.
    - Formlar, denetimler vb. gibi kaynak dosyalar için tasarımcı ilişkilendirme algılama

## <a name="default-analysis-scope"></a>Varsayılan analiz kapsamı

Varsayılan olarak, visual _studio'da açılan_ tüm dosyalar için tanılamanın arka plan hesaplaması için canlı kod çözümlemesi yürütülür. Yukarıda belirtilen _diğer arka plan analizlerinin_ birkaçı, en az bir açık dosyaya sahip olan tüm projeler için yürütülür. Birkaç arka plan analizleri tüm çözüm için yürütmek iken.

## <a name="custom-analysis-scope"></a>Özel analiz kapsamı

Her arka plan çözümlemesi varsayılan kapsamı, müşteri senaryolarının ve çözümlerinin çoğu için en iyi kullanıcı deneyimi, işlevselliği ve performansı için ayarlanmıştır. Ancak, müşterilerin arka plan çözümlemesi azaltmak veya artırmak için bu kapsamı özelleştirmek isteyebilirsiniz durumlar vardır. Örnek:

- Güç tasarrufu modu: Kullanıcılar dizüstü bilgisayar pili ile çalışıyorsa, daha uzun pil ömrü için güç tüketimini en aza indirmek isteyebilirler. Bu senaryoda, arka plan çözümlemesi en aza indirmek isteyebilirsiniz.
- İsteğe bağlı kod analizi: Kullanıcılar canlı çözümleyici yürütmeyi kapatmayı ve isteğe bağlı kod çözümlemesi manuel olarak çalıştırmayı tercih ederlerse, arka plan çözümlemesi en aza indirmek isterler. [Bkz. Nasıl: İsteğe bağlı kod çözümlemesi el ile çalıştırın.](./how-to-run-code-analysis-manually-for-managed-code.md)
- Tam çözüm analizi: Kullanıcılar, düzenleyicide açık olup olmadıklarına bakılmaksızın, çözümdeki tüm dosyalardaki tüm tanılamaları her zaman görmek istiyorlarsa. Bu senaryoda, tüm çözüm için arka plan çözümleme kapsamını en üst düzeye çıkarmak isteyebilirsiniz.

Visual Studio 2019 sürüm 16.5'ten başlayarak, kullanıcılar C# ve Visual Basic projeleri için tanılama hesaplaması da dahil olmak üzere tüm canlı kod analizlerinin kapsamını açıkça özelleştirebilirler. Kullanılabilir analiz kapsamları şunlardır:

- **Geçerli belge**: Yalnızca düzenleyicideki geçerli veya görünür dosyayı yürütmek için canlı kod çözümleme kapsamını en aza indirir.
- **Açık belgeler**: Yukarıdaki bölümde açıklandığı gibi varsayılan canlı kod analizi kapsamı.
- **Tüm çözüm**: Tüm çözümdeki tüm dosya ve projeler için yürütmek için canlı kod analizi kapsamını en üst düzeye çıkarır.

Aşağıdaki adımları izleyerek Araçlar Seçenekleri iletişim kutusunda yukarıdaki özel çözümleme kapsamlarından birini seçebilirsiniz:

1. **Seçenekler** iletişim kutusunu açmak için Visual Studio'daki menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

2. **Seçenekler** iletişim kutusunda Metin **Düzenleyicisi** > **C#** veya **Temel** > **Gelişmiş'i**seçin.

3. Çözümleme kapsamını özelleştirmek için istediğiniz **Arka Plan çözümleme kapsamını** seçin. Bitirdiğinde **Tamam'ı** seç.

![Analiz kapsamı.](./media/background-analysis-scope.png)

> [!NOTE]
> Visual Studio 2019 sürüm 16.5'ten önce, kullanıcılar **Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **C#** veya **Temel** > **Gelişmiş** sekmesinden tam çözüm analizi **ni etkinleştir** onay kutusunu kullanarak tanılama hesaplaması için analiz kapsamını tüm çözüme özelleştirebilirler. Önceki Visual Studio sürümlerinde arka plan çözümlemesi kapsamını en aza indirmek için destek yoktur.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Canlı kod analizi kapsamını otomatik olarak en aza indirir

Visual Studio 200 MB veya daha az sistem belleği kullanılabilir olduğunu algılarsa, canlı kod çözümleme kapsamını "Geçerli Belge"ye otomatik olarak en aza indirir. Bu durumda, Visual Studio'nun bazı özellikleri devre dışı bırakıldığını bildiren bir uyarı görüntülenir. Bir düğme, isterseniz önceki çözümleme kapsamına geri dönmenizi sağlar.

![Analiz kapsamını en aza indiren uyarı metni](./media/fsa_alert.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik özelliği askıya alma](./automatic-feature-suspension.md)
- [Güç tasarrufu modu özelliği isteği](https://github.com/dotnet/roslyn/issues/38429)
