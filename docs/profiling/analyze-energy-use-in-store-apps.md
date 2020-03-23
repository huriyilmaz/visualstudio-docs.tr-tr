---
title: UWP uygulamalarında enerji kullanımını analiz edin | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- uwp
monikerRange: vs-2017
ms.openlocfilehash: 0fc78a84d0c2f86e8db6c4703cc7404a32508d72
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73144737"
---
# <a name="analyze-energy-use-in-uwp-apps"></a>UWP uygulamalarında enerji kullanımını analiz etme

Visual Studio **Enerji Tüketimi** profilleyicisi, uwp uygulamalarının güç ve enerji tüketimini, zamanın tamamını veya bir kısmını kendi pilleriyle çalıştıran düşük güçlü tablet cihazlarda analiz emenize yardımcı olur. Enerjisini pilden alan bir aygıtta çok fazla enerji kullanan bir uygulama, çok fazla müşteri memnuniyetsizliğine neden olabilir ve sonunda müşteriler uygulamayı kaldırmaya da karar verebilir. Enerji kullanımını optimize etmek, uygulamanızın müşteriler tarafından benimsenmesini ve kullanımını artırabilir.

## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a>Enerji Tüketimi profil oluşturucusu nedir, nasıl çalışır ve neleri ölçer?

Enerji Tüketimi profil oluşturucusu, profil oluşturma oturumu sırasında bir cihazın ekran, CPU ve ağ bağlantıları etkinliklerini yakalar. Sonra, bu etkinlikler için kullanılan güçle ilgili ve profil oluşturma oturumunun toplam enerji miktarı için tahminler oluşturur.

> [!NOTE]
> Enerji profil oluşturucusu, güç ve enerji kullanımını tahmin etmek için, uygulamalarınızın çalıştırılabileceği düşük güçlü tablet cihazları temsil eden standart bir referans cihaz donanımı içeren bir yazılım modeli kullanır. En iyi tahminleri sağlamak için, düşük güç kullanan bir tablet cihazdaki profil verilerini toplamanız önerilir.
>
> Bu model düşük güç tüketen çeşitli cihazlar için iyi tahminler sağlasa da, profilini oluşturduğunuz cihazın gerçek değerleri muhtemelen farklı olur. Diğer kaynaklara göre daha maliyetli ve dolayısıyla optimizasyon için iyi aday olabilecek ekran, CPU ve ağ etkinliklerini bulmak için değerleri kullanın.

Enerji Tüketimi *profilleyicigüç* ve *enerji*bu tanımları kullanır:

- *Güç,* belirli bir süre içinde yapılan işleri gerçekleştirmek için kuvvetin kullanıldığı hızı ölçer. Elektrik biliminde, standart güç birimi bir *watt'* tır, bir voltun elektriksel potansiyel farkı ile akım bir amper indiğinde işin yapıldığı oran olarak tanımlanır. Güç **Kullanımı** grafiğinde, birimler watt'ın binde biri olan miliwatt **mW** olarak görüntülenir.

   Güç bir miktar olduğundan, bir yönü (bir zaman dilimi içinde artabilir veya azalabilir) ve bir de hızı (işin artış veya azalış miktarı) olduğu unutulmamalıdır.

- *Enerji,* bir pilin güç kapasitesi nde olduğu gibi kapasite veya potansiyel olarak veya bir süre içinde harcanan toplam güç miktarı olarak toplam güç miktarını ölçer. Enerji birimi watt-saat olup, bir saat boyunca sürekli olarak uygulanan bir watt'lık güç miktarıdır. Enerji **Özeti'nde,** üniteler miliwatt-saat **mW-h**olarak görüntülenir.

![Enerji kapasitesi, kullanılan güç, kullanılan toplam enerji](../profiling/media/energyprof_capcitypowerused.png)

Örneğin, bir tabletteki tam şarjlı bir pilde belli miktarda depolanmış enerji vardır. Bir ağ üzerinden iletişim kurma, değerleri hesaplama veya grafikleri görüntüleme gibi görevleri gerçekleştirmek için enerji kullanıldıkça, pilin gücü farklı oranlarda harcanır. Herhangi bir zaman dilimi için, harcanan güç toplamı da enerji ile ölçülür.

