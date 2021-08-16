---
title: UWP uygulamaları ve uygulamaları için enerji kullanımını analiz | Microsoft Docs
description: Pille Visual Studio UWP uygulamalarının enerji ve güç taleplerini analiz etmek için Visual Studio Enerji Tüketimi profilleyicisini kullanın.
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
ms.technology: vs-ide-debug
ms.workload:
- uwp
monikerRange: vs-2017
ms.openlocfilehash: d759f13d3c6c7da554465e7a7efd5ecaf984c2c949610151145651cb3fc511b6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121257621"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>UWP uygulamalarında enerji kullanımını analiz etme

Visual Studio **Enerji** Tüketimi profilleyicisi, UWP uygulamalarının zaman içinde veya bir kısmını kendi pillerinde çalıştıran düşük güç tüketimine sahip tabletlerde güç ve enerji tüketimini analiz etmenize yardımcı olur. Enerjisini pilden alan bir aygıtta çok fazla enerji kullanan bir uygulama, çok fazla müşteri memnuniyetsizliğine neden olabilir ve sonunda müşteriler uygulamayı kaldırmaya da karar verebilir. Enerji kullanımını en iyi duruma getirme, uygulamanın müşteriler tarafından benimsenme ve kullanımını artırabilir.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Enerji Tüketimi profil oluşturucusu nedir, nasıl çalışır ve neleri ölçer?

Enerji Tüketimi profil oluşturucusu, profil oluşturma oturumu sırasında bir cihazın ekran, CPU ve ağ bağlantıları etkinliklerini yakalar. Sonra, bu etkinlikler için kullanılan güçle ilgili ve profil oluşturma oturumunun toplam enerji miktarı için tahminler oluşturur.

> [!NOTE]
> Enerji profil oluşturucusu, güç ve enerji kullanımını tahmin etmek için, uygulamalarınızın çalıştırılabileceği düşük güçlü tablet cihazları temsil eden standart bir referans cihaz donanımı içeren bir yazılım modeli kullanır. En iyi tahminleri sağlamak için, düşük güç kullanan bir tablet cihazdaki profil verilerini toplamanız önerilir.
>
> Bu model düşük güç tüketen çeşitli cihazlar için iyi tahminler sağlasa da, profilini oluşturduğunuz cihazın gerçek değerleri muhtemelen farklı olur. Diğer kaynaklara göre daha maliyetli ve dolayısıyla optimizasyon için iyi aday olabilecek ekran, CPU ve ağ etkinliklerini bulmak için değerleri kullanın.

Enerji Tüketimi profilleyicisi şu güç ve *enerji tanımlarını* *kullanır:*

- *Güç,* bir süre içinde yapılan işlemleri gerçekleştirmek için kullanılan zorlama oranını ölçür. Elektrik bilimine göre standart güç birimi watt'tır. Bu, bir volt elektrik olası farkı üzerinden geçerli akışlardan biri ampere olduğunda yapılan çalışma hızı olarak tanımlanır. Güç **Kullanımı grafiğinde** birimler, watt'ın binde biri olan miliwatt **mW** olarak görüntülenir.

   Güç bir miktar olduğundan, bir yönü (bir zaman dilimi içinde artabilir veya azalabilir) ve bir de hızı (işin artış veya azalış miktarı) olduğu unutulmamalıdır.

- *Enerji,* bir pilin güç kapasitesinde olduğu gibi kapasite veya potansiyel olarak ya da bir süre boyunca tüketen toplam güç miktarı olarak toplam güç miktarını ölçür. Enerji birimi watt-saat olup, bir saat boyunca sürekli olarak uygulanan bir watt'lık güç miktarıdır. Enerji **Özeti 'de** birimler miliwatt-saat **mW-h olarak görüntülenir.**

![Enerji kapasitesi, kullanılan güç, kullanılan toplam enerji](../profiling/media/energyprof_capcitypowerused.png)

Örneğin, bir tabletteki tam şarjlı bir pilde belli miktarda depolanmış enerji vardır. Bir ağ üzerinden iletişim kurma, değerleri hesaplama veya grafikleri görüntüleme gibi görevleri gerçekleştirmek için enerji kullanıldıkça, pilin gücü farklı oranlarda harcanır. Herhangi bir zaman dilimi için, harcanan güç toplamı da enerji ile ölçülür.

