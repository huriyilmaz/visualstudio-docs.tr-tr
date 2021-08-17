---
title: Microsoft Monitoring Agent | Microsoft Docs
description: Microsoft Monitoring Agent, performans ASP.NET ve diğer sorunlar için SharePoint 2010 ve 2013 uygulamalarını izlemek üzere ASP.NET'i kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 46a05ec70f392fe46696f536cfd9792e2e9ddc5a11a0b22509a661254065f008
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121391141"
---
# <a name="using-the-microsoft-monitoring-agent-c-visual-basic"></a>Microsoft Monitoring Agent kullanma (C#, Visual Basic)

IIS tarafından barındırılan ASP.NET web uygulamalarını ve SharePoint 2010 veya 2013 uygulamalarını kullanarak hataları, performans sorunlarını veya diğer sorunları yerel **olarak Microsoft Monitoring Agent.** Tanılama olaylarını aracıdan bir IntelliTrace günlük (.iTrace) dosyasına kaydedebilirsiniz. Ardından, tüm tanılama araçlarıyla ilgili Visual Studio Enterprise hataları ayıklamak için Professional veya Community sürümleri) Visual Studio açabilirsiniz. Aracıyı İzleme modunda çalıştırarak IntelliTrace tanılama verilerini ve yöntem verilerini de **toplayabilirsiniz.** Microsoft Monitoring Agent, Application Analizler ve [System Center](/azure/application-insights/) Operation Manager [ile tümleştirebilirsiniz.](/previous-versions/system-center/system-center-2012-R2/hh205987(v=sc.12)) Microsoft Monitoring Agent, hedef sistemin ortamını yüklenirken değiştirmez.

> [!NOTE]
> IntelliTrace tek başına toplayıcısını kullanarak hedef ortamı değiştirmeden uzak makinelerde web, SharePoint, WPF ve Windows Form uygulamaları için **IntelliTrace** tanılama ve yöntem verilerini de toplayabilirsiniz. Tek başına toplayıcının performans etkisi, izleyici modunda Microsoft Monitoring Agent **daha fazla performans etkisine** sahip olur. Bkz. [IntelliTrace tek başına toplayıcıyı kullanma.](../debugger/using-the-intellitrace-stand-alone-collector.md)

 System Center 2012 kullanıyorsanız, sorunlarla ilgili uyarı almak ve kayıtlı IntelliTrace günlük dosyalarının bağlantılarını içeren Team Foundation Server iş öğeleri oluşturmak için Microsoft İzleme Aracısı'nı İşlem Yöneticisi ile birlikte kullanın. Ardından, bu iş öğelerini daha ayrıntılı hata ayıklama için başkalarına atayabilirsiniz. Bkz. [Operations Manager Ile Geliştirme İşlemleri ve İzleme](/previous-versions/system-center/system-center-2012-R2/jj614609(v=sc.12)) ile Tümleştirme [Microsoft Monitoring Agent.](/previous-versions/system-center/system-center-2012-R2/dn465153(v=sc.12))

 Başlamadan önce oluşturulan ve dağıtılan kod için eşleşen kaynağa ve sembollere sahip olup olmadığınızı kontrol edin. Bu, hata ayıklamaya ve IntelliTrace günlüğünde tanılama olaylarını taramaya başladığınızda doğrudan uygulama koduna gitmenizi sağlar. [Derlemelerinizi, dağıtılan](../debugger/diagnose-problems-after-deployment.md) kodunuz Visual Studio eşleşen kaynağı otomatik olarak bulup açacak şekilde ayarlayın.

