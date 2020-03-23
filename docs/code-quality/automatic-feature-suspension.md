---
title: Otomatik özelliği askıya alma
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- live code analysis
- background analysis
- analysis scope
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8480eb57a08905c2a593adbab519ae793638888
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431247"
---
# <a name="automatic-feature-suspension"></a>Otomatik özelliği askıya alma

Kullanılabilir sistem belleğiniz 200 MB veya daha az düşerse, Visual Studio kod düzenleyicisinde aşağıdaki iletiyi görüntüler:

![Tam çözüm çözümlemesi askıya alma metni](../code-quality/media/fsa_alert.png)

Visual Studio düşük bir bellek durumu algıladığında, sabit kalmasına yardımcı olmak için bazı gelişmiş özellikleri otomatik olarak askıya akarar. Visual Studio eskisi gibi çalışmaya devam ediyor, ancak performansı bozulur.

Düşük bellek durumunda, aşağıdaki eylemler gerçekleşir:

- Visual C# ve Visual Basic için canlı kod analizi minimum kapsama indirgenir.

- Visual C# ve Visual Basic için [Çöp Toplama](/dotnet/standard/garbage-collection/index) (GC) düşük gecikme modu devre dışı bırakılır.

- Visual Studio önbellekleri kızartılır.

## <a name="improve-visual-studio-performance"></a>Visual Studio performansını artırın

Büyük çözümler veya düşük bellek koşullarıyla uğraşırken Visual Studio performansını nasıl artırılanız ile ilgili ipuçları ve püf noktaları [için, büyük çözümler için Performans](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)hususları'na bakın.

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Canlı kod analizi minimum kapsama indirgenir

Varsayılan olarak, canlı kod çözümlemesi açık belgeler ve projeler için yürütür. Bu çözümleme kapsamını geçerli belgeye indirgenecek veya tüm çözüme yükseltilecek şekilde özelleştirebilirsiniz. Daha fazla bilgi için [bkz: Yönetilen kod için canlı kod çözümlemesi kapsamını yapılandırma.](./configure-live-code-analysis-scope-managed-code.md) Düşük bellek durumunda, Visual Studio canlı analiz kapsamını geçerli belgeye indirgenmeye zorlar. Ancak, görüntülendiğinde bilgi çubuğundaki **Yeniden etkinleştir** düğmesini seçerek veya Visual Studio'yu yeniden başlatarak tercih ettiğiniz analiz kapsamını yeniden etkinleştirebilirsiniz. Seçenekler iletişim kutusu her zaman geçerli canlı kod çözümleme kapsam ayarlarını gösterir.

## <a name="gc-low-latency-disabled"></a>GC düşük gecikmeli devre dışı

GC düşük gecikme modunu yeniden etkinleştirmek için Visual Studio'yı yeniden başlatın. Varsayılan olarak Visual Studio, yazmanızın herhangi bir GC operasyonunu engellemediğinden emin olmak için her yazdığınızda GC düşük gecikme moduna olanak tanır. Ancak, düşük bellek durumu Visual Studio'nun otomatik süspansiyon uyarısını görüntülemesine neden oluyorsa, GC düşük gecikme modu bu oturum için devre dışı bırakılır. Visual Studio'yu yeniden başlatmak varsayılan GC davranışını yeniden etkinleştirir. Daha fazla bilgi için bkz. <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio önbellekleri kızartılmış

Geçerli geliştirme oturumunuza devam ederseniz veya Visual Studio'yu yeniden başlatırsanız, tüm Visual Studio önbellekleri hemen boşaltılır, ancak yeniden doldurulmaya başlar. Sifonlanan önbellekler aşağıdaki özellikler için önbellekleri içerir:

- Tüm referansları bulun

- Gezinme

- Kullanma Ekle

Buna ek olarak, dahili Visual Studio işlemleri için kullanılan önbellekler de temizlenir.

> [!NOTE]
> Otomatik özellikli süspansiyon uyarısı, oturum başına değil, çözüm başına yalnızca bir kez gerçekleşir. Bu, Visual Basic'ten Visual C# (veya tam tersi) geçiş yapıp başka bir düşük bellek koşuluyla karşılaştığınızda, başka bir otomatik özellik süspansiyon uyarısı alabileceğiniz anlamına gelir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapilir: Yönetilen kod için canlı kod çözümleme kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md)
- [Atık Toplamanın Temelleri](/dotnet/standard/garbage-collection/fundamentals)
- [Büyük çözümler için performans konuları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)