## <a name="identify-scenarios-with-user-marks&quot;></a>Kullanıcı işaretleriyle senaryoları tanımlama
 Zaman *çizelgesinde alanları tanımlamaya* yardımcı olmak için profil oluşturma verilerinize kullanıcı işaretleri ekleyebilirsiniz.

 ![Zaman çizelgesinde kullanıcı işaretleri](../profiling/media/profilers_usermarktimeline.png &quot;PROFILERS_UserMarkTimeline")

 İşaret, zaman çizelgesinde yöntemin yürütüldüğü zamanda turuncu bir üçgen olarak görünür. İşaret üzerinde beklediğinizde, ileti ve saat araç ipucu olarak görüntülenir. İki veya daha fazla kullanıcı işareti birbirine yakınsa, işaretler birleştirilir ve araç ipucu verileri birleştirilir. İşaretleri ayırmak için zaman çizelgesinde yakınlaştırma yapabilirsiniz.

 **C#, Visual Basic, C++ koduna işaret ekleme**

 C#, Visual Basic, C++ koduna kullanıcı işareti eklemek için önce bir nesnesi <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> oluşturun. Ardından, <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> kodda işaretlemek istediğiniz noktalarda yöntemlere çağrılar ekler. Çağrılarda [LoggingLevel.Information](xref:Windows.Foundation.Diagnostics.LoggingLevel) kullanın.

 Yöntem yürütüldüğünde, profil oluşturma verilerine bir iletiyle birlikte bir kullanıcı işareti eklenir.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType> arabirimini <xref:Windows.Foundation.IClosable?displayProperty=nameWithType> <xref:System.IDisposable?displayProperty=nameWithType> (C# ve VB'de olduğu gibi) uygulamaya alır. İşletim sistemi kaynaklarının sızmasını önlemek için, bir günlük kanalıyla bitirdikten <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> sonra çağrısı <xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType> (C# ve VB'de).
> - Her açık günlük kanalının benzersiz bir adı olması gerekir. Dağıtılmaz bir kanalla aynı adla yeni bir günlük kanalı oluşturma girişiminde bulunduysanız bir özel durum oluşturur.

Örneğin kod için bkz. Windows SDK'sı Örnek [Günlük KaydıSession örneği.](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336)

::: moniker range="vs-2017"
**JavaScript koduna işaret ekleme**

Kullanıcı işaretleri eklemek için, kodunuzda işaretlemek istediğiniz noktalarda aşağıdaki kodu ekleyin:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription,* kullanıcı işareti araç ipucunda iletiyi içeren bir dizedir.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>Profil oluşturma için ortamınızı yapılandırma
 İyi tahminler elde etmek için pillerle desteklenen düşük güçlü bir cihazda uygulamanın enerji kullanımının profilini oluşturmak gerekir. Bu Visual Studio çoğu cihazda çalışmay olduğundan, uzak araçları kullanarak Visual Studio bilgisayarınızı cihaza bağlamanız Visual Studio gerekir. Uzaktaki bir cihaza bağlanmak için, hem Visual Studio projesini hem de uzak cihazı yapılandırmanız gerekir. Daha [fazla bilgi için bkz. Uzak makinede UWP](../debugger/run-windows-store-apps-on-a-remote-machine.md) uygulamaları çalıştırma.

> [!TIP]
> - Enerji profili oluşturma, UWP simülatöründe veya Visual Studio önerilmez. Gerçek cihazda profil oluşturmak çok daha gerçekçi veriler sağlar.
> - Hedef cihazda profil oluşturmayı, kendi pilleriyle çalışırken gerçekleştirin.
> - Aynı kaynakları (ağ, CPU veya ekran) kullanabilecek diğer uygulamaları kapatın.

## <a name="collect-energy-profile-data-for-your-app"></a>Uygulamanız için enerji profili verilerini toplama

1. Hata Ayıklama **menüsünde Hata** Ayıklama Olmadan **Tanılamayı Başlat'ı seçin.**

     ![Günlükte Enerji Tüketimi'Performans Profili Oluşturucu](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. Enerji **Tüketimi'ne ve** ardından Başlat'a **seçin.**

    > [!NOTE]
    > Enerji Tüketimi **profilleyicisini** başlatarak bir  Kullanıcı Hesabı Denetimi penceresi görebilir ve bu pencereyi çalıştırmak için *izniniziVsEtwCollector.exe.* **Evet'i seçin.**

3. Veri toplamak için uygulamanızda alıştırma yapın.

4. Profil oluşturmayı durdurmak için Visual Studio (Alt + Sekme) seçeneğine geri dönüp Tanılama hub'ı sayfasında **Koleksiyonu** durdur'a tıklayın.

     ![Veri toplamayı durdurma](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Yüklü bir uygulama için enerji profili verilerini toplama
 Enerji Tüketimi aracı yalnızca bir Visual Studio çözümünden başlatılan veya Microsoft Store. Bir çözüm içinde açık Visual Studio, varsayılan hedef Başlangıç hedefi **Project.** Yüklü bir uygulamayı hedeflemek için:

1. Hedefi **Değiştir'i** ve ardından Yüklü **Uygulama'yi seçin.**

2. Yüklü **Uygulama Paketi Seçin listesinden** hedefi seçin.

3. Giriş **sayfasında Enerji** Tüketimi'Performans Profili Oluşturucu seçin.

4. Profil **oluşturmayı başlatmak** için Başlat'ı seçin.

   Profil oluşturmayı durdurmak için Visual Studio (Alt + Sekme) seçeneğine geri dönüp Tanılama hub'ı sayfasında **Koleksiyonu** durdur'a tıklayın.

## <a name="analyze-energy-profile-data"></a>Enerji profili verilerini analiz etme
 Enerji profili verileri Visual Studio belge penceresinde görüntülenir:

 ![Enerji profili oluşturma rapor sayfası](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|Görüntü|Açıklama|
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|Rapor dosyası Rapor *YYYYMMD-HHMM*.diagsession olarak adlandırılmıştır. Raporu kaydetmeye karar verirseniz adını değiştirebilirsiniz.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Zaman çizelgesi profil oluşturma oturumunun uzunluğunu, uygulama yaşam döngüsü etkinleştirme olaylarını ve kullanıcı işaretlerini gösterir.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|Mavi çubukları sürükleyip zaman çizelgesinde bir bölgeyi seçerek, raporu zaman çizelgesinin bir bölümüyle sınırlandırabilirsiniz.|
|![4. Adım](../profiling/media/procguid_4.png "ProcGuid_4")|Güç **Kullanımı** grafiği, profil oluşturma oturumu sırasında bir cihaz kaynağında oluşan güç çıkışı değişikliğini görüntüleyen çok satırlı bir grafiktir. Enerji Tüketimi profil oluşturucusu CPU, ağ etkinliği ve ekran görüntüsü tarafından kullanılan gücü izler.|
|![5. Adım](../profiling/media/procguid_6.png "ProcGuid_6")|Kaynaklar **(Kapalı/Kapalı)**  grafiği, ağ enerji maliyetlerinin ayrıntılarını sağlar. Ağ **çubuğu,** ağ bağlantısının açık olduğu zamanı temsil eder. Veri **Aktarımı** alt çubuğu, uygulamanın ağ üzerinden veri alma veya gönderme zamanıdır.|
|![6. Adım](../profiling/media/procguid_6a.png "ProcGuid_6a")|Enerji **Kullanımı Özeti** CPU, ağ etkinliği ve ekran görüntüsü tarafından seçilen zaman çizelgesinde kullanılan toplam enerjinin orantılı miktarını gösterir.|

 **Enerji profili verilerini analiz etmek için**

 Kaynağın gücünün tepe noktasına vardığı bir alan bulun. Tepe noktası alanını, uygulamanızın işlevselliğiyle ilişkilendirin. Sonra zaman çizelgesindeki denetim çubuklarını kullanarak, zaman çizelgesinde alanı yakınlaştırın. Ağ kullanımına odaklanıyorsanız,  ağ bağlantısının açık olduğu zamanı uygulamanın bağlantı üzerinden veri alma veya aktarma zamanıyla karşılaştırmak için Kaynaklar **(Açık/Kapalı)** grafiğindeki Ağ düğümünü genişletin. Ağın gereksiz yere açık kaldığı süreyi azaltmak çok etkili bir optimizasyondur.

## <a name="optimize-energy-use"></a>Enerji kullanımını en iyi duruma getirme
 Ağ bağlantılarında veri aktarmaktan başka, bağlantı başlatma, sürdürme ve kapatma ile ilgili enerji maliyetleri de vardır. Bazı ağlar veri gönderildikten veya alındıktan sonra, tek bağlantı üzerinden daha fazla veri iletimine olanak sağlamak için bağlantıyı bir süre daha sürdürür. Kaynak **(Aç/Kapat) bölmesini kullanarak,** uygulamanın bağlantıyla nasıl etkileşim kura olduğunu inceleyebilirsiniz.

 ![Kaynaklar &#40;&#47;Kapalı&#41; bölmesi](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 Ağ **ve** **Veri** Aktarımı çubukları, bir dizi küçük veri paketini aralıklı olarak iletmek için bağlantının uzun süre açık olduğunu gösteriyorsa, verileri toplu olarak göndererek tek bir iletimde gönderebilir, ağın açık olduğu zamanı azaltabilirsiniz ve böylece enerji maliyetlerinden tasarruf edin.

 ![Enerji Tüketimi Özeti bölmesi](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Ekranın enerji giderleri üzerinde daha az denetiminiz vardır. Çoğu ekranlar açık renkleri görüntülemek için koyu renklere göre daha fazla enerji harcar ve dolayısıyla koyu renk arka plan kullanmak giderleri azaltmanın bir yoludur.

## <a name="other-resources"></a>Diğer kaynaklar

- [C#/VB/C++ ve XAML](/previous-versions/windows/apps/hh452985\(v\=win.10\)) için bağlantı durumu ve maliyet yönetimi bölümleri, Windows ağ trafiği maliyetini en aza indirmek için kullanabileceği ağ bağlantısı bilgilerini sağlayan Windows API'lerini açıklar. 

   UWP Visual Studio için sanal simülatör, ağ bilgisi API'lerinin veri bağlantısı özelliklerinin benzetimini sağlar. Bkz. [Simülatörde UWP uygulamaları çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md)

- **CPU Kullanımı** araçları, verimsiz işlevler nedeniyle CPU yükünü azaltmanıza yardımcı olabilir. Bkz. [CPU kullanımını analiz etme.](../profiling/beginners-guide-to-performance-profiling.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)