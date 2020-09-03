---
title: Hata ayıklayıcı Ile veya olmadan Profil Oluşturma Araçları çalıştırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fb07e9bc6c308e27e3ad054c5aeb0b12c092054
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534010"
---
# <a name="running-profiling-tools-with-or-without-the-debugger"></a>Hata Ayıklayıcı ile veya Hata Ayıklayıcı Olmadan Profil Oluşturma Araçlarını Çalıştırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio artık, bazıları hata ayıklayıcı ile veya olmayan bir dizi performans aracı sunuyor (örneğin, **CPU kullanımı** ve **bellek kullanımı**). Hata ayıklayıcı olmayan performans araçları sürüm yapılandırmalarında çalıştırılmak üzere tasarlanmıştır. hata ayıklayıcı tümleşik araçlar hata ayıklama yapılandırmalarında çalıştırılmak üzere tasarlanmıştır.  
  
## <a name="should-i-run-the-tool-with-or-without-the-debugger"></a>Aracı hata ayıklayıcı olmadan mi yoksa çalıştırmalıyım?  
 Hata ayıklayıcı ile tümleşik performans araçları, hata ayıklayıcı olmayan birçok aracı yapmanızı sağlar; örneğin kesme noktaları ayarlayabilir ve değişken değerlerini inceleyebilirsiniz. Hata ayıklayıcı olmayan araçlar, sunulan uygulamanın kullanıcılarının göreceği bir deneyim sunar.  
  
 Amacınıza uygun bir araç türü konusunda karar vermenize yardımcı olabilecek bazı sorular aşağıda verilmiştir:  
  
1. Sorun uygulama geliştirilirken mi bulundu, yoksa yayımlanmış sürümde mi bulundu?  
  
     Geliştirme sırasında ilgilendiğiniz sorun bulunursa, büyük olasılıkla bir sürüm derlemesinde performans araçlarını çalıştırmanız gerekmez. Yayın sürümünde bulunursa, sorunu bir sürüm yapılandırmasıyla yeniden oluşturmanız ve ardından hata ayıklayıcının daha fazla araştırma için yardımcı olup olmadığına karar vermeniz gerekir.  
  
2. Sorun CPU yoğunluklu işlemden kaynaklanıyor mu?  
  
     Birçok sorun, dosya g/ç veya ağ yanıt verme gibi dış performans sorunlarından kaynaklanır, bu nedenle performans araçlarını hata ayıklayıcıya da olmadan çalıştırıp çalıştırmadığınızda çok daha fazla farklılık yapmamamalıdır. Sorununuz CPU yoğun çağrılardan kaynaklanıyorsa, yayın ve hata ayıklama yapılandırmalarının arasındaki fark önemli ölçüde olabilir ve hata ayıklayıcı ile tümleşik araçları kullanmadan önce yayın derlemesinde sorunun mevcut olup olmadığını denetlemeniz gerekir  
  
3. Performansı tam olarak ölçmenize mi, yoksa yaklaşık bir sayı kabul etmeniz mi gerekiyor?  
  
     Hata ayıklama derlemeleri, sürüm derlemelerinin sağladığı belirli iyileştirmeler yoktur, örneğin işlev çağrıları ve sabitler, kullanılmayan kod yollarını ayıklamalar ve hata ayıklayıcı tarafından kullanılamayacak yollarla değişkenleri depolar. Hata ayıklayıcı, hata ayıklama için gerekli olan belirli işlemleri gerçekleştirdiğinden (örneğin, özel durum ve modül yükleme olayları) performans sürelerini değiştirir. Bu nedenle, hata ayıklayıcı ile tümleşik araçlarındaki performans numaraları yalnızca onlarca milisaniye içinde doğru olur. Hata ayıklayıcı olmayan araçlarla yayın yapılandırmalarının performans numaraları çok daha kesindir.  
  
## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Hata ayıklarken profil oluşturma verilerini topla  
 Aşağıdaki bölüm yerel olarak hata ayıklama ile ilgilidir. Daha sonraki bölümlerde, bir cihazda hata ayıklama veya uzaktan hata ayıklama hakkında bilgi edinebilirsiniz.  
  
