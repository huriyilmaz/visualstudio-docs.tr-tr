---
title: Mağaza uygulamalarında enerji kullanımını analiz etme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 96d06843-b97e-45a8-8126-07478a40bfc4
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 82f5e6401ba65a0dfaffc268890ece0166432c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532957"
---
# <a name="analyze-energy-use-in-store-apps"></a>Store uygulamalarında enerji kullanımını analiz etme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio **enerji tüketimi** profil oluşturucusu, Windows Mağazası uygulamalarının güç ve enerji tüketimini, sürenin tamamını veya bir kısmını kendi pillerinde çalıştıran düşük güçte tablet cihazlarından çözümlemenize yardımcı olur. Enerjisini pilden alan bir aygıtta çok fazla enerji kullanan bir uygulama, çok fazla müşteri memnuniyetsizliğine neden olabilir ve sonunda müşteriler uygulamayı kaldırmaya da karar verebilir. Enerji kullanımını en iyi duruma getirmek, uygulamalarınızın müşteriler tarafından benimsenmesini ve kullanılmasını artırabilir.  
  
## <a name="what-the-energy-consumption-profiler-is-how-it-works-and-what-it-measures"></a><a name="BKMK_What_the_Energy_Consumption_tool_is__how_it_works__and_what_it_measures"></a> Enerji tüketimi profil oluşturucunun ne olduğu, nasıl çalıştığı ve ne ölçtüğünden  
 Enerji Tüketimi profil oluşturucusu, profil oluşturma oturumu sırasında bir cihazın ekran, CPU ve ağ bağlantıları etkinliklerini yakalar. Sonra, bu etkinlikler için kullanılan güçle ilgili ve profil oluşturma oturumunun toplam enerji miktarı için tahminler oluşturur.  
  
> [!NOTE]
> Enerji profil oluşturucusu, güç ve enerji kullanımını tahmin etmek için, uygulamalarınızın çalıştırılabileceği düşük güçlü tablet cihazları temsil eden standart bir referans cihaz donanımı içeren bir yazılım modeli kullanır. En iyi tahminleri sağlamak için, düşük güç kullanan bir tablet cihazdaki profil verilerini toplamanız önerilir.  
>   
> Bu model düşük güç tüketen çeşitli cihazlar için iyi tahminler sağlasa da, profilini oluşturduğunuz cihazın gerçek değerleri muhtemelen farklı olur. Diğer kaynaklara göre daha maliyetli ve dolayısıyla optimizasyon için iyi aday olabilecek ekran, CPU ve ağ etkinliklerini bulmak için değerleri kullanın.  
  
 Enerji tüketimi Profil Oluşturucusu, bu *Güç* ve *enerji*tanımlarını kullanır:  
  
- *Güç* , bir süre içinde yapılan işleri gerçekleştirmek için zorlamalı kullanım oranını ölçer. Elektrik biliminde standart güç birimi, tek bir volt 'in bir elektrik potansiyel farkı aracılığıyla geçerli akışlardan biri olduğunda çalışmanın oranı olarak tanımlanan bir *vat*'dir. **Güç kullanımı** grafiğinde birimler, bir vat 'nin bir thousandth olan milivat **MW** olarak görüntülenir.  
  
   Güç bir miktar olduğundan, bir yönü (bir zaman dilimi içinde artabilir veya azalabilir) ve bir de hızı (işin artış veya azalış miktarı) olduğu unutulmamalıdır.  
  
- *Enerji* , bir pilin güç kapasitesine göre veya bir süre boyunca toplam güç miktarı kadar olan toplam güç miktarını kapasite veya potansiyel olarak ölçer. Enerji birimi watt-saat olup, bir saat boyunca sürekli olarak uygulanan bir watt'lık güç miktarıdır. **Enerji özetinde**birimler milivat-saat **MW-h**olarak görüntülenir.  
  
  ![Enerji kapasitesi, kullanılan güç, kullanılan toplam enerji](../profiling/media/energyprof-capcitypowerused.png "ENERGYPROF_CapcityPowerUsed")  
  
  Örneğin, bir tabletteki tam şarjlı bir pilde belli miktarda depolanmış enerji vardır. Bir ağ üzerinden iletişim kurma, değerleri hesaplama veya grafikleri görüntüleme gibi görevleri gerçekleştirmek için enerji kullanıldıkça, pilin gücü farklı oranlarda harcanır. Herhangi bir zaman dilimi için, harcanan güç toplamı da enerji ile ölçülür.  
  