1. [1. Adım: Microsoft Monitoring Agent](#SetUpMonitoring)

2. [2. Adım: Uygulamalarınızı izlemeye başlama](#MonitorEvents)

3. [3. Adım: Kaydedilen olayları kaydetme](#SaveEvents)

## <a name="step-1-set-up-microsoft-monitoring-agent"></a><a name="SetUpMonitoring"></a>1. Adım: Microsoft Monitoring Agent

 Uygulamanızı değiştirmeden yerel izleme yapmak için web sunucunuz üzerinde bağımsız aracıyı ayarlayın. System Center 2012 kullanıyorsanız [bkz. Microsoft Monitoring Agent.](/previous-versions/system-center/system-center-2012-R2/dn465156(v=sc.12))

### <a name="set-up-the-standalone-agent"></a><a name="SetUpStandaloneMMA"></a> Tek başına aracıyı ayarlama

1. Şunlardan emin olun:

    - Web sunucunuz desteklenen Internet Information Services [(IIS) sürümlerini çalıştırdı.](/previous-versions/system-center/system-center-2012-R2/dn465154(v=sc.12))

    - Web sunucunuzda .NET Framework 3.5, 4 veya 4.5 sürümü var.

    - Web sunucunuz 3.0 veya Windows PowerShell çalışıyor. [S: 2.0 Windows PowerShell varsa ne olur?](#PowerShell2)

    - Web sunucunuz üzerinde, PowerShell komutlarını çalıştırmak ve izleme başlattığınızda uygulama havuzunu geri dönüştürmek için yönetici izinlerine sahipsiniz.

    - Microsoft İzleme Aracısı'nın önceki sürümlerini kaldırdınız.

2. [Microsoft İndirme Merkezi Microsoft Monitoring Agent den](https://www.microsoft.com/download/details.aspx?id=40316)web sunucunuza **32** bitMMASetup-i386.exeveya 64 bitMMASetup-AMD64.exesürümü **MMASetup-AMD64.exe)** ücretsiz sürümünü indirin.

3. İndirdiğiniz yürütebilen dosyayı çalıştırarak yükleme sihirbazını başlatın.

4. IntelliTrace günlüklerini depolamak için web sunucunuzda güvenli bir dizin oluşturun, **örneğin, C:\IntelliTraceLogs**.

     Bu dizini izlemeye başlamadan önce oluşturduğunuzdan emin olun. Uygulamanın yavaşlamaması için yerel yüksek hızlı diskte çok etkin olmayan bir konum seçin.

    > [!IMPORTANT]
    > IntelliTrace günlükleri kişisel ve hassas veriler içerebilir. Bu dizini yalnızca dosyalarla çalışması gereken kimliklerle sınırlayın. Şirketinizin gizlilik ilkelerini kontrol edin.

5. İşlev düzeyinde ayrıntılı izleme yapmak veya SharePoint uygulamalarını izlemek için, web uygulamanızı veya SharePoint uygulamanızı barındıran uygulama havuzuna IntelliTrace günlük dizini için okuma ve yazma izni verin. [S: Nasıl yaparım? havuzu için izinler ayarlanacak mı?](#FullPermissionsITLog)

### <a name="q--a"></a>Soru-Cevap

#### <a name="q-what-if-i-have-windows-powershell-20"></a><a name="PowerShell2"></a>S: 2.0 Windows PowerShell varsa ne olur?
 **A:** PowerShell 3.0'ın kullanılması kesinlikle önerilir. Aksi halde, PowerShell'i her çalıştırdığınızda Microsoft İzleme Aracısı PowerShell cmdlet'lerini içeri aktarmanız gerekir. Ayrıca, indirilebilen Yardım içeriğine de erişiminiz olmayacaktır.

1. ISE **Windows PowerShell** Windows PowerShell **komut** istemi penceresini yönetici olarak açın.

2. Varsayılan yükleme konumundan Microsoft İzleme Aracısı PowerShell modülünü içeri aktarın:

     **PS C:>Import-Module "C:\Program Files\Microsoft Monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**

3. [En son Yardım içeriğini](/previous-versions/system-center/developer/cc817313(v=msdn.10)) almak için TechNet'i ziyaret edin.

#### <a name="q-how-do-i-set-up-permissions-for-the-application-pool"></a><a name="FullPermissionsITLog"></a> S: Nasıl yaparım? havuzu için izinler ayarlanacak mı?
 **A:** Windows **icacls komutunu** kullanın veya Windows Explorer'ı (veya Dosya Gezgini). Örnek:

- **Windows icacls komutuyla izinleri ayarlamak** için:

  - DefaultAppPool uygulama **havuzunda bir** web uygulaması için:

     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`

  - SharePoint **- 80** uygulama SharePoint bir uygulama için:

     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`

    -veya-

- Windows Explorer (veya Dosya Gezgini) ile izinleri ayarlamak için:

  1. IntelliTrace günlük dizini için Özellikler'i açın. 

  2. Güvenlik sekmesinde **Düzenle,** **Ekle'yi** **seçin.**

  3. Bu nesne **türünü seçin kutusunda Yerleşik güvenlik** sorumluları'nın **göründüğünden emin** olun. Orada yoksa, eklemek için **Nesne Türleri'ne** tıklayın.

  4. Yerel bilgisayarınızın Bu konumdan **kutusunda göründüğünden emin** olun. Orada yoksa, değiştirmek için **Konumlar'ı** seçin.

  5. Seçlanacak **nesne adlarını girin kutusuna** web uygulamasının veya uygulamanın uygulama havuzunu SharePoint ekleyin.

  6. Adı **çözümlemek için** Adları Denetleme'yi seçin. **Tamam'ı seçin.**

  7. Uygulama havuzunun Okuma ve yürütme **izinlerine & olun.**

## <a name="step-2-start-monitoring-your-app"></a><a name="MonitorEvents"></a> 2. Adım: Uygulamalarınızı izlemeye başlama
 [Start-WebApplicationMonitoring komutunu](/previous-versions/system-center/powershell/system-center-2012-r2/dn472749(v=sc.20)) kullanarak Windows PowerShell izlemeye başlayabilirsiniz. System Center 2012 kullanıyorsanız [bkz. Microsoft Monitoring Agent.](/previous-versions/system-center/system-center-2012-R2/dn465157(v=sc.12)).

1. Web sunucunuzda yönetici olarak **Windows PowerShell** veya Windows PowerShell **ISE** komut istemi penceresini açın.

     ![Yönetici Windows PowerShell olarak oturum açma](../debugger/media/ffr_powershellrunadmin.png "FFR_PowerShellRunAdmin")

2. [Start-WebApplicationMonitoring komutunu çalıştırarak](/previous-versions/system-center/powershell/system-center-2012-r2/dn472749(v=sc.20)) uygulamanızı izlemeye başlayabilirsiniz. Bu, web sunucunuzdaki tüm web uygulamalarını yeniden başlatır.

     Kısa sözdizimi şu şekildedir:

     **Start-WebApplicationMonitoring** *" \<appName> "* *\<monitoringMode>* *" \<outputPath> "* *\<UInt32>* *" \<collectionPlanPathAndFileName>*

     Yalnızca web uygulaması adını ve basit İzleyici modunu kullanan bir **örnek:**

     **PS C:>Start-WebApplicationMonitoring "FabrikamFabrikamFiber.Web" İzleyicisi "C:IntelliTraceLogs"**

     IIS yolunu ve basit İzleyici modunu kullanan bir örnek aşağıdaki **gibidir:**

     **PS C:>Start-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web" İzleyicisi "C:IntelliTraceLogs"**

     İzlemeye başladıktan sonra, uygulamalarınız yeniden başlatılırken Microsoft İzleme Aracısı'nın durakladığını görebilirsiniz.

     ![MMA onayı ile izlemeye başlama](../debugger/media/ffr_powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")

    |Ad|Açıklama|
    |-|-|
    |*"\<appName>"*|IIS içinde web sitesinin yolunu ve web uygulamasının adını belirtin. İsterseniz IIS yolunu da ekleyebilirsiniz.<br /><br /> *" \<IISWebsiteName> \\<IISWebAppName \> "*<br /><br /> -veya-<br /><br /> **"IIS:\sites** *\\<IISWebsiteName \> \\<IISWebAppName \> "*<br /><br /> Bu yolu IIS Yöneticisi'nde bulabilirsiniz. Örnek:<br /><br /> ![IIS web sitesi ve web uygulamasının yolu](../debugger/media/ffr_iismanager.png "FFR_IISManager")<br /><br /> [Get-WebSite ve Get](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee807832(v=technet.10)) [WebApplication komutlarını da kullanabilirsiniz.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee790554(v=technet.10))|
    |*\<monitoringMode>*|İzleme modunu belirtin:<br /><br /> <ul><li>**İzleme:** Özel durum olayları ve performans olayları hakkında en az ayrıntıyı kaydetme. Bu mod varsayılan toplama planını kullanır.</li><li>**İzleme:** Belirtilen koleksiyon planını kullanarak işlev düzeyi ayrıntılarını SharePoint 2010 SharePoint 2013 uygulamalarını izleme. Bu mod, uygulamanızın daha yavaş çalışmasına neden olabilir.<br /><br /> <ul><li>[S: Nasıl yaparım? havuzu için izinler ayarlanacak mı?](#FullPermissionsITLog)</li><li>[S: Nasıl yaparım? yavaşlatmadan en fazla veri mi elde ediyorsunuz?](#Minimizing)</li></ul><br />     Bu örnek, bir SharePoint sitesi üzerindeki SharePoint uygulaması için olayları kaydeder:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp" Trace "C:\Program Files\Microsoft Monitoring Agent\Agent\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogs"**</li><li>**Özel:** Belirtilen özel koleksiyon planını kullanarak özel ayrıntıları kaydetme. İzleme başladıktan sonra toplama planını değiştirirseniz izlemeyi yeniden başlatmanız gerekir.</li></ul>|
    |*"\<outputPath>"*|IntelliTrace günlüklerinin depolanacağı tam dizin yolunu belirtin. Bu dizini izlemeye başlamadan önce oluşturduğunuzdan emin olun.|
    |*\<UInt32>*|IntelliTrace günlüğünün çıkabileceği en büyük boyutu belirtin. IntelliTrace günlüğü için varsayılan en büyük boyut 250 MB'tır.<br /><br /> Günlük bu sınıra ulaştığında, aracı yeni girişlere yer açmak için en eski girişlerin üzerine yazar. Bu sınırı değiştirmek için **-MaximumFileSizeInMegabytes** seçeneğini kullanın veya koleksiyon `MaximumLogFileSize` planında özniteliğini düzenleyin.|
    |*"\<collectionPlanPathAndFileName>"*|Toplama planının tam yolunu veya göreli yolunu ve dosya adını belirtin. Bu plan, aracı için ayarları yapılandıran bir .xml dosyasıdır.<br /><br /> Bu planlar aracıyla birlikte gelir ve web uygulamaları ve SharePoint uygulamalarıyla çalışır:<br /><br /> -   **collection_plan.ASP.NET.default.xml**<br />     Yalnızca özel durumlar, performans olayları, veritabanı çağrıları ve Web sunucusu istekleri gibi olayları toplar.<br />-   **collection_plan.ASP.NET.trace.xml**<br />     Varsayılan toplama planındaki verilere ek olarak işlev düzeyi çağrıları toplar. Bu plan ayrıntılı analiz için iyidir ancak uygulamanızı yavaşlatabilir.<br /><br /> Bu planların yerelleştirilmiş sürümlerini aracının alt klasörlerinde bulabilirsiniz. Ayrıca, bu [planları özelleştirilebilir veya uygulamanın yavaşlamaması](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) için kendi planlarınızı oluşturabilirsiniz. Özel planları aracıyla aynı güvenli konuma yerleştirin.<br /><br /> [S: Nasıl yaparım? yavaşlatmadan en fazla veri mi elde ediyorsunuz?](#Minimizing)|

     Tam söz dizimi ve diğer örnekler hakkında daha fazla bilgi için **get-help Start-WebApplicationMonitoring -detailed** komutunu veya **get-help Start-WebApplicationMonitoring -examples komutunu** çalıştırın.

3. Tüm izlenen web uygulamalarının durumunu kontrol etmek için [Get-WebApplicationMonitoringStatus komutunu](/previous-versions/system-center/powershell/system-center-2012-r2/dn472751(v=sc.20)) çalıştırın.

### <a name="q--a"></a>Soru-Cevap

#### <a name="q-how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> S: Nasıl yaparım? yavaşlatmadan en fazla veri mi elde ediyorsunuz?
 **A:** Microsoft Monitoring Agent fazla veri toplayabilirsiniz ve toplamayı seçtiğiniz verilere ve nasıl toplanıza bağlı olarak uygulama performansını etkiler. Aşağıda, uygulamalarınızı yavaşlatmadan en fazla veriye erişim elde etmenin bazı yolları vesiniz:

- Web uygulamaları ve SharePoint uygulamaları için, aracı belirtilen uygulama havuzunu paylaşan her uygulama için veri kaydeder. Bu aynı uygulama havuzunu paylaşan herhangi bir uygulamayı, toplamayı tek bir uygulamanın modüllerine kısıtlamanıza rağmen yavaşlatabilir. Diğer uygulamaları yavaşlatmayı önlemek için, her uygulamayı kendi uygulama havuzunda barındırın.

- Toplama planında aracının veri topladığı olayları gözden geçirin. İlgili olmayan veya ilginizi toplamaya gerek olmayan olayları devre dışı bırakmak için koleksiyon planını düzenleyin. Bu, başlangıç performansını ve çalışma zamanı performansını geliştirebilir.

   Bir olayı devre dışı bırakmak için `enabled` öğesinin `<DiagnosticEventSpecification>` özniteliğini olarak `false` ayarlayın:

   `<DiagnosticEventSpecification enabled="false">`

   Öznitelik `enabled` yoksa olay etkinleştirilir.

   Örnek:

  - Windows Workflow kullanmayan uygulamalar için Windows Workflow olaylarını devre dışı bırakın.

  - Kayıt defterine erişen ancak kayıt defteri ayarlarında sorun göstermeyen uygulamalar için kayıt defteri olaylarını devre dışı bırakın.

- Toplama planında aracının veri topladığı modülleri gözden geçirin. Toplama planını yalnızca ilginizi çeken modülleri içerecek şekilde düzenleyin.

   Bu uygulama başladığında ve çalıştığında aracının topladığı yöntem çağrı bilgisi ve diğer araç verisi miktarını azaltır. Bu veriler, hata ayıklarken kod içinde adım adım ilerlemenize ve işlev çağrılarına gönderilen ve bu çağrılardan alınan değerleri gözden geçirmenize yardımcı olur.

  1. Koleksiyon planını açın. öğesini `<ModuleList>` bulun.

  2. içinde `<ModuleList>` `isExclusionList` özniteliğini olarak `false` ayarlayın.

  3. Her modülü şunlardan biri ile belirtmek için öğesini kullanın: dosya adı, dize değeri, adı bu dizeyi veya ortak anahtarı içeren herhangi `<Name>` bir modülü dahil etmek için.

     Bu örnek, Fabrikam Fiber web uygulamasının yalnızca ana modülünden veri toplayan bir liste oluşturur:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>FabrikamFiber.Web.dll</Name>
  </ModuleList>

  ```

   Adı "Fabrikam" olan herhangi bir modülden veri toplamak için aşağıdakine benzer bir liste oluşturun:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>Fabrikam</Name>
  </ModuleList>

  ```

   Modüllerden ortak anahtar belirteçlerini belirterek veri toplamak için aşağıdakine benzer bir liste oluşturun:

  ```xml
  <ModuleList isExclusionList="false">
     <Name>PublicKeyToken:B77A5C561934E089</Name>
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>
     <Name>PublicKeyToken:31BF3856AD364E35</Name>
     <Name>PublicKeyToken:89845DCD8080CC91</Name>
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>
  </ModuleList>

  ```

   **S: Bunun yerine neden yalnızca modülleri dışlamam gerekir?**

   **A:** Varsayılan olarak, koleksiyon planları özniteliğini olarak ayarerek modülleri `isExclusionList` `true` dışlar. Ancak bu, yine de üçüncü taraf veya açık kaynak modüller gibi listenin ölçütlerine uymayan veya ilgilenmediğiniz modüllerden veri toplayabilir.

#### <a name="q-what-values-does-the-agent-collect"></a>S: Aracı hangi değerleri toplar?

**A:** Performans üzerindeki etkiyi azaltmak için aracı yalnızca şu değerleri toplar:

- Yöntemlere geçirilen ve yöntemlerden döndürülen ilkel veri türleri

- Yöntemlere geçirilen veya yöntemlerden geri döndürülen en üst düzey nesnelerin alanlarındaki ilkel veri türleri

Örneğin, bir tamsayıyı ve `AlterEmployee` nesnesini kabul eden bir yöntem imzanız olduğunu `id` `Employee` `oldemployee` varsayalım:

`public Employee AlterEmployee(int id, Employee oldemployee)`

Türün `Employee` şu öznitelikleri vardır: `Id` , ve `Name` `HomeAddress` . ile türü arasında bir `Employee` ilişki `Address` vardır.

![Çalışan ile Adres arasındaki ilişki](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

Aracı `id`, `Employee.Id` ve `Employee.Name` değerlerini ve `Employee` yönteminden döndürülen `AlterEmployee` nesnesini kaydeder. Ancak aracı `Address` nesnesi hakkında, nesnenin null olup olmadığı dışında bilgi kaydetmez. Aracı, ayrıca, `AlterEmployee` yöntemindeki yerel değişkenlerle ilgili olarak, diğer yöntemler bu yerel değişkenleri parametre olarak kullanıp onların yöntem parametresi olarak kaydedilmesini sağlamadığı sürece, veri kaydetmez.

## <a name="step-3-save-recorded-events"></a><a name="SaveEvents"></a> 3. Adım: Kaydedilen olayları kaydetme
 Bir hata veya performans sorunu bulduğunuzda, kayıtlı olayları bir IntelliTrace günlüğüne kaydedin. Aracı günlüğü yalnızca olay kaydettiyse oluşturur. System Center 2012 kullanıyorsanız [bkz. Microsoft Monitoring Agent.](/previous-versions/system-center/system-center-2012-R2/dn465157(v=sc.12)).

### <a name="save-recorded-events-but-continue-monitoring"></a>Kayıtlı olayları kaydedip izlemeye devam etme
 IntelliTrace günlüğünü oluşturmak istediğinizde ancak uygulamanızı yeniden başlatmak veya izlemeyi durdurmak istemediğinizde bu adımları izleyin. Aracı, sunucu veya uygulama yeniden başlasa bile izlemeye devam eder.

1. Web sunucunuzda yönetici olarak Windows PowerShell komut istemi penceresi açın.

2. IntelliTrace günlüğünün anlık görüntüsünü kaydetmek için [Checkpoint-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472750(v=sc.20)) komutunu çalıştırın:

    **Checkpoint-WebApplicationMonitoring** *"<\<IISWebsiteName> \\ IISWebAppName \> "*

    \- veya -

    **Checkpoint-WebApplicationMonitoring "IIS:\sites** *\\<IISWebsiteName \> \\<IISWebAppName \> "*

    Örnek:

    **PS C: \\>Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**

    -veya-

    **PS C:>Checkpoint-WebApplicationMonitoring "IIS:sitesFabrikamFabrikamFiber.Web"**

    Daha fazla bilgi için **get-help Checkpoint-WebApplicationMonitoring -examples** komutunu veya **get-help Checkpoint-WebApplicationMonitoring komutunu** çalıştırın.

3. Günlüğü güvenli bir paylaşılan klasöre kopyalayın ve ardından günlüğü Visual Studio Enterprise (Professional veya Community açın).

   > [!IMPORTANT]
   > Kişisel ve hassas veriler içerebileceklerinden, IntelliTrace günlüklerini paylaşırken dikkatli olun. Bu günlüklere erişebilen kişilerin o verileri görme izni olduğundan emin olun. Şirketinizin gizlilik ilkelerini kontrol edin.

   **Sonraki:** [Visual Studio Enterprise'da kayıtlı olayları tanılama](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)

### <a name="save-recorded-events-and-stop-monitoring"></a>Kayıtlı olayları kaydedip izlemeyi durdurma
 Belirli bir sorunu yeniden oluştururken yalnızca tanı bilgilerini almak istediğinizde bu adımları izleyin. Bu, web sunucunuzdaki tüm web uygulamalarını yeniden başlatır.

1. Web sunucunuzda yönetici olarak Windows PowerShell komut istemi penceresi açın.

2. IntelliTrace günlüğünü oluşturmak ve belirli bir web uygulamasını izlemeyi durdurmak için [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) komutunu çalıştırın:

    **Stop-WebApplicationMonitoring** *"<\<IISWebsiteName> \\ IISWebAppName \> "*

    \- veya -

    **Stop-WebApplicationMonitoring "IIS:\sites** *\\<IISWebsiteName \> \\<IISWebAppName \> "*

    Veya tüm web uygulamalarının izlenmesini durdurmak için:

    **Stop-WebApplicationMonitoring -All**

    Örnek:

    **PS C: \\>Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**

    \- veya -

    **PS C: \\>Stop-WebApplicationMonitoring "IIS:\sites\Fabrikam\FabrikamFiber.Web"**

    Daha fazla bilgi için **get-help Stop-WebApplicationMonitoring -examples** komutunu veya **get-help Stop-WebApplicationMonitoring komutunu** çalıştırın.

3. Günlüğü güvenli bir paylaşılan klasöre kopyalayın ve ardından günlük dosyasını içeren bir bilgisayardan Visual Studio Enterprise.

   **Sonraki:** [Visual Studio Enterprise'da kayıtlı olayları tanılama](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)

## <a name="q--a"></a>Soru-Cevap

### <a name="q-where-can-i-get-more-information"></a>S: Nereden daha fazla bilgi edinebilirim?

#### <a name="blogs"></a>Bloglar
 [Yeni Microsoft Monitoring Agent](https://devblogs.microsoft.com/devops/introducing-microsoft-monitoring-agent/)

 [Üretim Sunucularında IntelliTrace Koleksiyonunu En Iyi Duruma Getirme](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

#### <a name="forums"></a>Forumlar
 [Visual Studio Tanılama](https://social.msdn.microsoft.com/Forums/en-US/home)