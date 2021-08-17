---
title: Hata ayıklayıcısı ile çalıştırma işlemleri iliştirme
description: Yerel veya uzak bir Visual Studio çalışan bir işleme hata ayıklayıcının nasıl ekli olduğunu keşfedin.
ms.custom: SEO-VS-2020
ms.date: 06/28/2021
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
ms.openlocfilehash: cc725e1c3a92b4295c2f354cf7f7506773ada9d3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121844"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile çalıştırma işlemleri iliştirme

Yerel veya uzak Visual Studio çalışan bir işleme hata ayıklayıcısını iliştirebilirsiniz. İşlem çalıştırıldıktan sonra İşleme Ekle'yi seçin veya Visual Studio'de  >   **Ctrl** + **Alt** + **p**  tuşlarına basın ve hata ayıklayıcıyı işleme eklemek için İşleme Ekle iletişim kutusunu kullanın.

Yerel veya **uzak** bilgisayarlarda çalışan uygulamalarda hata ayıklamak, aynı anda birden çok işlemde hata ayıklamak, Visual Studio'de oluşturulmadı olan uygulamalarda hata ayıklamak veya hata ayıklayıcı eklenmiş olarak Visual Studio'den başlamadıysanız herhangi bir uygulamada hata ayıklamak için İşleme İliştir'i kullanabilirsiniz. Örneğin, hata ayıklayıcı olmadan bir uygulama çalıştırıyorsanız ve bir özel durumla karşılaşıyorsanız, hata ayıklayıcıyı uygulamayı çalıştıran işleme iliştirerek hata ayıklamaya başlayabilirsiniz.

> [!TIP]
> Hata ayıklama senaryonda İşleme **Ekle'nin** kullanılamayacak mı? Bkz. [Yaygın hata ayıklama senaryoları.](#BKMK_Scenarios)

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Yerel makineniz üzerinde çalışan bir işleme ekleme