## <a name="identify-scenarios-with-user-marks"></a><a name="BKMK_Identify_scenarios_with_user_marks"></a> Kullanıcı işaretleriyle senaryoları tanımla  
 Zaman çizelgesi cetvelindeki alanların tanımlanmasına yardımcı olması için profil oluşturma verilerinize *Kullanıcı işaretleri* ekleyebilirsiniz.  
  
 ![Zaman çizelgesinde Kullanıcı işaretleri](../profiling/media/profilers-usermarktimeline.png "PROFILERS_UserMarkTimeline")  
  
 İşaret, zaman çizelgesinde yöntemin yürütüldüğü zamanda turuncu bir üçgen olarak görünür. İşaret üzerinde beklediğinizde, ileti ve saat araç ipucu olarak görüntülenir. İki veya daha fazla kullanıcı işareti birbirine yakınsa, işaretler birleştirilir ve araç ipucu verileri birleştirilir. İşaretleri ayırmak için zaman çizelgesinde yakınlaştırma yapabilirsiniz.  
  
 **C#, Visual Basic, C++ koduna işaret ekleme**  
  
 C#, Visual Basic, C++ koduna kullanıcı işareti eklemek için, önce bir [Windows. Foundation. Diagnostics LoggingChannel](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.aspx) nesnesi oluşturun. Ardından, kodunuzda işaretlemek istediğiniz noktalarda [LoggingChannel. LogMessage](https://msdn.microsoft.com/library/windows/apps/dn264210.aspx) yöntemlerine çağrı ekleyin. Çağrılarındaki [LoggingLevel. Information](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.logginglevel.aspx) kullanın.  
  
 Yöntem yürütüldüğünde, profil oluşturma verilerine bir iletiyle birlikte bir kullanıcı işareti eklenir.  
  
