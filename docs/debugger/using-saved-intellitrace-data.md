---
title: Kaydedilen IntelliTrace verilerini | Microsoft Docs
description: Belirli bir yürütme noktasında hata ayıklamaya başlamak için bir Intellitrace dosyası (.iTrace) kullanın. Dosya, Intellitrace'in uygulama çalıştırarak kaydettiği bilgileri içerir.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627824"
---
# <a name="using-saved-intellitrace-data-c-visual-basic-c"></a>Kaydedilen IntelliTrace verilerini kullanma (C#, Visual Basic, C++)

IntelliTrace günlüğü (.iTrace) dosyasından hata ayıklamaya başlarken, uygulamanın yürütülmesinde belirli noktalara gidin. Bu dosya, uygulama çalışırken IntelliTrace tarafından kaydedilen performans olaylarını, özel durumları, iş parçacıklarını, test adımlarını, modülleri ve diğer sistem bilgilerini içerebilir.

 Bilgisayarınızda yüklü olduğundan emin olun:

- Uygulama kodunuz için kaynak dosyaları ve sembol (.pdb) dosyalarını eşleştirme. Aksi Visual Studio, kaynak konumları çözümleyemezse ve "Semboller bulunamadı" iletisi gösterir. Bkz. [Sembol Belirtme (.pdb) ve Kaynak Dosyaları ve](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) [Dağıtımdan sonra sorunları tanılama.](../debugger/diagnose-problems-after-deployment.md)

- Visual Studio Enterprise .iTrace Professional açmak için geliştirme bilgisayarınızda veya başka bir bilgisayarda Professional veya Community sürümleri değil)

- Şu kaynaklardan bir .iTrace dosyası:

    |**Kaynak**|**Bkz.**|
    |----------------|-------------|
    |Visual Studio Enterprise'de intelliTrace oturumu (Professional veya Community değil)|[IntelliTrace Özellikleri](../debugger/intellitrace-features.md)|
    |Microsoft Monitoring Agent web uygulamaları ve dağıtımda çalışan SharePoint uygulamaları için System Center 2012 R2 Operations Manager ile ASP.NET veya tek başına|-   [Dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md)<br />-   [System Center 2012 R2 Operations Manager Için Operations Manager](/previous-versions/system-center/system-center-2012-R2/dn249700(v=sc.12))|

## <a name="what-do-you-want-to-do"></a><a name="GetStarted"></a> Ne yapmak istiyorsunuz?