1. Hata ayıklamak istediğiniz projeyi açın, ardından hata **Ayıkla/hata ayıklamayı Başlat** **(ya da** araç çubuğundan veya **F5**' i Başlat) seçeneğine tıklayın.  
  
2. **Tanılama araçları** penceresi devre dışı bırakılmadığı takdirde otomatik olarak görünür. Pencereyi yeniden getirmek için **Hata Ayıkla/Windows/tanılama araçları göster**' e tıklayın.  
  
3. İçin veri toplamak istediğiniz senaryoları çalıştırın.  
  
    Oturumu çalıştırırken olaylar, işlem belleği ve CPU kullanımı hakkındaki bilgileri görebilirsiniz.  
  
    Aşağıdaki grafikte, Visual Studio 2015 güncelleştirme 1 ' deki **Tanılama araçları** penceresi gösterilmektedir:  
  
    ![DiagnosticTools&#45;güncelleştirme 1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-güncelleştirme 1")  
  
4. Araç çubuğundaki **araçları seç** ayarı Ile **bellek kullanımı** veya **CPU kullanımı** (ya da her ikisi) görmeyi seçebilirsiniz. Visual Studio Enterprise çalıştırıyorsanız, **Araçlar/Seçenekler/IntelliTrace**' de IntelliTrace 'i etkinleştirebilir veya devre dışı bırakabilirsiniz.  
  
5. Hata ayıklamayı durdurduğunuzda Tanılama oturumu sonlanır.  
  
   Visual Studio 2015 güncelleştirme 1 ' de, **Tanılama araçları** penceresi ilgilendiğiniz olaylara odaklanmanıza daha kolay hale getirir.   Olay adları artık kategori ön ekleri (**hareket**, **program çıktısı**, **kesme noktası**, **Dosya** vb.) ile gösteriliyor, böylece belirli bir kategorinin listesini hızlıca tarayabilir veya ilgilendiğiniz kategorileri atlayabilirsiniz.  
  
   Bu pencerede artık, olay listesinde herhangi bir yerde belirli bir dizeyi bulabilmeniz için bir arama kutusu vardır. Örneğin, aşağıdaki grafik, bu dört olay ile eşleşen "install" dizesi için bir aramanın sonuçlarını gösterir:  
  
   ![DiagnosticsEventSearch](../profiling/media/diagnosticseventsearch.png "DiagnosticsEventSearch")  
  
   Ayrıca, penceredeki olayları da filtreleyerek pencere içinde izleyebilirsiniz. **Filtre** açılan listesinde, belirli olay kategorilerini denetleyebilir veya işaretini kaldırabilirsiniz:. Kategori adları, ön ek adlarıyla aynıdır.  
  
   ![DiagnosticEventFilter](../profiling/media/diagnosticeventfilter.png "DiagnosticEventFilter")  
  
   Daha fazla bilgi için, [Tanılama Araçları penceresinin Olaylar sekmesinde arama ve filtreleme](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/)bölümüne bakın.  
  
## <a name="collect-profiling-data-without-debugging"></a>Profil oluşturma verilerini hata ayıklama olmadan topla  
 Bazı profil araçları, çalıştırmak için yönetici ayrıcalıkları gerektirir. Visual Studio 'Yu yönetici olarak başlatabilir veya tanılama oturumunu başlattığınızda araçları yönetici olarak çalıştırmayı tercih edebilirsiniz.  
  
1. Projeyi Visual Studio'da açın.  
  
2. **Hata Ayıkla** menüsünde, performans profili **Oluşturucu...** (kısayol tuşu: alt + f2) öğesini seçin.  
  
3. Tanılama başlatma sayfasında, oturumda çalıştırılacak bir veya daha fazla araç seçin. Yalnızca proje türü, işletim sistemi ve programlama dili için geçerli olan araçlar görüntülenir. Bir tanılama aracı seçtiğinizde, aynı tanılama oturumunda çalıştırılabilen araçlara yönelik seçimler devre dışı bırakılır. Seçimlerinizin bir C# Windows Evrensel uygulaması için nasıl görünebileceğini aşağıda bulabilirsiniz:  
  
    ![Tanılama araçlarını seçin](../profiling/media/diag-selecttool.png "DIAG_SelectTool")  
  
4. Tanılama oturumu başlatmak için **Başlat**' a tıklayın.  
  
5. Veri toplamak istediğiniz senaryoları çalıştırın.  
  
    Oturum çalıştırırken, bazı araçlar tanılama araçları başlatma sayfasında gerçek zamanlı verilerin grafiklerini görüntüler.  
  
    ![Performans ve tanılama fası üzerinde veri toplama](../profiling/media/pdhub-collectdata.png "PDHUB_CollectData")  
  
6. Tanılama oturumunu sonlandırmak için, **toplamayı durdur**' a tıklayın.  
  
   Tanılama oturumunda veri toplamayı durdurduğunuzda, veriler çözümlenir ve rapor tanılama sayfasında görüntülenir.  
  
   Ayrıca, tanılama araçları başlatma sayfasındaki son açılan listeden kaydedilmiş. Diagnostic oturum dosyalarını da açabilirsiniz.  
  
   ![Kayıtlı bir tanılama oturum dosyası açın](../profiling/media/pdhub-openexistingdiagsession.png "PDHUB_OpenExistingDiagSession")  
  
## <a name="the-profiling-report"></a>Profil oluşturma raporu  
 ![Tanılama araçları raporu](../profiling/media/diag-report.png "DIAG_Report")  
  
|Görüntü|Description|  
|-|-|  
|![1. Adım](../profiling/media/procguid-1.png "ProcGuid_1")|Zaman çizelgesi profil oluşturma oturumunun uzunluğunu, uygulama yaşam döngüsü etkinleştirme olaylarını ve kullanıcı işaretlerini gösterir.|  
|![2. Adım](../profiling/media/procguid-2.png "ProcGuid_2")|Mavi çubukları sürükleyip zaman çizelgesinde bir bölgeyi seçerek, raporu zaman çizelgesinin bir bölümüyle sınırlandırabilirsiniz.|  
|![3. Adım](../profiling/media/procguid-3.png "ProcGuid_3")|Bir araç, bir veya daha fazla ana grafik görüntüler. Tanılama oturumunuz birden çok araç ile oluşturulduysa, tüm ana grafikler görüntülenir.|  
|![4. adım](../profiling/media/procguid-4.png "ProcGuid_4")|Tek tek grafikleri daraltabilir ve genişletebilirsiniz.|  
|![5. adım](../profiling/media/procguid-6.png "ProcGuid_6")|Verileriniz birden çok araçtan bilgi içerdiğinde, araç ayrıntıları sekmeler altında toplanır.|  
|![6. adım](../profiling/media/procguid-6a.png "ProcGuid_6a")|Bir araç, bir veya daha fazla ayrıntı görünümüne sahip olabilir. Görünüm, zaman çizelgesinin seçili bölgesine göre filtrelenir.|  
  
## <a name="setting-the-analysis-target-to-another-device"></a>Analiz hedefini başka bir cihazla ayarlama  
 Visual Studio projesinden uygulamanızı başlatmanın yanı sıra, alternatif hedeflerde tanılama oturumları da çalıştırabilirsiniz. Örneğin, Windows uygulama mağazasından yüklenmiş uygulamanızın bir sürümünde performans sorunlarını tanılamak isteyebilirsiniz.  
  
 ![Tanılama araçları analiz hedefini seçin](../profiling/media/pdhub-chooseanalysistarget.png "PDHUB_ChooseAnalysisTarget")  
  
 Zaten bir cihazda yüklü olan uygulamaları başlatabilir veya zaten çalışmakta olan bazı uygulamalara tanılama araçlarını ekleyebilirsiniz. **Çalışan uygulamayı** veya **yüklü uygulamayı**seçtiğinizde, belirtilen dağıtım hedefinde bulunan uygulamaları bulan listeden uygulamayı seçersiniz.  
  
 ![Tanılama için çalışan veya yüklü bir uygulama seçin](../profiling/media/pdhub-selectrunningapp.png "PDHUB_SelectRunningApp")  
  
 **Internet Explorer**' ı seçtiğinizde, URL 'yi belirtirsiniz ve telefon dağıtımı hedefini değiştirebilirsiniz.  
  
 ![Internet Explorer 'da görüntülenecek URL 'yi belirtin](../profiling/media/pdhub-choosephoneanalysistarget.png "PDHUB_ChoosePhoneAnalysisTarget")  
  
## <a name="remote-debugging"></a>Uzaktan Hata Ayıklama  
 Bir uzak bılgısayarda veya tablette Tanılama oturumu çalıştırmak, Visual Studio uzak araçlarının uzak hedefte yüklü ve çalışır olmasını gerektirir. Masaüstü uygulamaları için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).  Windows Evrensel uygulamaları için bkz. [uzak makinede Windows Mağazası uygulamaları çalıştırma](../debugger/run-windows-store-apps-on-a-remote-machine.md).  
  
## <a name="blog-posts-and-msdn-articles-from-the-diagnostics-development-team"></a>Tanılama geliştirme ekibinden blog gönderileri ve MSDN makaleleri  
 [MSDN Magazine: Visual Studio 2015 ' de hata ayıklarken performansı çözümleme](https://msdn.microsoft.com/magazine/dn973013.aspx)  
  
 [MSDN Magazine: sorunları daha hızlı tanılamak için IntelliTrace kullanın](https://msdn.microsoft.com/magazine/dn973014.aspx)  
  
 [Blog gönderisi: Visual Studio 2015 ' de bellek kullanımı aracı ile olay Işleyicisi sızıntılarını tanılama](https://devblogs.microsoft.com/devops/diagnosing-event-handler-leaks-with-the-memory-usage-tool-in-visual-studio-2015/)  
  
 [Video: Microsoft Visual Studio Ultimate 2015 ' de IntelliTrace ile geçmiş hata ayıklama](https://channel9.msdn.com/Events/Ignite/2015/BRK3716)  
  
 [Video: Visual Studio 2015 kullanarak performans sorunlarını giderme](https://channel9.msdn.com/Events/Build/2015/3-731)  
  
 [PerfTips: Visual Studio ile hata ayıklarken bir bakışta performans bilgileri](https://devblogs.microsoft.com/devops/perftips-performance-information-at-a-glance-while-debugging-with-visual-studio/)  
  
 [Visual Studio 2015 Tanılama Araçları hata ayıklayıcı penceresi](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [Visual Studio Enterprise 2015 ' de IntelliTrace](https://devblogs.microsoft.com/devops/intellitrace-in-visual-studio-ultimate-2015/)
