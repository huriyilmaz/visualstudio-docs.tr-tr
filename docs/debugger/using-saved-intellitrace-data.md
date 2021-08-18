---
title: Kayıtlı IntelliTrace verilerini kullanma | Microsoft Docs
description: Belirli bir yürütme noktasında hata ayıklamayı başlatmak için bir IntelliTrace dosyası (. iTrace) kullanın. Dosya, uygulamanın bir çalıştırağından kaydedilen IntelliTrace 'in bilgilerini içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.norepro
helpviewer_keywords:
- iTrace files
- IntelliTrace, log files
- IntelliTrace log files
- .iTrace files
ms.assetid: 9f2cce86-345a-4e22-84ba-91542d81e67a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: a62e0714da65552eedc6ca989a5035cdcf655b8d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096836"
---
# <a name="using-saved-intellitrace-data-c-visual-basic-c"></a>Kayıtlı IntelliTrace verilerini kullanma (C#, Visual Basic, C++)

IntelliTrace günlük (. iTrace) dosyasından hata ayıklamayı başlattığınızda uygulamanızın yürütmesindeki belirli noktalara gidin. Bu dosya, uygulamanız çalışırken IntelliTrace 'in kaydettiği performans olayları, özel durumlar, iş parçacıkları, test adımları, modüller ve diğer sistem bilgilerini içerebilir.

 Bilgisayarınızda yüklü olduğundan emin olun:

