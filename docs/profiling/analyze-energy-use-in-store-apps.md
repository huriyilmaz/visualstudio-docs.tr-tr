---
title: UWP uygulamalarında enerji kullanımını analiz etme | Microsoft Docs
description: Pil destekli cihazlarda çalışan UWP uygulamalarının enerji ve güç gereksinimlerini analiz etmek için Visual Studio enerji tüketimi profil oluşturucuyu kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
monikerRange: vs-2017
ms.openlocfilehash: af27524b9b057e1a7dc852bd10d7acd23cf8bd04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901240"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>UWP uygulamalarında enerji kullanımını analiz etme

Visual Studio **enerji tüketimi** profil oluşturucusu, kendi pillerinde saatin tümünü veya bir kısmını çalıştıran düşük güçte tablet CIHAZLARıNDAKI UWP uygulamalarının güç ve enerji tüketimini çözümlemenize yardımcı olur. Enerjisini pilden alan bir aygıtta çok fazla enerji kullanan bir uygulama, çok fazla müşteri memnuniyetsizliğine neden olabilir ve sonunda müşteriler uygulamayı kaldırmaya da karar verebilir. Enerji kullanımını iyileştirmek, uygulamanızın benimseme ve kullanım kullanımını artırabilir.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Enerji Tüketimi profil oluşturucusu nedir, nasıl çalışır ve neleri ölçer?

Enerji Tüketimi profil oluşturucusu, profil oluşturma oturumu sırasında bir cihazın ekran, CPU ve ağ bağlantıları etkinliklerini yakalar. Sonra, bu etkinlikler için kullanılan güçle ilgili ve profil oluşturma oturumunun toplam enerji miktarı için tahminler oluşturur.

> [!NOTE]
> Enerji profil oluşturucusu, güç ve enerji kullanımını tahmin etmek için, uygulamalarınızın çalıştırılabileceği düşük güçlü tablet cihazları temsil eden standart bir referans cihaz donanımı içeren bir yazılım modeli kullanır. En iyi tahminleri sağlamak için, düşük güç kullanan bir tablet cihazdaki profil verilerini toplamanız önerilir.
>
> Bu model düşük güç tüketen çeşitli cihazlar için iyi tahminler sağlasa da, profilini oluşturduğunuz cihazın gerçek değerleri muhtemelen farklı olur. Diğer kaynaklara göre daha maliyetli ve dolayısıyla optimizasyon için iyi aday olabilecek ekran, CPU ve ağ etkinliklerini bulmak için değerleri kullanın.

Enerji tüketimi Profil Oluşturucusu, bu *Güç* ve *enerji* tanımlarını kullanır:

- *Güç* , bir süre içinde yapılan işleri gerçekleştirmek için zorlamalı kullanım oranını ölçer. Elektrik biliminde standart güç birimi, tek bir volt 'in bir elektrik potansiyel farkı aracılığıyla geçerli akışlardan biri olduğunda çalışmanın oranı olarak tanımlanan bir *vat*'dir. **Güç kullanımı** grafiğinde birimler, bir vat 'nin bir thousandth olan milivat **MW** olarak görüntülenir.

   Güç bir miktar olduğundan, bir yönü (bir zaman dilimi içinde artabilir veya azalabilir) ve bir de hızı (işin artış veya azalış miktarı) olduğu unutulmamalıdır.

- *Enerji* , bir pilin güç kapasitesine göre veya bir süre boyunca toplam güç miktarı kadar olan toplam güç miktarını kapasite veya potansiyel olarak ölçer. Enerji birimi watt-saat olup, bir saat boyunca sürekli olarak uygulanan bir watt'lık güç miktarıdır. **Enerji özetinde** birimler milivat-saat **MW-h** olarak görüntülenir.

![Enerji kapasitesi, kullanılan güç, kullanılan toplam enerji](../profiling/media/energyprof_capcitypowerused.png)

Örneğin, bir tabletteki tam şarjlı bir pilde belli miktarda depolanmış enerji vardır. Bir ağ üzerinden iletişim kurma, değerleri hesaplama veya grafikleri görüntüleme gibi görevleri gerçekleştirmek için enerji kullanıldıkça, pilin gücü farklı oranlarda harcanır. Herhangi bir zaman dilimi için, harcanan güç toplamı da enerji ile ölçülür.