- [IntelliTrace günlüğünü açma](#Open)

- [IntelliTrace günlüğünü anlama](#Understand)

- [IntelliTrace günlüğünden hata ayıklamaya başlama](#StartDebugging)

## <a name="open-an-intellitrace-log"></a><a name="Open"></a> IntelliTrace günlüğünü açma
 Dosyanın yer Visual Studio Enterprise .iTrace dosyasını açın.

- Dosyanın dışında .iTrace dosyasına çift Visual Studio veya dosyayı dosyanın içinden Visual Studio.

     \- veya -

- .iTrace dosyası bir iş Team Foundation Server bağlı ise, iş öğesinde şu adımları izleyin:

  - Tüm **Bağlantılar altında**.iTrace dosyasını bulun. Açın.

    \- veya -

  - Yeniden **Proje Adımları'nın** altında **IntelliTrace bağlantısını** seçin.

> [!TIP]
> Hata ayıklama sırasında IntelliTrace dosyasını kapattıysanız, dosyayı kolayca yeniden açabilirsiniz. Hata Ayıklama **menüsüne gidin,** **IntelliTrace**, Günlük Özetini **Göster'i seçin.** IntelliTrace **penceresinde Günlük Özetini** **Göster'i de seçebilirsiniz.** Bu yalnızca IntelliTrace ile hata ayıklama sırasında kullanılabilir.

## <a name="understand-the-intellitrace-log"></a><a name="Understand"></a> IntelliTrace günlüğünü anlama
 .iTrace dosyasındaki aşağıdaki bölümlerden bazıları yalnızca belirli bir kaynaktan veri toplanmışsa (örneğin, belirli bir SharePoint görüntülenir.

|**Section**|**Içerir**|**Koleksiyon Kaynağı**|
|-----------------|------------------|---------------------------|
|[Performans İhlalleri](#Performance)|Yapılandırılmış eşiği aşan işlev çağrılarını olan performans olayları|Microsoft Monitoring Agent toplayıcı veya IIS üzerinde barındırılan web uygulamaları için System Center 2012 R2 Operations Manager ASP.NET ile birlikte|
|[Özel Durum Verileri](#ExceptionData)|Her özel durum için tam çağrı yığını da dahil olmak üzere özel durumlar|Tüm kaynaklar|
|[Analysis](#Analysis)|Yalnızca SharePoint 2010 ve SharePoint 2013 uygulamaları için. Hata ayıklayıcı olayları SharePoint, ULS olayları, işlanmamış özel durumlar ve hata ayıklayıcının kaydettiği diğer veriler gibi IntelliTrace ve Microsoft Monitoring Agent tanılama.|Microsoft Monitoring Agent toplayıcı veya 2012 R2 System Center ile Operations Manager|
|[Sistem Bilgileri](#SystemInfo)|Ayarlar sisteminin özellikleri ve belirtimleri|Tüm kaynaklar|
|[İş Parçacıkları Listesi](#ThreadsList)|Koleksiyon sırasında çalışan iş parçacıkları|Tüm kaynaklar|
|[Modül](#Modules)|Hedef işlem tarafından yüklendiklerine göre yüklenen modüller.|Tüm kaynaklar|
|[Web İsteği](#Modules)|Üretim IIS web uygulamaları ve 2010 ve SharePoint 2013 için web SharePoint verileri|Microsoft Monitoring Agent ve tek başına toplayıcı|

 Aşağıda, her bölümdeki bilgileri bulanıza yardımcı olacak bazı ipuçları ve bulabilirsiniz:

- Verileri sıralamak için bir sütun üst bilgisi seçin.

- Verileri filtrelemek için arama kutusunu kullanın. Düz metin araması, saat sütunları dışındaki tüm sütunlarda çalışır. Ayrıca, aramaları sütun başına bir filtre ile belirli bir sütuna filtreleyebilirsiniz. Boşluk yazmadan sütun adını, iki nokta üst üste (**:**) ve arama değerini yazın. Başka bir sütun ve arama değeri eklemek **için bunu** noktalı virgül ( ; ) ile izleyin.

     Örneğin, Açıklama sütununda "yavaş" sözcüğüne sahip performans olaylarını **bulmak için** yazın:

     `Description:slow`

## <a name="start-debugging-from-an-intellitrace-log"></a><a name="StartDebugging"></a> IntelliTrace günlüğünden hata ayıklamaya başlama

### <a name="performance-violations"></a><a name="Performance"></a> Performans İhlalleri
 Uygulamanıza kaydedilen performans olaylarını gözden geçirme. Sık sık yaşanmaan olayları gizleysiniz.

##### <a name="to-start-debugging-from-a-performance-event"></a>Bir performans olayından hata ayıklamaya başlamak için

1. Performans **İhlalleri** altında kayıtlı performans olaylarını, bunların toplam yürütme zamanlarını ve diğer olay bilgilerini gözden geçirebilirsiniz. Sonra belirli performans olayı sırasında çağrılan yöntemlerde fazla araştırma yapın.

     ![Performans olayı ayrıntılarını görüntüleme](../debugger/media/ffr_itsummarypageperformance.png "FFR_ITSummaryPagePerformance")

     Ayrıca, olayı çift tıklatabilirsiniz.

2. Olay sayfasında, bu çağrılar için yürütme zamanını gözden geçirin. Yürütme ağacında yavaş bir çağrı bulun.

     İç içe ya da başka şekilde birden fazla çağrınız varsa, en yavaş çağrılar kendi bölümünde görüntülenir.

3. O anda kaydedilen iç içe geçmiş çağrıları ve parametre değerlerini gözden geçirmek için bu çağrıyı genişletin.

     (Klavye: İç içe bir çağrıyı göstermek veya gizlemek için **sırasıyla Sağ Ok veya** **Sol Ok** tuşuna basın. İç içe bir çağrı için parametre değerlerini göstermek ve gizlemek için Boşluk **tuşuna** basın.)

     Çağrısından hata ayıklamayı başlat.

     ![Yöntem çağrısından hata ayıklamayı başlatma](../debugger/media/ffr_itsummarypageperformancemethodscalled.png "FFR_ITSummaryPagePerformanceMethodsCalled")

     Ayrıca çağrıya çift tıklar veya **Enter** tuşuna basarak da tıklarsiniz.

     Yöntem uygulama kodunuzda ise, Visual Studio bu yönteme gider.

     ![Performans olayından uygulama koduna gidin](../debugger/media/ffr_itsummarypageperformancegotocode.png "FFR_ITSummaryPagePerformanceGoToCode")

     Artık diğer kayıtlı değerleri, çağrı yığınını gözden geçirebilir, kodunuz üzerinde adım atabilir veya **IntelliTrace** penceresini kullanarak bu performans olayı sırasında çağrılan diğer yöntemler arasında ["zamanda"](../debugger/intellitrace.md) geri veya ileri doğru ilerlemek için kullanabilirsiniz.

### <a name="exception-data"></a><a name="ExceptionData"></a> Özel Durum Verileri
 Uygulamanıza yönelik olarak atılan ve kaydedilen özel durumları gözden geçirme. Yalnızca en son özel durumu görmek için aynı türe ve çağrı yığınına sahip özel durumları grupabilirsiniz.

##### <a name="to-start-debugging-from-an-exception"></a>Özel bir özel durumdan hata ayıklamayı başlatmak için

1. Özel **Durum Verileri altında,** kayıtlı özel durum olaylarını, bunların türlerini, iletilerini ve özel durumların ne zaman olduğunu gözden geçirebilirsiniz. Kodu daha ayrıntılı incelemek için özel durumlar grubu içindeki en son olaydan başlayın.

     ![Özel durum olayından hata ayıklamayı başlatma](../debugger/media/ffr_itsummarypageexception.png "FFR_ITSummaryPageException")

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
 SharePoint bağıntı kimliği kullanarak SharePoint 2010 ve SharePoint 2013 uygulamalarıyla ilgili sorunları tanılar veya bulunan iş Microsoft Monitoring Agent gözden geçirme.

- Eşleşen web SharePoint ve olaylarını bulmak için bir bağıntı kimliği kullanın. Bir olay seçin ve ardından olayın nerede ve ne zaman meydana geldiğinde hata ayıklamaya başlayabilirsiniz.

- İş Microsoft Monitoring Agent özel durumlar bulduysanız, bir özel durum seçin ve ardından özel durumun nerede ve ne zaman olduğu noktasında hata ayıklamaya başlayabilirsiniz.

##### <a name="start-debugging-with-a-sharepoint-correlation-id"></a>SharePoint bağıntı kimliği ile hata ayıklamayı başlat

1. Bağıntı SharePoint kimliğini kaynağından kopyalayın.

    Örnek:

    ![IntelliTrace &#45; SharePoint hatası &#45; bağıntı kimliği](../debugger/media/sharepointerror_intellitrace.png "SharePointError_IntelliTrace")

2. .iTrace dosyasını açın, analiz'e gidin ve eşleşen web isteğini ve SharePoint olaylarını gözden geçirmek için veri bağıntı kimliğini girin. 

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

1. Özel durum SharePoint bir bağıntı kimliği seçin. Özel durumlar türe ve çağrı yığınına göre gruplanır.

2. (İsteğe bağlı) Bir **özel durum** grubu için çağrı yığınını görmek için Çağrı Yığını'yı genişletin.

3. Özel **durumun nerede ve ne** zaman olduğu noktasında hata ayıklamaya başlamak için Hata Ayıklama Özel Durumu'u seçin.

    ![IntelliTrace günlüğü &#45; SharePoint özel durumlar için](../debugger/media/sharepointunhandledexceptions_intellitrace.png "SharePointUnhandledExceptions_IntelliTrace")

   Bir izlenecek yol için [bkz. IntelliTrace Kullanarak SharePoint Uygulamanın Hata Ayıklaması.](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md) Aracı tarafından kaydedilen veri türleri için bkz. [IntelliTrace Özellikleri.](../debugger/intellitrace-features.md)

### <a name="threads-list"></a><a name="ThreadsList"></a> İş Parçacıkları Listesi
 Hedef işlemde çalışan kayıtlı iş parçacıklarını inceleme. Seçilen bir iş parçacığında ilk geçerli IntelliTrace olayından hata ayıklamaya başlayabilirsiniz.

##### <a name="to-start-debugging-from-a-specific-thread"></a>Belirli bir iş parçacığından hata ayıklamaya başlamak için

1. İş **Parçacıkları Listesi altında** bir iş parçacığı seçin.

2. İş Parçacıkları **Listesi'nin alt kısmında** Hata **Ayıklamayı Başlat'ı seçin.** Ayrıca bir iş parçacığına çift tıklar.

    Uygulamanın başladığı yerden hata ayıklamaya başlamak için Ana İş **Parçacığı'ya çift tıklayın.** Bkz. [IntelliTrace Özellikleri.](../debugger/intellitrace-features.md)

   Kullanıcının oluşturduğu iş parçacığı verileri, bir sunucunun IIS tarafından barındırılan Web uygulamaları için oluşturduğu ve yönet olduğu iş parçacıklarından daha kullanışlı olabilir.

|**Sütun**|**Şu sayfayı gösterir:**|
|----------------|-------------------|
|**ID**|İş Parçacığı Kimliği numarası|
|**Ad**|İş parçacığı adı. Adlandırlanmamış iş parçacıkları " " olarak \<No Name> görünür.|
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
