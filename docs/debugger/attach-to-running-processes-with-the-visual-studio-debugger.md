---
title: Hata ayıklayıcısı ile çalıştırma işlemleri iliştirme
description: Yerel veya uzak bir Visual Studio çalışan bir işleme hata ayıklayıcının nasıl ekli olduğunu keşfedin.
ms.custom: SEO-VS-2020
ms.date: 09/10/2021
ms.topic: conceptual
f1_keywords:
- vs.debug.processes.attach
- vs.debug.process
- vs.debug.programs
- vs.debug.detaching
- vs.debug.processes
- vs.debug.error.attach
- vs.debug.remotemachine
dev_langs:
- CSharp
- FSharp
- C++
- VB
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ad2da32cf1d500d1f3890730dc7ba0aaa0b2fd6c
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970133"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile çalıştırma işlemleri iliştirme

Yerel veya uzak Visual Studio çalışan bir işleme hata ayıklayıcısını iliştirebilirsiniz. İşlem çalıştırıldıktan sonra İşleme Ekle'yi seçin veya Visual Studio'de  >   **Ctrl** + **Alt** + **p**  tuşlarına basın ve hata ayıklayıcıyı işleme eklemek için İşleme Ekle iletişim kutusunu kullanın.

Yerel veya **uzak** bilgisayarlarda çalışan uygulamalarda hata ayıklamak, aynı anda birden çok işlemde hata ayıklamak, Visual Studio'de oluşturulmadı olan uygulamalarda hata ayıklamak veya hata ayıklayıcı ekli olarak Visual Studio'den başlatmadınız herhangi bir uygulamada hata ayıklamak için İşleme İliştir'i kullanabilirsiniz. Örneğin, hata ayıklayıcı olmadan bir uygulama çalıştırıyorsanız ve bir özel durumla karşılaşıyorsanız, hata ayıklayıcıyı uygulamayı çalıştıran işleme iliştirerek hata ayıklamaya başlayabilirsiniz.

> [!TIP]
> Hata ayıklama senaryonda İşleme **Ekle'nin** kullanılamayacak mı? Bkz. [Yaygın hata ayıklama senaryoları.](#BKMK_Scenarios)

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Yerel makineniz üzerinde çalışan bir işleme ekleme

