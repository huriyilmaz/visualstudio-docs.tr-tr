---
title: Otomatik özelliği askıya alma
ms.date: 11/04/2016
description: Sistem Visual Studio azaltmayı, atık toplama düşük gecikme modunu kapatmayı ve sistem belleği sınırlı olduğunda önbellekleri boşaltmayı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632990"
---
# <a name="automatic-feature-suspension"></a>Otomatik özelliği askıya alma

Kullanılabilir sistem belleğiniz 200 MB veya daha azsa Visual Studio düzenleyicide aşağıdaki iletiyi görüntüler:

![Tam çözüm analizini askıya alan uyarı metni](../code-quality/media/fsa_alert.png)

Düşük Visual Studio durumu algılayan kullanıcılar, kararlı kalmaya yardımcı olmak için belirli gelişmiş özellikleri otomatik olarak askıya alır. Visual Studio daha önce olduğu gibi çalışmaya devam eder, ancak performansı düşer.

Yetersiz bellek durumunda aşağıdaki eylemler gerçekleştirin:

- Visual C# ve Visual Basic için canlı kod analizi minimum kapsama indirildi.

- [](/dotnet/standard/garbage-collection/index) Visual C# için Atık Toplama (GC) düşük gecikme süresi modu ve Visual Basic devre dışı bırakıldı.

- Visual Studio önbellekler boşaltıldı.

## <a name="improve-visual-studio-performance"></a>Performans Visual Studio geliştirme

Büyük çözümler veya düşük bellek koşullarıyla çalışırken Visual Studio performansı artırmaya yönelik ipuçları ve püf noktaları için bkz. Büyük çözümler için [performansla ilgili dikkat edilmesi gerekenler.](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)

## <a name="live-code-analysis-is-reduced-to-minimal-scope"></a>Canlı kod analizi minimum kapsama indirildi

Varsayılan olarak, açık belgeler ve projeler için canlı kod analizi yürütülür. Bu analiz kapsamını geçerli belgeye azaltılacak veya çözümün tamamına artırılacak şekilde özelleştirebilirsiniz. Daha fazla bilgi için [bkz. Nasıl yapılandırılır: Yönetilen kod için canlı kod analizi kapsamını yapılandırma.](./configure-live-code-analysis-scope-managed-code.md) Düşük bellek koşulunda, Visual Studio analiz kapsamını geçerli belgeye indir indiren bir durumdur. Ancak, bilgi çubuğunda göründüğünde Yeniden etkinleştir düğmesini  seçerek veya bu düğmeyi yeniden başlatarak tercih ettiğiniz analiz kapsamını yeniden Visual Studio. Seçenekler iletişim kutusu her zaman geçerli canlı kod analizi kapsam ayarlarını gösterir.

## <a name="gc-low-latency-disabled"></a>GC düşük gecikme süresi devre dışı

GC düşük gecikme süresi modunu yeniden etkinleştirmek için Visual Studio. Varsayılan olarak Visual Studio yazma işlemlerinizin herhangi bir GC işlemlerini engellemesini engellemek için her yazdığınızda GC düşük gecikme süresi modunu sağlar. Ancak, düşük bellek koşulu otomatik Visual Studio uyarısını görüntülemeye neden oluyorsa, gc düşük gecikme süresi modu o oturum için devre dışı bırakılır. Yeniden Visual Studio varsayılan GC davranışını yeniden sağlar. Daha fazla bilgi için bkz. <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio önbellekler boşaltıldı

Geçerli geliştirme oturuma devam eder veya Visual Studio yeniden Visual Studio tüm önbellekler hemen boşaltılır, ancak yeniden doldurularak başlar. Boşaltan önbellekler, aşağıdaki özelliklerin önbelleklerini içerir:

- Tüm başvuruları bulma

- Şu sayfaya gidin:

- Kullanarak Ekleme

Ayrıca, iç depolama işlemleri için Visual Studio önbellekler de temiz olur.

> [!NOTE]
> Otomatik özellik askıya alma uyarısı, oturum başına değil çözüm temelinde yalnızca bir kez gerçekleşir. Bu, visual C# Visual Basic (veya tam tersi) geçiş yapın ve başka bir düşük bellek koşuluyla karşıdan çıkarsanız başka bir otomatik özellik askıya alma uyarısı alasınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılandırılır: Yönetilen kod için canlı kod analizi kapsamını yapılandırma](./configure-live-code-analysis-scope-managed-code.md)
- [Atık Toplamanın Temelleri](/dotnet/standard/garbage-collection/fundamentals)
- [Büyük çözümler için performansla ilgili dikkat edilmesi gerekenler](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Performance-considerations-for-large-solutions.md)