## <a name="identify-scenarios-with-user-marks"></a>Kullanıcı işaretleriyle senaryoları tanımlama
 Zaman çizelgesi cetvelindeki alanları belirlemeye yardımcı olmak için profil oluşturma verilerinize *kullanıcı işaretleri* ekleyebilirsiniz.

 ![Zaman çizelgesindeki kullanıcı işaretleri](../profiling/media/profilers_usermarktimeline.png "PROFILERS_UserMarkTimeline")

 İşaret, zaman çizelgesinde yöntemin yürütüldüğü zamanda turuncu bir üçgen olarak görünür. İşaret üzerinde beklediğinizde, ileti ve saat araç ipucu olarak görüntülenir. İki veya daha fazla kullanıcı işareti birbirine yakınsa, işaretler birleştirilir ve araç ipucu verileri birleştirilir. İşaretleri ayırmak için zaman çizelgesinde yakınlaştırma yapabilirsiniz.

 **C#, Visual Basic, C++ koduna işaret ekleme**

 C#, Visual Basic, C++ koduna kullanıcı işareti <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=fullName> eklemek için önce bir nesne oluşturun. Ardından, kodunuzdaki işaretlemek istediğiniz noktalara <xref:Windows.Foundation.Diagnostics.LoggingChannel.LogMessage%2A?displayProperty=nameWithType> yöntemlere çağrılar ekleyin. Aramalarda [LoggingLevel.Information'ı](xref:Windows.Foundation.Diagnostics.LoggingLevel) kullanın.

 Yöntem yürütüldüğünde, profil oluşturma verilerine bir iletiyle birlikte bir kullanıcı işareti eklenir.