Daha önce bağlı olduğunu bir işleme hızla yeniden iliştirk için [bkz. Bir işleme yeniden iliştirin.](#BKMK_reattach)

**Yerel bilgisayarınızda bir işleme eklemek için:**

1. Bu Visual Studio İşleme **Ekle** iletişim kutusunu açmak için İşleme Ekle  >   'yi seçin **(veya Ctrl** + **Alt** + **P** **tuşlarına** basın).

1. Bağlantı türünü **kontrol edin.**

   Çoğu senaryoda Varsayılan 'i **kullanabilirsiniz.** Bazı senaryolar için farklı bir bağlantı türü gerekli olabilir. Daha fazla bilgi için bu makaledeki diğer bölümlere veya [Yaygın hata ayıklama senaryolarına bakın.](#BKMK_Scenarios)

1. Bağlantı **hedefi'nin yerel** makinenizin adını ayarlayın.

   ![Bağlantı hedefi yerel makine adına ayarlanmış şekilde İşleme ekle iletişim kutusunun ekran görüntüsü.](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. Kullanılabilir **işlemler listesinde,** eklemek istediğiniz işlemi veya işlemleri bulun ve seçin.

   - Bir işlemi hızlı bir şekilde seçmek için İşlemleri filtrele kutusuna **adını veya ilk harfini** yazın.

   - İşlem adını bilmiyorsanız listeye göz atabilir veya bazı yaygın işlem adları için yaygın hata ayıklama [senaryolarına](#BKMK_Scenarios) göz atabilirsiniz.

   >[!TIP]
   >İşleme Ekle iletişim kutusu açıkken  işlemler arka planda başlat ve durarken, çalışan işlemlerin listesi her zaman güncel olmayacaktır. Geçerli listeyi görmek **için** Istediğiniz zaman Yenile'yi seçebilirsiniz.

1. Ekle **alanında** hata ayıklamayı planla kod türünün listelenmiş olduğundan emin olun. Varsayılan Otomatik **ayarı** çoğu uygulama türü için çalışır.

   Varsayılan bağlantı türünü **kullanıyorsanız,** eklemek istediğiniz kod türünü el ile seçebilirsiniz. Aksi takdirde Seç **seçeneği** devre dışı bırakılabilir.

   Kod türlerini el ile seçmek için:
   1. **Seç**’e tıklayın.
   1. Kod Türü **Seç iletişim kutusunda** Bu kod türlerinde hata **ayıkla'ya tıklayın.**
      Listede bir işleme eklemeye çalışma sırasında hatayla karşınıza çıkarsanız, sorunu gidermeye yardımcı olmak için Kod Türü Seç iletişim [kutusunu](#BKMK_Troubleshoot_attach_errors) kullanabilirsiniz. [](../debugger/select-code-type-dialog-box.md)
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. **Tamam**’ı seçin.

1. **Ekle'yi seçin.**

>[!NOTE]
>Hata ayıklama için birden çok uygulamaya bağlı olabilirsiniz, ancak aynı anda hata ayıklayıcıda yalnızca bir uygulama etkindir. Etkin uygulamayı Hata Ayıklama Konumu araç Visual Studio **İşlemler** **penceresinden ayarlayın.**

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Uzak bir bilgisayarda işleme ekleme

Ayrıca İşleme Ekle iletişim kutusunda  uzak bir bilgisayar seçebilirsiniz, o bilgisayarda çalışan kullanılabilir işlemlerin listesini ekleyebilirsiniz ve hata ayıklama için bir veya daha fazla işleme ekleyebilirsiniz. Uzak hata ayıklayıcı (*msvsmon.exe*) uzak bilgisayarda çalışıyor olmalıdır. Daha fazla bilgi için [bkz. Uzaktan hata ayıklama.](../debugger/remote-debugging.md)

IIS'ye dağıtılmış olan uygulama ASP.NET hata ayıklamaya ilişkin daha eksiksiz yönergeler için bkz. Uzak iis ASP.NET bilgisayarda uzaktan [hata ayıklama.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)

**Uzak bir bilgisayarda çalışan bir işleme eklemek için:**

1. Bu Visual Studio İşleme **Ekle** iletişim kutusunu açmak için İşleme Ekle  >   'yi seçin **(veya Ctrl** + **Alt** + **P** **tuşlarına** basın).

1. Bağlantı türünü **kontrol edin.**

   Çoğu senaryoda Varsayılan 'i **kullanabilirsiniz.** Linux'da veya kapsayıcılı uygulamada hata ayıklama gibi bazı senaryolar farklı bir bağlantı türü gerektirir. Daha fazla bilgi için bu makaledeki diğer bölümlere veya [Yaygın hata ayıklama senaryolarına bakın.](#BKMK_Scenarios)

1. Bağlantı **hedefi kutusunda,** aşağıdaki yöntemlerden birini kullanarak uzak bilgisayarı seçin:

   - Bağlantı hedefi'nin yanındaki açılan **oku seçin** ve açılan listeden bilgisayar adını seçin.
   - Bağlantı hedefi kutusuna bilgisayar **adını yazın ve** Enter tuşuna **basın.**

     Gerekli Visual Studio bilgisayar adına eklendiğinden emin olun. Bu bağlantı noktası şu biçimde görünür: **\<remote computer name> :p ort**

     ::: moniker range=">= vs-2022"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini (örneğin, ) kullanmayı `123.45.678.9:4022` deneyin. 4026, Visual Studio 2022 uzaktan hata ayıklayıcısı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için [bkz. Uzaktan hata ayıklayıcı bağlantı noktası atamaları.](remote-debugger-port-assignments.md)

     ::: moniker-end
     ::: moniker range="vs-2019"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini (örneğin, ) kullanmayı `123.45.678.9:4022` deneyin. 4024, Visual Studio 2019 uzaktan hata ayıklayıcısı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için [bkz. Uzaktan hata ayıklayıcı bağlantı noktası atamaları.](remote-debugger-port-assignments.md)

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini (örneğin, ) kullanmayı `123.45.678.9:4022` deneyin. 4022, Visual Studio 2017 uzaktan hata ayıklayıcısı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için [bkz. Uzaktan hata ayıklayıcı bağlantı noktası atamaları.](remote-debugger-port-assignments.md)

     ::: moniker-end

   - Bağlantı **hedefi kutusunun** yanındaki Bul **düğmesini seçerek** Uzak Bağlantılar **iletişim kutusunu** açın. Uzak **Bağlantılar** iletişim kutusu, yerel alt ağ veya doğrudan bilgisayarınıza bağlı tüm cihazları listeler. Uzak cihazları bulmak [için sunucuda UDP bağlantı noktası 3702'yi](../debugger/remote-debugger-port-assignments.md) açmanız gerekir. İstediğiniz bilgisayarı veya cihazı seçin ve seç'e **tıklayın.**

   > [!NOTE]
   > Hata **ayıklama oturumları** arasında Bağlantı türü ayarı devam eder. Bağlantı **hedefi ayarı,** yalnızca bu hedefle başarılı bir hata ayıklama bağlantısı oluştu ise hata ayıklama oturumları arasında devam eder.

3. Kullanılabilir **işlemler** listesini doldurmak için **Yenile'ye** tıklayın.

    >[!TIP]
    >İşleme Ekle iletişim kutusu açıkken  işlemler arka planda başlat ve durarken, çalışan işlemlerin listesi her zaman güncel olmayacaktır. Geçerli listeyi görmek **için** Istediğiniz zaman Yenile'yi seçebilirsiniz.

4. Kullanılabilir **işlemler listesinde,** eklemek istediğiniz işlemi veya işlemleri bulun ve seçin.

   - Bir işlemi hızlı bir şekilde seçmek için İşlemleri filtrele kutusuna **adını veya ilk harfini** yazın.

   - İşlem adını bilmiyorsanız listeye göz atabilir veya bazı yaygın işlem adları için yaygın hata ayıklama [senaryolarına](#BKMK_Scenarios) göz atabilirsiniz.

   - Tüm kullanıcı hesapları altında çalışan işlemleri bulmak için Tüm **kullanıcılardan işlemleri göster onay** kutusunu seçin.

     >[!NOTE]
     >Güvenilmeyen bir kullanıcı hesabına ait bir işleme eklemeye çalışsanız, bir güvenlik uyarısı iletişim kutusu onayı görüntülenir. Daha fazla bilgi için bkz. Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu bir [işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme iliştirin.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

5. Ekle **alanında** hata ayıklamayı planla kod türünün listelenmiş olduğundan emin olun. Varsayılan Otomatik **ayarı** çoğu uygulama türü için çalışır.

   Varsayılan bağlantı türünü **kullanıyorsanız,** eklemek istediğiniz kod türünü el ile seçebilirsiniz. Aksi takdirde Seç **seçeneği** devre dışı bırakılabilir.

   Kod türlerini el ile seçmek için:
   1. **Seç**’e tıklayın.
   1. Kod Türü **Seç iletişim kutusunda** Bu kod türlerinde hata **ayıkla'ya tıklayın.**
      Listede bir işleme eklemeye çalışma sırasında hatayla karşınıza çıkarsanız, sorunu gidermeye yardımcı olmak için Kod Türü Seç iletişim [kutusunu](#BKMK_Troubleshoot_attach_errors) kullanabilirsiniz. [](../debugger/select-code-type-dialog-box.md)
   1. **Tamam**’ı seçin.

6. **Ekle'yi seçin.**

>[!NOTE]
>Hata ayıklama için birden çok uygulamaya bağlı olabilirsiniz, ancak aynı anda hata ayıklayıcıda yalnızca bir uygulama etkindir. Etkin uygulamayı Hata Ayıklama Konumu araç Visual Studio **İşlemler** **penceresinden ayarlayın.**

Bazı durumlarda, Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata  ayıklasanız, Kullanılabilir işlemler listesi tüm kullanılabilir işlemleri görüntülemez. Bir hesabı Visual Studio hesabı olan bir kullanıcı olarak çalıştırıyorsanız, Kullanılabilir işlemler listesi Oturum 0'da çalışan işlemleri göstermez.  Oturum 0, hizmetler ve diğer sunucu işlemleri için kullanılır, örneğin *w3wp.exe.* Bir yönetici hesabı altında veya Terminal Hizmetleri oturumu yerine sunucu konsolundan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştırarak sorunu çözebilirsiniz.

Bu geçici çözümlerin hiçbiri mümkünse, üçüncü bir seçenek de komut satırına bağlı olarak komutunu `vsjitdebugger.exe -p <ProcessId>` çalıştırarak Windows eklemektir. İşlem kimliğini belirlemek için *tlist.exe.* Daha fazla *tlist.exe* için, WDK ve WinDbg indirmeleri Windows için Hata Ayıklama [Araçları'nın indirip yükleyin.](/windows-hardware/drivers/download-the-wdk)

## <a name="attach-to-a-net-core-process-running-on-azure-app-service-windows"></a>Azure App Service üzerinde çalışan bir .NET Core Windows ekleme

Azure App Service 'de (Windows) yayımlarsanız, Barındırma altındaki **...**  menüsünün altında Hata Ayıklayıcı ekle seçeneğini **bulabilirsiniz.** Visual Studio, uzaktan hata ayıklayıcıyı profilin yayım Azure App Service (Windows) örneğine eklemeye çalışır.

:::image type="content" source="../debugger/media/attach-debugger-publish-profile.png" alt-text="Yayımlama özeti sayfasının içindeki Hata Ayıklayıcı ekle seçeneğinin ekran görüntüsü.":::

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH kullanarak Linux üzerinde çalışan bir .NET Core sürecine ekleme

Daha fazla bilgi için bkz. [SSH kullanarak Linux üzerinde çalışan uzaktan hata ayıklama .NET Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Docker kapsayıcısında çalışan bir işleme iliştirme

Visual Studio 2019 ' den başlayarak, Visual Studio hata ayıklayıcısını bir docker kapsayıcısında çalışan bir işleme ekleyebilirsiniz. Linux .NET Core Docker kapsayıcısı için bkz. [Linux Docker kapsayıcısında çalışan bir Işleme iliştirme](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container). Windows docker kapsayıcısı için, bkz. [Windows docker kapsayıcısında çalışan bir işleme iliştirme](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container).

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Bir işleme yeniden iliştir

Daha önce iliştirmiş olduğunuz işlemlere hızlı bir şekilde **yeniden iliştirebilirsiniz**  >    +  + . Bu komutu seçtiğinizde, hata ayıklayıcı, ilk olarak önceki işlem KIMLIĞIYLE eşleştirmeye çalışırken ve başarısız olursa, önceki işlem adıyla eşleşen son işlemler için iliştirmeye çalışacaktır. Eşleşme bulunmazsa veya birkaç işlem aynı ada sahip ise, doğru işlemi seçebilmeniz **Için Işleme İliştir** iletişim kutusu açılır.

> [!NOTE]
> **işleme yeniden iliştir** komutu, Visual Studio 2017 ' den başlayarak kullanılabilir.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Ortak hata ayıklama senaryoları

**Işleme eklemeyi** ve hangi işlemin iliştirileyeceğini belirlemenize yardımcı olmak için, aşağıdaki tabloda, mevcut yerlerde daha fazla yönergelerin bağlantılarıyla birlikte birkaç ortak hata ayıklama senaryosu gösterilmektedir. (Liste kapsamlı değildir.)

evrensel Windows uygulaması (UWP) uygulamaları gibi bazı uygulama türlerinde doğrudan bir işlem adına iliştiremezsiniz, ancak bunun yerine Visual Studio **yüklü uygulama paketini hata ayıkla** menü seçeneğini kullanın (bkz. tablo).

Hata ayıklayıcının C++ dilinde yazılmış koda eklemesi için kodun bir yayma yapması gerekir `DebuggableAttribute` . [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) bağlayıcı seçeneğiyle bağlantı kurarak bunu kodunuza otomatik olarak ekleyebilirsiniz.

İstemci tarafında komut dosyası hata ayıklaması için, tarayıcıda betik hata ayıklaması etkinleştirilmelidir. chrome üzerinde istemci tarafı komut dosyasında hata ayıklamak için, kod türü olarak **javascript (Chrome)** veya **javascript (Microsoft Edge-Chromium)** seçeneğini belirleyin ve uygulama türüne bağlı olarak, tüm Chrome örneklerini kapatıp tarayıcıyı hata ayıklama modunda ( `chrome.exe --remote-debugging-port=9222` bir komut satırından yazın) başlatmanız gerekebilir. Visual Studio önceki sürümlerinde Chrome için betik hata ayıklayıcı **Web paketi** idi.

eklenecek çalışan bir işlemi hızlıca seçmek için, Visual Studio ' de **Ctrl** + **Alt** + **P** yazın ve ardından işlem adının ilk harfini yazın.

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|ııs sunucusunda uzaktan hata ayıklama ASP.NET 4 veya 4,5|Uzak araçları kullanma ve **Işleme iliştirme**|*w3wp.exe*|bkz. uzaktan [hata ayıklama ASP.NET uzak ııs bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|ııs sunucusunda uzaktan hata ayıklama ASP.NET Core|Uzak araçları kullanma ve **Işleme iliştirme**|*w3wp.exe* veya *dotnet.exe*|.NET Core 3 ' te başlayarak, *w3wp.exe* işlemi varsayılan [uygulama içi barındırma modelinde](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models)kullanılır. Uygulama dağıtımı için bkz. [IIS 'de yayımlama](/aspnet/core/host-and-deploy/iis/). daha ayrıntılı bilgi için bkz. uzaktan [hata ayıklama ASP.NET Core uzak bir ııs bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach) .|
|Desteklenen uygulama türleri için yerel bir IIS sunucusunda istemci tarafı komut dosyasında hata ayıkla |**İşlemek Için İliştir** kullanın|*chrome.exe*, *MicrosoftEdgeCP.exe* veya *iexplore.exe*|Betik hata ayıklaması etkinleştirilmelidir. Chrome için Ayrıca, hata ayıklama modunda ( `chrome.exe --remote-debugging-port=9222` bir komut satırından tür) Chrome 'u çalıştırmanız ve **Iliştirme** alanında **JavaScript (Chrome)** öğesini seçmeniz gerekir.|
|yerel makinede bir C#, Visual Basic veya C++ uygulamasında hata ayıklama|Standart hata ayıklama (**F5**) veya **İşleme İliştir**|*\<appname>.exe*|Çoğu senaryoda standart hata ayıklama kullanın ve **Işleme iliştirilemiyor**.|
|Windows masaüstü uygulamasında uzaktan hata ayıklama|Uzak araçlar|Yok| bkz. [bir C# veya Visual Basic uygulamasında uzaktan hata ayıklama](../debugger/remote-debugging-csharp.md) veya [C++ uygulamasında uzaktan hata ayıklama](../debugger/remote-debugging-cpp.md)|
|Linux’ta .NET Core hatalarını ayıklama|**İşlemek Için İliştir** kullanın|*dotnet.exe* veya benzersiz bir işlem adı|SSH kullanmak için bkz. [SSH kullanarak Linux üzerinde çalışan uzaktan hata ayıklama .NET Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). Kapsayıcılı uygulamalar için bkz. [Docker kapsayıcısında çalışan bir Işleme iliştirme](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container).|
|Kapsayıcılı bir uygulamada hata ayıklama|**İşlemek Için İliştir** kullanın|*dotnet.exe* veya benzersiz bir işlem adı|Bkz. [Docker kapsayıcısında çalışan bir Işleme iliştirme](../debugger/attach-to-process-running-in-docker-container.md)|
|Linux üzerinde uzaktan hata ayıklama Python|**İşlemek Için İliştir** kullanın|*hata ayıklama GPY*|Bkz. [Python araçlarından uzaktan iliştirme](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|uygulamayı hata ayıklayıcı olmadan başlattıktan sonra yerel makinede ASP.NET bir uygulamada hata ayıklayın|**İşlemek Için İliştir** kullanın|*iiexpress.exe*|Bu, uygulamanızın profil oluşturma sırasında (örneğin) daha hızlı yüklenmesini sağlamak için yararlı olabilir. |
|Sunucu işlemindeki desteklenen diğer uygulama türlerinde hata ayıkla|Sunucu uzakta ise uzak Araçlar 'ı kullanın ve **Işleme ekleyin**|*chrome.exe*, *iexplore.exe* veya diğer süreçler|Gerekirse, işlemi tanımlamada yardımcı olması için Kaynak İzleyicisi kullanın. Bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).|
|evrensel Windows uygulamasının (UWP), OneCore, HoloLens veya ıot uygulamasının uzaktan hata ayıklaması|Yüklü uygulama paketinin hatalarını ayıkla|Yok|Bkz. **Işleme İliştir** kullanmak yerine [yüklü uygulama paketinin hatalarını ayıkla](debug-installed-app-package.md)|
|Windows bir Universal app (UWP), OneCore, HoloLens veya ıot uygulamasının hatalarını ayıklayın Visual Studio|Yüklü uygulama paketinin hatalarını ayıkla|Yok|Bkz. **Işleme İliştir** kullanmak yerine [yüklü uygulama paketinin hatalarını ayıkla](debug-installed-app-package.md)|

## <a name="use-debugger-features"></a>Hata ayıklayıcı özelliklerini kullanma

bir işleme eklenirken Visual Studio hata ayıklayıcının tüm özelliklerini (kesme noktaları gibi) kullanmak için, uygulamanın yerel kaynak ve sembollerle tam olarak eşleşmesi gerekir. Diğer bir deyişle, hata ayıklayıcı doğru [sembol (. pdb) dosyalarını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)yükleyebilmelidir. Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryolarında, Visual Studio ' de zaten açık olan kaynak kodu (veya kaynak kodun bir kopyası) olmalıdır. Uzak makinedeki derlenen uygulama ikilileri, yerel makineyle aynı derlemeden gelmelidir.

bazı yerel hata ayıklama senaryolarında, uygulamayla ilgili doğru sembol dosyaları varsa kaynak erişimi olmadan Visual Studio hata ayıklaması yapabilirsiniz. Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir. Daha fazla bilgi için bkz. [sembol ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> İliştirme hatalarını giderme

Bazı senaryolarda hata ayıklayıcı, hata ayıklamanın kod türünü doğru şekilde belirlemek için yardıma ihtiyaç duyuyor olabilir. Bağlantı değerleri doğru ayarlandıysa ( **kullanılabilir işlemler** listesinde doğru işlemi görüntüleyebilirsiniz), ancak hata ayıklayıcı Iliştirilemezse **bağlantı türü** listesinde en uygun bağlantı türünü seçmeyi deneyin, örneğin bir Linux veya Python uygulamasında hata ayıklaması yapıyorsanız, bu gerekli olabilir. Varsayılan bağlantı türünü kullanıyorsanız, bu bölümün ilerleyen kısımlarında açıklandığı gibi, bağlanmak üzere belirli bir kod türünü seçebilirsiniz.

Hata ayıklayıcı çalışan bir işleme iliştirayarlandığında, işlem bir veya daha fazla kod türü içerebilir. Hata ayıklayıcının iliştirebilecek kod türleri [kod türü seç](../debugger/select-code-type-dialog-box.md) iletişim kutusunda görüntülenir ve seçilir.

Bazen hata ayıklayıcı, bir kod türüne başarıyla eklenebilir, ancak başka bir kod türüne eklenemez. Genellikle bu durum şu durumlarda oluşur:

- Uzak bir bilgisayarda çalışan bir işleme iliştirmeye çalışırsınız. Uzak bilgisayarda, bazı kod türleri için yüklenmiş uzaktan hata ayıklama bileşenleri bulunabilir, ancak diğerleri için kullanılamaz.
- Doğrudan veritabanı hata ayıklaması için iki veya daha fazla işleme eklemeye çalışırsınız. SQL hata ayıklaması yalnızca tek bir işleme eklemeyi destekler.

Hata ayıklayıcı bazı kod türlerine iliştirilemiyor, ancak bunların tümüne değil, hangi türlerin iliştirileyemedi tanımlayan bir ileti görürsünüz.

Hata ayıklayıcı en az bir kod türüne başarıyla iliştirmesine devam ederseniz işlemde hata ayıklaması yapabilirsiniz. Yalnızca başarıyla eklenmiş kod türlerinde hata ayıkabileceksiniz. İşlemde eksiz kod yine de çalıştırılmaz, ancak kesme noktaları ayar devredilemez, veriler görüntüilemez veya bu kod üzerinde başka hata ayıklama işlemleri gerçekleştirilemez.

Hata ayıklayıcının bir kod türüne neden eklenemedikleri hakkında daha ayrıntılı bilgi almak için yalnızca bu kod türüne yeniden eklemeyi deneyin.

**Bir kod türünün neden eklenemedikleri hakkında belirli bilgiler almak için:**

1. İşlemden ayırma. Hata **Ayıkla menüsünde,** Tüm Öğeleri **Ayır'ı seçin.**

1. Yalnızca eklenemedi kod türünü seçerek işleme yeniden iliştirin.

    1. İşleme **Ekle iletişim** kutusunda, Kullanılabilir işlemler listesinde **işlemi** seçin.

    2. **Seç**’i seçin.

    3. Kod **Türü Seç iletişim kutusunda** Bu kod türlerinde **hata ayıkla'ya ve** eklenamayan kod türü'ne tıklayın. Diğer kod türlerinin seçimini kaldırın.

    4. **Tamam**’ı seçin.

    5. İşleme **Ekle iletişim kutusunda** Ekle'yi **seçin.**

    Bu kez, ekleme tamamen başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)
- [Tam Zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
