---
title: Otomatik Özellik askıya alma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b9c80ba76ba2da978c9cb475299ba0fc9e614120
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655146"
---
# <a name="automatic-feature-suspension"></a>Otomatik özelliği askıya alma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Kullanılabilir sistem belleğiniz 200 MB veya daha az kalırsa, Visual Studio kod düzenleyicisinde aşağıdaki iletiyi görüntüler.

 ![Tam çözüm analizini askıya alarak uyarı metni](../code-quality/media/fsa-alert.png "FSA_Alert")

 Visual Studio düşük bellekli bir durum algıladığında, kararlı kalmasını sağlamak için bazı gelişmiş özellikleri otomatik olarak askıya alır. Bu gelişmiş özellik askıya alma uyarısı göründüğünde, Visual Studio daha önce olduğu gibi çalışmaya devam eder, ancak performansı biraz düşürülmüş olur.

 Düşük bellek koşulunda aşağıdakiler gerçekleşir:

- Visual C# ve Visual Basic için tam çözüm Analizi devre dışı bırakıldı.

- Visual C# için [çöp toplama](https://msdn.microsoft.com/library/22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9) (GC) düşük gecikme modu ve Visual Basic devre dışı bırakıldı.

- Visual Studio önbellekleri temizlendi.

## <a name="improve-visual-studio-performance"></a>Visual Studio performansını geliştirme
 Büyük çözümlerle veya düşük bellek koşullarıyla çalışırken Visual Studio performansının nasıl iyileştirecağıyla ilgili ipuçları ve püf noktaları için bkz. [büyük çözümler Için performans konuları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).

## <a name="full-solution-analysis-suspended"></a>Tam çözüm Analizi askıya alındı
 Varsayılan olarak, tam çözüm Analizi Visual Basic için etkinleştirilmiştir ve Visual C# için devre dışı bırakılır. Ancak, düşük bellek koşulunda, Seçenekler iletişim kutusundaki ayarlarından bağımsız olarak hem Visual Basic hem de Visual C# için tam çözüm Analizi otomatik olarak devre dışıdır. Ancak, Seçenekler iletişim kutusunda **tam çözüm analizini etkinleştir** onay kutusunu seçerek veya Visual Studio 'yu yeniden başlatarak, görüntülenen bilgi çubuğundaki **yeniden etkinleştir** düğmesini seçerek tam çözüm analizini yeniden etkinleştirebilirsiniz. Seçenekler iletişim kutusu her zaman geçerli tam çözüm Analizi ayarlarını gösterir. Daha fazla bilgi için bkz. [nasıl yapılır: tam çözüm analizini etkinleştirme ve devre dışı bırakma](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).

## <a name="gc-low-latency-disabled"></a>GC düşük gecikme süresi devre dışı
 GC düşük gecikmeli modunu yeniden etkinleştirmek için Visual Studio 'Yu yeniden başlatın.  Varsayılan olarak, yazılarınızın herhangi bir GC işlemini engellemediğinden emin olmak için her yazarken, Visual Studio GC düşük gecikme süresi modunu sağlar. Ancak, düşük bellek durumu Visual Studio 'Nun otomatik askıya alma uyarısını görüntülemesine neden oluyorsa, GC düşük gecikme modu bu oturum için devre dışıdır. Visual Studio 'Yu yeniden başlatmak, varsayılan GC davranışını yeniden etkinleştirir. Daha fazla bilgi için bkz. <xref:System.Runtime.GCLatencyMode>.

## <a name="visual-studio-caches-flushed"></a>Visual Studio önbellekleri temizlendi

Tüm Visual Studio önbellekler hemen boşaltılır, ancak geçerli geliştirme oturumunuza devam ederseniz veya Visual Studio 'Yu yeniden başlattığınızda yeniden doldurmak üzere başlatılır. Temizlenen önbellekler aşağıdaki özelliklere yönelik önbellekleri içerir.

- Tüm başvuruları bul

- Şuraya gidin

- Kullanarak Ekle

Ayrıca, iç Visual Studio işlemleri için kullanılan önbellekler da temizlenir.

> [!NOTE]
> Otomatik Özellik askıya alma uyarısı, her oturum için değil, her çözüm temelinde yalnızca bir kez gerçekleşir. Bu, Visual Basic 'den Visual C# ' ye (veya tam tersi) geçiş yaptıysanız ve başka bir düşük bellek koşuluyla çalıştırırsanız, başka bir otomatik özellik askıya alma uyarısı elde edebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl Yapılır: Tam Çözüm Analizini Etkinleştirme ve Devre Dışı Bırakma](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)
- [Atık Toplamanın Temelleri](https://msdn.microsoft.com/library/67c5a20d-1be1-4ea7-8a9a-92b0b08658d2)
- [Büyük çözümler için performans konuları](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)