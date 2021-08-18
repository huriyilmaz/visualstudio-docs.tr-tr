---
title: IntelliTrace tek başına toplayıcıyı kullanma | Microsoft Docs
description: IntelliTrace tek başına toplayıcıyı kullanarak hedef sistemin ortamını değiştirmeden Visual Studio yüklemeden veri toplayın.
ms.custom: SEO-VS-2020
ms.date: 07/30/2019
ms.topic: conceptual
f1_keywords:
- vs.historicaldebug.collectdataoutsideVS
helpviewer_keywords:
- IntelliTrace, debugging applications in production
ms.assetid: 1bde9807-8219-4a2a-a440-ac5ee5178159
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f91f9692ab0cd6c9b8cc4cbaf9cdc44cd4d12ad5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146595"
---
# <a name="using-the-intellitrace-stand-alone-collector-c-visual-basic"></a>IntelliTrace tek başına toplayıcıyı kullanma (C#, Visual Basic)

IntelliTrace tek başına toplayıcısı, hedef makineye yüklemeden ve hedef sistemin ortamını değiştirmeden üretim sunucularında veya diğer ortamlarda uygulamalarınız için Visual Studio **IntelliTrace** tanılama verilerini toplamanızı sağlar. IntelliTrace tek başına toplayıcı web, SharePoint, WPF ve Windows Forms uygulamaları üzerinde çalışır. Veri toplamayı tamamlayarak toplayıcıyı silebilir ve kaldırabilirsiniz.

 IntelliTrace'i uygulamalı olarak izleyin: Hata ayıklama için [üretimde IntelliTrace](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production) verilerini toplama ve analiz etme (Channel 9 videosu)

> [!NOTE]
> İzleme modunda uzak makinelerde çalışan web ve SharePoint uygulamaları için aynı IntelliTrace **verilerini Microsoft Monitoring Agent** **de toplayabilirsiniz.**
>
> Aracıyı İzleme modunda çalıştırarak IntelliTrace verisinde performansla ilgili olayları **toplayabilirsiniz.** **İzleme** modunun, İzleme modundan veya **IntelliTrace** tek başına toplayıcıdan daha az performans etkisi vardır.  Microsoft Monitoring Agent, hedef sistemin ortamını yüklenirken değiştirmez. Bkz. [Microsoft Monitoring Agent.](../debugger/using-the-microsoft-monitoring-agent.md)
> IntelliTrace tek başına toplayıcısı İşlem Anlık Görüntülerini desteklemez.

 **Gereksinimler**

- .NET Framework 3.5 veya daha yüksek

- Visual Studio Enterprise bir geliştirme Professional veya Community üzerinde .iTrace dosyalarını açmak için bir geliştirme bilgisayarına veya başka bir bilgisayara yükleme (ancak bu sürümler değil)

  > [!NOTE]
  > Sembol (.pdb) dosyalarınızı kaydetmeyi emin olun. IntelliTrace ile hata ayıklamak ve kodda adım adım bilgi için eşleşen kaynak dosyalarına ve sembol dosyalarına sahip olmak gerekir. Bkz. [Dağıtımdan sonra sorunları tanılama.](../debugger/diagnose-problems-after-deployment.md)

  **SSS**

