---
title: Profil oluşturma ayarlarını iyileştirme | Microsoft Docs
description: Visual Studio Performans Profili Oluşturucu ve Tanılama Araçları genel performansını etkileyen birçok farklı ayara sahip olduğunu öğrenin.
ms.date: 4/29/2020
ms.topic: how-to
helpviewer_keywords:
- Profiler, improve performance
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 482ee640f4b84348e00f2f3da42a4dbe13f73460
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725688"
---
# <a name="optimizing-profiler-settings"></a>Profil Oluşturma ayarlarını iyileştirme

Performans Profili Oluşturucu ve Tanılama Araçları penceresinde Visual Studio araçların genel performansını etkileyen birçok farklı ayar vardır. Bazı ayarların değiştirilmesi, analiz işleminin hızlı bir şekilde çalışmasına veya sonuçların işlendikleri sırada ek bekleme sürelere neden olabilir. Belirli ayarların özeti ve bunların performans üzerindeki etkisi aşağıda verilmiştir.

## <a name="symbol-settings"></a>Sembol Ayarlar

Hata ayıklayıcı seçeneklerinde bulunan sembol ayarları ( Hata Ayıklama **> Seçenekleri >** Semboller veya Araçlar > Seçenekler > Hata Ayıklama > **Sembolleri)** araçlarda sonuç oluşturmanın ne kadar süreceeği üzerinde önemli bir etkisi vardır. Sembol sunucularının etkinleştirilmesi veya **_NT_SYMBOL_PATH** profil oluşturmanın rapora yüklenen her modül için sembol isteğinde bulunur. Şu anda profil oluşturma, otomatik sembol yükleme tercihi ne olursa olsun her zaman tüm sembolleri otomatik olarak yükler.

![Sembol yükleme sayfası](../profiling/media/symbolloading.png "Sembol Yükleme")

Sembol yükleme ilerleme durumu, çıkış **başlığı** altındaki Çıkış penceresinde **Tanılama Araçları** görülebilir.

![Sembol yükleme ilerleme durumu](../profiling/media/symbolloadingprogress.png "Sembol Yükleme İlerleme Durumu")

Semboller indirildikten sonra önbelleğe alınarak daha sonra yapılan analiz hızlandırilir ancak yine de dosyaların yüklenmesi ve analiz güncelleştirmesi gerekir. Sembol yüklemesi analizi yavaşlatıyorsa, sembol sunucularını kapatmayı ve sembol önbelleğinizi temizlemeyi deneyin. Bunun yerine, projeniz için yerel olarak yerleşik sembollere güvenin.

## <a name="show-external-code"></a>Dış Kodu Göster

Performans Profili Oluşturucu ve **Tanılama Araçları** pencere içindeki **araçların** çoğunda kullanıcı kodu ve dış kod kavramı vardır. Kullanıcı kodu, açık çözüm veya açık çalışma alanı tarafından inşa edilen herhangi bir koddur. Dış kod başka bir şey. Dış kodu **göster** ayarını devre dışı  bırakarak veya Yalnızca kodu göster ayarını etkinleştirerek, araçların dış kodu tek bir birinci düzey çerçevede toplamasına izin verir ve sonuçları göstermek için gereken işlem miktarını büyük ölçüde azaltabilirsiniz. Bu, kullanıcıların verilerin en az işlenmesini sağlarken yavaşlamaya neden olan dış kodda nelerin çağrıldılarını görmelerini sağlar. Mümkün olduğunda Dış **kodu göster'i** devre dışı bırakın ve çözümle ilgili tanılama için çözümün veya çalışma alanının açık olduğundan emin olur.

## <a name="trace-duration"></a>İzleme Süresi

Daha kısa sürelerin profil oluşturması daha az veriyle sonuçlanıyor ve analiz daha hızlı uzıyor. Genellikle izlemelerinizi beş dakikadan uzun bir performans verisi ile sınırlamayı denemenizi öneririz. [CPU](../profiling/cpu-usage.md) Kullanımı aracı gibi bazı araçlar, toplanan veri miktarını analiz etmek istediğiniz senaryoyla sınırlayarak veri toplamayı duraklatmanizi sağlar.

## <a name="sampling-frequency"></a>Örnekleme Sıklığı

CPU Kullanımı aracı ve NET [Nesne](../profiling/cpu-usage.md) Ayırma aracı gibi [bazı araçlar](../profiling/dotnet-alloc-tool.md) örnekleme sıklığını ayarlamanıza olanak sağlar. Bu örnekleme sıklığını artırmak daha kesin bir şekilde ölçmenizi sağlar, ancak oluşturulan veri miktarını artırır. Genellikle, belirli bir sorun araştırılıyorsa bu ayarı varsayılan hızda bırakmak en iyisidir.

![Tanılama Hub'ı Özellikler Sayfası](../profiling/media/diaghubpropertiespage.png "Tanılama Hub'ı Özellikler Sayfası")

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md)
- [Aynı anda birden çok profil oluşturucu aracını kullanma](../profiling/use-multiple-profiler-tools-simultaneously.md)
- [Performans bilgilerini toplama metotlarını anlama](../profiling/understanding-performance-collection-methods-perf-profiler.md)