- Uygulama kodunuz için eşleşen kaynak dosyalar ve sembol (. pdb) dosyaları. aksi takdirde, Visual Studio kaynak konumları çözemez ve "semboller bulunamadı" iletisini gösterir. Bkz. [simge (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) ve [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

- geliştirme bilgisayarınızda veya başka bir bilgisayarda. itrace dosyaları açmak için Visual Studio Enterprise (ancak Professional veya Community sürümler)

- Şu kaynaklardan birinden bir. iTrace dosyası:

    |**Kaynak**|**Bkz.**|
    |----------------|-------------|
    |Visual Studio Enterprise bir ıntellitrace oturumu (ancak Professional veya Community sürümlerde değil)|[IntelliTrace Özellikleri](../debugger/intellitrace-features.md)|
    |dağıtımda çalışan ASP.NET web uygulamaları ve SharePoint uygulamaları için tek başına veya System Center 2012 R2 Operations Manager ile Microsoft Monitoring Agent|-   [Dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md)<br />-   [System Center 2012 R2 'deki yenilikler Operations Manager](/previous-versions/system-center/system-center-2012-R2/dn249700(v=sc.12))|

## <a name="what-do-you-want-to-do"></a><a name="GetStarted"></a> Ne yapmak istiyorsunuz?

- [Bir IntelliTrace günlüğü açın](#Open)

- [IntelliTrace günlüğünü anlayın](#Understand)

- [IntelliTrace günlüğünden hata ayıklamayı Başlat](#StartDebugging)

## <a name="open-an-intellitrace-log"></a><a name="Open"></a> Bir IntelliTrace günlüğü açın
 Visual Studio Enterprise olan bir bilgisayarda. itrace dosyasını açın.

- Visual Studio dışında. itrace dosyasına çift tıklayın veya dosyayı Visual Studio içinde açın.

     \- veya

- . itrace dosyası Team Foundation Server iş öğesine eklenmişse, iş öğesinde şu adımları izleyin:

  - **Tüm bağlantılar** altında. iTrace dosyasını bulun. Açın.

    \- veya

  - Yeniden **üretme adımları** altında **IntelliTrace** bağlantısını seçin.

> [!TIP]
> Hata ayıklama sırasında IntelliTrace dosyasını kapattıysanız, kolayca yeniden açabilirsiniz. **Hata Ayıkla** menüsüne gidin, **IntelliTrace**' i ve **günlük özetini göster**' i seçin. **IntelliTrace** penceresinde **günlük özetini göster** ' i de seçebilirsiniz. Bu yalnızca IntelliTrace ile hata ayıklarken kullanılabilir.

## <a name="understand-the-intellitrace-log"></a><a name="Understand"></a> IntelliTrace günlüğünü anlayın
 . itrace dosyasındaki aşağıdaki bölümlerden bazıları yalnızca belirli bir kaynaktan (örneğin, SharePoint uygulamalardan) veri topladıysanız görünür.

|**Section**|**Vardır**|**Koleksiyon kaynağı**|
|-----------------|------------------|---------------------------|
|[Performans Ihlalleri](#Performance)|Yapılandırılan eşiği aşan işlev çağrılarına sahip performans olayları|ııs 'de barındırılan ASP.NET web apps için tek başına toplayıcı veya System Center 2012 R2 Operations Manager Microsoft Monitoring Agent|
|[Özel durum verileri](#ExceptionData)|Her özel durum için tam çağrı yığını da dahil olmak üzere özel durumlar|Tüm kaynaklar|
|[Çözümlemeleri](#Analysis)|yalnızca SharePoint 2010 ve SharePoint 2013 uygulamaları için. hata ayıklayıcı olayları, ULS olayları, işlenmemiş özel durumlar ve Microsoft Monitoring Agent kaydettiği diğer veriler gibi ıntellitrace ve SharePoint olaylarını tanılayın.|tek başına toplayıcı veya System Center 2012 R2 Operations Manager Microsoft Monitoring Agent|
|[Sistem bilgisi](#SystemInfo)|konak sisteminin Ayarlar ve belirtimleri|Tüm kaynaklar|
|[İş parçacıkları listesi](#ThreadsList)|Koleksiyon sırasında çalıştırılan iş parçacıkları|Tüm kaynaklar|
|[Modül](#Modules)|Hedef işlemin yüklendikleri sırada yüklediği modüller.|Tüm kaynaklar|
|[Web Isteği](#Modules)|üretim ııs web uygulamaları için web istek verileri ve 2010 SharePoint ve SharePoint 2013|Microsoft Monitoring Agent ve tek başına toplayıcı|

 Her bölümde bilgi bulmanıza yardımcı olacak bazı ipuçları aşağıda verilmiştir:

- Verileri sıralamak için bir sütun üst bilgisi seçin.

- Verileri filtrelemek için arama kutusunu kullanın. Düz metin arama, zaman sütunları hariç tüm sütunlarda çalışmaktadır. Ayrıca, aramaları sütun başına bir filtreye sahip belirli bir sütuna göre filtreleyebilirsiniz. Boşluk olmadan sütun adını, iki nokta üst üste (**:**) ve arama değerini yazın. Başka bir sütun ve arama değeri eklemek için bunu noktalı virgül (**;**) ile izleyin.

     Örneğin, **Açıklama** sütununda "yavaş" kelimesiyle ilgili performans olaylarını bulmak için şunu yazın:

     `Description:slow`

## <a name="start-debugging-from-an-intellitrace-log"></a><a name="StartDebugging"></a> IntelliTrace günlüğünden hata ayıklamayı Başlat

### <a name="performance-violations"></a><a name="Performance"></a> Performans Ihlalleri
 Uygulamanız için kaydedilen performans olaylarını gözden geçirin. Sık gerçekleşmeyecek olayları gizleyebilirsiniz.

##### <a name="to-start-debugging-from-a-performance-event"></a>Bir performans olayından hata ayıklamayı başlatmak için

1. **Performans ihlalleri** altında, kaydedilen performans olaylarını, bunların toplam yürütme sürelerini ve diğer olay bilgilerini gözden geçirin. Sonra belirli performans olayı sırasında çağrılan yöntemlerde fazla araştırma yapın.

     ![Performans olayı ayrıntılarını görüntüleme](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Ayrıca, olayı çift tıklatabilirsiniz.

2. Olay sayfasında, bu çağrılar için yürütme zamanını gözden geçirin. Yürütme ağacında yavaş bir çağrı bulun.

     İç içe ya da başka şekilde birden fazla çağrınız varsa, en yavaş çağrılar kendi bölümünde görüntülenir.

3. Bu noktada kaydedilen tüm iç içe çağrıları ve parametre değerlerini gözden geçirmek için o çağrıyı genişletin.

     (Klavye: iç içe bir çağrıyı göstermek veya gizlemek Için sırasıyla **sağ ok** veya **sol ok** tuşuna basın. İç içe bir çağrının parametre değerlerini göstermek ve gizlemek için, **boşluk** tuşuna basın.)

     Çağrıdan hata ayıklamayı başlatın.

     ![Yöntem çağrısından hata ayıklamayı Başlat](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Ayrıca, çağrıya çift tıklayarak veya **ENTER** tuşuna basmanız yeterlidir.

     Yöntem uygulama kodunuzda ise, Visual Studio bu yönteme gider.

     ![Performans olayından uygulama koduna git](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Artık kaydedilen diğer değerleri, çağrı yığınını gözden geçirebilir, kodunuzda adım adım ilerlerseniz veya bu performans olayı sırasında çağrılan [diğer yöntemler arasında "zamanda" geriye veya ileri doğru gitmek](../debugger/intellitrace.md) için **IntelliTrace** penceresini kullanabilirsiniz.

### <a name="exception-data"></a><a name="ExceptionData"></a> Özel durum verileri
 Uygulamanız için oluşturulan ve kaydedilen özel durumları gözden geçirin. Yalnızca en son özel durumu görmeniz için aynı türe ve çağrı yığınına sahip olan özel durumları gruplandırabilirsiniz.

##### <a name="to-start-debugging-from-an-exception"></a>Bir özel durumdan hata ayıklamayı başlatmak için

1. **Özel durum verileri** altında, kaydedilen özel durum olaylarını, türleri, iletileri ve özel durumların ne zaman oluştuğunu gözden geçirin. Kodu daha ayrıntılı incelemek için özel durumlar grubu içindeki en son olaydan başlayın.

     ![Özel durum olayından hata ayıklamayı Başlat](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

     Ayrıca, olayı çift tıklatabilirsiniz. Olaylar gruplanamamışsa Bu Olayda Hata **Ayıkla'ya seçin.**

     Uygulama kodunuzda bir özel durum oluştuysa, Visual Studio özel durumun olduğu yere gider.

     ![Bir özel durum olayından uygulama koduna gidin](../debugger/media/ffr_itsummarypageexceptiongotocode.png "FFR_ITSummaryPageExceptionGoToCode")

     Artık diğer kayıtlı değerleri, çağrı yığınını gözden geçirebilirsiniz veya **IntelliTrace** penceresini kullanarak diğer kayıtlı olaylar, ilgili kod ve zaman içinde bu noktalarda kaydedilen değerler arasında ["zamanda"](../debugger/intellitrace.md)geri veya ileri doğru ilerlemek için kullanabilirsiniz.

    |**Sütun**|**Şu sayfayı gösterir:**|
    |----------------|-------------------|
    |**Tür**|Özel durumun .NET türü|
    |**Gruplanmamış özel** durumlar için en yeni ileti **veya** gruplandırlanmamış özel durumlar için İleti|Özel durum tarafından sağlanan ileti|
    |**Gruplandı** özel durum sayısı|Özel durumun kaç kez atılan sayısı|
    |**Gruplanmamış** özel durumlar için iş parçacığı kimliği|Özel durumun neden olduğu iş parçacığının kimliği|
    |**En Yeni Olay Zamanı** veya **Olay Zamanı**|Özel durum atılan zaman damgası|
    |**Çağrı Yığını**|Özel durum için çağrı yığını.<br /><br /> Çağrı yığınını görmek için listeden bir özel durum seçin. Çağrı yığını, özel durum listesinin altında görünür.|

### <a name="analysis"></a><a name="Analysis"></a> Analysis
 SharePoint bağıntı kimliği kullanarak SharePoint 2010 ve SharePoint 2013 uygulamalarıyla ilgili sorunları tanılar veya bulunan iş Microsoft Monitoring Agent gözden geçirin.

- Eşleşen web SharePoint ve olaylarını bulmak için bir bağıntı kimliği kullanın. Bir olay seçin ve ardından olayın nerede ve ne zaman meydana geldiğinde hata ayıklamaya başlayabilirsiniz.

- İş Microsoft Monitoring Agent özel durumlar bulduysanız, bir özel durum seçin ve ardından özel durumun nerede ve ne zaman olduğu noktasında hata ayıklamaya başlayabilirsiniz.

##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>SharePoint bağıntı kimliği ile hata ayıklamayı başlat

1. Kaynak SharePoint kimliğini kopyalayın.

    Örnek:

    ![IntelliTrace &#45; SharePoint hatası &#45; bağıntı kimliği](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")

2. .iTrace dosyasını açın, analiz'e gidin ve eşleşen web isteğini ve SharePoint kaydedilen olayları gözden geçirmek için veri bağıntı kimliğini girin. 

    ![IntelliTrace günlüğü &#45; bağıntı SharePoint girin](../debugger/media/entersharepointcorrelationid.png "Entersharepointbağıntıkimliği")

3. Olay **İsteği altında** olayları incele. En üstten başlayarak olaylar gerçekleştik düzende görünür.

   1. Ayrıntılarını görmek için bir olay seçin.

   2. Hata **ayıklamayı olayın** meydana olduğu noktada başlatmak için Hata Ayıklamayı Başlat'ı seçin.

      ![IntelliTrace günlük dosyası &#45; Web isteği günlük &#43; görüntüleme](../debugger/media/entersharepointcorrelationid2.png "EnterSharePointCorrelationID2")

   IntelliTrace olaylarıyla SharePoint bu tür olayları da görebilir:

- **Kullanıcı profili olayları**

     Bu olaylar, bir SharePoint profili yüklerken ve kullanıcı profili özellikleri okundu veya değiştiriken olur.

- **Birleşik Günlük Sistemi (ULS) olayları**

     Microsoft Monitoring Agent ULS olaylarının SharePoint alt kümesini ve şu alanları kaydedmektedir:

    |**IntelliTrace alanı**|**SharePoint ULS alanı**|
    |----------------------------|------------------------------|
    |**ID**|**Eventıd**|
    |**Düzey**|**Düzey**|
    |**Kategori Kimliği**|**Kategori Kimliği**|
    |**Kategori**|**Kategori**|
    |**Alan**|**Ürün**|
    |**Çıktı**|**İleti**|
    |**Bağıntı Kimliği**|**Bağıntı Kimliği**|

##### <a name="start-debugging-from-an-unhandled-exception"></a>İşlenmemiş bir özel durumdan hata ayıklamayı başlat

1. Özel durum SharePoint bağıntı kimliğini seçin. Özel durumlar türe ve çağrı yığınına göre gruplanır.

2. (İsteğe bağlı) Bir **özel durum** grubu için çağrı yığınını görmek için Çağrı Yığını'yı genişletin.

3. Özel **durumun nerede ve ne** zaman olduğu noktasında hata ayıklamaya başlamak için Hata Ayıklama Özel Durumu'u seçin.

    ![intelliTrace günlüğü &#45; SharePoint özel durumlar](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")

   Bir izlenecek yol için [bkz. IntelliTrace Kullanarak SharePoint Uygulamanın Hata Ayıklaması.](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md) Aracı tarafından kaydedilen veri türleri için bkz. [IntelliTrace Özellikleri.](../debugger/intellitrace-features.md)

### <a name="threads-list"></a><a name="ThreadsList"></a> İş Parçacıkları Listesi
 Hedef işlemde çalışan kayıtlı iş parçacıklarını inceleme. Seçilen iş parçacığında ilk geçerli IntelliTrace olayından hata ayıklamaya başlayabilirsiniz.

##### <a name="to-start-debugging-from-a-specific-thread"></a>Belirli bir iş parçacığından hata ayıklamaya başlamak için

1. İş **Parçacıkları Listesi altında** bir iş parçacığı seçin.

2. İş Parçacıkları **Listesi'nin alt kısmında** Hata **Ayıklamayı Başlat'ı seçin.** Ayrıca bir iş parçacığına çift tıklar.

    Uygulamanın başladığı yerden hata ayıklamaya başlamak için Ana İş **Parçacığı'ya çift tıklayın.** Bkz. [IntelliTrace Özellikleri.](../debugger/intellitrace-features.md)

   Kullanıcının oluşturduğu iş parçacığı verileri, bir sunucunun IIS tarafından barındırılan Web uygulamaları için oluşturduğu ve yönet olduğu iş parçacıklarından daha kullanışlı olabilir.

|**Sütun**|**Şu sayfayı gösterir:**|
|----------------|-------------------|
|**ID**|İş Parçacığı Kimliği numarası|
|**Ad**|İş parçacığı adı. Adlandırlanmamış iş parçacıkları " \<No Name> olarak görünür.|
|**Başlangıç Zamanı**|İş parçacığının oluşturulma zamanı|
|**Bitiş Zamanı**|İş parçacığının tamamlanma zamanı|

##### <a name="to-start-debugging-from-a-specific-test-step"></a>Belirli bir test adımdan hata ayıklamaya başlamak için

1. Test **Adımları Kılavuzu'alanını genişletin.** Bir test adımı seçin.

2. Test Adımları **Kılavuzu'nda hata ayıklamayı** **başlat'ı seçin.** Ayrıca bir test adımına çift tıklarsiniz.

     Bu, seçilen test adımından sonraki ilk geçerli IntelliTrace olayından hata ayıklamayı başlatır.

     Test verileri mevcut olduğunda IntelliTrace, test çalıştırması gerçekleştirmek Team Foundation Server ilişkili derleme derlemesini çözümlemeye çalışır. Derleme bulunursa, uygulamanın ilişkili sembolleri otomatik olarak çözümlenir.

|**Alan**|**Şu sayfayı gösterir:**|
|---------------|-------------------|
|**Test Oturumu**|Kaydedilen test oturumları. Genellikle yalnızca bir tanedir. Test verileri el ile keşif testi kullanılarak oluşturulduktan sonra bu liste boş olur.|
|**Test çalışması**|Seçili test oturumundan test çalışmaları. Test verileri el ile araştırmacı test kullanılarak oluşturulduysa bu liste boştur.|
|**Test adımları Kılavuzu**|Pass veya fail test sonucuyla kaydedilen test adımları|

### <a name="system-info"></a><a name="SystemInfo"></a> Sistem bilgisi
 Bu bölümde, uygulamayı barındıran sistemle ilgili ayrıntılar gösterilir; Örneğin, donanım, işletim sistemi, ortam ve işleme özgü bilgiler.

### <a name="modules"></a><a name="Modules"></a> Modüler
 Bu bölümde, hedef işlemin yüklendiği modüller gösterilmektedir. Modüller yüklendikleri sırada görüntülenir.

|**Sütun**|**Şunu gösterir**|
|----------------|-------------------|
|**Modül adı**|Modül dosyası adı|
|**Modül yolu**|Modülün yüklendiği disk konumu|
|**Modül KIMLIĞI**|Sürüme özgü olan modülün benzersiz tanıtıcısı ve eşleşen sembol (PDB) dosyalarına katkıda bulunur. Bkz. [simge (. pdb) dosyalarını ve kaynak dosyaları bulma](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).|

### <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?
 [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md)

 [IntelliTrace Özellikleri](../debugger/intellitrace-features.md)

 [El ile testlerde daha fazla tanılama verisi toplayın](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts&preserve-view=true)

 [IntelliTrace](../debugger/intellitrace.md)

#### <a name="forums"></a>Forumlar
 [Visual Studio Hata Ayıklayıcısı](https://social.msdn.microsoft.com/Forums/en-US/home)

#### <a name="guidance"></a>Rehber
 [Visual Studio 2012 ile sürekli teslim için test etme-bölüm 6: bir test araç kutusu](/previous-versions/msp-n-p/jj159337(v=pandp.10))