- [Toplayıcıyla hangi uygulamalar çalışır?](#WhatApps)

- [Nasıl kullanmaya başlayabilirim?](#GetStarted)

- [Uygulamamı yavaşlatmadan en fazla veriyi nasıl edinebilirsiniz?](#Minimizing)

- [IntelliTrace verilerini başka nereden edinebilirsiniz?](#WhereElse)

## <a name="what-apps-work-with-the-collector"></a><a name="WhatApps"></a> Toplayıcıyla hangi uygulamalar çalışır?

- ASP.NET Internet Information Services (IIS) sürüm 7.0, 7.5, 8.0, 12.0 ve 16.0'da barındırılan web uygulamaları

- SharePoint 2010 ve SharePoint 2013 uygulamaları

- Windows Presentation Foundation (WPF) ve Windows Forms uygulamaları.

## <a name="how-do-i-get-started"></a><a name="GetStarted"></a> Nasıl yaparım? mi?

1. [Toplayıcıyı yükleme](#BKMK_Install_the_IntelliTrace_Stand_Alone_Collector)

2. [Toplayıcı dizini için izinleri ayarlama](#ConfigurePermissionsRunningCollector)

3. [Web uygulamaları veya web uygulamaları için veri toplamak için IntelliTrace PowerShell cmdlet'SharePoint yükleme](#BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets)

4. [.iTrace dosya dizini için izinleri ayarlama](#BKMK_Create_and_Configure_a_Log_File_Directory)

5. [Web uygulamasından veya web uygulamasından SharePoint toplama](#BKMK_Collect_Data_from_IIS_Application_Pools)

     -veya-

     [Yönetilen bir uygulamanın verilerini toplama](#BKMK_Collect_Data_from_Executables)

6. [.iTrace dosyasını Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="install-the-collector"></a><a name="BKMK_Install_the_IntelliTrace_Stand_Alone_Collector"></a> Toplayıcıyı yükleme

1. Uygulamanın sunucusunda toplayıcı dizinini oluşturun, örneğin: **C:\IntelliTraceCollector**

2. Toplayıcıyı Microsoft İndirme [Merkezi'nden](https://visualstudio.microsoft.com/downloads/#intellitrace-standalone-collector-for-visual-studio-2019), [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=intellitrace%20standalone%20collector%20visual%20studio%202017)veya Visual Studio 2013 Update 3 yükleme klasöründen edinin. [Visual Studio için IntelliTrace Collector 2013 Güncelleştirme 4:](https://www.microsoft.com/download/details.aspx?id=44909)

   - **Microsoft İndirme Merkezi** veya **my.visualstudio.com:**

     1. uygulamanın **IntelliTraceCollector.exe** İndir'i **seçin.**

     2. Dosyayı IntelliTraceCollector.exe dizine kaydedin, örneğin: **C:\IntelliTraceCollector**

     3. IntelliTraceCollector.exe. Bu, IntelliTraceCollection.cab ayıklar.

        \- veya -

   - **Visual Studio klasörü:**

     1. Toplayıcının IntelliTraceCollection.cab klasördeki dosyaları kopyalayın, örneğin:

          **.. \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace**

          veya önceki sürümler için Visual Studio:

          **.. \Microsoft Visual Studio 12.0\Common7\IDE\CommonExtensions\Microsoft\IntelliTrace\12.0.0**

     2. Toplayıcı IntelliTraceCollection.cab dizine bir dosya koyabilirsiniz, örneğin: **C:\IntelliTraceCollector**

3. Şu IntelliTraceCollection.cab:

   1. Uygulamanın sunucusunda yönetici olarak bir komut istemi penceresi açın.

   2. Toplayıcı dizinine göz atma, örneğin: **C:\IntelliTraceCollector**

   3. Aşağıdakini **genişletmek** için sonundaki nokta (**.**) dahil olmak üzere expand IntelliTraceCollection.cab:

        `expand  /f:* IntelliTraceCollection.cab .`

       > [!NOTE]
       > period (**.**) yerelleştirilmiş koleksiyon planlarını içeren alt klasörleri korur.

## <a name="set-up-permissions-for-the-collector-directory"></a><a name="ConfigurePermissionsRunningCollector"></a> Toplayıcı dizini için izinleri ayarlama

1. Uygulamanın sunucusunda yönetici olarak bir komut istemi penceresi açın.

2. Sunucu yöneticisine toplayıcı Windows tam izinleri vermek için Windows **icacls** komutunu kullanın. Örnek:

     `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\AdministratorID>* `":F`

3. Bir Web uygulaması veya uygulama için veri SharePoint için:

    1. Toplayıcı dizininde IntelliTrace PowerShell cmdlet'lerini çalıştıracak kişiye tam izinleri verin.

         Örnek:

         `icacls "C:\IntelliTraceCollector" /grant "` *\<Domain\UserID>* `":F`

    2. Web uygulaması için uygulama havuzuna veya uygulamanın toplayıcı SharePoint okuma ve yürütme izinlerini verin.

         Örnek:

        - DefaultAppPool uygulama **havuzunda bir** Web uygulaması için:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\DefaultAppPool":RX`

        - SharePoint **- 80** uygulama SharePoint bir uygulama için:

             `icacls "C:\IntelliTraceCollector" /grant "IIS APPPOOL\SharePoint - 80":RX`

## <a name="install-intellitrace-powershell-cmdlets-to-collect-data-for-web-apps-or-sharepoint-applications"></a><a name="BKMK_Set_up_the_IntelliTrace_PowerShell_commandlets"></a>Web uygulamaları veya web uygulamaları için veri toplamak için IntelliTrace PowerShell cmdlet'SharePoint yükleme

1. Uygulamanın sunucusunda PowerShell'in etkinleştirildiğinden emin olun. Windows Server'ın çoğu sürümlerinde, bu özelliği yönetim aracında **Sunucu Yöneticisi** abilirsiniz.

     ![PowerShell'i Sunucu Yöneticisi](../debugger/media/intellitrace_servermanager_addpowershell.png "INTELLITRACE_ServerManager_AddPowerShell")

2. IntelliTrace PowerShell cmdlet'lerini yükleyin.

    1. Yönetici olarak bir PowerShell komut penceresi açın.

        1. Başlat, **Tüm** Programlar, **Donatılar** **ve** **Windows PowerShell.**

        2. Aşağıdaki adımlardan birini seçin:

            - 64 bit işletim sistemlerinde, komutu için kısayol menüsünü **Windows PowerShell.** Yönetici olarak **çalıştır'ı seçin.**

            - 32 bit işletim sistemlerinde Windows PowerShell **(x86) kısayol menüsünü açın.** Yönetici olarak **çalıştır'ı seçin.**

    2. PowerShell komut penceresinde **import-Module** komutunu kullanarak komutunu **Microsoft.VisualStudio.IntelliTrace.PowerShell.dll.**

         Örnek:

         `Import-Module "C:\IntelliTraceCollector\Microsoft.VisualStudio.IntelliTrace.PowerShell.dll"`

## <a name="set-up-permissions-for-the-itrace-file-directory"></a><a name="BKMK_Create_and_Configure_a_Log_File_Directory"></a> .iTrace dosya dizini için izinleri ayarlama

1. Uygulamanın sunucusunda .iTrace dosya dizinini oluşturun, örneğin: **C:\IntelliTraceLogFiles**

   > [!NOTE]
   > - Uygulamanın yavaşlamaması için yerel yüksek hızlı diskte çok etkin olmayan bir konum seçin.
   >   - .iTrace dosyalarını ve toplayıcı dosyalarını aynı yere koyabilirsiniz. Ancak, bir Web uygulamanız veya SharePoint, burasının uygulamayı barındıran dizinin dışında olduğundan emin olun.
   >
   > [!IMPORTANT]
   > - .iTrace dosya dizinini yalnızca toplayıcıyla çalışması gereken kimliklerle kısıtlar. IntelliTrace, yöntem parametrelerine veya dönüş değerlerine geçen tüm verileri kaydedeyene kadar bir .iTrace dosyası kullanıcılardan, veritabanlarından, diğer kaynak konumlardan ve bağlantı dizelerinden alınan veriler gibi hassas bilgiler içerebilir.
   >   - .iTrace dosyalarını açanların hassas verileri görüntüleme yetkisine sahip olduğundan emin olun. .iTrace dosyalarını paylaştığınızda dikkatli olun. Diğer kişilerin erişimi olması gerekirse, dosyaları güvenli bir paylaşılan konuma kopyalayın.

2. Web uygulaması veya SharePoint için uygulama havuzuna .iTrace dosya dizininde tam izinler verin. Windows **icacls** komutunu kullanabilir veya Windows Gezgini'ni (veya Dosya Gezgini) kullanabilirsiniz.

    Örnek:

   - **Windows icacls komutuyla izinleri ayarlamak** için:

     - DefaultAppPool uygulama **havuzunda bir** Web uygulaması için:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\DefaultAppPool":F`

     - SharePoint **- 80** uygulama SharePoint bir uygulama için:

        `icacls "C:\IntelliTraceLogFiles" /grant "IIS APPPOOL\SharePoint - 80":F`

       -veya-

   - Windows Explorer (veya Dosya Gezgini) ile izinleri ayarlamak için:

     1. .iTrace dosya dizini için Özellikler'i açın. 

     2. Güvenlik sekmesinde **Düzenle,** **Ekle'yi** **seçin.**

     3. Bu nesne **türünü seçin kutusunda Yerleşik güvenlik** **sorumluları'nın göründüğünden emin** olun. Orada yoksa, eklemek için **Nesne Türleri'ne** tıklayın.

     4. Yerel bilgisayarınızın Bu konumdan **kutusunda göründüğünden emin** olun. Orada yoksa, değiştirmek için **Konumlar'ı** seçin.

     5. Seçlanacak **nesne adlarını girin kutusuna** Web uygulamasının veya uygulamanın uygulama havuzunu SharePoint ekleyin.

     6. Adı **çözümlemek için** Adları Denetleme'yi seçin. **Tamam'ı seçin.**

     7. Uygulama havuzunun Tam denetimine sahip **olduğundan emin olun.**

## <a name="collect-data-from-a-web-app-or-sharepoint-application"></a><a name="BKMK_Collect_Data_from_IIS_Application_Pools"></a>Web uygulamasından veya web uygulamasından SharePoint toplama

1. Veri toplamaya başlamak için yönetici olarak bir PowerShell komut penceresi açın ve şu komutu çalıştırın:

     `Start-IntelliTraceCollection` `"` *\<ApplicationPool>* `"` *\<PathToCollectionPlan>* *\<FullPathToITraceFileDirectory>*

    > [!IMPORTANT]
    > Bu komutu çalıştırdikten sonra, veri toplamaya başlamak istediğinizden onaylamak için **Y** yazın.

     Örneğin, **80** uygulama havuzu SharePoint bir SharePoint veri toplamak için:

     `Start-IntelliTraceCollection "SharePoint - 80" "C:\IntelliTraceCollector\collection_plan.ASP.NET.default.xml" "C:\IntelliTraceLogFiles"`

    |Ad|Açıklama|
    |-|-|
    |*ApplicationPool*|Uygulama havuzunun, uygulamanın çalıştır olduğu ad|
    |*PathToCollectionPlan*|Toplayıcı için ayarları yapılandıran bir .xml planı yolu.<br /><br /> Toplayıcıyla birlikte gelen bir plan belirterek. Aşağıdaki planlar Web uygulamaları ve SharePoint çalışır:<br /><br /> - collection_plan.ASP.NET.default.xml<br />     Özel durumlar, veritabanı çağrıları ve Web SharePoint dahil olmak üzere yalnızca IntelliTrace olaylarını ve olaylarını toplar.<br />- collection_plan.ASP.NET.trace.xml<br />     İşlev çağrılarını ve tüm verileri collection_plan.ASP.NET.default.xml. Bu plan ayrıntılı analiz için iyidir, ancak uygulamalarınızı daha fazla collection_plan.ASP.NET.default.xml.<br /><br /> Uygulamanın yavaşlamaması için bu planları özelleştirin veya kendi planınızı oluşturun. Güvenlik için, özel planları toplayıcı dosyalarıyla aynı güvenli konuma koyabilirsiniz. Bkz. [IntelliTrace Koleksiyon](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) Planları Oluşturma ve Özelleştirme Nasıl yaparım? uygulamamı [yavaşlatmadan en fazla veriye](#Minimizing) sahip olmak mı? **Not:**  Varsayılan olarak, .iTrace dosyasının en büyük boyutu 100 MB'tır. .iTrace dosyası bu sınıra ulaştığında toplayıcı, daha yeni girişlere yer açacak şekilde dosyanın ilk girişlerini siler. Bu sınırı değiştirmek için koleksiyon planının özniteliğini `MaximumLogFileSize` düzenleyin. <br /><br /> *Bu koleksiyon planlarının yerelleştirilmiş sürümlerini nerede bulamıyorum?*<br /><br /> Yerelleştirilmiş planları toplayıcının alt klasörlerinde bulabilirsiniz.|
    |*FullPathToITraceFileDirectory*|.iTrace dosya dizininin tam yolu. **Güvenlik Notu:**  Göreli yol değil tam yolu sağlar.|

     Toplayıcı, uygulama havuzuna iliştirilen verileri toplamaya başlar.

     *Şu anda .iTrace dosyasını açabilir miyim?* Hayır, dosya veri toplama sırasında kilitlenir.

2. Sorunu yeniden oluşturun.

3. .iTrace dosyasının denetim noktasını oluşturmak için şu söz dizimi kullanın:

     `Checkpoint-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

4. Koleksiyon durumunu kontrol etmek için şu söz dizimlerini kullanın:

     `Get-IntelliTraceCollectionStatus`

5. Veri toplamayı durdurmak için şu söz dizimini kullanın:

     `Stop-IntelliTraceCollection` `"` *\<ApplicationPool>* `"`

    > [!IMPORTANT]
    > Bu komutu çalıştırdikten sonra, veri toplamayı durdurmak istediğinizden onaylamak için **Y** yazın. Aksi takdirde, toplayıcı veri toplamaya devam eder, iTrace dosyası kilitli kalır veya dosya herhangi bir yararlı veri içere içerebilir.

6. [.iTrace dosyasını Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="collect-data-from-a-managed-app"></a><a name="BKMK_Collect_Data_from_Executables"></a> Yönetilen bir uygulamanın verilerini toplama

1. Uygulamasını başlatmak ve aynı anda veri toplamak için şu söz dizimini kullanın:

     *\<FullPathToIntelliTraceCollectorExecutable>* `\IntelliTraceSC.exe launch /cp:` *\<PathToCollectionPlan>* `/f:` *\<FullPathToITraceFileDirectoryAndFileName>* *\<PathToAppExecutableFileAndFileName>*

     Örneğin, MyApp adlı bir uygulamanın verilerini **toplamak için:**

     `C:IntelliTraceCollectorIntelliTraceSC.exe launch /cp:"C:IntelliTraceCollectorcollection_plan.ASP.NET.default.xml" /f:"C:IntelliTraceLogFilesMyApp.itrace" "C:MyAppMyApp.exe"`

    |Ad|Açıklama|
    |-|-|
    |*FullPathToIntelliTraceCollectorExecutable*|Toplayıcı yürütülebilir dosyasının tam yolu, IntelliTraceSC.exe|
    |*PathToCollectionPlan*|Toplayıcı için ayarları yapılandıran bir .xml planı yolu.<br /><br /> Toplayıcıyla birlikte gelen bir plan belirterek. Aşağıdaki planlar yönetilen uygulamalar için çalışır:<br /><br /> - collection_plan.ASP.NET.default.xml<br />     Yalnızca özel durumlar, veritabanı çağrıları ve Web sunucusu istekleri gibi IntelliTrace olaylarını toplar.<br />- collection_plan.ASP.NET.trace.xml<br />     İşlev çağrılarını ve tüm verileri collection_plan.ASP.NET.default.xml. Bu plan ayrıntılı analiz için iyidir, ancak uygulamalarınızı daha fazla collection_plan.ASP.NET.default.xml.<br /><br /> Uygulamanın yavaşlamaması için bu planları özelleştirin veya kendi planınızı oluşturun. Güvenlik için, özel planları toplayıcı dosyalarıyla aynı güvenli konuma koyabilirsiniz. Bkz. [IntelliTrace Koleksiyon](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/) Planları Oluşturma ve Özelleştirme Nasıl yaparım? uygulamamı [yavaşlatmadan en fazla veriye](#Minimizing) sahip olmak mı? **Not:**  Varsayılan olarak, .iTrace dosyasının en büyük boyutu 100 MB'tır. .iTrace dosyası bu sınıra ulaştığında toplayıcı, daha yeni girişlere yer açacak şekilde dosyanın ilk girişlerini siler. Bu sınırı değiştirmek için koleksiyon planının özniteliğini `MaximumLogFileSize` düzenleyin. <br /><br /> *Bu koleksiyon planlarının yerelleştirilmiş sürümlerini nerede bulamıyorum?*<br /><br /> Yerelleştirilmiş planları toplayıcının alt klasörlerinde bulabilirsiniz.|
    |*FullPathToITraceFileDirectoryAndFileName*|.iTrace dosya dizininin tam yolu ve .itrace uzantısına sahip **.iTrace dosya** adı. **Güvenlik Notu:**  Göreli yol değil tam yolu sağlar.|
    |*PathToAppExecutableFileAndFileName*|Yönetilen uygulamanın yolu ve dosya adı|

2. Uygulamadan çıkarak veri toplamayı durdurun.

3. [.iTrace dosyasını Visual Studio Enterprise](#BKMK_View_IntelliTrace_Log_Files)

## <a name="open-the-itrace-file-in-visual-studio-enterprise"></a><a name="BKMK_View_IntelliTrace_Log_Files"></a>.iTrace dosyasını Visual Studio Enterprise

> [!NOTE]
> IntelliTrace ile hata ayıklamak ve kodda adım adım bilgi için eşleşen kaynak dosyalarına ve sembol dosyalarına sahip olmak gerekir. Bkz. [Dağıtımdan sonra sorunları tanılama.](../debugger/diagnose-problems-after-deployment.md)

1. .iTrace dosyasını taşıma veya bu dosyayı Visual Studio Enterprise (Professional veya Community kopyalayın).

2. Dosyanın dışında .iTrace dosyasına çift Visual Studio veya dosyayı dosyanın içinden Visual Studio.

     Visual Studio **IntelliTrace Özet sayfası** görüntülenir. Çoğu bölümde olayları veya diğer öğeleri gözden geçirebilirsiniz, bir öğe seçebilir ve intelliTrace ile bir olayın nerede ve ne zaman meydana geldiğinde hata ayıklamaya başlayabilirsiniz. Bkz. [Kayıtlı IntelliTrace verilerini kullanma.](../debugger/using-saved-intellitrace-data.md)

    > [!NOTE]
    > IntelliTrace ile hata ayıklamak ve kodda adım adım yol yapmak için, geliştirme makinenize eşleşen kaynak dosyalarına ve sembol dosyalarına sahipsiniz. Bkz. [Dağıtımdan sonra sorunları tanılama.](../debugger/diagnose-problems-after-deployment.md)

## <a name="how-do-i-get-the-most-data-without-slowing-down-my-app"></a><a name="Minimizing"></a> Nasıl yaparım? yavaşlatmadan en fazla veri mi elde ediyor?
 IntelliTrace çok fazla veri toplayabilirsiniz. Bu nedenle, uygulama performansının etkisi IntelliTrace'in toplayan verilere ve analiz etme türüne bağlıdır. Bkz. [Üretim Sunucularında IntelliTrace Koleksiyonunu En Iyi Duruma Getirme.](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 Aşağıda, uygulamalarınızı yavaşlatmadan en fazla veriye erişim elde etmenin bazı yolları vesiniz:

- Toplayıcıyı yalnızca bir sorun olduğunu veya sorunu yeniden oluşturanın bir zaman içinde çalıştırın.

   Koleksiyonu başlatma, sorunu yeniden oluşturma ve ardından toplamayı durdurma. .iTrace dosyasını dosyanın Visual Studio Enterprise ve verileri inceleme. Bkz. [.iTrace dosyasını Visual Studio Enterprise.](#BKMK_View_IntelliTrace_Log_Files)

- Web uygulamaları ve SharePoint uygulamaları için toplayıcı, belirtilen uygulama havuzunu paylaşan her uygulamanın verilerini kaydedmektedir. Bir koleksiyon planında yalnızca tek bir uygulama için modül belirtebilirsiniz ancak bu, aynı uygulama havuzunu paylaşan tüm uygulamalarda yavaşlamaya neden olabilir.

   Toplayıcının diğer uygulamaları yavaşlatmalarını önlemek için her uygulamayı kendi uygulama havuzunda barındırabilirsiniz.

- IntelliTrace'in veri toplayan koleksiyon planında olayları gözden geçirme. İlgili olmayan veya ilginizi toplamaya gerek olmayan olayları devre dışı bırakmak için koleksiyon planını düzenleyin.

   Bir olayı devre dışı bırakmak için `enabled` öğesinin `<DiagnosticEventSpecification>` özniteliğini olarak `false` ayarlayın:

   `<DiagnosticEventSpecification enabled="false">`

   Öznitelik `enabled` yoksa olay etkinleştirilir.

   *Bu, performansı nasıl artırır?*

  - Uygulamayla ilgili olmayan olayları devre dışı bırakarak başlatma süresini azaltabilirsiniz. Örneğin, Windows kullanmayan uygulamalar için İş Akışı olaylarını Windows devre dışı bırakabilirsiniz.

  - Kayıt defterine erişen ancak kayıt defteri ayarlarıyla ilgili sorunları göstermeyen uygulamalar için kayıt defteri olaylarını devre dışı bırakarak hem başlatma hem de çalışma zamanı performansını geliştirebilirsiniz.

- IntelliTrace'in veri toplayan koleksiyon planı modüllerini gözden geçirme. Koleksiyon planını yalnızca ilginizi gereken modülleri içerecek şekilde düzenleyin:

  1. Koleksiyon planını açın. öğesini `<ModuleList>` bulun.

  2. içinde `<ModuleList>` `isExclusionList` özniteliğini olarak `false` ayarlayın.

  3. Her modülü şunlardan biri ile belirtmek için öğesini kullanın: dosya adı, dize değeri, adı bu dizeyi veya ortak anahtarı içeren herhangi `<Name>` bir modülü dahil etmek için.

     Örneğin, Fabrikam Fiber Web uygulamasının yalnızca ana Web modülünden veri toplamak için aşağıdakine benzer bir liste oluşturun:

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

   *Bu, performansı nasıl artırır?*

   Bu, intelliTrace'in uygulama başlatıldığında ve çalıştır olduğunda toplayan yöntem çağrı bilgileri ve diğer izleme verileri miktarını azaltır. Bu veriler şunları sağlar:

  - Verileri toplayarak kodda adım adım inin.

  - İşlev çağrılarına geçirilen ve işlev çağrılarından döndürülen değerleri inceleme.

    *Bunun yerine modüller neden dışlansın?*

    Varsayılan olarak, koleksiyon planları özniteliğini olarak ayarerek modülleri `isExclusionList` `true` dışlar. Ancak, modüllerin hariç tutularak yine de listenin ölçütlerine uygun olmayan ve üçüncü taraf veya açık kaynak modüller gibi ilgini toplamayabilirsiniz.

- *IntelliTrace'in toplaması mümkün olmayan veriler var mı?*

   Evet, performans etkisini azaltmak için IntelliTrace, veri toplamayı yöntemlere geçirilen ve yöntemlerden döndürülen ilkel veri türlerinin değerleriyle ve yöntemlerden geçirilen ve yöntemlerden döndürülen üst düzey nesnelerdeki alanlardaki temel veri türlerinin değerleriyle kısıtlar.

   Örneğin, bir tamsayıyı ve `AlterEmployee` nesnesini kabul eden bir yöntem imzanız olduğunu `id` `Employee` `oldemployee` varsayalım:

   `public Employee AlterEmployee(int id, Employee oldemployee)`

   Türün `Employee` şu öznitelikleri vardır: `Id` , ve `Name` `HomeAddress` . ile türü arasında bir `Employee` ilişki `Address` vardır.

   ![Çalışan ile Adres arasındaki ilişki](../debugger/media/employeeaddressrelationship.png "EmployeeAddressRelationship")

   Toplayıcı, yönteminden `id` `Employee.Id` döndürülen , ve `Employee.Name` `Employee` nesnesinin değerlerini `AlterEmployee` kaydeder. Ancak toplayıcı, nesneyle ilgili bilgileri null olup `Address` olmadığı dışında kaydetmez. Toplayıcı ayrıca, diğer yöntemler bu yerel değişkenleri parametre olarak kullanmadıkça yönteminde yerel değişkenlerle ilgili verileri kaydetmez ve bu noktada yöntem parametresi `AlterEmployee` olarak kaydedilirler.

## <a name="where-else-can-i-get-intellitrace-data"></a><a name="WhereElse"></a> IntelliTrace verilerini başka nereden edinebilirsiniz?

IntelliTrace verilerini bir IntelliTrace hata ayıklama oturumundan Visual Studio Enterprise. Bkz. [IntelliTrace Özellikleri.](../debugger/intellitrace-features.md)

## <a name="where-can-i-get-more-information"></a>Daha fazla bilgiyi nereden bulabilirim?
 [Kayıtlı IntelliTrace verilerini kullanma](../debugger/using-saved-intellitrace-data.md)

 [IntelliTrace](../debugger/intellitrace.md)

### <a name="blogs"></a>Bloglar
 [IntelliTrace Tek Başına Toplayıcıyı Uzaktan Kullanma](https://devblogs.microsoft.com/devops/using-the-intellitrace-standalone-collector-remotely/)

 [IntelliTrace Koleksiyon Planları Oluşturma ve Özelleştirme](https://devblogs.microsoft.com/devops/modifying-an-intellitrace-collection-plan-for-the-stand-alone-collector/)

 [Üretim Sunucularında IntelliTrace Koleksiyonunu En Iyi Duruma Getirme](https://devblogs.microsoft.com/devops/optimizing-intellitrace-collection-on-production-server/)

 [Microsoft DevOps](https://devblogs.microsoft.com/devops/)

### <a name="forums"></a>Forumlar
 [Visual Studio Hata Ayıklayıcısı](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="videos"></a>Videolar
 [Channel 9 videosu: IntelliTrace verilerini toplama ve analiz etme](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Collecting-and-analyzing-data-in-production)