> [!NOTE]
> - Windows. Foundation. Diagnostics LoggingChannel, [Windows. Foundation. ıloılabilir](https://msdn.microsoft.com/library/windows/apps/windows.foundation.iclosable.aspx) arabirimini uygular (C# ve vb 'de [System. IDisposable](https://msdn.microsoft.com/library/System.IDisposable.aspx) olarak tasarlanan). İşletim sistemi kaynaklarının sızmasını önlemek için, bir günlüğe kaydetme kanalı ile işiniz bittiğinde, [LoggingChannel. Close](https://msdn.microsoft.com/library/windows/apps/windows.foundation.diagnostics.loggingchannel.close.aspx)() (C# ve vb 'de Windows. Foundation. Diagnostics. LoggingChannel. Dispose ()) çağırın.  
>   - Her açık günlük kanalının benzersiz bir adı olması gerekir. Elde kalan bir kanal ile aynı adda yeni bir günlük kanalı oluşturmaya çalışmak özel duruma neden olur.  
  
 **JavaScript koduna işaretler ekleme**  
  
 Kullanıcı işaretleri eklemek için, kodunuzda işaretlemek istediğiniz noktalarda aşağıdaki kodu ekleyin:  
  
```  
if (performance && performance.mark) {  
    performance.mark(markDescription);  
}  
```  
  
 *MarkDescription* , kullanıcı işareti araç ipucunda görüntülenecek iletiyi içeren bir dizedir.  
  
## <a name="configure-your-environment-for-profiling"></a><a name="BKMK_Configure_your_environment_for_profiling"></a> Ortamınızı profil oluşturma için yapılandırma  
 İyi tahminler elde etmek için, pilden güç alan düşük güçlü cihazda uygulamanın enerji kullanımının profilini oluşturmak isteyebilirsiniz. Visual Studio bu cihazların çoğunda çalışmadığından, Visual Studio bilgisayarınızı cihaza, Visual Studio uzak araçlarını kullanarak bağlamanız gerekir. Uzaktaki bir cihaza bağlanmak için, hem Visual Studio projesini hem de uzak cihazı yapılandırmanız gerekir. Daha fazla bilgi için bkz. [uzak makinede Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md) .  
  
> [!TIP]
> - Windows Mağazası simulatorunda veya Visual Studio bilgisayarında enerji profili oluşturmanız önerilmez. Gerçek cihazda profil oluşturmak çok daha gerçekçi veriler sağlar.  
>   - Hedef cihazda profil oluşturmayı, kendi pilleriyle çalışırken gerçekleştirin.  
>   - Aynı kaynakları (ağ, CPU veya ekran) kullanabilecek diğer uygulamaları kapatın.  
  
## <a name="collect-energy-profile-data-for-your-app"></a><a name="BKMK_Collect_energy_profile_data_for_your_app"></a> Uygulamanız için enerji profili verilerini toplayın  
  
1. **Hata Ayıkla** menüsünde, **hata ayıklama olmadan Tanılamayı Başlat**' ı seçin.  
  
     ![Tanılama merkezinde enerji tüketimini seçin](../profiling/media/energyprof-diagnosticshub.png "ENERGYPROF_DiagnosticsHub")  
  
2. **Enerji tüketimini** seçin ve ardından **Başlat**' ı seçin.  
  
    > [!NOTE]
    > **Enerji tüketimi** profil oluşturucuyu başlattığınızda, VsEtwCollector.exe çalıştırmak için izninizi ısteyen bir **Kullanıcı hesabı denetim** penceresi görebilirsiniz. **Evet**' i seçin.  
  
3. Veri toplamak için uygulamanızda alıştırma yapın.  
  
4. Profil oluşturmayı durdurmak için, Visual Studio 'ya geri dönün (Alt + Tab) ve tanılama hub 'ı sayfasında **toplamayı durdur** ' u seçin.  
  
     ![Veri toplamayı durdur](../profiling/media/xamlprof-stopcollection.png "XAMLProf_StopCollection")  
  
     Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.  
  
## <a name="collect-energy-profile-data-for-an-installed-app"></a><a name="BKMK_Collect_energy_profile_data_for_an_installed_app"></a> Yüklü bir uygulama için enerji profili verilerini toplama  
 Enerji Tüketimi aracı yalnızca, bir Visual Studio çözümünden başlatılan veya Windows mağazasından yüklenen Windows Store 8.1 uygulamalarında çalıştırılabilir. Visual Studio 'da bir çözüm açıldığında, varsayılan hedef **Başlangıç projem**tir. Yüklü bir uygulamayı hedeflemek için:  
  
1. **Hedefi Değiştir** ' i seçin ve ardından **yüklü uygulama**' yı seçin.  
  
2. **Yüklü uygulama paketini Seç** listesinden hedefi seçin.  
  
3. Tanılama hub 'ı sayfasında **enerji tüketimini** seçin.  
  
4. Profil oluşturmaya başlamak için **Başlat** ' ı seçin.  
  
   Profil oluşturmayı durdurmak için, Visual Studio 'ya geri dönün (Alt + Tab) ve tanılama hub 'ı sayfasında **toplamayı durdur** ' u seçin.  
  
## <a name="analyze-energy-profile-data"></a><a name="BKMK_Analyze_energy_profile_data"></a> Enerji profili verilerini analiz etme  
 Enerji profili verileri Visual Studio belge penceresinde görüntülenir:  
  
 ![Enerji profili Oluşturucu rapor sayfası](../profiling/media/energyprof-all.png "ENERGYPROF_All")  
  
|Görüntü|Description|  
|-|-|  
|![1. Adım](../profiling/media/procguid-1.png "ProcGuid_1")|Rapor dosyası, Report*YYYYMMDD-SSMM*. diagsession olarak adlandırılır. Raporu kaydetmeye karar verirseniz adını değiştirebilirsiniz.|  
|![2. Adım](../profiling/media/procguid-2.png "ProcGuid_2")|Zaman çizelgesi profil oluşturma oturumunun uzunluğunu, uygulama yaşam döngüsü etkinleştirme olaylarını ve kullanıcı işaretlerini gösterir.|  
|![3. Adım](../profiling/media/procguid-3.png "ProcGuid_3")|Mavi çubukları sürükleyip zaman çizelgesinde bir bölgeyi seçerek, raporu zaman çizelgesinin bir bölümüyle sınırlandırabilirsiniz.|  
|![4. adım](../profiling/media/procguid-4.png "ProcGuid_4")|**Güç kullanımı** grafiği, profil oluşturma oturumu sırasında bir cihaz kaynağı nedeniyle oluşan güç çıktısındaki değişikliği görüntüleyen çok satırlı bir grafiktir. Enerji Tüketimi profil oluşturucusu CPU, ağ etkinliği ve ekran görüntüsü tarafından kullanılan gücü izler.|  
|![5. adım](../profiling/media/procguid-6.png "ProcGuid_6")|**Kaynaklar (açık/kapalı)** grafiğinde ağ enerji maliyetlerinin ayrıntıları sağlanmaktadır. **Ağ** çubuğu, ağ bağlantısının açık olduğu süreyi temsil eder. **Veri aktarımı** alt çubuğu, uygulamanın ağ üzerinden veri aldığı veya gönderdiği süredir.|  
|![6. adım](../profiling/media/procguid-6a.png "ProcGuid_6a")|**Enerji Kullanım Özeti** , seçili zaman çizelgesinde CPU, ağ etkinliği ve ekran görüntüsü tarafından kullanılan toplam enerji miktarının orantılı miktarını gösterir.|  
  
 **Enerji profili verilerini analiz etmek için**  
  
 Kaynağın gücünün tepe noktasına vardığı bir alan bulun. Tepe noktası alanını, uygulamanızın işlevselliğiyle ilişkilendirin. Sonra zaman çizelgesindeki denetim çubuklarını kullanarak, zaman çizelgesinde alanı yakınlaştırın. Ağ kullanımına odaklandıysanız, ağ bağlantısının açık olduğu zamanı, uygulamanın bağlantı üzerinden veri aldığı veya aktaran zamana göre karşılaştırmak için **kaynaklar (açık/kapalı)** grafiğinde **ağ** düğümünü genişletin. Ağın gereksiz yere açık kaldığı süreyi azaltmak çok etkili bir optimizasyondur.  
  
## <a name="optimize-energy-use"></a><a name="BKMK_Optimize_energy_use"></a> Enerji kullanımını iyileştirin  
 Ağ bağlantılarında veri aktarmaktan başka, bağlantı başlatma, sürdürme ve kapatma ile ilgili enerji maliyetleri de vardır. Bazı ağlar veri gönderildikten veya alındıktan sonra, tek bağlantı üzerinden daha fazla veri iletimine olanak sağlamak için bağlantıyı bir süre daha sürdürür. Uygulamanızın bağlantıyla etkileşim kurma şeklini incelemek için **kaynaklar (açık/kapalı)** bölmesini kullanabilirsiniz.  
  
 ![&#41; bölmedeki&#47;&#40;kaynaklar](../profiling/media/energyprof-resources.png "ENERGYPROF_Resources")  
  
 **Ağ** ve **veri aktarımı** çubuklar, bir dizi küçük veri paketini zaman zaman aktarmak için bağlantının açık olduğunu gösterip, verileri tek bir iletime göndermek için toplu olarak kullanabilir, ağın açık olduğu süreyi azaltabilir ve böylece enerji maliyetlerini kaydedebilirsiniz.  
  
 ![Enerji tüketimi Özet bölmesi](../profiling/media/energyprof-summary.png "ENERGYPROF_Summary")  
  
 Ekranın enerji giderleri üzerinde daha az denetiminiz vardır. Çoğu ekranlar açık renkleri görüntülemek için koyu renklere göre daha fazla enerji harcar ve dolayısıyla koyu renk arka plan kullanmak giderleri azaltmanın bir yoludur.  
  
## <a name="other-resources"></a><a name="BKMK_Other_resources"></a> Diğer kaynaklar  
  
- Windows Geliştirme Merkezi 'ndeki [C#/vb/c + + ve xaml](https://msdn.microsoft.com/0ee0b706-8432-4d49-9801-306ed90764e1) ve [JavaScript ve HTML](https://msdn.microsoft.com/372afa6a-1c7c-4657-967d-03a77cd8e933) için **bağlantı durumu ve maliyet yönetimi** bölümlerine, uygulamanızın ağ trafiği maliyetini en aza indirmek Için kullanabileceği ağ bağlantısı bilgilerini sağlayan Windows API 'leri açıklanır.  
  
     Windows Mağazası uygulamaları için Visual Studio simulator, ağ bilgi API'lerinin veri bağlantısı özelliklerinin simulasyonunu yapmanıza olanak sağlar. Bkz [. benzeticide Windows Mağazası uygulamalarını çalıştırma](../debugger/run-windows-store-apps-in-the-simulator.md)  
  
- **JavaScript Işlev zamanlaması** ve **CPU kullanımı** araçları, VERIMSIZ işlevler nedeniyle, CPU yükünü azaltmanıza yardımcı olabilir. Bkz. [CPU kullanımını çözümleme](../profiling/analyze-cpu-usage-in-a-windows-universal-app.md).
