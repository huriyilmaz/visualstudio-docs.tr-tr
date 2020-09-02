---
title: Kayıtlı IntelliTrace verilerini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
caps.latest.revision: 112
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f6047e6104467b5b0516fba26fc39f402dfaac9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75845655"
---
# <a name="using-saved-intellitrace-data"></a>Kayıtlı IntelliTrace verilerini kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

IntelliTrace günlük (. iTrace) dosyasından hata ayıklamayı başlattığınızda uygulamanızın yürütmesindeki belirli noktalara gidin. Bu dosya, uygulamanız çalışırken IntelliTrace 'in kaydettiği performans olayları, özel durumlar, iş parçacıkları, test adımları, modüller ve diğer sistem bilgilerini içerebilir.  
  
 Bilgisayarınızda yüklü olduğundan emin olun:  
  
- Uygulama kodunuz için eşleşen kaynak dosyalar ve sembol (. pdb) dosyaları. Aksi halde, Visual Studio kaynak konumları çözümleyemez ve "semboller bulunamadı" iletisini gösterir. Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) ve [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).  
  
- Geliştirme bilgisayarınızda veya başka bir bilgisayarda. iTrace dosyaları açmak için Visual Studio Enterprise (profesyonel veya Community Edition değil)  
  
- Şu kaynaklardan birinden bir. iTrace dosyası:  
  
    |**Kaynak**|**Bakýn**|  
    |----------------|-------------|  
    |Visual Studio Enterprise (Professional veya Community Edition) bir IntelliTrace oturumu|[IntelliTrace Özellikleri](../debugger/intellitrace-features.md)|  
    |Microsoft Test Yöneticisi bir test oturumu. Bu, bir. iTrace dosyasını Team Foundation Server iş öğesine ekler.|[El ile testlerde daha fazla tanılama verisi toplayın](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)|  
    |ASP.NET Web Apps ve dağıtımda çalışan SharePoint uygulamaları için tek başına veya System Center 2012 R2 Operations Manager ile Microsoft Monitoring Agent|-   [Dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md)<br />-   [System Center 2012 R2 'deki yenilikler Operations Manager](https://technet.microsoft.com/library/dn249700.aspx)|  
  
## <a name="what-do-you-want-to-do"></a><a name="GetStarted"></a> Ne yapmak istiyorsunuz?  
  
- [Bir IntelliTrace günlüğü açın](#Open)  
  
- [IntelliTrace günlüğünü anlayın](#Understand)  
  
- [IntelliTrace günlüğünden hata ayıklamayı Başlat](#StartDebugging)  
  
## <a name="open-an-intellitrace-log"></a><a name="Open"></a> Bir IntelliTrace günlüğü açın  
 Visual Studio Enterprise olan bir bilgisayarda. iTrace dosyasını açın.  
  
- Visual Studio dışında. iTrace dosyasına çift tıklayın veya dosyayı Visual Studio içinde açın.  
  
     \- veya  
  
- . İTrace dosyası Team Foundation Server iş öğesine eklenmişse, iş öğesinde şu adımları izleyin:  
  
  - **Tüm bağlantılar**altında. iTrace dosyasını bulun. Açın.  

    \- veya  

  - Yeniden **üretme adımları**altında **IntelliTrace** bağlantısını seçin.  
  
> [!TIP]
> Hata ayıklama sırasında IntelliTrace dosyasını kapattıysanız, kolayca yeniden açabilirsiniz. **Hata Ayıkla** menüsüne gidin, **IntelliTrace**' i ve **günlük özetini göster**' i seçin. **IntelliTrace** penceresinde **günlük özetini göster** ' i de seçebilirsiniz. Bu yalnızca IntelliTrace ile hata ayıklarken kullanılabilir.  
  
## <a name="understand-the-intellitrace-log"></a><a name="Understand"></a> IntelliTrace günlüğünü anlayın  
 . İTrace dosyasındaki aşağıdaki bölümlerden bazıları yalnızca belirli bir kaynaktaki verileri (örneğin, Test Yöneticisi veya SharePoint uygulamalarından) topladıysanız görünür.  
  
|**Section**|**Vardır**|**Koleksiyon kaynağı**|  
|-----------------|------------------|---------------------------|  
|[Performans Ihlalleri](#Performance)|Yapılandırılan eşiği aşan işlev çağrılarına sahip performans olayları|IIS 'de barındırılan ASP.NET Web Apps için tek başına veya System Center 2012 R2 Operations Manager ile Microsoft Monitoring Agent|  
|[Özel durum verileri](#ExceptionData)|Her özel durum için tam çağrı yığını da dahil olmak üzere özel durumlar|Tüm kaynaklar|  
|[Çözümlemeleri](#Analysis)|Yalnızca SharePoint 2010 ve SharePoint 2013 uygulamaları için. Hata ayıklayıcı olayları, ULS olayları, işlenmemiş özel durumlar ve Microsoft Monitoring Agent kaydettiği diğer veriler gibi IntelliTrace ve SharePoint olaylarını tanılayın.|Microsoft Monitoring Agent, tek başına veya System Center 2012 R2 Operations Manager|  
|[Sistem bilgisi](#SystemInfo)|Konak sisteminin ayarları ve belirtimleri|Tüm kaynaklar|  
|[İş parçacıkları listesi](#ThreadsList)|Koleksiyon sırasında çalıştırılan iş parçacıkları|Tüm kaynaklar|  
|[Test verileri](#TestData)|Test adımları ve sonuçları test oturumundan|Test Yöneticisi|  
|[Modül](#Modules)|Hedef işlemin yüklendikleri sırada yüklediği modüller.|Tüm kaynaklar|  
  
 Her bölümde bilgi bulmanıza yardımcı olacak bazı ipuçları aşağıda verilmiştir:  
  
- Verileri sıralamak için bir sütun üst bilgisi seçin.  
  
- Verileri filtrelemek için arama kutusunu kullanın. Düz metin arama, zaman sütunları hariç tüm sütunlarda çalışmaktadır. Ayrıca, aramaları sütun başına bir filtreye sahip belirli bir sütuna göre filtreleyebilirsiniz. Boşluk olmadan sütun adını, iki nokta üst üste (**:**) ve arama değerini yazın. Başka bir sütun ve arama değeri eklemek için bunu noktalı virgül (**;**) ile izleyin.  
  
     Örneğin, **Açıklama** sütununda "yavaş" kelimesiyle ilgili performans olaylarını bulmak için şunu yazın:  
  
     `Description:slow`  
  
## <a name="start-debugging-from-an-intellitrace-log"></a><a name="StartDebugging"></a> IntelliTrace günlüğünden hata ayıklamayı Başlat  
  
### <a name="performance-violations"></a><a name="Performance"></a> Performans Ihlalleri  
 Uygulamanız için kaydedilen performans olaylarını gözden geçirin. Sık gerçekleşmeyecek olayları gizleyebilirsiniz.  
  
##### <a name="to-start-debugging-from-a-performance-event"></a>Bir performans olayından hata ayıklamayı başlatmak için  
  
1. **Performans ihlalleri**altında, kaydedilen performans olaylarını, bunların toplam yürütme sürelerini ve diğer olay bilgilerini gözden geçirin. Sonra belirli performans olayı sırasında çağrılan yöntemlerde fazla araştırma yapın.  
  
     ![Performans olayı ayrıntılarını görüntüleme](../debugger/media/ffr-itsummarypageperformance.png "FFR_ITSummaryPagePerformance")  
  
     Ayrıca, olayı çift tıklatabilirsiniz.  
  
2. Olay sayfasında, bu çağrılar için yürütme zamanını gözden geçirin. Yürütme ağacında yavaş bir çağrı bulun.  
  
     İç içe ya da başka şekilde birden fazla çağrınız varsa, en yavaş çağrılar kendi bölümünde görüntülenir.  
  
3. Bu noktada kaydedilen tüm iç içe çağrıları ve parametre değerlerini gözden geçirmek için o çağrıyı genişletin.  
  
     (Klavye: iç içe bir çağrıyı göstermek veya gizlemek Için sırasıyla **sağ ok** veya **sol ok** tuşuna basın. İç içe bir çağrının parametre değerlerini göstermek ve gizlemek için, **boşluk** tuşuna basın.)  
  
     Çağrıdan hata ayıklamayı başlatın.  
  
     ![Yöntem çağrısından hata ayıklamayı Başlat](../debugger/media/ffr-itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")  
  
     Ayrıca, çağrıya çift tıklayarak veya **ENTER** tuşuna basmanız yeterlidir.  
  
     Yöntem uygulama kodunuzda ise, Visual Studio bu yönteme gider.  
  
     ![Performans olayından uygulama koduna git](../debugger/media/ffr-itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")  
  
     Artık kaydedilen diğer değerleri, çağrı yığınını gözden geçirebilir, kodunuzda adım adım ilerlerseniz veya bu performans olayı sırasında çağrılan [diğer yöntemler arasında "zamanda" geriye veya ileri doğru gitmek](../debugger/intellitrace.md) için **IntelliTrace** penceresini kullanabilirsiniz.  
  
### <a name="exception-data"></a><a name="ExceptionData"></a> Özel durum verileri  
 Uygulamanız için oluşturulan ve kaydedilen özel durumları gözden geçirin. Yalnızca en son özel durumu görmeniz için aynı türe ve çağrı yığınına sahip olan özel durumları gruplandırabilirsiniz.  
  
##### <a name="to-start-debugging-from-an-exception"></a>Bir özel durumdan hata ayıklamayı başlatmak için  
  
1. **Özel durum verileri**altında, kaydedilen özel durum olaylarını, türleri, iletileri ve özel durumların ne zaman oluştuğunu gözden geçirin. Kodu daha ayrıntılı incelemek için özel durumlar grubu içindeki en son olaydan başlayın.  
  
     ![Özel durum olayından hata ayıklamayı Başlat](../debugger/media/ffr-itsummarypageexception.png "FFR_ITSummaryPageException")  
  
     Ayrıca, olayı çift tıklatabilirsiniz. Olaylar gruplandırılmamışsa, **Bu olayın hatalarını ayıkla**' yı seçin.  
  
     Uygulama kodunuzda bir özel durum oluştuysa, Visual Studio özel durumun olduğu yere gider.  
  
     ![Özel durum olayından uygulama koduna git](../debugger/media/ffr-itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")  
  
     Artık kaydedilen diğer değerleri, çağrı yığınını gözden geçirebilir veya diğer kayıtlı olaylar, ilgili kod ve bu noktalarda kaydedilmiş değerler [arasında "zamanda" geriye veya ileri doğru gitmek](../debugger/intellitrace.md)için **IntelliTrace** penceresini kullanabilirsiniz.  
  
    |**Column**|**Şunu gösterir**|  
    |----------------|-------------------|  
    |**Tür**|Özel durumun .NET türü|  
    |Gruplandırılabilen özel durumlar veya Gruplandırılmamış özel durumlar için **ileti** Için **en yeni ileti**|Özel durum tarafından girilen ileti|  
    |Gruplanmış özel durum **sayısı**|Özel durumun kaç kez oluşturulduğu|  
    |Gruplandırılmamış özel durumlar için **Iş parçacığı kimliği**|Özel durumu oluşturan iş parçacığının KIMLIĞI|  
    |**En yeni olay saati** veya **Olay saati**|Özel durum oluştuğunda kaydedilen zaman damgası|  
    |**Çağrı yığını**|Özel durum için çağrı yığını.<br /><br /> Çağrı yığınını görmek için listeden bir özel durum seçin. Çağrı yığını, özel durum listesinin altında görüntülenir.|  
  
### <a name="analysis"></a><a name="Analysis"></a> Çözümlemeleri  
 SharePoint bağıntı KIMLIĞI kullanarak SharePoint 2010 ve SharePoint 2013 uygulamalarıyla ilgili sorunları tanılayın veya Microsoft Monitoring Agent bulunan işlenmemiş özel durumları gözden geçirin.  
  
- Eşleşen web isteğini ve olaylarını bulmak için bir SharePoint bağıntı KIMLIĞI kullanın. Bir olay seçin ve sonra olayın gerçekleştiği noktada ve hata ayıklamaya başlayın.  
  
- İşlenmemiş özel durumlar Microsoft Monitoring Agent, bir özel durum seçin ve sonra özel durumun oluştuğu noktada hata ayıklamayı başlatın.  
  
##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>SharePoint bağıntı kimliği ile hata ayıklamayı başlat  
  
1. SharePoint bağıntı KIMLIĞINI kaynağından kopyalayın.  
  
    Örneğin:  
  
    ![IntelliTrace &#45; SharePoint hatası &#45; bağıntı KIMLIĞI](../debugger/media/sharepointerror-intellitrace.png "SharePointError_IntelliTrace")  
  
2. . İTrace dosyasını açın, ardından **analiz** ' a gidin ve eşleşen web isteğini ve kayıtlı olayları gözden geçirmek için SHAREPOINT bağıntı kimliği ' ni girin.  
  
    ![IntelliTrace günlüğü &#45; SharePoint bağıntı KIMLIĞI girin](../debugger/media/entersharepointcorrelationid.png "Entersharepointbağıntıkimliği")  
  
3. **Istek olayları**' nın altında, olayları inceleyin. En üstten başlayarak olaylar gerçekleşdikleri sırada görüntülenir.  
  
   1. Ayrıntılarını görmek için bir olay seçin.  
  
   2. Olayın gerçekleştiği noktada hata ayıklamayı başlatmak için **hata ayıklamayı Başlat** ' ı seçin.  
  
      ![IntelliTrace günlük dosyası &#45; Web isteği &#43; olaylarını görüntüleme](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")  
  
   Bu tür SharePoint olaylarını IntelliTrace olaylarıyla birlikte görebilirsiniz:  
  
- **Kullanıcı profili olayları**  
  
     Bu olaylar SharePoint bir kullanıcı profili yüklediğinde ve Kullanıcı profili özellikleri okunmasından veya değiştirildiğinde gerçekleşir.  
  
- **Birleşik günlüğe kaydetme sistemi (ULS) olayları**  
  
     Microsoft Monitoring Agent, SharePoint ULS olaylarının bir alt kümesini ve bu alanları kaydeder:  
  
    |**IntelliTrace alanı**|**SharePoint ULS alanı**|  
    |----------------------------|------------------------------|  
    |**Numarasını**|**Even**|  
    |**Düzeyde**|**Düzeyde**|  
    |**Kategori Kimliği**|**Kategori Kimliği**|  
    |**Kategori**|**Kategori**|  
    |**Alan**|**Ürün**|  
    |**Çıktı**|**İleti**|  
    |**Bağıntı kimliği**|**Bağıntı kimliği**|  
  
##### <a name="start-debugging-from-an-unhandled-exception"></a>İşlenmemiş bir özel durumdan hata ayıklamayı başlat  
  
1. Özel durum için bir SharePoint bağıntı KIMLIĞI seçin. Özel durumlar türe ve çağrı yığınına göre gruplandırılır.  
  
2. Seçim Bir özel durum grubu için çağrı yığınını görmek için **çağrı yığınını** genişletin.  
  
3. Özel durumun oluştuğu noktada hata ayıklamayı başlatmak için **hata ayıklama özel durumunu** seçin.  
  
    ![IntelliTrace log &#45; SharePoint işlenmemiş özel durumları](../debugger/media/sharepointunhandledexceptions-intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")  
  
   İzlenecek yol için bkz. [Izlenecek yol: IntelliTrace kullanarak bir SharePoint uygulamasında hata ayıklama](https://msdn.microsoft.com/library/4bd80d2f-f680-4bf4-81c3-f14e8185f6a4). Aracının kaydettiği veri türleri için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).  
  
### <a name="threads-list"></a><a name="ThreadsList"></a> İş parçacıkları listesi  
 Hedef işlemde çalıştırılan kayıtlı iş parçacıklarını inceleyin. Seçili bir iş parçacığında ilk geçerli IntelliTrace olayından hata ayıklamaya başlayabilirsiniz.  
  
##### <a name="to-start-debugging-from-a-specific-thread"></a>Belirli bir iş parçacığından hata ayıklamaya başlamak için  
  
1. **Iş parçacıkları listesinde**bir iş parçacığı seçin.  
  
2. **Iş parçacıkları listesinin**en altında, **hata ayıklamayı Başlat**' ı seçin. Ayrıca, bir iş parçacığına çift tıklayabilirsiniz.  
  
    Uygulamanın başladığı yerden hata ayıklamaya başlamak için **ana Iş parçacığı**' ne çift tıklayın. [IntelliTrace özelliklerine](../debugger/intellitrace-features.md)bakın.  
  
   Kullanıcının oluşturduğu iş parçacığı verileri, bir sunucunun oluşturduğu ve IIS tarafından barındırılan Web uygulamaları için yönettiği iş parçacıklarından daha faydalı olabilir.  
  
|**Column**|**Şunu gösterir**|  
|----------------|-------------------|  
|**ID**|İş parçacığı KIMLIK numarası|  
|**Ad**|İş parçacığı adı. Adlandırılmamış iş parçacıkları "" olarak görünür \<No Name> .|  
|**Başlangıç Zamanı**|İş parçacığının oluşturulduğu zaman|  
|**Bitiş zamanı**|İş parçacığının tamamlandığı zaman|  
  
### <a name="test-data"></a><a name="TestData"></a> Test verileri  
 Uygulamanızı test ederken kaydedilen Test Yöneticisi IntelliTrace verilerini inceleyin.  
  
##### <a name="to-start-debugging-from-a-specific-test-step"></a>Belirli bir test adımından hata ayıklamayı başlatmak için  
  
1. **Test adımları kılavuzunu**genişlet. Bir test adımı seçin.  
  
2. **Test adımları kılavuzunun**en altında, **hata ayıklamayı Başlat**' ı seçin. Ayrıca, bir test adımına çift tıklayabilirsiniz.  
  
     Bu, seçilen test adımından sonra ilk geçerli IntelliTrace olayından hata ayıklamayı başlatır.  
  
     Test verileri mevcut olduğunda, IntelliTrace test çalıştırmasını gerçekleştirmek için kullanılan ilişkili Team Foundation Server derlemesini çözümlemeye çalışır. Yapı bulunursa, uygulamanın ilişkili sembolleri otomatik olarak çözümlenir.  
  
|**Alan**|**Şunu gösterir**|  
|---------------|-------------------|  
|**Test oturumu**|Kaydedilen test oturumları. Genellikle yalnızca bir tane vardır. Test verileri el ile araştırmacı test kullanılarak oluşturulduysa bu liste boştur.|  
|**Test çalışması**|Seçili test oturumundan test çalışmaları. Test verileri el ile araştırmacı test kullanılarak oluşturulduysa bu liste boştur.|  
|**Test adımları Kılavuzu**|Pass veya fail test sonucuyla kaydedilen test adımları|  
  
### <a name="system-info"></a><a name="SystemInfo"></a> Sistem bilgisi  
 Bu bölümde, uygulamayı barındıran sistemle ilgili ayrıntılar gösterilir; Örneğin, donanım, işletim sistemi, ortam ve işleme özgü bilgiler.  
  
### <a name="modules"></a><a name="Modules"></a> Modüler  
 Bu bölümde, hedef işlemin yüklendiği modüller gösterilmektedir. Modüller yüklendikleri sırada görüntülenir.  
  
|**Column**|**Şunu gösterir**|  
|----------------|-------------------|  
|**Modül Adı**|Modül dosyası adı|  
|**Modül yolu**|Modülün yüklendiği disk konumu|  
|**Modül KIMLIĞI**|Sürüme özgü olan modülün benzersiz tanıtıcısı ve eşleşen sembol (PDB) dosyalarına katkıda bulunur. Bkz. [simge (. pdb) dosyalarını ve kaynak dosyaları bulma](https://msdn.microsoft.com/05384c85-d264-4e18-abaa-aa482ab25470).|  
  
### <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?  
 [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)  
  
 [IntelliTrace Özellikleri](../debugger/intellitrace-features.md)  
  
 [El ile testlerde daha fazla tanılama verisi toplayın](https://msdn.microsoft.com/library/bb5a2cc0-84f5-4dfe-9560-ca3d313aefd2)  
  
 [IntelliTrace](../debugger/intellitrace.md)  
  
#### <a name="forums"></a>Forumlar  
 [Visual Studio Hata Ayıklayıcısı](https://social.msdn.microsoft.com/Forums/vsdebug)  
  
#### <a name="guidance"></a>Rehber  
 [Visual Studio 2012 ile sürekli teslim için test etme – Bölüm 6: test araç kutusu](https://msdn.microsoft.com/library/jj159337.aspx)
