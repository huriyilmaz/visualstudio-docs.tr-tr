---
title: IntelliTrace tek başına toplayıcıyı kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
caps.latest.revision: 111
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40a61ef8c8b3f389af97024475fab9a625131a44
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297120"
---
# <a name="using-the-intellitrace-stand-alone-collector"></a>IntelliTrace tek başına toplayıcıyı kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**IntelliTrace tek başına toplayıcısı** , Visual Studio 'yu hedef makineye yüklemeden ve hedef sistemin ortamını değiştirmeden, üretim sunucularında veya diğer ortamlarda uygulamalarınız için IntelliTrace Tanılama verileri toplamanıza olanak tanır. IntelliTrace tek başına toplayıcısı Web, SharePoint, WPF ve Windows Forms uygulamalarda kullanılabilir. Veri toplamayı tamamladıktan sonra kaldırmak için toplayıcıyı silmeniz yeterlidir.

 IntelliTrace 'i çalışırken izleyin: [hata ayıklama için üretimde IntelliTrace verilerini toplama ve analiz etme (Channel 9 Videosu)](https://go.microsoft.com/fwlink/?LinkID=251851)

> [!NOTE]
> Ayrıca, **izleme** modundaki **Microsoft Monitoring Agent** kullanarak uzak makinelerde çalışan Web ve SharePoint uygulamaları için aynı IntelliTrace verilerini toplayabilirsiniz.
>
> Aracıyı **izleyici** modunda çalıştırarak, IntelliTrace verilerinde performansla ilgili olayları toplayabilirsiniz. **İzleyici** modunun, **Izleme** modundan veya **IntelliTrace tek başına toplayıcısından**daha az performans etkisi vardır. Microsoft Monitoring Agent, yüklendiğinde hedef sistemin ortamını değiştirir. Bkz. [Microsoft Monitoring Agent kullanımı](../debugger/using-the-microsoft-monitoring-agent.md).

 **Requirements**

- .NET Framework 3,5, 4 veya 4,5