> [!NOTE]
> - <xref:Windows.Foundation.Diagnostics.LoggingChannel?displayProperty=nameWithType><xref:Windows.Foundation.IClosable?displayProperty=nameWithType> arabirimi uygular (C# <xref:System.IDisposable?displayProperty=nameWithType> ve VB olarak yansıtılır). İşletim sistemi kaynaklarının sızdırmasını önlemek için, bir günlük kanalıyla işi bittiğinde (C# <xref:Windows.Foundation.Diagnostics.LoggingChannel.Close%2A?displayProperty=nameWithType> <xref:Windows.Foundation.Diagnostics.LoggingChannel.Dispose%2A?displayProperty=nameWithType> ve VB'de) arayın.
> - Her açık günlük kanalının benzersiz bir adı olması gerekir. Rahatsız olmayan bir kanalla aynı ada sahip yeni bir günlük kanalı oluşturmaya çalışırsanız, bir özel durum atılır.

Örneğin kod, Windows SDK Örnek [Günlük Oturumu örneğine](https://code.msdn.microsoft.com/windowsapps/LoggingSession-Sample-ccd52336)bakın.

::: moniker range="vs-2017"
**JavaScript koduna işaret ekleme**

Kullanıcı işaretleri eklemek için, kodunuzda işaretlemek istediğiniz noktalarda aşağıdaki kodu ekleyin:

```JavaScript
if (performance && performance.mark) {
    performance.mark(markDescription);
}
```

*markDescription,* kullanıcı işareti araç ipucunda görüntülenecek iletiyi içeren bir dizedir.
::: moniker-end

## <a name="configure-your-environment-for-profiling"></a>Profil oluşturma için ortamınızı yapılandırma
 İyi tahminler elde etmek için, uygulamanın enerji kullanımını pilleri tarafından desteklenen düşük güçlü bir cihazda profilini çıkarmak istersiniz. Visual Studio bu aygıtların çoğunda çalışmadığından, Visual Studio bilgisayarınızı Visual Studio uzak araçlarını kullanarak aygıta bağlamanız gerekir. Uzaktaki bir cihaza bağlanmak için, hem Visual Studio projesini hem de uzak cihazı yapılandırmanız gerekir. Daha fazla bilgi için [uzak bir makinede UWP uygulamalarını çalıştır'a](../debugger/run-windows-store-apps-on-a-remote-machine.md) bakın.

> [!TIP]
> - UWP simülatöründe veya Visual Studio bilgisayarında enerji profiloluşturmayı önermiyoruz. Gerçek cihazda profil oluşturmak çok daha gerçekçi veriler sağlar.
> - Hedef cihazda profil oluşturmayı, kendi pilleriyle çalışırken gerçekleştirin.
> - Aynı kaynakları (ağ, CPU veya ekran) kullanabilecek diğer uygulamaları kapatın.

## <a name="collect-energy-profile-data-for-your-app"></a>Uygulamanız için enerji profili verilerini toplama

1. Hata **Ayıklama** menüsünde Hata **Ayıklama olmadan Tanılama Başlat'ı**seçin.

     ![Tanılama merkezinde Enerji Tüketimi'ni seçin](../profiling/media/energyprof_diagnosticshub.png "ENERGYPROF_DiagnosticsHub")

2. **Enerji Tüketimi'ni** seçin ve ardından **Başlat'ı**seçin.

    > [!NOTE]
    > **Enerji Tüketimi** profiloluşturcunu başlattığınızda, *VsEtwCollector.exe'yi*çalıştırmak için izninizi isteyen bir **Kullanıcı Hesabı Denetimi** penceresi görebilirsiniz. **Evet'i**seçin.

3. Veri toplamak için uygulamanızda alıştırma yapın.

4. Profil oluşturmayı durdurmak için Visual Studio'ya (Alt + Sekme) geri dön ve Tanılama hub sayfasında **koleksiyonu durdur'u** seçin.

     ![Veri toplamayı durdurma](../profiling/media/xamlprof_stopcollection.png "XAMLProf_StopCollection")

     Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.

## <a name="collect-energy-profile-data-for-an-installed-app"></a>Yüklü bir uygulama için enerji profili verilerini toplama
 Enerji Tüketimi aracı yalnızca Visual Studio çözümünden başlatılan veya Microsoft Mağazası'ndan yüklenen UWP uygulamalarında çalıştırılabilir. Visual Studio'da bir çözüm açıldığında, varsayılan hedef **Başlangıç Projesi'dir.** Yüklü bir uygulamayı hedeflemek için:

1. **Hedefi Değiştir'i** seçin ve ardından **Yüklü Uygulamayı**seçin.

2. Yüklü **Uygulama Paketi Seç** listesinden hedefi seçin.

3. Tanılama merkezi sayfasında **Enerji Tüketimi'ni** seçin.

4. Profil oluşturmayı başlatmak için **Başlat'ı** seçin.

   Profil oluşturmayı durdurmak için Visual Studio'ya (Alt + Sekme) geri dön ve Tanılama hub sayfasında **koleksiyonu durdur'u** seçin.

## <a name="analyze-energy-profile-data"></a>Enerji profili verilerini analiz etme
 Enerji profili verileri Visual Studio belge penceresinde görüntülenir:

 ![Enerji profilci raporu sayfası](../profiling/media/energyprof_all.png "ENERGYPROF_All")

|||
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|Rapor dosyası,*Rapor YYYYMMDD-HHMM*.diagsession adlı. Raporu kaydetmeye karar verirseniz adını değiştirebilirsiniz.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Zaman çizelgesi profil oluşturma oturumunun uzunluğunu, uygulama yaşam döngüsü etkinleştirme olaylarını ve kullanıcı işaretlerini gösterir.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|Mavi çubukları sürükleyip zaman çizelgesinde bir bölgeyi seçerek, raporu zaman çizelgesinin bir bölümüyle sınırlandırabilirsiniz.|
|![Adım 4](../profiling/media/procguid_4.png "ProcGuid_4")|**Güç Kullanımı** grafiği, profil oluşturma oturumu sırasında bir aygıt kaynağının neden olduğu güç çıkışındaki değişikliği görüntüleyen çok satırlı bir grafiktir. Enerji Tüketimi profil oluşturucusu CPU, ağ etkinliği ve ekran görüntüsü tarafından kullanılan gücü izler.|
|![5. Adım](../profiling/media/procguid_6.png "ProcGuid_6")|**Kaynaklar (A/Kapama)** grafiği, ağ enerji maliyetlerinin ayrıntılarını sağlar. **Ağ** çubuğu, ağ bağlantısının açık olduğu zamanı gösterir. **Veri Aktarımı** alt çubuğu, uygulamanın ağ üzerinden veri aldığı veya gönderdiği zamandır.|
|![6. Adım](../profiling/media/procguid_6a.png "ProcGuid_6a")|**Enerji Kullanım Özeti,** CPU, ağ etkinliği ve ekran ekranı tarafından seçili zaman çizelgesinde kullanılan toplam enerjinin orantılı miktarını gösterir.|

 **Enerji profili verilerini analiz etmek için**

 Kaynağın gücünün tepe noktasına vardığı bir alan bulun. Tepe noktası alanını, uygulamanızın işlevselliğiyle ilişkilendirin. Sonra zaman çizelgesindeki denetim çubuklarını kullanarak, zaman çizelgesinde alanı yakınlaştırın. Ağ kullanımına odaklanmışsanız, ağ bağlantısının açık olduğu süreyi uygulamanın bağlantı üzerinden veri aldığı veya aktardığı zamana karşılaştırmak için **Kaynaklar (Açık/Kapalı)** grafiğindeki **Ağ** düğümünü genişletin. Ağın gereksiz yere açık kaldığı süreyi azaltmak çok etkili bir optimizasyondur.

## <a name="optimize-energy-use"></a>Enerji kullanımını en iyi duruma getirme
 Ağ bağlantılarında veri aktarmaktan başka, bağlantı başlatma, sürdürme ve kapatma ile ilgili enerji maliyetleri de vardır. Bazı ağlar veri gönderildikten veya alındıktan sonra, tek bağlantı üzerinden daha fazla veri iletimine olanak sağlamak için bağlantıyı bir süre daha sürdürür. Uygulamanızın bağlantıyla etkileşimini incelemek için **Kaynaklar (Açık/Kapalı)** bölmesini kullanabilirsiniz.

 ![Kaynaklar &#40;&#47;&#41; bölmede](../profiling/media/energyprof_resources.png "ENERGYPROF_Resources")

 **Ağ** ve **Veri Aktarım** çubukları, bir dizi küçük veri paketini aralıklı olarak iletmek için bağlantının uzun süreler boyunca açık olduğunu gösterirse, verileri tek bir aktarımda göndermek için toplu olarak işleyebilir, ağın açık olduğu süreyi azaltabilir ve böylece enerji maliyetlerinden tasarruf edebilirsiniz.

 ![Enerji Tüketimi Özeti bölmesi](../profiling/media/energyprof_summary.png "ENERGYPROF_Summary")

 Ekranın enerji giderleri üzerinde daha az denetiminiz vardır. Çoğu ekranlar açık renkleri görüntülemek için koyu renklere göre daha fazla enerji harcar ve dolayısıyla koyu renk arka plan kullanmak giderleri azaltmanın bir yoludur.

## <a name="other-resources"></a>Diğer kaynaklar

- [C#/VB/C++ ve XAML'nin](/previous-versions/windows/apps/hh452985\(v\=win.10\)) **Bağlantı durumu ve maliyet yönetimi** bölümleri, uygulamanızın ağ trafiğinin maliyetini en aza indirmek için kullanabileceği ağ bağlantısı bilgilerini sağlayan Windows API'lerini açıklar.

   UWP uygulamaları için Visual Studio simülatörü, ağ bilgi API'lerinin veri bağlantısı özelliklerini simüle etmenizi sağlar. Bkz. [Simülatördeki UWP uygulamalarını çalıştırın](../debugger/run-windows-store-apps-in-the-simulator.md)

- **CPU Kullanım** araçları, verimsiz işlevlerden kaynaklandığı zaman CPU yükünü azaltmanıza yardımcı olabilir. Bkz. [CPU kullanımını analiz edin.](../profiling/beginners-guide-to-performance-profiling.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)