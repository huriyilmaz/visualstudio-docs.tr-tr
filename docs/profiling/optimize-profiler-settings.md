---
title: Profil Oluşturucu ayarlarını iyileştirme | Microsoft Docs
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 1f0629228c2fcad1f8ea36db2e4d0c67a68715e4
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400317"
---
# <a name="optimizing-profiler-settings"></a>Profil Oluşturucu ayarlarını iyileştirme

Visual Studio 'da performans profil oluşturucu ve Tanılama Araçları penceresinin, araçların genel performansını etkileyen birçok farklı ayarı vardır. Bazı ayarları değiştirmek analizin hızla çalışmasına neden olabilir veya araçlara sonuçları işlerken ek bekleme süreleriyle sonuçlanır. Aşağıda belirli ayarların bir özeti ve performans üzerindeki etkileri verilmiştir.

## <a name="symbol-settings"></a>Sembol ayarları

Hata ayıklayıcı seçeneklerinde bulunan semboller ayarları ( **hata ayıklama > seçenekleri > sembol** veya **araçların > seçenekler > hata ayıklama > sembolleri** ), araçların sonuçları oluşturmak için ne kadar sürdüğünü önemli ölçüde etkiler. Sembol sunucularının etkinleştirilmesi veya **_NT_SYMBOL_PATH** kullanılması, profil oluşturucunun bir rapordaki her bir yüklü modül için semboller istemesine neden olur. Şu anda profil oluşturucu otomatik sembol yükleme tercihine bakılmaksızın her zaman otomatik olarak tüm sembolleri yükler.

![Sembol yükleme sayfası](../profiling/media/symbolloading.png "Sembol yükleme")

Sembol yüklemesinde ilerleme, **Tanılama araçları** başlığı altındaki **Çıkış** penceresinde görülebilir.

![Sembol yükleme ilerleme durumu](../profiling/media/symbolloadingprogress.png "Sembol yükleme Ilerleme durumu")

İndirildikten sonra, simgeler önbelleğe alınır ve bu da gelecekteki analizler hızlanır ancak yine de dosyaların yüklenmesi ve çözümlenmesi gerekmektedir. Sembol yüklemesi, Analizi yavaşlatıyorsa, sembol sunucularını kapatmayı ve sembol önbelleğinizi temizlemenizi deneyin. Bunun yerine, projeniz için yerel olarak oluşturulan simgelere güvenin.

## <a name="show-external-code"></a>Dış kodu göster

**Performans profil oluşturucu** ve **Tanılama araçları** penceresinde araçların birçoğu, bir Kullanıcı kodu kavramı ve harici kod kavramıdır. Kullanıcı kodu, açık çözüm veya açık çalışma alanı tarafından oluşturulan koddur. Dış kod başka bir şeydir. **Dış kodu göster** ayarını devre dışı bırakmak veya **yalnızca kendi kodumu** etkin halde göstermek için, araçların dış kodu tek bir birinci düzey çerçeveye toplamasını ve sonuçları göstermek için gereken işleme miktarını büyük ölçüde azaltmasına izin verebilirsiniz. Bu sayede, verilerin en düşük düzeyde işlenmesine karşın yavaş bir şekilde oluşturulan harici kodda çağrılan Özellikler görebilirler. Mümkün olduğunda, **dış kodu gösterme** devre dışı bırakın ve analiz ettiğiniz diagsession için çözüm veya çalışma alanı açık olduğundan emin olun.

## <a name="trace-duration"></a>İzleme süresi

Daha küçük süreler profil oluşturma daha az veri ile sonuçlanır ve bu daha hızlı analiz edilir. Genellikle, izlemelerinizi beş dakikadan fazla performans verilerinden daha uzun süre olmayacak şekilde sınırlamayı öneririz. [CPU kullanımı](../profiling/cpu-usage.md) aracı gibi bazı araçlar, araç çalışırken veri toplamayı duraklatmanıza izin verir. böylece, analiz ederken ilgilendiğiniz senaryoya toplanan veri miktarını sınırlayabilirsiniz.

## <a name="sampling-frequency"></a>Örnekleme sıklığı

[CPU kullanımı](../profiling/cpu-usage.md) aracı ve [net nesne ayırma](../profiling/dotnet-alloc-tool.md) aracı gibi bazı araçlar, örnekleme sıklığı ayarlamanıza olanak sağlar. Bu örnekleme sıklığının artırılması daha kesin bir şekilde ölçmenize olanak tanır, ancak oluşturulan veri miktarını artırır. Genellikle, belirli bir sorun araştırılmadığı müddetçe bu ayarı varsayılan hızda bırakmak en iyisidir.

![DIAG hub özellikleri sayfası](../profiling/media/diaghubpropertiespage.png "DIAG hub özellikleri sayfası")

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Aynı anda birden çok profil oluşturucu aracını kullanma](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Performans bilgilerini toplama metotlarını anlama](../profiling/understanding-performance-collection-methods-perf-profiler.md)