## <a name="identify-scenarios-with-user-marks"></a>Kullanıcı işaretleriyle senaryoları tanımlama
 Zaman çizelgesi cetvelindeki alanların tanımlanmasına yardımcı olması için profil oluşturma verilerinize *Kullanıcı işaretleri* ekleyebilirsiniz.

 ![Zaman çizelgesinde Kullanıcı işaretleri](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 İşaret, zaman çizelgesinde yöntemin yürütüldüğü zamanda turuncu bir üçgen olarak görünür. İşaret üzerinde beklediğinizde, ileti ve saat araç ipucu olarak görüntülenir. İki veya daha fazla kullanıcı işareti birbirine yakınsa, işaretler birleştirilir ve araç ipucu verileri birleştirilir. İşaretleri ayırmak için zaman çizelgesinde yakınlaştırma yapabilirsiniz.

 **C#, Visual Basic, C++ koduna işaret ekleme**

 C#, Visual Basic, C++ koduna kullanıcı işareti eklemek için, önce bir <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> nesne oluşturun. Ardından <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> , kodunuzda işaretlemek istediğiniz noktalarda çağrılar ekleyin. Çağrılarındaki [LoggingLevel. Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) kullanın.

 Yöntem yürütüldüğünde, profil oluşturma verilerine bir iletiyle birlikte bir kullanıcı işareti eklenir.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType> arabirimini uygular <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> ( <xref:System.IDisposable?displayProperty=nameWithType> C# ve vb 'de olarak tasarlanan). İşletim sistemi kaynaklarının sızmasını önlemek için, <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> <xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType> bir günlük kanalı ile işiniz bittiğinde çağırın (C# ve vb 'de).
> - Her açık günlük kanalının benzersiz bir adı olması gerekir. Aktiften çıkarılan bir kanalla aynı ada sahip yeni bir günlük kanalı oluşturmaya çalışırsanız, bir özel durum oluşturulur.

Örnek kod için Windows SDK örnek [LoggingSession örneğine](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336)bakın.

::: moniker range="vs-2017"
**JavaScript koduna işaretler ekleme**

Kullanıcı işaretleri eklemek için, kodunuzda işaretlemek istediğiniz noktalarda aşağıdaki kodu ekleyin:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*MarkDescription* , kullanıcı işareti araç ipucunda görüntülenecek iletiyi içeren bir dizedir.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>Profil oluşturma için ortamınızı yapılandırma
 İyi tahminleri elde etmek için, pili pille çalışan düşük güç kullanan bir cihazda uygulamanın enerji kullanımını profil altında bulabilirsiniz. Visual Studio bu cihazların çoğunda çalışmadığından Visual Studio bilgisayarınızı Visual Studio uzak araçlarını kullanarak cihaza bağlamanız gerekir. Uzaktaki bir cihaza bağlanmak için, hem Visual Studio projesini hem de uzak cihazı yapılandırmanız gerekir. Daha fazla bilgi için bkz. [uzak MAKINEDE UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md) .

> [!TIP]
> - UWP simülatörü veya Visual Studio bilgisayarında enerji profili oluşturma önerilmez. Gerçek cihazda profil oluşturmak çok daha gerçekçi veriler sağlar.
> - Hedef cihazda profil oluşturmayı, kendi pilleriyle çalışırken gerçekleştirin.
> - Aynı kaynakları (ağ, CPU veya ekran) kullanabilecek diğer uygulamaları kapatın.

## <a name="collect-energy-profile-data-for-your-app"></a>Uygulamanız için enerji profili verilerini toplama

1. **Hata Ayıkla** menüsünde, **hata ayıklama olmadan Tanılamayı Başlat**' ı seçin.

     ![Performans profil oluşturucusu 'nda enerji tüketimini seçme](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. **Enerji tüketimini** seçin ve ardından **Başlat**' ı seçin.

    > [!NOTE]
    > **Enerji tüketimi** profil oluşturucuyu başlattığınızda, *VsEtwCollector.exe* çalıştırmak Için Izninizi ısteyen bir **Kullanıcı hesabı denetim** penceresi görebilirsiniz. **Evet**' i seçin.

3. Veri toplamak için uygulamanızda alıştırma yapın.

4. Profil oluşturmayı durdurmak için, Visual Studio 'ya geri dönün (Alt + Tab) ve tanılama hub 'ı sayfasında **toplamayı durdur** ' u seçin.

     ![Veri toplamayı durdur](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Yüklü bir uygulama için enerji profili verilerini toplama
 Enerji tüketimi aracı yalnızca bir Visual Studio çözümünden başlatılan veya Microsoft Store yüklenen UWP uygulamalarında çalıştırılabilir. Visual Studio 'da bir çözüm açıldığında, varsayılan hedef **Başlangıç projem** tir. Yüklü bir uygulamayı hedeflemek için:

1. **Hedefi Değiştir** ' i seçin ve ardından **yüklü uygulama**' yı seçin.

2. **Yüklü uygulama paketini Seç** listesinden hedefi seçin.

3. Performans profili Oluşturucu sayfasında **enerji tüketimini** seçin.

4. Profil oluşturmaya başlamak için **Başlat** ' ı seçin.

   Profil oluşturmayı durdurmak için, Visual Studio 'ya geri dönün (Alt + Tab) ve tanılama hub 'ı sayfasında **toplamayı durdur** ' u seçin.

## <a name="analyze-energy-profile-data"></a>Enerji profili verilerini analiz etme
 Enerji profili verileri Visual Studio belge penceresinde görüntülenir:

 ![Enerji profili Oluşturucu rapor sayfası](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|Görüntü|Description|
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|Rapor dosyası, Report *YYYYMMDD-SSMM*. diagsession olarak adlandırılır. Raporu kaydetmeye karar verirseniz adını değiştirebilirsiniz.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Zaman çizelgesi profil oluşturma oturumunun uzunluğunu, uygulama yaşam döngüsü etkinleştirme olaylarını ve kullanıcı işaretlerini gösterir.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|Mavi çubukları sürükleyip zaman çizelgesinde bir bölgeyi seçerek, raporu zaman çizelgesinin bir bölümüyle sınırlandırabilirsiniz.|
|![4. adım](../profiling/media/procguid_4.png "ProcGuid_4")|**Güç kullanımı** grafiği, profil oluşturma oturumu sırasında bir cihaz kaynağı nedeniyle oluşan güç çıktısındaki değişikliği görüntüleyen çok satırlı bir grafiktir. Enerji Tüketimi profil oluşturucusu CPU, ağ etkinliği ve ekran görüntüsü tarafından kullanılan gücü izler.|
|![5. adım](../profiling/media/procguid_6.png "ProcGuid_6")|**Kaynaklar (açık/kapalı)** grafiğinde ağ enerji maliyetlerinin ayrıntıları sağlanmaktadır. **Ağ** çubuğu, ağ bağlantısının açık olduğu süreyi temsil eder. **Veri aktarımı** alt çubuğu, uygulamanın ağ üzerinden veri aldığı veya gönderdiği süredir.|
|![6. adım](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Enerji Kullanım Özeti** , seçili zaman çizelgesinde CPU, ağ etkinliği ve ekran görüntüsü tarafından kullanılan toplam enerji miktarının orantılı miktarını gösterir.|

 **Enerji profili verilerini analiz etmek için**

 Kaynağın gücünün tepe noktasına vardığı bir alan bulun. Tepe noktası alanını, uygulamanızın işlevselliğiyle ilişkilendirin. Sonra zaman çizelgesindeki denetim çubuklarını kullanarak, zaman çizelgesinde alanı yakınlaştırın. Ağ kullanımına odaklandıysanız, ağ bağlantısının açık olduğu zamanı, uygulamanın bağlantı üzerinden veri aldığı veya aktaran zamana göre karşılaştırmak için **kaynaklar (açık/kapalı)** grafiğinde **ağ** düğümünü genişletin. Ağın gereksiz yere açık kaldığı süreyi azaltmak çok etkili bir optimizasyondur.

## <a name="optimize-energy-use"></a>Enerji kullanımını en iyi duruma getirme
 Ağ bağlantılarında veri aktarmaktan başka, bağlantı başlatma, sürdürme ve kapatma ile ilgili enerji maliyetleri de vardır. Bazı ağlar veri gönderildikten veya alındıktan sonra, tek bağlantı üzerinden daha fazla veri iletimine olanak sağlamak için bağlantıyı bir süre daha sürdürür. Uygulamanızın bağlantıyla etkileşim kurma şeklini incelemek için **kaynaklar (açık/kapalı)** bölmesini kullanabilirsiniz.

 ![&#41; bölmedeki&#47;&#40;kaynaklar](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 **Ağ** ve **veri aktarımı** çubuklar, bir dizi küçük veri paketini zaman zaman aktarmak için bağlantının açık olduğunu gösterip, verileri tek bir iletime göndermek için toplu olarak kullanabilir, ağın açık olduğu süreyi azaltabilir ve böylece enerji maliyetlerini kaydedebilirsiniz.

 ![Enerji tüketimi Özet bölmesi](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Ekranın enerji giderleri üzerinde daha az denetiminiz vardır. Çoğu ekranlar açık renkleri görüntülemek için koyu renklere göre daha fazla enerji harcar ve dolayısıyla koyu renk arka plan kullanmak giderleri azaltmanın bir yoludur.

## <a name="other-resources"></a>Diğer kaynaklar

- [C#/vb/c + + ve xaml](/previous-versions/windows/apps/hh452985\(v\=win.10\)) için **bağlantı durumu ve maliyet yönetimi** bölümleri, uygulamanızın ağ trafiği maliyetini en aza indirmek için kullanabileceği ağ bağlantısı bilgilerini sağlayan Windows API 'lerini anlatmaktadır.

   UWP uygulamaları için Visual Studio simülatörü, ağ bilgileri API 'lerinin veri bağlantısı özelliklerinin benzetimini yapmanızı sağlar. Bkz [. simülatörde UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md)

- **CPU kullanım** araçları, verimsiz IŞLEVLERDEN kaynaklanan CPU yükünü azaltmanıza yardımcı olabilir. Bkz. [CPU kullanımını çözümleme](../profiling/beginners-guide-to-performance-profiling.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)