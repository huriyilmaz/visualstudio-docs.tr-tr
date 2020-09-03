---
title: Microsoft Monitoring Agent kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: fd0a86b9-015d-408e-aa58-59a0a97826ac
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f70d3799bfae96b15c13a42c3c11246d1e89ba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520581"
---
# <a name="using-the-microsoft-monitoring-agent"></a>Microsoft İzleme Aracısı’nı kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Ile ilgili en son belgeler için [Microsoft Monitoring Agent kullanma](/visualstudio/debugger/using-the-microsoft-monitoring-agent)konusuna bakın.

**Microsoft Monitoring Agent**kullanarak IIS ile barındırılan ASP.NET Web uygulamalarını ve SharePoint 2010 veya 2013 uygulamalarını hatalara, performans sorunlarına veya diğer sorunlar için yerel olarak izleyebilirsiniz. Tanılama olaylarını aracıdan bir IntelliTrace günlük (.iTrace) dosyasına kaydedebilirsiniz. Daha sonra, tüm Visual Studio tanılama araçlarıyla ilgili sorunları ayıklamak için Visual Studio Enterprise (profesyonel veya Community Edition değil) içinde günlük dosyasını açabilirsiniz. Ayrıca, aracıyı **izleme** modunda çalıştırarak IntelliTrace Tanılama verileri ve yöntem verileri toplayabilirsiniz. Microsoft Monitoring Agent, [Application Insights](/azure/azure-monitor/app/app-insights-overview) ve [System Center Operation Manager](https://technet.microsoft.com/library/hh205987.aspx)ile tümleştirilebilir. Microsoft Monitoring Agent, yüklendiğinde hedef sistemin ortamını değiştirir.  
  
> [!NOTE]
> Ayrıca, **IntelliTrace tek başına toplayıcıyı**kullanarak hedef ortamı değiştirmeden uzak makinelerde web, SHAREPOINT, WPF ve Windows form uygulamaları için IntelliTrace Tanılama ve yöntem verileri toplayabilirsiniz. Tek başına toplayıcı, Microsoft Monitoring Agent **izleme** modunda çalıştırmadan daha fazla performans etkisine sahiptir. Bkz. [IntelliTrace tek başına toplayıcıyı kullanma](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
 System Center 2012 kullanıyorsanız, sorunlarla ilgili uyarı almak ve kayıtlı IntelliTrace günlük dosyalarının bağlantılarını içeren Team Foundation Server iş öğeleri oluşturmak için Microsoft İzleme Aracısı'nı İşlem Yöneticisi ile birlikte kullanın. Ardından, bu iş öğelerini daha ayrıntılı hata ayıklama için başkalarına atayabilirsiniz. Bkz. [Operations Manager geliştirme Işlemleriyle tümleştirme](https://technet.microsoft.com/library/jj614609.aspx) ve [Microsoft Monitoring Agent ile izleme](https://technet.microsoft.com/library/dn465153.aspx).  
  
 Başlamadan önce oluşturulan ve dağıtılan kod için eşleşen kaynağa ve sembollere sahip olup olmadığınızı kontrol edin. Bu, hata ayıklamaya ve IntelliTrace günlüğünde tanılama olaylarını taramaya başladığınızda doğrudan uygulama koduna gitmenizi sağlar. Visual Studio 'Nun dağıtılan kodunuz için eşleşen kaynağı otomatik olarak bulup açmasını sağlamak için [derlemelerinizi ayarlayın](../debugger/diagnose-problems-after-deployment.md) .  
  
1. [1. Adım: Microsoft Monitoring Agent ayarlama](#SetUpMonitoring)  
  
2. [2. Adım: uygulamanızı izlemeye başlama](#MonitorEvents)  
  
3. [3. Adım: kayıtlı olayları kaydetme](#SaveEvents)  
  
## <a name="step-1-set-up-microsoft-monitoring-agent"></a><a name="SetUpMonitoring"></a> 1. Adım: Microsoft Monitoring Agent ayarlama  
 Uygulamanızı değiştirmeden yerel izleme yapmak için web sunucunuz üzerinde bağımsız aracıyı ayarlayın. System Center 2012 kullanıyorsanız bkz. [yükleme Microsoft Monitoring Agent](https://technet.microsoft.com/library/dn465156.aspx).  
  
### <a name="set-up-the-standalone-agent"></a><a name="SetUpStandaloneMMA"></a> Tek başına aracıyı ayarlama  
  
1. Şunlardan emin olun:  
  
    - Web sunucunuz [Internet Information Services (IIS) desteklenen sürümlerini](https://technet.microsoft.com/library/dn465154.aspx)çalıştırıyor.  
  
    - Web sunucunuzda .NET Framework 3.5, 4 veya 4.5 sürümü var.  
  
    - Web sunucunuz Windows PowerShell 3,0 veya üstünü çalıştırıyor. [S: Windows PowerShell 2,0 varsa ne yapmalıyım?](#PowerShell2)  
  
    - Web sunucunuz üzerinde, PowerShell komutlarını çalıştırmak ve izleme başlattığınızda uygulama havuzunu geri dönüştürmek için yönetici izinlerine sahipsiniz.  
  
    - Microsoft İzleme Aracısı'nın önceki sürümlerini kaldırdınız.  
  
2. 32 bit sürümü **MMASetup-i386.exe** veya 64 bit sürümü **MMASetup-AMD64.exe**olan [ücretsiz Microsoft Monitoring Agent](https://go.microsoft.com/fwlink/?LinkID=309771), Microsoft İndirme Merkezi 'nden Web sunucunuza indirin.  
  
3. İndirdiğiniz yürütebilen dosyayı çalıştırarak yükleme sihirbazını başlatın.  
  
4. IntelliTrace günlüklerini depolamak için Web sunucunuzda güvenli bir dizin oluşturun, örneğin, **C:\IntelliTraceLogs**.  
  
     Bu dizini izlemeye başlamadan önce oluşturduğunuzdan emin olun. Uygulamanızı yavaşlatmayı önlemek için, yerel bir yüksek hızlı diskte çok etkin olmayan bir konum seçin.  
  
    > [!IMPORTANT]
    > IntelliTrace günlükleri kişisel ve hassas veriler içerebilir. Bu dizini yalnızca dosyalarla çalışması gereken kimliklerle sınırlayın. Şirketinizin gizlilik ilkelerini denetleyin.  
  
5. İşlev düzeyinde ayrıntılı izleme yapmak veya SharePoint uygulamalarını izlemek için, web uygulamanızı veya SharePoint uygulamanızı barındıran uygulama havuzuna IntelliTrace günlük dizini için okuma ve yazma izni verin. [S: uygulama havuzu için izinleri ayarla Nasıl yaparım??](#FullPermissionsITLog)  
  
### <a name="q--a"></a>Soru-Cevap  
  
#### <a name="q-what-if-i-have-windows-powershell-20"></a><a name="PowerShell2"></a> S: Windows PowerShell 2,0 varsa ne yapmalıyım?  
 Y **:** PowerShell 3,0 kullanmanızı kesinlikle öneririz. Aksi halde, PowerShell'i her çalıştırdığınızda Microsoft İzleme Aracısı PowerShell cmdlet'lerini içeri aktarmanız gerekir. Ayrıca, indirilebilen Yardım içeriğine de erişiminiz olmayacaktır.  
  
1. Yönetici olarak bir **Windows PowerShell** veya **Windows PowerShell ISE** komut istemi penceresi açın.  
  
2. Varsayılan yükleme konumundan Microsoft İzleme Aracısı PowerShell modülünü içeri aktarın:  
  
     **PS C: >Import-Module "C:\Program Files\Microsoft Monitoring Agent\Agent\PowerShell\Microsoft.MonitoringAgent.PowerShell\Microsoft.MonitoringAgent.PowerShell.dll"**  
  
3. En son yardım içeriğini almak için [TechNet sitesini ziyaret edin](https://technet.microsoft.com/systemcenter/default) .  
  
#### <a name="q-how-do-i-set-up-permissions-for-the-application-pool"></a><a name="FullPermissionsITLog"></a> S: uygulama havuzu için izinleri ayarla Nasıl yaparım??  
 Y **:** Windows **ıccacls** komutunu kullanın veya Windows Gezgini (veya dosya Gezgini) kullanın. Örneğin:  
  
- Windows **ıccacls** komutuyla izinleri ayarlamak için:  
  
  - **DefaultAppPool** uygulama havuzundaki bir Web uygulaması için:  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\DefaultAppPool":RX`  
  
  - **SharePoint-80** uygulama havuzundaki bir SharePoint uygulaması için:  
  
     `icacls "C:\IntelliTraceLogs" /grant "IIS APPPOOL\SharePoint - 80":RX`  
  
    -veya-  
  
- Windows Gezgini (veya dosya Gezgini) ile izinleri ayarlamak için:  
  
  1. IntelliTrace günlük dizini için **özellikleri** açın.  
  
  2. **Güvenlik** sekmesinde **Düzenle**, **Ekle**' yi seçin.  
  
  3. **Bu nesne türünü seç** kutusunda **yerleşik güvenlik sorumlularının** göründüğünden emin olun. Bu yoksa eklemek için **nesne türleri** ' ni seçin.  
  
  4. **Bu konumdan** yerel bilgisayarınızın göründüğünden emin olun. Orada yoksa, değiştirmek için **konumlar** ' ı seçin.  
  
  5. **Seçilecek nesne adlarını girin** kutusunda, Web uygulaması veya SharePoint uygulaması için uygulama havuzunu ekleyin.  
  
  6. Adı çözümlemek için **adları denetle** ' yi seçin. **Tamam ' ı**seçin.  
  
  7. Uygulama havuzunun **okuma & yürütme** izinlerine sahip olduğundan emin olun.  
  
## <a name="step-2-start-monitoring-your-app"></a><a name="MonitorEvents"></a> 2. Adım: uygulamanızı izlemeye başlama  
 Uygulamanızı izlemeye başlamak için Windows PowerShell [Start-WebApplicationMonitoring](https://technet.microsoft.com/library/dn472749(v=sc.20).aspx) komutunu kullanın. System Center 2012 kullanıyorsanız bkz. [Microsoft Monitoring Agent Web uygulamalarını izleme](https://technet.microsoft.com/library/dn465157.aspx).  
  
1. Web sunucunuzda, yönetici olarak bir **Windows PowerShell** veya **Windows PowerShell ISE** komut istemi penceresi açın.  
  
     ![Windows PowerShell 'i yönetici olarak açın](../debugger/media/ffr-powershellrunadmin.png "FFR_PowerShellRunAdmin")  
  
2. Uygulamanızı izlemeye başlamak için [Start-WebApplicationMonitoring](https://technet.microsoft.com/library/dn472749(v=sc.20).aspx) komutunu çalıştırın. Bu, web sunucunuzdaki tüm web uygulamalarını yeniden başlatır.  
  
     Kısa sözdizimi şu şekildedir:  
  
     **Start-WebApplicationMonitoring** *" \<appName> "* " *\<monitoringMode>* * \<outputPath> "* *\<UInt32>* *" \<collectionPlanPathAndFileName> "*  
  
     Yalnızca Web uygulaması adı ve basit **izleme** modunu kullanan bir örnek aşağıda verilmiştir:  
  
     **PS C: >start-WebApplicationMonitoring "FabrikamFabrikamFiber. Web" Monitor "C:IntelliTraceLogs"**  
  
     IIS yolu ve basit **izleme** modunu kullanan bir örnek aşağıda verilmiştir:  
  
     **PS C: >start-WebApplicationMonitoring "IIS: sitesFabrikamFabrikamFiber. Web" Monitor "C:IntelliTraceLogs"**  
  
     İzlemeye başladıktan sonra, uygulamalarınız yeniden başlatılırken Microsoft İzleme Aracısı'nın durakladığını görebilirsiniz.  
  
     ![MMA onayı ile izlemeyi Başlat](../debugger/media/ffr-powershellstartmonitoringconfirmation.png "FFR_PowerShellStartMonitoringConfirmation")  
  
    |Öğe|Açıklama|  
    |-|-|  
    |*"\<appName>"*|IIS içinde web sitesinin yolunu ve web uygulamasının adını belirtin. İsterseniz IIS yolunu da ekleyebilirsiniz.<br /><br /> *" \<IISWebsiteName> \\<ııswebappname \> "*<br /><br /> -veya-<br /><br /> **"IIS: \ siteler** * \\<ııswebsitename \> \\<iiswebappname \> "*<br /><br /> Bu yolu IIS Yöneticisi'nde bulabilirsiniz. Örneğin:<br /><br /> ![IIS Web sitesi ve Web uygulaması yolu](../debugger/media/ffr-iismanager.png "FFR_IISManager")<br /><br /> [Get-website](https://technet.microsoft.com/library/ee807832.aspx) ve [Get WebApplication](https://technet.microsoft.com/library/ee790554.aspx) komutlarını da kullanabilirsiniz.|  
    |*\<monitoringMode>*|İzleme modunu belirtin:<br /><br /> <ul><li>**İzleme**: özel durum olayları ve performans olayları hakkında en az ayrıntıları kaydedin. Bu mod varsayılan toplama planını kullanır.</li><li>**Trace**: belirtilen koleksiyon planını kullanarak işlev düzeyi ayrıntılarını kaydedin veya SharePoint 2010 ve SharePoint 2013 uygulamalarını izleyin. Bu mod, uygulamanızın daha yavaş çalışmasına neden olabilir.<br /><br /> <ul><li>[S: uygulama havuzu için izinleri ayarla Nasıl yaparım??](#FullPermissionsITLog)</li><li>[S: uygulamamı yavaşlatmadan en çok veriyi almak Nasıl yaparım??](#Minimizing)</li></ul><br />     Bu örnek, bir SharePoint sitesi üzerindeki SharePoint uygulaması için olayları kaydeder:<br /><br />     **Start-WebApplicationMonitoring "FabrikamSharePointSite\FabrikamSharePointApp" Trace "C:\Program Files\Microsoft Monitoring Agent\Agent\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogs"**</li><li>**Özel**: belirtilen özel toplama planını kullanarak özel ayrıntıları kaydedin. İzleme başladıktan sonra toplama planını değiştirirseniz izlemeyi yeniden başlatmanız gerekir.</li></ul>|  
    |*"\<outputPath>"*|IntelliTrace günlüklerinin depolanacağı tam dizin yolunu belirtin. Bu dizini izlemeye başlamadan önce oluşturduğunuzdan emin olun.|  
    |*\<UInt32>*|IntelliTrace günlüğünün çıkabileceği en büyük boyutu belirtin. IntelliTrace günlüğü için varsayılan en büyük boyut 250 MB'tır.<br /><br /> Günlük bu sınıra ulaştığında, aracı yeni girişlere yer açmak için en eski girişlerin üzerine yazar. Bu sınırı değiştirmek için **-maximumfilesizeınmegabayt** seçeneğini kullanın veya `MaximumLogFileSize` koleksiyon planındaki özniteliği düzenleyin.|  
    |*"\<collectionPlanPathAndFileName>"*|Toplama planının tam yolunu veya göreli yolunu ve dosya adını belirtin. Bu plan, aracı için ayarları yapılandıran bir .xml dosyasıdır.<br /><br /> Bu planlar aracıyla birlikte gelir ve web uygulamaları ve SharePoint uygulamalarıyla çalışır:<br /><br /> -   **collection_plan.ASP.NET.default.xml**<br />     Yalnızca özel durumlar, performans olayları, veritabanı çağrıları ve Web sunucusu istekleri gibi olayları toplar.<br />-   **collection_plan.ASP.NET.trace.xml**<br />     Varsayılan toplama planındaki verilere ek olarak işlev düzeyi çağrıları toplar. Bu plan ayrıntılı analiz için iyidir ancak uygulamanızı yavaşlatabilir.<br /><br /> Bu planların yerelleştirilmiş sürümlerini aracının alt klasörlerinde bulabilirsiniz. Ayrıca, uygulamanızı yavaşlatmayı önlemek için [Bu planları özelleştirebilir veya kendi planlarınızı oluşturabilirsiniz](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) . Özel planları aracıyla aynı güvenli konuma yerleştirin.<br /><br /> [S: uygulamamı yavaşlatmadan en çok veriyi almak Nasıl yaparım??](#Minimizing)|  
  
     Tam sözdizimi ve diğer örnekler hakkında daha fazla bilgi için **Get-Help Start-WebApplicationMonitoring – Detailed** komutunu veya **Get-Help Start-WebApplicationMonitoring – examples** komutunu çalıştırın.  
  
3. Tüm izlenen Web uygulamalarının durumunu denetlemek için [Get-WebApplicationMonitoringStatus](https://technet.microsoft.com/library/dn472751(v=sc.20).aspx) komutunu çalıştırın.  
  
### <a name="q--a"></a>Soru-Cevap  
  
#### <a name="q-how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> S: uygulamamı yavaşlatmadan en çok veriyi almak Nasıl yaparım??  
 Y **:** Microsoft Monitoring Agent, çok sayıda veri toplayabilir ve toplamayı seçtiğiniz verilere ve bu verileri nasıl topladığınıza bağlı olarak uygulamanızın performansını etkiler. Uygulamanızı yavaşlatmadan en çok veriyi almanın bazı yolları aşağıda verilmiştir:  
  
- Web uygulamaları ve SharePoint uygulamaları için, aracı belirtilen uygulama havuzunu paylaşan her uygulama için veri kaydeder. Bu aynı uygulama havuzunu paylaşan herhangi bir uygulamayı, toplamayı tek bir uygulamanın modüllerine kısıtlamanıza rağmen yavaşlatabilir. Diğer uygulamaları yavaşlatmayı önlemek için, her uygulamayı kendi uygulama havuzunda barındırın.  
  
- Toplama planında aracının veri topladığı olayları gözden geçirin. İlgili olmayan veya ilgilendiğiniz olayları devre dışı bırakmak için koleksiyon planını düzenleyin. Bu, başlangıç ve çalışma zamanı performansını artırabilir.  
  
   Bir olayı devre dışı bırakmak için `enabled` öğesi için özniteliğini şu `<DiagnosticEventSpecification>` şekilde ayarlayın `false` :  
  
   `<DiagnosticEventSpecification enabled="false">`  
  
   `enabled`Öznitelik yoksa, olay etkinleştirilir.  
  
   Örneğin:  
  
  - Windows Workflow kullanmayan uygulamalar için Windows Workflow olaylarını devre dışı bırakın.  
  
  - Kayıt defterine erişen ancak kayıt defteri ayarlarında sorun göstermeyen uygulamalar için kayıt defteri olaylarını devre dışı bırakın.  
  
- Toplama planında aracının veri topladığı modülleri gözden geçirin. Toplama planını yalnızca ilginizi çeken modülleri içerecek şekilde düzenleyin.  
  
   Bu uygulama başladığında ve çalıştığında aracının topladığı yöntem çağrı bilgisi ve diğer araç verisi miktarını azaltır. Bu veriler, hata ayıklarken kod içinde adım adım ilerlemenize ve işlev çağrılarına gönderilen ve bu çağrılardan alınan değerleri gözden geçirmenize yardımcı olur.  
  
  1. Toplama planını açın. Öğesini bulun `<ModuleList>` .  
  
  2. İçinde `<ModuleList>` , `isExclusionList` özniteliğini olarak ayarlayın `false` .  
  
  3. `<Name>`Her modülü aşağıdakilerden biriyle belirtmek için öğesini kullanın: dosya adı, adı bu dizeyi içeren herhangi bir modül dahil olmak üzere dize değeri veya ortak anahtar.  
  
     Bu örnek, Fabrikam Fiber web uygulamasının yalnızca ana modülünden veri toplayan bir liste oluşturur:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>FabrikamFiber.Web.dll</Name>  
  </ModuleList>  
  
  ```  
  
   Adı "Fabrikam" içeren tüm modüllerden veri toplamak için, şöyle bir liste oluşturun:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>Fabrikam</Name>  
  </ModuleList>  
  
  ```  
  
   Ortak anahtar belirteçlerini belirterek modüllerden veri toplamak için şöyle bir liste oluşturun:  
  
  ```xml  
  <ModuleList isExclusionList="false">  
     <Name>PublicKeyToken:B77A5C561934E089</Name>  
     <Name>PublicKeyToken:B03F5F7F11D50A3A</Name>  
     <Name>PublicKeyToken:31BF3856AD364E35</Name>  
     <Name>PublicKeyToken:89845DCD8080CC91</Name>  
     <Name>PublicKeyToken:71E9BCE111E9429C</Name>  
  </ModuleList>  
  
  ```  
  
   **S: bunun yerine yalnızca modülleri dışlamadınız mı?**  
  
   Y **:** Varsayılan olarak, koleksiyon planları özniteliğini olarak ayarlayarak modülleri hariç tutar `isExclusionList` `true` . Ancak bu, yine de üçüncü taraf veya açık kaynak modüller gibi listenin ölçütlerine uymayan veya ilgilenmediğiniz modüllerden veri toplayabilir.  
  
#### <a name="q-what-values-does-the-agent-collect"></a>S: Aracı hangi değerleri toplar?  
 Y **:** Performansla ilgili etkileri azaltmak için, aracı yalnızca şu değerleri toplar:  
  
- Yöntemlere geçirilen ve yöntemlerden döndürülen ilkel veri türleri  
  
- Yöntemlere geçirilen veya yöntemlerden geri döndürülen en üst düzey nesnelerin alanlarındaki ilkel veri türleri  
  
  Örneğin, bir `AlterEmployee` tamsayı ve bir nesne kabul eden bir yöntem imzasına sahip olduğunuzu varsayalım `id` `Employee` `oldemployee` :  
  
  `public Employee AlterEmployee(int id, Employee oldemployee)`  
  
  `Employee`Tür şu özniteliklere sahiptir: `Id` , `Name` ve `HomeAddress` . Ve türü arasında bir ilişki ilişkisi var `Employee` `Address` .  
  
  ![Çalışan ve adres arasındaki ilişki](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")  
  
  Aracı `id`, `Employee.Id` ve `Employee.Name` değerlerini ve `Employee` yönteminden döndürülen `AlterEmployee` nesnesini kaydeder. Ancak aracı `Address` nesnesi hakkında, nesnenin null olup olmadığı dışında bilgi kaydetmez. Aracı, ayrıca, `AlterEmployee` yöntemindeki yerel değişkenlerle ilgili olarak, diğer yöntemler bu yerel değişkenleri parametre olarak kullanıp onların yöntem parametresi olarak kaydedilmesini sağlamadığı sürece, veri kaydetmez.  
  
## <a name="step-3-save-recorded-events"></a><a name="SaveEvents"></a> 3. Adım: kayıtlı olayları kaydetme  
 Bir hata veya performans sorunu bulduğunuzda, kayıtlı olayları bir IntelliTrace günlüğüne kaydedin. Aracı günlüğü yalnızca olay kaydettiyse oluşturur. System Center 2012 kullanıyorsanız bkz. [Microsoft Monitoring Agent Web uygulamalarını izleme](https://technet.microsoft.com/library/dn465157.aspx).  
  
### <a name="save-recorded-events-but-continue-monitoring"></a>Kayıtlı olayları kaydedip izlemeye devam etme  
 IntelliTrace günlüğünü oluşturmak istediğinizde ancak uygulamanızı yeniden başlatmak veya izlemeyi durdurmak istemediğinizde bu adımları izleyin. Aracı, sunucu veya uygulama yeniden başlasa bile izlemeye devam eder.  
  
1. Web sunucunuzda, yönetici olarak bir Windows PowerShell komut istemi penceresi açın.  
  
2. IntelliTrace günlüğünün bir anlık görüntüsünü kaydetmek için [Checkpoint-WebApplicationMonitoring](https://technet.microsoft.com/library/dn472750(v=sc.20).aspx) komutunu çalıştırın:  
  
    **Checkpoint-WebApplicationMonitoring** *" \<IISWebsiteName> \\<ııswebappname \> "*  
  
    \- veya  
  
    **Checkpoint-WebApplicationMonitoring "IIS: \ Sites** * \\<ııswebsitename \> \\<iiswebappname \> "*  
  
    Örneğin:  
  
    **PS C: \\>Checkpoint-WebApplicationMonitoring "Fabrikam\FabrikamFiber.Web"**  
  
    -veya-  
  
    **PS C: >Checkpoint-WebApplicationMonitoring "IIS: sitesFabrikamFabrikamFiber. Web"**  
  
    Daha fazla bilgi için **Get-Help Checkpoint-WebApplicationMonitoring – Detailed** komutunu veya **Get-Help Checkpoint-WebApplicationMonitoring – örnekler** komutunu çalıştırın.  
  
3. Günlüğü güvenli bir paylaşılan klasöre kopyalayın ve ardından Visual Studio Enterprise (Professional veya Community Edition değil) olan bir bilgisayardan günlüğü açın.  
  
   > [!IMPORTANT]
   > Kişisel ve hassas veriler içerebileceklerinden, IntelliTrace günlüklerini paylaşırken dikkatli olun. Bu günlüklere erişebilen kişilerin o verileri görme izni olduğundan emin olun. Şirketinizin gizlilik ilkelerini denetleyin.  
  
   **Sonraki:** [Visual Studio Enterprise kayıtlı olayları Tanıla](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
### <a name="save-recorded-events-and-stop-monitoring"></a>Kayıtlı olayları kaydedip izlemeyi durdurma  
 Belirli bir sorunu yeniden oluştururken yalnızca tanı bilgilerini almak istediğinizde bu adımları izleyin. Bu, web sunucunuzdaki tüm web uygulamalarını yeniden başlatır.  
  
1. Web sunucunuzda, yönetici olarak bir Windows PowerShell komut istemi penceresi açın.  
  
2. IntelliTrace günlüğünü oluşturmak ve belirli bir Web uygulamasını izlemeyi durdurmak için [Stop-WebApplicationMonitoring](https://technet.microsoft.com/library/dn472753(v=sc.20).aspx) komutunu çalıştırın:  
  
    **Stop-WebApplicationMonitoring** *" \<IISWebsiteName> \\<ııswebappname \> "*  
  
    \- veya  
  
    **Stop-WebApplicationMonitoring "IIS: \ Sites** * \\<ııswebsitename \> \\<iiswebappname \> "*  
  
    Ya da tüm Web uygulamalarının izlenmesini durdurmak için:  
  
    **Stop-WebApplicationMonitoring-tümü**  
  
    Örneğin:  
  
    **PS C: \\>Stop-WebApplicationMonitoring "Fabrikam\iFabrikamFiber.Web"**  
  
    \- veya  
  
    **PS C: \\>Stop-WebApplicationMonitoring "IIS: \ sites\Fabrikam\FabrikamFiber.Web"**  
  
    Daha fazla bilgi için **Get-Help Stop-WebApplicationMonitoring – Detailed** komutunu veya **Get-Help Stop-WebApplicationMonitoring – examples** komutunu çalıştırın.  
  
3. Günlüğü güvenli bir paylaşılan klasöre kopyalayın ve ardından Visual Studio Enterprise olan bir bilgisayardan günlüğü açın.  
  
   **Sonraki:** [Visual Studio Enterprise kayıtlı olayları Tanıla](../debugger/diagnose-problems-after-deployment.md#InvestigateEvents)  
  
## <a name="q--a"></a>Soru-Cevap  
  
### <a name="q-where-can-i-get-more-information"></a>S: Nereden daha fazla bilgi edinebilirim?  
  
#### <a name="blogs"></a>Bloglar  
 [Microsoft Monitoring Agent tanıtımı](https://devblogs.microsoft.com/devops/introducing-microsoft-monitoring-agent-2/)  
  
 [Üretim sunucularında IntelliTrace toplamasını iyileştirme](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)  
  
#### <a name="forums"></a>Forumlar  
 [Visual Studio tanılama](https://social.msdn.microsoft.com/Forums/vsdebug)