Daha önce bağlı olduğunu bir işleme hızla yeniden iliştirk için [bkz. Bir işleme yeniden iliştirin.](#BKMK_reattach)

**Yerel bilgisayarınızda bir işleme eklemek için:**

1. Bu Visual Studio İşleme **Ekle 'yi**  >   seçin (veya **Ctrl** + **Alt** + **P** tuşlarına basarak)  İşleme Ekle iletişim kutusunu açın.

1. Bağlantı türünü **kontrol edin.**

   Çoğu senaryoda Varsayılan 'i **kullanabilirsiniz.** Bazı senaryolar için farklı bir bağlantı türü gerekli olabilir. Daha fazla bilgi için bu makaledeki diğer bölümlere veya [Yaygın hata ayıklama senaryolarına bakın.](#BKMK_Scenarios)

1. Bağlantı **hedefi'nin yerel** makinenizin adını ayarlayın.

   ![Bağlantı hedefi yerel makine adına ayarlanmış şekilde İşleme ekle iletişim kutusunun ekran görüntüsü.](../debugger/media/DBG_Basics_Attach_To_Process.png)

1. Kullanılabilir **işlemler listesinde,** eklemek istediğiniz işlemi veya işlemleri bulun ve seçin.

   - Bir işlemi hızlı bir şekilde seçmek için İşlemleri filtrele kutusuna **adını veya ilk harfini** yazın.

   - İşlem adını bilmiyorsanız listeye göz atabilir veya bazı yaygın işlem adları için yaygın hata ayıklama [senaryolarına](#BKMK_Scenarios) göz atabilirsiniz.

   >[!TIP]
   >İşleme Ekle iletişim kutusu açıkken  işlemler arka planda başlat ve durarken, çalışan işlemlerin listesi her zaman güncel olmayacaktır. Geçerli listeyi **görmek için** istediğiniz zaman Yenile'yi seçebilirsiniz.

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

IIS'ye dağıtılmış olan uygulama ASP.NET hata ayıklamaya ilişkin daha eksiksiz yönergeler için bkz. Uzak iis ASP.NET üzerinde uzaktan [hata ayıklama.](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)

**Uzak bir bilgisayarda çalışan bir işleme eklemek için:**

1. Bu Visual Studio İşleme **Ekle 'yi**  >   seçin (veya **Ctrl** + **Alt** + **P** tuşlarına basarak)  İşleme Ekle iletişim kutusunu açın.

1. Bağlantı türünü **kontrol edin.**

   Çoğu senaryoda Varsayılan 'i **kullanabilirsiniz.** Linux'da veya kapsayıcılı uygulamada hata ayıklama gibi bazı senaryolar farklı bir bağlantı türü gerektirir. Daha fazla bilgi için bu makaledeki diğer bölümlere veya [Yaygın hata ayıklama senaryolarına bakın.](#BKMK_Scenarios)

1. Bağlantı **hedefi kutusunda,** aşağıdaki yöntemlerden birini kullanarak uzak bilgisayarı seçin:

   - Bağlantı hedefi'nin yanındaki açılan **oku seçin** ve açılan listeden bilgisayar adını seçin.
   - Bağlantı hedefi kutusuna bilgisayar **adını yazın ve** Enter tuşuna **basın.**

     Gerekli Visual Studio bilgisayar adına eklendiğinden emin olun. Bu bağlantı noktası şu biçimde görünür: **\<remote computer name> :p ort**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini (örneğin, ) kullanmayı `123.45.678.9:4022` deneyin. 4024, Visual Studio 2019 x64 uzaktan hata ayıklayıcısı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için [bkz. Uzaktan hata ayıklayıcı bağlantı noktası atamaları.](remote-debugger-port-assignments.md)

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini (örneğin, ) kullanmayı `123.45.678.9:4022` deneyin. 4022, Visual Studio 2017 x64 uzaktan hata ayıklayıcısı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için [bkz. Uzaktan hata ayıklayıcı bağlantı noktası atamaları.](remote-debugger-port-assignments.md)

     ::: moniker-end

   - Bağlantı **hedefi kutusunun** yanındaki Bul **düğmesini seçerek** Uzak Bağlantılar **iletişim kutusunu** açın. Uzak **Bağlantılar** iletişim kutusu, yerel alt ağ veya doğrudan bilgisayarınıza bağlı tüm cihazları listeler. Uzak cihazları bulmak [için sunucuda UDP bağlantı noktası 3702'yi](../debugger/remote-debugger-port-assignments.md) açmanız gerekir. İstediğiniz bilgisayarı veya cihazı seçin ve seç'e **tıklayın.**

   > [!NOTE]
   > Hata **ayıklama oturumları** arasında Bağlantı türü ayarı devam eder. Bağlantı **hedefi ayarı,** yalnızca bu hedefle başarılı bir hata ayıklama bağlantısı oluştu ise hata ayıklama oturumları arasında devam eder.

3. Kullanılabilir **işlemler** listesini doldurmak için **Yenile'ye** tıklayın.

    >[!TIP]
    >İşleme Ekle iletişim kutusu açıkken  işlemler arka planda başlat ve durarken, çalışan işlemlerin listesi her zaman güncel olmayacaktır. Geçerli listeyi **görmek için** istediğiniz zaman Yenile'yi seçebilirsiniz.

4. Kullanılabilir **işlemler listesinde,** eklemek istediğiniz işlemi veya işlemleri bulun ve seçin.

   - Bir işlemi hızlı bir şekilde seçmek için İşlemleri filtrele kutusuna **adını veya ilk harfini** yazın.

   - İşlem adını bilmiyorsanız listeye göz atabilir veya bazı yaygın işlem adları için yaygın hata ayıklama [senaryolarına](#BKMK_Scenarios) göz atabilirsiniz.

   - Tüm kullanıcı hesapları altında çalışan işlemleri bulmak için Tüm **kullanıcılardan işlemleri göster onay** kutusunu seçin.

     >[!NOTE]
     >Güvenilmeyen bir kullanıcı hesabına ait bir işleme eklemeye çalışsanız, bir güvenlik uyarısı iletişim kutusu onayı görüntülenir. Daha fazla bilgi için bkz. Güvenlik Uyarısı: Güvenilmeyen bir kullanıcının sahip olduğu bir işleme [ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme iliştirin.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

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

Bazı durumlarda, Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata  ayıklasanız, Kullanılabilir işlemler listesi kullanılabilir tüm işlemleri görüntülemez. Bir hesabı Visual Studio kullanıcı olarak çalıştırıyorsanız, Kullanılabilir işlemler  listesi Oturum 0'da çalışan işlemleri göstermez. Oturum 0, hizmetler ve diğer sunucu işlemleri için kullanılır; örneğin, *w3wp.exe.* Bir yönetici hesabı altında veya Terminal Hizmetleri oturumu yerine sunucu konsolundan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştırarak sorunu çözebilirsiniz.

Bu geçici çözümlerin hiçbiri mümkünse, üçüncü bir seçenek de komut satırına komut satırı kullanarak `vsjitdebugger.exe -p <ProcessId>` Windows eklemektir. İşlem kimliğini belirlemek için *tlist.exe.* Daha fazla *tlist.exe,* WDK ve WinDbg indirmeleri üzerinden Windows için Hata Ayıklama [Araçları'Windows](/windows-hardware/drivers/download-the-wdk)indirin ve yükleyin.

## <a name="attach-to-a-net-core-process-running-on-azure-app-service-windows"></a>Azure App Service üzerinde çalışan bir .NET Core Windows ekleme

Azure App Service 'de (Windows) yayımlama yapıyorsanız, Barındırma altında **...** menüsünün altında Hata Ayıklayıcı ekle seçeneğini **bulabilirsiniz.**  Visual Studio uzaktan hata ayıklayıcıyı profilin yayım Azure App Service (Windows) örneğine eklemeye çalışır.

:::image type="content" source="../debugger/media/attach-debugger-publish-profile.png" alt-text="Yayımlama özeti sayfasının içindeki Hata Ayıklayıcı ekle seçeneğinin ekran görüntüsü.":::

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH kullanarak Linux üzerinde çalışan bir .NET Core sürecine ekleme

Daha fazla bilgi için [bkz. SSH kullanarak Linux](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)üzerinde çalışan uzaktan hata ayıklama .NET Core.

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Docker kapsayıcısı üzerinde çalışan bir işleme ekleme

2019'Visual Studio başlayarak, Visual Studio hata ayıklayıcısını Docker kapsayıcısı üzerinde çalışan bir işleme iliştirabilirsiniz. Linux .NET Core Docker kapsayıcısı için [bkz. Linux Docker kapsayıcısı üzerinde çalışan bir işleme ekleme.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container) Daha Windows Docker kapsayıcısı için [bkz. Docker kapsayıcısı üzerinde Windows işleme ekleme.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container)

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Bir işleme yeniden

Hata Ayıklama İşleme Yeniden İliştir ( Shift Alt P ) 'ı seçerek daha önce bağlı olduğunuz işlemlere hızla yeniden  >    +  + **iliştirin.** Bu komutu seçtiğiniz zaman, hata ayıklayıcı ilk olarak önceki işlem kimliğiyle eşleşmeyi deneyerek ve başarısız olursa, önceki işlem adıyla eşleştirerek, ekli son işlemlere hemen eklemeye dener. Eşleşme bulunamasa veya birden fazla işlem aynı adı  alıyorsa, doğru işlemi seçerek İşleme Ekle iletişim kutusu açılır.

> [!NOTE]
> İşleme **Yeniden Ekle komutu,** 2017'Visual Studio kullanılabilir.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Yaygın hata ayıklama senaryoları

İşleme Ekle'nin kullanıp kullanmaymayacaklarını ve hangi işleme ekleneceklerini belirlemenize yardımcı olmak için, aşağıdaki tabloda bazı yaygın hata ayıklama senaryoları ve varsa daha fazla yönergelerin bağlantıları yer almaktadır.  (Liste kapsamlı değildir.)

Evrensel Windows Uygulaması (UWP) uygulamaları gibi bazı uygulama türleri için doğrudan bir işlem adına eklemezsiniz, ancak bunun yerine Visual Studio'de Yüklü Uygulama PaketiNde Hata Ayıklama menü seçeneğini kullanırsınız (tabloya bakın). 

Hata ayıklayıcının C++ ile yazılmış koda eklemesi için kodun yayma ihtiyacı `DebuggableAttribute` vardır. [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) linker seçeneğiyle bağlantı kullanarak bunu kodunuza otomatik olarak ekebilirsiniz.

İstemci tarafı betik hata ayıklaması için tarayıcıda betik hata ayıklama etkinleştirilmelidir. Chrome'da istemci tarafı betiğinde hata ayıklamak için kod türü olarak **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge - Chromium)** seçin ve uygulama türünüze bağlı olarak tüm Chrome örneklerini kapatmanız ve tarayıcıyı hata ayıklama modunda başlatmanız (bir komut satırıyla yazın) gerekebilirsiniz. `chrome.exe --remote-debugging-port=9222` Visual Studio'nin önceki sürümlerinde Chrome için betik hata ayıklayıcısı **Web seti'dir.**

Hızla iliştirilen bir işlemi seçmek için, Visual Studio **Ctrl** Alt P yazın ve ardından işlem adının ilk +  + harfini yazın.

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|IIS sunucusunda ASP.NET 4 veya 4.5'te uzaktan hata ayıklama|Uzak araçları kullanma ve **İşleme Ekleme**|*w3wp.exe*|Bkz. [Uzak iis ASP.NET uzaktan hata ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS sunucusunda ASP.NET Core hata ayıklama|Uzak araçları kullanma ve **İşleme Ekleme**|*w3wp.exe* veya *dotnet.exe*|.NET Core 3'te *w3wp.exe* işlem varsayılan uygulama içinde barındırma modeli [için kullanılır.](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) Uygulama dağıtımı için bkz. [IIS'de yayımlama.](/aspnet/core/host-and-deploy/iis/) Daha ayrıntılı bilgi için [bkz. Uzak bir IIS ASP.NET Core uzaktan hata ayıklama ve hata ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Desteklenen uygulama türleri için yerel IIS sunucusunda istemci tarafı betiği hata ayıklama |İşleme **Ekle'nin kullanımı**|*chrome.exe*, *MicrosoftEdgeCP.exe* veya *iexplore.exe*|Betik hata ayıklama etkinleştirilmelidir. Chrome için Chrome'u hata ayıklama modunda da çalıştırmalı (komut satırına yazın) ve Ekle alanında `chrome.exe --remote-debugging-port=9222` **JavaScript (Chrome)** **seçeneğini de seçmeniz** gerekir.|
|Yerel makinede C#, Visual Basic veya C++ uygulamasında hata ayıklama|Standart hata ayıklama (**F5**) veya İşleme **Ekleme kullanma**|*\<appname>.exe*|Çoğu senaryoda, İşleme Ekle değil standart hata **ayıklama kullanın.**|
|Windows masaüstü uygulamasında uzaktan hata ayıklama|Uzak araçlar|Yok| Bkz. [C# veya Visual Basic](../debugger/remote-debugging-csharp.md) uzaktan hata ayıklama veya [C++](../debugger/remote-debugging-cpp.md) uygulamasında uzaktan hata ayıklama|
|Linux’ta .NET Core hatalarını ayıklama|İşleme **Ekle'nin kullanımı**|*dotnet.exe* işlem adı veya benzersiz bir işlem adı|SSH kullanmak için [bkz. SSH kullanarak Linux](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)üzerinde çalışan uzaktan hata ayıklama .NET Core. Kapsayıcılı uygulamalar için [bkz. Docker kapsayıcısı içinde çalışan bir işleme ekleme.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container)|
|Kapsayıcılı uygulamada hata ayıklama|İşleme **Ekle'nin kullanımı**|*dotnet.exe* işlem adı veya benzersiz bir işlem adı|Bkz. [Docker kapsayıcısı içinde çalışan işleme ekleme](../debugger/attach-to-process-running-in-docker-container.md)|
|Linux üzerinde Python'da uzaktan hata ayıklama|İşleme **Ekle'nin kullanımı**|*hata ayıklama*|Bkz. [Python Araçlarından uzaktan ekleme](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Hata ayıklayıcı ASP.NET sonra yerel makinede bir uygulamanın hata ayıklamasını ayıklama|İşleme **Ekle'nin kullanımı**|*iiexpress.exe*|Bu, profil oluşturma gibi (örneğin) uygulama yüklemenizi daha hızlı hale toplamaya yardımcı olabilir. |
|Sunucu işlemi üzerinde desteklenen diğer uygulama türlerinde hata ayıklama|Sunucu uzaksa, uzak araçları kullanın ve İşleme **Ekle'ye**|*chrome.exe*, *iexplore.exe* veya diğer işlemler|Gerekirse, işlemi Kaynak İzleyicisi yardımcı olmak için Kaynak İzleyicisi kullanın. Bkz. [Uzaktan hata ayıklama.](../debugger/remote-debugging.md)|
|Evrensel Windows Uygulaması (UWP), OneCore, HoloLens veya IoT uygulamasında uzaktan hata ayıklama|Yüklü uygulama paketinde hata ayıklama|Yok|Bkz. [İşleme Ekleme kullanmak yerine yüklü](debug-installed-app-package.md) bir uygulama **paketinde hata ayıklama**|
|Visual Studio'den başlamadıysanız Universal Windows App (UWP), OneCore, HoloLens veya IoT uygulamasında hata Visual Studio|Yüklü uygulama paketinde hata ayıklama|Yok|Bkz. [İşleme Ekleme kullanmak yerine yüklü](debug-installed-app-package.md) bir uygulama **paketinde hata ayıklama**|

## <a name="use-debugger-features"></a>Hata ayıklayıcı özelliklerini kullanma

Bir işleme ekleme sırasında Visual Studio hata ayıklayıcısının tüm özelliklerini kullanmak için uygulamanın yerel kaynağınız ve simgeleriniz ile tam olarak eşleşmesi gerekir. Diğer bir nedenle, hata ayıklayıcı doğru sembol [(.pdb) dosyalarını yükleyemedi.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryoları için kaynak kodun (veya kaynak kodun bir kopyasının) önceden açık olması Visual Studio. Uzak makinede derlenmiş uygulama ikilileri, yerel makineyle aynı derlemeden gelbelir.

Bazı yerel hata ayıklama senaryolarında, uygulamayla Visual Studio sembol dosyaları varsa, kaynak erişimine sahip değilken hata ayıklama sırasında hata ayıkabilirsiniz. Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir. Daha fazla bilgi için [bkz. Sembol ve kaynak dosyalarını belirtme.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Ekleme hatalarını giderme

Bazı senaryolarda, hata ayıklayıcının hata ayıklamak için kod türünü doğru şekilde tanımlamaya ihtiyacı olabilir. Bağlantı değerleri doğru ayarlanmışsa (Kullanılabilir işlemler listesinde doğru  işlemi görüntülebilirsiniz), ancak hata ayıklayıcı eklenemezse, Bağlantı türü  listesinden en uygun bağlantı türünü seçmeyi deneyin. Bu tür bir Linux veya Python uygulamasında hata ayıklarken gerekli olabilir. Varsayılan bağlantı türünü kullanıyorsanız, bu bölümün ilerleyen kısımlarında açıklandığı gibi, alternatif olarak bağlanmak istediğiniz kod türünü de kullanabilirsiniz.

Hata ayıklayıcı çalışan bir işleme ekli olduğunda, işlem bir veya daha fazla kod türü içerebilir. Hata ayıklayıcının eklenemiyor kod türleri Kod Türünü Seç [iletişim kutusunda görüntülenir ve](../debugger/select-code-type-dialog-box.md) seçilir.

Bazen, hata ayıklayıcı bir kod türüne başarıyla iliştirebilirsiniz, ancak başka bir kod türüne ekleyemez. Bu durum genellikle aşağıdakiler olduğunda gerçekleşir:

- Uzak bilgisayarda çalışan bir işleme eklemeye çalışıyorsanız. Uzak bilgisayarda bazı kod türleri için uzaktan hata ayıklama bileşenleri yüklü olabilir, ancak diğerleri için yüklenmez.
- Doğrudan veritabanı hata ayıklaması için iki veya daha fazla işleme eklemeye çalışabilirsiniz. SQL hata ayıklama yalnızca tek bir işleme iliştirme desteği sağlar.

Hata ayıklayıcısı kod türlerinin bazılarını (ancak hepsini değil) ekleyemediyse, hangi türlerin eklenemedi olduğunu belirten bir iletiyle karşılaşabilirsiniz.

Hata ayıklayıcı en az bir kod türüne başarıyla eklense, işlemde hata ayıklamaya geçebilirsiniz. Yalnızca başarıyla eklenmiş kod türlerinde hata ayıkabileceksiniz. İşlemde eksiz kod yine de çalıştırılmaz, ancak kesme noktaları ayar devredilemez, veriler görüntüilemez veya bu kod üzerinde başka hata ayıklama işlemleri gerçekleştirilemez.

Hata ayıklayıcının bir kod türüne neden eklenemedikleri hakkında daha ayrıntılı bilgi almak için yalnızca bu kod türüne yeniden eklemeyi deneyin.

**Bir kod türünün neden eklenemedikleri hakkında belirli bilgiler almak için:**

1. İşlemden ayırma. Hata **Ayıkla menüsünde,** Tüm Öğeleri **Ayır'ı seçin.**

1. Yalnızca eklenemedi kod türünü seçerek işleme yeniden iliştirin.

    1. İşleme **Ekle iletişim** kutusunda, Kullanılabilir işlemler listesinde **işlemi** seçin.

    2. **Seç**’i seçin.

    3. Kod **Türü Seç iletişim kutusunda** Bu kod türlerinde **hata ayıkla'ya ve** eklenamayan kod türü'ne tıklayın. Diğer kod türlerinin seçimini kaldırın.

    4. **Tamam**’ı seçin.

    5. İşleme Ekle **iletişim kutusunda** Ekle'yi **seçin.**

    Bu kez, ekleme tamamen başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)
- [Tam Zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
