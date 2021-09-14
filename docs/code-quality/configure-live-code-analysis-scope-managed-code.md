---
title: .NET için canlı kod analizi kapsamını yapılandırma
ms.date: 09/01/2020
description: Visual Studio'da arka plan analizi hakkında bilgi Visual Studio. Analizi görünür belge, tüm açık belgeler veya tüm dosya ve projelerle sınırlamaya bakın.
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
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 664d24c2732ee2c63475ac986fa9bbab78831493
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632054"
---
# <a name="configure-live-code-analysis-for-net"></a>.NET için canlı kod analizini yapılandırma

Visual Studio, düzenleyicide kaynak dosyalarını düzenlerken arka plan analizi olarak da adlandırılan bir grup canlı kod analizi yürütür. Bazı durumlarda kabul edilebilir bir IDE düzenleme deneyimi için Visual Studio az analiz gerekir. Bu özelliklerin bazıları IDE özellikleri için geliştirilmiş yanıt hızına sahiptir. Bazıları Roslyn çözümleyicilerinden gelen tanılama ve kod düzeltmeleri gibi ek IDE işlevlerini etkinleştirmektir. İşlevselliğe bağlı olarak, bu analizler aşağıdaki gibi gruplanabilir:

- **Tanılamanın arka plan hesaplaması:** Kaynak dosyalarda hataları, uyarıları ve önerileri hesaplamak için analiz. Bu tanılamalar, hata listesinde girdiler olarak ve düzenleyicide geçişler olarak görünür. İki kategoriye ayrılırlar:
  - C# ve Visual Basic derleyici tanılamaları
  - Roslyn çözümleyicisi tanılaması, şunları içerir:

    - Kod stili önerileri için yerleşik IDE çözümleyicileri
    - Kod kalitesi önerileri için yerleşik CA çözümleyicileri
    - Geçerli çözümde projeler [için yüklenmiş](./install-roslyn-analyzers.md) üçüncü taraf çözümleyici paketleri.

- **Diğer arka plan analizleri:** IDE özelliklerine yanıt verme hızını ve Visual Studio geliştirmek için analiz. Bu tür analizlere örnek olarak şu örnekler verilmiştir:
  - Açık dosyaların arka plan ayrıştırması.
  - Belirli IDE özelliklerinin daha iyi yanıt verme hızına yönelik sembolleri gerçekleştirmek için açık dosyalarla projelerin arka plan derlemesi.
  - Söz dizimi ve sembol önbellekleri bina.
  - Formlar, denetimler gibi kaynak dosyalar için tasarımcı ilişkilendirmesini algılama.

## <a name="default-analysis-scope"></a>Varsayılan analiz kapsamı

Varsayılan olarak, tanılamanın arka plan hesaplaması için canlı kod analizi, tanılamada açılan tüm dosyalar _için_ Visual Studio. Yukarıda bahsedilen _diğer arka plan analizlerinden_ birkaçı, en az bir açık dosyası olan tüm projeler için yürütülür. Çözümün tamamı için birkaç arka plan analizi yürütülür.

## <a name="custom-analysis-scope"></a>Özel analiz kapsamı

Her arka plan analizinin varsayılan kapsamı, müşteri senaryolarının ve çözümlerinin çoğu için en uygun kullanıcı deneyimi, işlevselliği ve performansı için ayarlanmıştır. Ancak müşterilerin arka plan analizini azaltmak veya artırmak için bu kapsamı özelleştirmek istemesi gereken durumlar vardır. Örnek:

- Güç tasarrufu modu: Kullanıcılar dizüstü bilgisayar pille çalıştırıyorsa, daha uzun pil ömrü için güç tüketimini en aza indirmek istiyor olabilir. Bu senaryoda arka plan analizini en aza indirmek ister.
- isteğe bağlı kod analizi: Kullanıcılar canlı çözümleyici yürütmeyi kapatmayı ve isteğe bağlı olarak kod analizini el ile çalıştırmayı tercih ederse arka plan analizini en aza indirmek ister. Bkz. [Nasıl yapılır: Kod analizini isteğe bağlı olarak el ile çalıştırma.](./how-to-run-code-analysis-manually-for-managed-code.md)
- Tam çözüm analizi: Kullanıcılar, düzenleyicide açık olup olmadığına bakılmaksızın çözümde yer alan tüm dosyalarda her zaman tüm tanılamaları görmek ister. Bu senaryoda, arka plan analizi kapsamını çözümün tamamına en üst düzeye çıkarmak ister.

2019 Visual Studio 16.5 sürümünden başlayarak, kullanıcılar C# ve Visual Basic projeleri için tanılama hesaplama dahil olmak üzere tüm canlı kod analizinin kapsamını açıkça özelleştirilebilir. Kullanılabilir analiz kapsamları:

- **Geçerli belge:** Canlı kod analizi kapsamını yalnızca düzenleyicide geçerli veya görünür dosya için yürütülecek şekilde en aza indirger.
- **Belgeleri açın:** Yukarıdaki bölümde açıklandığı gibi varsayılan canlı kod analizi kapsamı.
- **Çözümün tamamı:** Çözümün tamamına tüm dosya ve projeler için yürütülecek canlı kod analizi kapsamını en üst düzeye çıkartır.

Aşağıdaki adımları kullanarak Araçlar Seçenekleri iletişim kutusunda yukarıdaki özel analiz kapsamlarından birini seçebilirsiniz:

1. Seçenekler iletişim **kutusunu açmak** için, araç çubuğundaki menü çubuğunda Visual Studio Seçenekleri'ne   >  **tıklayın.**

2. Seçenekler iletişim **kutusunda Metin** Düzenleyici C# **veya Temel**  >   **Gelişmiş'i**  >  **seçin.**

3. Analiz kapsamını özelleştirmek **için istediğiniz Arka plan** analizi kapsamını seçin. **Bitirin** ve Tamam'ı seçin.

![Analiz kapsamı.](./media/background-analysis-scope.png)

> [!NOTE]
> 2019 Visual Studio 16.5 sürümünden önce kullanıcılar, Araçlar  Seçenekler Metin Düzenleyici C# veya Temel Gelişmiş sekmesindeki Tam çözüm analizini etkinleştir onay kutusunu kullanarak tanılama hesaplaması için analiz kapsamını çözümün tamamına  >    >    >     >   özelleştirilebilir. Önceki sürümlerde arka plan analizi kapsamını en aza indirme desteği Visual Studio yoktur.

## <a name="automatically-minimize-live-code-analysis-scope"></a>Canlı kod analizi kapsamını otomatik olarak en aza indirme

Bu Visual Studio 200 MB veya daha az sistem belleğinin kullanılabilir olduğunu algılarsa, canlı kod analizi kapsamını otomatik olarak "Geçerli Belge" olarak en aza indirger. Bu durumda, bazı özellikleri devre dışı bırakarak Visual Studio bir uyarı görüntülenir. Bir düğme, 2004'e geri dönmenizi sağlar.

![Analiz kapsamını en aza indiren uyarı metni](./media/fsa_alert.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik özelliği askıya alma](./automatic-feature-suspension.md)
- [Güç kaydetme modu özellik isteği](https://github.com/dotnet/roslyn/issues/38429)