- Geliştirme bilgisayarındaki veya başka bir bilgisayardaki. iTrace dosyalarını açmak için Visual Studio Enterprise (profesyonel veya Community Edition değil)

  > [!NOTE]
  > Sembol (. pdb) dosyalarınızı kaydettiğinizden emin olun. IntelliTrace ile hata ayıklamak ve kodda adım adım ilerlemek için, eşleşen kaynak dosyaları ve sembol dosyalarınız olmalıdır. Bkz. [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

  **SSS**

- [Toplayıcıyla hangi uygulamalar çalışıyor?](#WhatApps)

- [Nasıl yaparım? başlamak istiyor musunuz?](#GetStarted)

- [Uygulamamı yavaşlatmadan en çok veriyi nasıl alabilirim?](#Minimizing)

- [IntelliTrace verilerini başka bir şekilde alabilirim?](#WhereElse)

## <a name="WhatApps"></a>Toplayıcıyla hangi uygulamalar çalışıyor?

- Internet Information Services (IIS) sürüm 7,0, 7,5 ve 8,0 üzerinde barındırılan Web Apps ASP.NET

- SharePoint 2010 ve SharePoint 2013 uygulamaları

- Windows Presentation Foundation (WPF) ve Windows Forms uygulamalar.

## <a name="GetStarted"></a>Nasıl yaparım? başlamak istiyor musunuz?

1. [Toplayıcıyı yükler](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [Toplayıcı dizini için izinleri ayarlama](#ConfigurePermissionsRunningCollector)

3. [Web uygulamaları veya SharePoint uygulamaları için veri toplamak üzere IntelliTrace PowerShell cmdlet 'lerini yükler](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [. İTrace dosya dizini için izinleri ayarlama](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [Bir Web uygulamasından veya SharePoint uygulamasından veri topla](#BKMK_Collect_Data_from_IIS_Application_Pools)

     veya

     [Yönetilen bir uygulamadan veri toplama](#BKMK_Collect_Data_from_Executables)

6. [. İTrace dosyasını Visual Studio Enterprise açın](#BKMK_View_IntelliTrace_Log_Files)

## <a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a>Toplayıcıyı yükler

1. Uygulamanızın sunucusunda, toplayıcı dizinini oluşturun, örneğin: **C:\IntelliTraceCollector**

2. Microsoft Indirme merkezi 'nden veya Visual Studio 2103 güncelleştirme 3 yükleme klasöründen toplayıcıya ulaşın. [Visual Studio için IntelliTrace Collector 2013 güncelleştirme 4](https://www.microsoft.com/download/details.aspx?id=44909)::

   - **Microsoft Indirme merkezi**:

     1. **IntelliTraceCollector. exe**' nin yanında **İndir**' i seçin.

     2. IntelliTraceCollector. exe ' yi toplayıcı dizinine kaydedin, örneğin: **C:\IntelliTraceCollector**

     3. IntelliTraceCollector. exe dosyasını çalıştırın. Bu, IntelliTraceCollection. cab dosyasını ayıklar.

        \- veya-

   - **Visual Studio yükleme klasörü**:

     1. IntelliTraceCollection. cab dosyasını şu klasörden kopyalayın:

          **.. \Microsoft Visual Studio 12.0 \ Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. IntelliTraceCollection. cab dosyasını toplayıcı dizinine yerleştirin, örneğin: **C:\IntelliTraceCollector**

3. IntelliTraceCollection. cab dosyasını genişletin:

   1. Uygulamanızın sunucusunda, yönetici olarak bir komut istemi penceresi açın.

   2. Toplayıcı dizinine gidin, örneğin: **C:\IntelliTraceCollector**

   3. IntelliTraceCollection. cab dosyasını genişletmek için, sonundaki nokta ( **.** ) da dahil olmak üzere **Expand** komutunu kullanın:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > Nokta ( **.** ), yerelleştirilmiş koleksiyon planları içeren alt klasörleri korur.

## <a name="ConfigurePermissionsRunningCollector"></a>Toplayıcı dizini için izinleri ayarlama

1. Uygulamanızın sunucusunda, yönetici olarak bir komut istemi penceresi açın.

2. Sunucu yöneticisine toplayıcı dizinine tam izinler vermek için Windows **ıccacls** komutunu kullanın. Örneğin:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\yönetimtorıd >* `":F`

3. Bir Web uygulaması veya SharePoint uygulaması için veri toplamak için:

    1. IntelliTrace PowerShell cmdlet 'lerini çalıştıracak kişiye Toplayıcı dizini için tam izinleri verin.

         Örneğin:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<etkialanı \ Kullanıcı kimliği >* `":F`

    2. Web uygulaması veya SharePoint uygulaması için uygulama havuzuna Toplayıcı dizini için okuma ve yürütme izinleri verin.

         Örneğin:

        - **DefaultAppPool** uygulama havuzundaki bir Web uygulaması için:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - **SharePoint-80** uygulama havuzundaki bir SharePoint uygulaması için:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a>Web uygulamaları veya SharePoint uygulamaları için veri toplamak üzere IntelliTrace PowerShell cmdlet 'lerini yükler

1. Uygulamanızın sunucusunda, PowerShell 'in etkinleştirildiğinden emin olun. Windows Server 'ın çoğu sürümünde, bu özelliği **Sunucu Yöneticisi** yönetim aracına ekleyebilirsiniz.

     ![Sunucu Yöneticisi kullanarak PowerShell ekleme](../debugger/media/intellitrace-servermanager-addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. IntelliTrace PowerShell cmdlet 'lerini yükler.

    1. Yönetici olarak bir PowerShell komut penceresi açın.

        1. **Başlat**, **tüm programlar**, **Donatılar**, **Windows PowerShell**seçeneklerini belirleyin.

        2. Aşağıdaki adımlardan birini seçin:

            - 64 bit işletim sistemlerinde, **Windows PowerShell**için kısayol menüsünü açın. **Yönetici olarak çalıştır**' ı seçin.

            - 32 bit işletim sistemlerinde, **Windows PowerShell (x86)** için kısayol menüsünü açın. **Yönetici olarak çalıştır**' ı seçin.

    2. PowerShell komut penceresinde, **Microsoft. VisualStudio. IntelliTrace. PowerShell. dll dosyasını**içeri aktarmak için **Import-Module** komutunu kullanın.

         Örneğin:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a>. İTrace dosya dizini için izinleri ayarlama

1. Uygulamanızın sunucusunda,. iTrace dosya dizinini oluşturun, örneğin: **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Uygulamanızı yavaşlatmayı önlemek için, yerel bir yüksek hızlı diskte çok etkin olmayan bir konum seçin.
   >   - . İTrace dosyalarını ve toplayıcı dosyalarını aynı yere koyabilirsiniz. Ancak, bir Web uygulamanız veya SharePoint uygulamanız varsa, bu yerde uygulamayı barındıran dizinin dışında olduğundan emin olun.
   >
   > [!IMPORTANT]
   > - . İTrace dosya dizinini yalnızca toplayıcıyla çalışması gereken kimliklerle sınırlayın. Bir. iTrace dosyası, kullanıcılar, veritabanları, diğer kaynak konumları ve bağlantı dizeleri gibi gizli bilgiler içerebilir, çünkü IntelliTrace Yöntem parametrelerine veya dönüş değeri olarak herhangi bir veriyi kaydedebilir.
   >   - . İTrace dosyalarını açabilen kişilerin hassas verileri görüntüleme yetkisine sahip olduğundan emin olun. . İTrace dosyalarını paylaşırken dikkatli olun. Diğer kişilerin erişimi olması gerekiyorsa, dosyaları güvenli bir paylaşılan konuma kopyalayın.

2. Bir Web uygulaması veya SharePoint uygulaması için, uygulama havuzuna. iTrace dosya dizinine tam izinleri verin. Windows **ıccacls** komutunu veya Windows Gezgini 'ni (veya dosya Gezgini) kullanabilirsiniz.

    Örneğin:

   - Windows **ıccacls** komutuyla izinleri ayarlamak için:

     - **DefaultAppPool** uygulama havuzundaki bir Web uygulaması için:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - **SharePoint-80** uygulama havuzundaki bir SharePoint uygulaması için:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       veya

   - Windows Gezgini (veya dosya Gezgini) ile izinleri ayarlamak için:

     1. . İTrace dosya dizini için **özellikleri** açın.

     2. **Güvenlik** sekmesinde **Düzenle**, **Ekle**' yi seçin.

     3. **Bu nesne türünü seç** kutusunda **yerleşik güvenlik sorumlularının** göründüğünden emin olun. Bu yoksa eklemek için **nesne türleri** ' ni seçin.

     4. **Bu konumdan** yerel bilgisayarınızın göründüğünden emin olun. Orada yoksa, değiştirmek için **konumlar** ' ı seçin.

     5. **Seçilecek nesne adlarını girin** kutusunda, Web uygulaması veya SharePoint uygulaması için uygulama havuzunu ekleyin.

     6. Adı çözümlemek için **adları denetle** ' yi seçin. **Tamam ' ı**seçin.

     7. Uygulama havuzunun **tam denetime**sahip olduğundan emin olun.

## <a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a>Bir Web uygulamasından veya SharePoint uygulamasından veri topla

1. Veri toplamaya başlamak için yönetici olarak bir PowerShell komut penceresi açın ve ardından şu komutu çalıştırın:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`\<*Pathtocollectionplan >* *\<Fullpathtoitkcefiledirectory >*

    > [!IMPORTANT]
    > Bu komutu çalıştırdıktan sonra, veri toplamaya başlamak istediğinizi onaylamak için **Y** yazın.

     Örneğin, **SharePoint-80** uygulama havuzundaki bir SharePoint uygulamasından veri toplamak için:

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |||
    |-|-|
    |*ApplicationPool*|Uygulamanızın çalıştırıldığı uygulama havuzunun adı|
    |*PathToCollectionPlan*|Toplayıcı için ayarları yapılandıran bir. xml dosyası olan bir koleksiyon planının yolu.<br /><br /> Toplayıcıyla birlikte gelen bir plan belirtebilirsiniz. Aşağıdaki planlar Web uygulamaları ve SharePoint uygulamaları için çalışır:<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     Özel durumlar, veritabanı çağrıları ve Web sunucusu istekleri dahil olmak üzere yalnızca IntelliTrace olaylarını ve SharePoint olaylarını toplar.<br />-collection_plan. ASP. NET. Trace. xml<br />     İşlev çağrılarını ve collection_plan. ASP. NET. default. xml dosyasındaki tüm verileri toplar. Bu plan ayrıntılı analiz için uygundur, ancak uygulamanızı collection_plan. ASP. NET. default. xml ' den daha uzun sürebilir.<br /><br /> Uygulamanızı yavaşlatmayı önlemek için, bu planları özelleştirin veya kendi planınızı oluşturun. Güvenlik için, tüm özel planları toplayıcı dosyalarıyla aynı güvenli konuma yerleştirin. Bkz. [IntelliTrace koleksiyon planları oluşturma ve özelleştirme](https://go.microsoft.com/fwlink/?LinkId=227871) ve [uygulamamı yavaşlatmadan en çok veriyi edinme nasıl yaparım?.](#Minimizing) **Note:**  Varsayılan olarak,. iTrace dosyasının en büyük boyutu 100 MB 'tır. . İTrace dosyası bu sınıra ulaştığında, toplayıcı yeni girişler için alan oluşturmak üzere dosyanın en eski girdilerini siler. Bu sınırı değiştirmek için, koleksiyon planının `MaximumLogFileSize` özniteliğini düzenleyin. <br /><br /> *Bu koleksiyon planlarının yerelleştirilmiş sürümlerini nereden bulabilirim?*<br /><br /> Yerelleştirilmiş planları toplayıcı alt klasörlerinde bulabilirsiniz.|
    |*Fullpathtoitkcefiledirectory*|. İTrace dosya dizininin tam yolu. **Güvenlik notno:**  Tam yolu belirtin, göreli bir yol değil.|

     Toplayıcı uygulama havuzuna iliştirir ve veri toplamaya başlar.

     *. İTrace dosyasını şu anda açabilir miyim?* Hayır, veri toplama sırasında dosya kilitlenir.

2. Sorunu yeniden üretin.

3. . İTrace dosyasının anlık görüntüsünü almak için şu sözdizimini kullanın:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`

4. Koleksiyon durumunu denetlemek için şu sözdizimini kullanın:

     `Get-IntelliTraceCollectionStatus`

5. Veri toplamayı durdurmak için şu sözdizimini kullanın:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool >* `"`

    > [!IMPORTANT]
    > Bu komutu çalıştırdıktan sonra, veri toplamayı durdurmak istediğinizi onaylamak için **Y** yazın. Aksi takdirde Toplayıcı veri toplamaya devam edebilir, iTrace dosyası kilitli kalır veya dosya yararlı bir veri içermeyebilir.

6. [. İTrace dosyasını Visual Studio Enterprise açın](#BKMK_View_IntelliTrace_Log_Files)

## <a name="BKMK_Collect_Data_from_Executables"></a>Yönetilen bir uygulamadan veri toplama

1. Uygulamanızı başlatmak ve verileri aynı anda toplamak için şu sözdizimini kullanın:

     *\<FullPathToIntelliTraceCollectorExecutable >* `\IntelliTraceSC.exe launch /cp:` *\<pathtocollectionplan >* `/f:` *\<Fullpathtoitkcefiledirectoryandfilename >* *\<pathtoappyürütülebilirfileandfilename >*

     Örneğin, **MyApp**adlı bir uygulamadan veri toplamak için:

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |||
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Collector yürütülebilirinin tam yolu, ıntellitracesc. exe|
    |*PathToCollectionPlan*|Toplayıcı için ayarları yapılandıran bir. xml dosyası olan bir koleksiyon planının yolu.<br /><br /> Toplayıcıyla birlikte gelen bir plan belirtebilirsiniz. Aşağıdaki planlar yönetilen uygulamalar için çalışır:<br /><br /> -   collection_plan.ASP.NET.default.xml<br />     Yalnızca özel durumlar, veritabanı çağrıları ve Web sunucusu istekleri dahil olmak üzere IntelliTrace olaylarını toplar.<br />-collection_plan. ASP. NET. Trace. xml<br />     İşlev çağrılarını ve collection_plan. ASP. NET. default. xml dosyasındaki tüm verileri toplar. Bu plan ayrıntılı analiz için uygundur, ancak uygulamanızı collection_plan. ASP. NET. default. xml ' den daha uzun sürebilir.<br /><br /> Uygulamanızı yavaşlatmayı önlemek için, bu planları özelleştirin veya kendi planınızı oluşturun. Güvenlik için, tüm özel planları toplayıcı dosyalarıyla aynı güvenli konuma yerleştirin. Bkz. [IntelliTrace koleksiyon planları oluşturma ve özelleştirme](https://go.microsoft.com/fwlink/?LinkId=227871) ve [uygulamamı yavaşlatmadan en çok veriyi edinme nasıl yaparım?.](#Minimizing) **Note:**  Varsayılan olarak,. iTrace dosyasının en büyük boyutu 100 MB 'tır. . İTrace dosyası bu sınıra ulaştığında, toplayıcı yeni girişler için alan oluşturmak üzere dosyanın en eski girdilerini siler. Bu sınırı değiştirmek için, koleksiyon planının `MaximumLogFileSize` özniteliğini düzenleyin. <br /><br /> *Bu koleksiyon planlarının yerelleştirilmiş sürümlerini nereden bulabilirim?*<br /><br /> Yerelleştirilmiş planları toplayıcı alt klasörlerinde bulabilirsiniz.|
    |*Fullpathtoitkcefiledirectoryanddosya adı*|. İTrace dosya dizininin tam yolu ve. iTrace dosya adı. **iTrace** uzantısı. **Güvenlik notno:**  Tam yolu belirtin, göreli bir yol değil.|
    |*PathToAppExecutableFileAndFileName*|Yönetilen uygulamanızın yolu ve dosya adı|

2. Uygulamadan çıkmadan veri toplamayı durdurun.

3. [. İTrace dosyasını Visual Studio Enterprise açın](#BKMK_View_IntelliTrace_Log_Files)

## <a name="BKMK_View_IntelliTrace_Log_Files"></a>. İTrace dosyasını Visual Studio Enterprise açın

> [!NOTE]
> IntelliTrace ile hata ayıklamak ve kodda adım adım ilerlemek için, eşleşen kaynak dosyaları ve sembol dosyalarınız olmalıdır. Bkz. [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

1. . İTrace dosyasını taşıyın veya Visual Studio Enterprise (Professional veya Community Edition değil) olan bir bilgisayara kopyalayın.

2. Visual Studio dışında. iTrace dosyasına çift tıklayın veya dosyayı Visual Studio içinde açın.

     Visual Studio, **IntelliTrace Özet** sayfasını gösterir. Çoğu bölümde, olayları veya diğer öğeleri gözden geçirebilir, bir öğe seçebilir ve bir olayın gerçekleştiği noktada ve IntelliTrace ile hata ayıklamaya başlayabilirsiniz. Bkz. [kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md).

    > [!NOTE]
    > IntelliTrace ile hata ayıklamak ve kodda adım adım ilerlemek için, geliştirme makinenizde eşleşen kaynak dosyaları ve sembol dosyaları olmalıdır. Bkz. [dağıtımdan sonra sorunları tanılama](../debugger/diagnose-problems-after-deployment.md).

## <a name="Minimizing"></a>Uygulamamı yavaşlatmadan en çok veriyi almak Nasıl yaparım??
 IntelliTrace pek çok veri toplayabilir, bu nedenle uygulamanızın performansı üzerindeki etki, IntelliTrace 'in topladığı verilere ve analiz yaptığı kodun türüne bağlıdır. Bkz. [Üretim sunucularında IntelliTrace toplamasını iyileştirme](https://go.microsoft.com/fwlink/?LinkId=255233).

 Uygulamanızı yavaşlatmadan en çok veriyi almanın bazı yolları aşağıda verilmiştir:

- Toplayıcı 'yı yalnızca bir sorun olduğunu düşündüğünüzde veya sorunu yeniden oluşturmak için çalıştırın.

   Koleksiyonu başlatın, sorunu yeniden oluşturun ve ardından toplamayı durdurun. Visual Studio Enterprise. iTrace dosyasını açın ve verileri inceleyin. Bkz [. Visual Studio Enterprise içindeki. iTrace dosyasını açma](#BKMK_View_IntelliTrace_Log_Files).

- Web uygulamaları ve SharePoint uygulamaları için toplayıcı, belirtilen uygulama havuzunu paylaşan her uygulama için verileri kaydeder. Bu, aynı uygulama havuzunu paylaşan herhangi bir uygulamayı yavaşlatabilir, ancak yalnızca bir koleksiyon planında tek bir uygulama için modüller belirleyebilseniz de olabilir.

   Toplayıcının diğer uygulamaları yavaşlatmasını engellemek için, her uygulamayı kendi uygulama havuzunda barındırın.

- IntelliTrace 'in veri topladığı toplama planındaki olayları gözden geçirin. İlgili olmayan veya ilgilendiğiniz olayları devre dışı bırakmak için koleksiyon planını düzenleyin.

   Bir olayı devre dışı bırakmak için, `<DiagnosticEventSpecification>` öğesi için `enabled` özniteliğini `false`olarak ayarlayın:

   `<DiagnosticEventSpecification enabled="false">`

   `enabled` özniteliği yoksa, olay etkinleştirilir.

   *Bu, performansı nasıl geliştirir?*

  - Uygulamayla ilgili olmayan olayları devre dışı bırakarak, başlangıç süresini azaltabilirsiniz. Örneğin, Windows Iş akışı kullanmayan uygulamalar için Windows Workflow olaylarını devre dışı bırakın.

  - Kayıt defterine erişen ancak kayıt defteri ayarlarıyla ilgili sorunları göstermemekte olan uygulamalar için kayıt defteri olaylarını devre dışı bırakarak, başlatma ve çalışma zamanı performansını geliştirebilirsiniz.

- IntelliTrace 'in veri topladığı toplama planındaki modülleri gözden geçirin. Koleksiyon planını yalnızca ilgilendiğiniz modülleri içerecek şekilde düzenleyin:

  1. Toplama planını açın. `<ModuleList>` öğesini bulun.

  2. `<ModuleList>`, `isExclusionList` özniteliğini `false`olarak ayarlayın.

  3. Her modülü aşağıdakilerden biriyle belirtmek için `<Name>` öğesini kullanın: dosya adı, adı bu dize veya ortak anahtar içeren herhangi bir modül dahil olmak üzere dize değeri.

     Örneğin, Fabrikam Fiber Web uygulamasının yalnızca ana Web modülünden veri toplamak için şöyle bir liste oluşturun:

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

   *Bu, performansı nasıl geliştirir?*

   Bu, uygulama başlatıldığında ve çalıştırıldığında IntelliTrace 'in topladığı Yöntem çağrısı bilgilerini ve diğer izleme verilerini azaltır. Bu veriler şunları yapmanızı sağlar:

  - Verileri topladıktan sonra kod adım adım.

  - İşlev çağrılarından geçirilen ve döndürülen değerleri inceleyin.

    *Bunun yerine modülleri dışlamayız?*

    Varsayılan olarak, koleksiyon planları `isExclusionList` özniteliğini `true`olarak ayarlayarak modülleri dışlayın. Ancak, modüllerin dışlanması hala, listenin ölçütlerine uymayan ve üçüncü taraf veya açık kaynaklı modüller gibi sizi ilgilendiremeyen modüllerden veri toplamaya neden olabilir.

- *IntelliTrace 'in toplamayacak herhangi bir veri var mı?*

   Evet, performans etkisini azaltmak için, IntelliTrace veri toplamayı, metotlara geçirilen ve metotlardan döndürülen temel veri türleri değerleriyle kısıtlar ve metotlara geçirilen ve metotlardan döndürülen üst düzey nesnelerdeki alanlarda ilkel veri türleri değerleri ile kısıtlar.

   Örneğin, bir tamsayı `id` ve `Employee` nesne `oldemployee`kabul eden bir `AlterEmployee` yöntemi imzasına sahip olduğunuzu varsayalım:

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   `Employee` türü şu özniteliklere sahiptir: `Id`, `Name`ve `HomeAddress`. `Employee` ve `Address` türü arasında bir ilişki ilişkisi vardır.

   ![Çalışan ve adres arasındaki ilişki](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   Toplayıcı, `AlterEmployee` yönteminden döndürülen `id`, `Employee.Id`, `Employee.Name` ve `Employee` nesnenin değerlerini kaydeder. Ancak toplayıcı, `Address` nesnesi hakkında, null olup olmadığı gibi bilgileri kaydetmez. Toplayıcı, bu yerel değişkenleri parametre olarak kullanmadığı sürece `AlterEmployee` yöntemindeki yerel değişkenlerle ilgili verileri de kaydetmez.

## <a name="WhereElse"></a>IntelliTrace verilerini başka bir şekilde alabilirim?

- Visual Studio Enterprise bir IntelliTrace hata ayıklama oturumundan, bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md).

- Microsoft Test Yöneticisi bir test oturumundan, bkz. [nasıl yapılır: IntelliTrace verilerini toplama, zor sorunları ayıklamaya yardımcı olma](/visualstudio/test/how-to-collect-intellitrace-data-to-help-debug-difficult-issues?view=vs-2015).

## <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?
 [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Bloglar
 [IntelliTrace tek başına toplayıcıyı uzaktan kullanma](https://go.microsoft.com/fwlink/?LinkId=262277)

 [IntelliTrace koleksiyon planları oluşturma ve özelleştirme](https://go.microsoft.com/fwlink/?LinkId=227871)

 [Üretim sunucularında IntelliTrace toplamasını iyileştirme](https://go.microsoft.com/fwlink/?LinkId=255233)

 [Visual Studio ALM + TFS blogu](https://go.microsoft.com/fwlink/?LinkID=201340)

### <a name="forums"></a>Forumlar
 [Visual Studio hata ayıklayıcısı](https://go.microsoft.com/fwlink/?LinkId=262263)

### <a name="videos"></a>Videolar
 [Channel 9 videosu: IntelliTrace verilerini toplama ve analiz etme](https://go.microsoft.com/fwlink/?LinkID=251851)
