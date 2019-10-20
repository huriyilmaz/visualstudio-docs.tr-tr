---
title: Otomatik özelliği askıya alma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dd399d78ac43085d89958ba358954f9e6cefe521
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606532"
---
# <a name="automatic-feature-suspension"></a>Otomatik özelliği askıya alma

Kullanılabilir sistem belleğiniz 200 MB veya daha az kalırsa, Visual Studio kod düzenleyicisinde şu iletiyi görüntüler:

![Tam çözüm analizini askıya alarak uyarı metni](../code-quality/media/fsa_alert.png)

Visual Studio düşük bellekli bir durum algıladığında, kararlı kalmasını sağlamak için bazı gelişmiş özellikleri otomatik olarak askıya alır. Visual Studio daha önce olduğu gibi çalışmaya devam eder, ancak performansı düşer.

Düşük bellek koşulunda aşağıdaki işlemler gerçekleşir:

- Görsel C# ve Visual Basic için tam çözüm Analizi devre dışı bırakıldı.

- Görsel C# ve Visual Basic Için [çöp toplama](/dotnet/standard/garbage-collection/index) (GC) düşük gecikme modu devre dışı.

- Visual Studio önbellekleri temizlendi.

## <a name="improve-visual-studio-performance"></a>Visual Studio performansını geliştirme

Büyük çözümlerle veya düşük bellek koşullarıyla çalışırken Visual Studio performansının nasıl iyileştirecağıyla ilgili ipuçları ve püf noktaları için bkz. [büyük çözümler Için performans konuları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Tam çözüm Analizi askıya alındı

Varsayılan olarak, tam çözüm Analizi Visual Basic için etkinleştirilmiştir ve görsel C#için devre dışı bırakılır. Ancak, düşük bellek koşulunda, Seçenekler iletişim kutusundaki ayarlarından bağımsız olarak hem Visual Basic hem de görsel C#için tam çözüm Analizi otomatik olarak devre dışıdır. Ancak, Seçenekler iletişim kutusunda **tam çözüm analizini etkinleştir** onay kutusunu seçerek veya Visual Studio 'yu yeniden başlatarak, görüntülenen bilgi çubuğundaki **yeniden etkinleştir** düğmesini seçerek tam çözüm analizini yeniden etkinleştirebilirsiniz. Seçenekler iletişim kutusu her zaman geçerli tam çözüm Analizi ayarlarını gösterir. Daha fazla bilgi için bkz. [nasıl yapılır: tam çözüm analizini etkinleştirme ve devre dışı bırakma](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC düşük gecikme süresi devre dışı

GC düşük gecikmeli modunu yeniden etkinleştirmek için Visual Studio 'Yu yeniden başlatın. Varsayılan olarak, yazılarınızın herhangi bir GC işlemini engellemediğinden emin olmak için her yazarken, Visual Studio GC düşük gecikme süresi modunu sağlar. Ancak, düşük bellek durumu Visual Studio 'Nun otomatik askıya alma uyarısını görüntülemesine neden oluyorsa, GC düşük gecikme modu bu oturum için devre dışıdır. Visual Studio 'Yu yeniden başlatmak için varsayılan GC davranışı etkinleştirilir. Daha fazla bilgi için bkz. <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio önbellekleri temizlendi

Geçerli geliştirme oturumunuza devam ederseniz veya Visual Studio 'yu yeniden başlatırsanız, tüm Visual Studio önbellekleri hemen boşaltılır, ancak yeniden oluşturmaya başlar. Temizlenen önbellekler aşağıdaki özelliklere yönelik önbellekleri içerir:

- Tüm başvuruları bul

- Şuraya gidin

- Kullanarak Ekle

Ayrıca, iç Visual Studio işlemleri için kullanılan önbellekler da temizlenir.

> [!NOTE]
> Otomatik Özellik askıya alma uyarısı, her oturum için değil, her çözüm temelinde yalnızca bir kez gerçekleşir. Bu, Visual Basic 'den görsele C# (veya tam tersi) geçiş yaptıysanız ve başka bir düşük bellek koşuluyla çalıştırırsanız, başka bir otomatik özellik askıya alma uyarısı elde edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Tam Çözüm Analizini Etkinleştirme ve Devre Dışı Bırakma](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Atık Toplamanın Temelleri](/dotnet/standard/garbage-collection/fundamentals)
- [Büyük çözümler için performans konuları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
