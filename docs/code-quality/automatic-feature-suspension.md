---
title: Otomatik özelliği askıya alma
ms.date: 11/04/2016
description: Visual Studio 'Nun analiz kapsamını nasıl azalttığını, çöp toplama düşük gecikme süresi modunu kapattığını ve sistem belleği sınırlı olduğunda önbellekler temizlenmesini öğrenin.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12b15ed8aa02e53841b85245350735258e7ec11d
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348547"
---
# <a name="automatic-feature-suspension"></a>Otomatik özelliği askıya alma

Kullanılabilir sistem belleğiniz 200 MB veya daha az kalırsa, Visual Studio kod düzenleyicisinde şu iletiyi görüntüler:

![Tam çözüm analizini askıya alarak uyarı metni](../code-quality/media/fsa_alert.png)

Visual Studio düşük bellekli bir durum algıladığında, kararlı kalmasını sağlamak için bazı gelişmiş özellikleri otomatik olarak askıya alır. Visual Studio daha önce olduğu gibi çalışmaya devam eder, ancak performansı düşer.

Düşük bellek koşulunda aşağıdaki işlemler gerçekleşir:

- Visual C# ve Visual Basic için canlı kod analizi, en az sayıda kapsama indirgenecek.

- Visual C# için [çöp toplama](/dotnet/standard/garbage-collection/index) (GC) düşük gecikme modu ve Visual Basic devre dışı bırakıldı.

- Visual Studio önbellekleri temizlendi.

## <a name="improve-visual-studio-performance"></a>Visual Studio performansını geliştirme

Büyük çözümlerle veya düşük bellek koşullarıyla çalışırken Visual Studio performansının nasıl iyileştirecağıyla ilgili ipuçları ve püf noktaları için bkz. [büyük çözümler Için performans konuları](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Canlı Kod Analizi, en az sayıda kapsama indirgenmiş

Varsayılan olarak, açık belgeler ve projeler için canlı kod analizi yürütülür. Bu analiz kapsamını, geçerli belgeye indirgenecek veya tüm çözüme artmış olacak şekilde özelleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod için canlı kod analizi kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md). Düşük bellek koşulunda, Visual Studio canlı analiz kapsamını geçerli belgeye indirgenmeye zorlar. Ancak, veya Visual Studio 'Yu yeniden başlatarak, görüntülenen bilgi çubuğundaki **yeniden etkinleştir** düğmesini seçerek tercih ettiğiniz analiz kapsamını yeniden etkinleştirebilirsiniz. Seçenekler iletişim kutusu her zaman geçerli canlı kod analizi kapsam ayarlarını gösterir.

## <a name="gc-low-latency-disabled"></a>GC düşük gecikme süresi devre dışı

GC düşük gecikmeli modunu yeniden etkinleştirmek için Visual Studio 'Yu yeniden başlatın. Varsayılan olarak, yazılarınızın herhangi bir GC işlemini engellemediğinden emin olmak için her yazarken, Visual Studio GC düşük gecikme süresi modunu sağlar. Ancak, düşük bellek durumu Visual Studio 'Nun otomatik askıya alma uyarısını görüntülemesine neden oluyorsa, GC düşük gecikme modu bu oturum için devre dışıdır. Visual Studio 'Yu yeniden başlatmak için varsayılan GC davranışı etkinleştirilir. Daha fazla bilgi için bkz. <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio önbellekleri temizlendi

Geçerli geliştirme oturumunuza devam ederseniz veya Visual Studio 'yu yeniden başlatırsanız, tüm Visual Studio önbellekleri hemen boşaltılır, ancak yeniden oluşturmaya başlar. Temizlenen önbellekler aşağıdaki özelliklere yönelik önbellekleri içerir:

- Tüm başvuruları bul

- Şuraya gidin

- Kullanarak Ekle

Ayrıca, iç Visual Studio işlemleri için kullanılan önbellekler da temizlenir.

> [!NOTE]
> Otomatik Özellik askıya alma uyarısı, her oturum için değil, her çözüm temelinde yalnızca bir kez gerçekleşir. Bu, Visual Basic 'den Visual C# ' ye (veya tam tersi) geçiş yaptıysanız ve başka bir düşük bellek koşuluyla çalıştırırsanız, başka bir otomatik özellik askıya alma uyarısı elde edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: yönetilen kod için canlı kod analizi kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md)
- [Atık Toplamanın Temelleri](/dotnet/standard/garbage-collection/fundamentals)
- [Büyük çözümler için performans konuları](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
