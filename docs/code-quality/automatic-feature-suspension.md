---
title: Otomatik özelliği askıya alma
ms.date: 11/04/2016
description: analiz kapsamını Visual Studio nasıl azalttığını, çöp toplama düşük gecikme süresi modunu kapatır ve sistem belleği sınırlı olduğunda önbellekleri temizler.
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
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 0a1791f02264a4e6a32976ef8975375196054b2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122053285"
---
# <a name="automatic-feature-suspension"></a>Otomatik özelliği askıya alma

kullanılabilir sistem belleğiniz 200 MB veya daha az kalırsa, Visual Studio kod düzenleyicisinde aşağıdaki iletiyi görüntüler:

![Tam çözüm analizini askıya alarak uyarı metni](../code-quality/media/fsa_alert.png)

Visual Studio düşük bir bellek koşulu algıladığında, bu, kalıcı kalmasını sağlamak için belirli gelişmiş özellikleri otomatik olarak askıya alır. Visual Studio daha önce olduğu gibi çalışmaya devam eder, ancak performansı düşer.

Düşük bellek koşulunda aşağıdaki işlemler gerçekleşir:

- Visual C# ve Visual Basic için canlı kod analizi, en az sayıda kapsama indirgenecek.

- Visual C# için [çöp toplama](/dotnet/standard/garbage-collection/index) (GC) düşük gecikme modu ve Visual Basic devre dışı bırakıldı.

- Visual Studio önbellekler temizlenir.

## <a name="improve-visual-studio-performance"></a>Visual Studio performansını iyileştirme

büyük çözümlerle veya düşük bellek koşullarına uyrken Visual Studio performansının nasıl iyileştirecağıyla ilgili ipuçları ve püf noktaları için bkz. [büyük çözümler için performans konuları](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md).

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Canlı Kod Analizi, en az sayıda kapsama indirgenmiş

Varsayılan olarak, açık belgeler ve projeler için canlı kod analizi yürütülür. Bu analiz kapsamını, geçerli belgeye indirgenecek veya tüm çözüme artmış olacak şekilde özelleştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: yönetilen kod için canlı kod analizi kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md). düşük bellek durumunda Visual Studio, canlı analiz kapsamını geçerli belgeye indirgenmeye zorlar. Ancak, görüntülenen bilgi çubuğundaki veya Visual Studio yeniden başlatarak **yeniden etkinleştir** düğmesini seçerek tercih ettiğiniz analiz kapsamını yeniden etkinleştirebilirsiniz. Seçenekler iletişim kutusu her zaman geçerli canlı kod analizi kapsam ayarlarını gösterir.

## <a name="gc-low-latency-disabled"></a>GC düşük gecikme süresi devre dışı

GC düşük gecikme modu modunu yeniden etkinleştirmek için Visual Studio yeniden başlatın. varsayılan olarak Visual Studio, yazılarınızın herhangi bir gc işlemini engellemediğinden emin olmak için her yazarken gc düşük gecikme süresi modunu sağlar. ancak, düşük bellek durumu Visual Studio otomatik askıya alma uyarısını görüntülemesine neden oluyorsa, GC düşük gecikme modu bu oturum için devre dışıdır. yeniden başlatma Visual Studio varsayılan GC davranışını yeniden etkinleştirilir. Daha fazla bilgi için bkz. <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio önbellekler temizlendi

geçerli geliştirme oturumunuza devam ederseniz veya Visual Studio yeniden başlatırsanız, tüm Visual Studio önbellekler hemen boşaltılır, ancak yeniden oluşturmaya başlar. Temizlenen önbellekler aşağıdaki özelliklere yönelik önbellekleri içerir:

- Tüm başvuruları bul

- Şuraya gidin

- Kullanarak Ekle

ayrıca, iç Visual Studio işlemler için kullanılan önbellekler da temizlenir.

> [!NOTE]
> Otomatik Özellik askıya alma uyarısı, her oturum için değil, her çözüm temelinde yalnızca bir kez gerçekleşir. bu, Visual Basic 'den Visual C# ' ye (veya tam tersi) geçiş yaptıysanız ve başka bir düşük bellek koşuluyla çalıştırırsanız, başka bir otomatik özellik askıya alma uyarısı elde edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: yönetilen kod için canlı kod analizi kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md)
- [Atık Toplamanın Temelleri](/dotnet/standard/garbage-collection/fundamentals)
- [Büyük çözümler için performans konuları](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
