---
title: Hata ayıklayıcısı ile çalıştırma işlemleri iliştirme | Microsoft Docs
ms.custom: seodec18
ms.date: 04/08/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1a41667592b6965497f9b87514719f7d8a5a442
ms.sourcegitcommit: 10d16e18c5f5e482c4c2856e6cacaad283463b65
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75775953"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile çalıştırma işlemleri iliştirme
Visual Studio hata ayıklayıcı bir yerel veya uzak bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalışmaya başladıktan sonra seçin **hata ayıklama** > **iliştirme** veya basın **Ctrl**+**Alt** + **P** Visual Studio ve kullanım **iliştirme** işleme hata ayıklayıcı için iletişim kutusu.

Kullanabileceğiniz **iliştirme** yerel veya uzak bilgisayarlarda çalışan uygulamalarında hata ayıklamak için aynı anda birden çok işlemde hata ayıklamak, hata ayıklama Visual Studio'da oluşturulmamış uygulamaları veya Visual Studio'dan başlamadı herhangi bir uygulamayı hata ayıklama hata ayıklayıcısı ekli. Örneğin, hata ayıklayıcı olmadan bir uygulama çalıştırıyorsanız ve özel durumu ise, sonra uygulama çalışan işlemi için hata ayıklayıcının ve hata ayıklama başlayın.

> [!TIP]
> Emin değilim kullanıp kullanmayacağınızı **iliştirme** hata ayıklama senaryonuz için? Bkz: [yaygın hata ayıklama senaryoları](#BKMK_Scenarios).

## <a name="BKMK_Attach_to_a_running_process"></a> Yerel makinenizde çalışan bir işleme iliştirin

Hızlı bir şekilde bağlı için daha önce bir İliştir için bkz: [bir İliştir](#BKMK_reattach).

Uzak bilgisayarda bir işlemde hata ayıklamak için bkz: [uzak bilgisayardaki bir işleme iliştirin](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Bir Linux Docker kapsayıcısında .NET Core işleminde hata ayıklamak için bkz. [bir Linux Docker kapsayıcısına iliştirme](#BKMK_Docker_Attach).
::: moniker-end

**Yerel bilgisayarınızda bir işleme iliştirmek için:**

1. Visual Studio'da **hata ayıklama** > **iliştirme** (veya basın **Ctrl**+**Alt** + **P**) açmak için **iliştirme** iletişim kutusu.

   **Bağlantı türü** ayarlanmalıdır **varsayılan**. **Bağlantı hedefi** , yerel makine adı olmalıdır.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. İçinde **kullanılabilir işlemler** listesinde, bulmak ve işlem ya da eklemek istediğiniz işlemleri seçin.

   - Bir işlemi hızlı bir şekilde seçmek için adını veya ilk harfini yazın **filtreleme işlemleri** kutusu.

   - İşlem adını bilmiyorsanız, listede göz atın veya bakın [yaygın hata ayıklama senaryoları](#BKMK_Scenarios) için bazı ortak işlem adları.

   >[!TIP]
   >İşlemler başlatabilir ve durdurabilirsiniz arka planda **iliştirme** iletişim kutusu açıkken, böylece çalışan işlemlerin listesi her zaman geçerli olmayabilir. Seçebileceğiniz **Yenile** geçerli listesini görmek için herhangi bir zamanda.

3. İçinde **ekleme** alan, hata ayıklama planladığınız kodun türünü listelendiğinden emin olun. Varsayılan **otomatik** works çoğu uygulama türleri için ayarlama.

   Kod türleri el ile seçmek için:
   1. Tıklayın **seçin**.
   1. İçinde **kod türünü seç** Seç iletişim kutusunda **bu tür kodlarda hata ayıklama**.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. Seçin **Tamam**.

4. Seçin **ekleme**.

>[!NOTE]
>Hata ayıklama için birden fazla uygulama için bağlı, ancak bir kerede yalnızca bir uygulama hata ayıklayıcıda etkin olur. Visual Studio'da etkin uygulaması ayarlayabilirsiniz **hata ayıklama konumu** araç veya **işlemleri** penceresi.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Uzak bilgisayardaki bir işleme ekleme

Uzak bir bilgisayarda da seçebilirsiniz **iliştirme** iletişim kutusunda, bu bilgisayar üzerinde çalışan kullanılabilir süreçlerin listesini görüntüleyebilir ve bir veya daha fazla hata ayıklama için ekleyebilirsiniz. Uzaktan hata ayıklayıcı (*msvsmon.exe*) uzak bilgisayar üzerinde çalışıyor olması gerekir. Daha fazla bilgi için [uzaktan hata ayıklama](../debugger/remote-debugging.md).

IIS'ye dağıtılan ASP.NET uygulamalarında hata ayıklama için daha eksiksiz yönergeler için bkz: [uzak bir IIS bilgisayarında ASP.NET hata ayıklama uzak](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Uzak bir bilgisayarda çalışan bir işleme iliştirmek için:**

1. Visual Studio'da **hata ayıklama** > **iliştirme** (veya basın **Ctrl**+**Alt** + **P**) açmak için **iliştirme** iletişim kutusu.

2. **Bağlantı türü** olmalıdır **varsayılan** çoğu durum için. İçinde **bağlantı hedefi** kutusunda, aşağıdaki yöntemlerden birini kullanarak uzak bilgisayarı seçin:

   - Aşağı açılan oku seçin **bağlantı hedefi**, aşağı açılan listeden bilgisayar adını seçin.
   - Bilgisayar adını **bağlantı hedefi** kutusuna yazın ve **ENTER**tuşuna basın.

     Visual Studio 'Nun gerekli bağlantı noktasını, şu biçimde görünen bilgisayar adına eklediğinden emin olun: **\<uzak bilgisayar adı >:p ort**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsa, IP kullanmayı deneyin ve bağlantı noktası adresi (örneğin, `123.45.678.9:4022`). 4024, Visual Studio 2019 x64 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları konusuna bakın [uzaktan hata ayıklayıcı bağlantı noktası atamaları](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsa, IP kullanmayı deneyin ve bağlantı noktası adresi (örneğin, `123.45.678.9:4022`). 4022 x64 Visual Studio 2017 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları konusuna bakın [uzaktan hata ayıklayıcı bağlantı noktası atamaları](remote-debugger-port-assignments.md).

     ::: moniker-end

   - Seçin **Bul** düğmesinin yanındaki **bağlantı hedefi** açılacak kutusuna **uzak bağlantıları** iletişim kutusu. **Uzak bağlantıları** iletişim kutusu, yerel alt ağda veya bilgisayarınıza doğrudan bağlı tüm cihazları listeler. Gerekebilir [açın UDP bağlantı noktası 3702](../debugger/remote-debugger-port-assignments.md) uzak cihazları bulmak için sunucuda. Bilgisayarı veya cihazı ve ardından seçin **seçin**.

   > [!NOTE]
   > **Bağlantı türü** ayarı, hata ayıklama oturumları arasında devam ettirir. **Bağlantı hedefi** ayarı, başarılı bir hata ayıklama bağlantı hedefleyen ile oluşursa hata ayıklama oturumları arasında devam ettirir.

3. Tıklayın **Yenile** doldurmak için **kullanılabilir işlemler** listesi.

    >[!TIP]
    >İşlemler başlatabilir ve durdurabilirsiniz arka planda **iliştirme** iletişim kutusu açıkken, böylece çalışan işlemlerin listesi her zaman geçerli olmayabilir. Seçebileceğiniz **Yenile** geçerli listesini görmek için herhangi bir zamanda.

4. İçinde **kullanılabilir işlemler** listesinde, bulmak ve işlem ya da eklemek istediğiniz işlemleri seçin.

   - Bir işlemi hızlı bir şekilde seçmek için adını veya ilk harfini yazın **filtreleme işlemleri** kutusu.

   - İşlem adını bilmiyorsanız, listede göz atın veya bakın [yaygın hata ayıklama senaryoları](#BKMK_Scenarios) için bazı ortak işlem adları.

   - Tüm kullanıcı hesapları altında çalışan işlemleri bulmak için seçin **tüm kullanıcıların işlemlerini göster** onay kutusu.

     >[!NOTE]
     >Güvenilmeyen bir kullanıcı tarafından sahip olunan bir işlem eklemeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görünecektir. Daha fazla bilgi için bkz [. güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir Işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)eklemeyin.

5. İçinde **ekleme** alan, hata ayıklama planladığınız kodun türünü listelendiğinden emin olun. Varsayılan **otomatik** works çoğu uygulama türleri için ayarlama.

   Kod türleri el ile seçmek için:
   1. Tıklayın **seçin**.
   1. İçinde **kod türünü seç** Seç iletişim kutusunda **bu tür kodlarda hata ayıklama**.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. Seçin **Tamam**.

6. Seçin **ekleme**.

>[!NOTE]
>Hata ayıklama için birden fazla uygulama için bağlı, ancak bir kerede yalnızca bir uygulama hata ayıklayıcıda etkin olur. Visual Studio'da etkin uygulaması ayarlayabilirsiniz **hata ayıklama konumu** araç veya **işlemleri** penceresi.

Bazı durumlarda, bir Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıkladığınızda **kullanılabilir işlemler** listesi kullanılabilir tüm işlemleri olmaz. Visual Studio sınırlı bir kullanıcı hesabı olan bir kullanıcı çalıştırıyorsanız, **kullanılabilir işlemler** listelemek 0 oturumunda çalışan işlemler olmaz. 0 oturumu Hizmetleri ve dahil olmak üzere diğer sunucu işlemleri için kullanılan *w3wp.exe*. Çalıştırarak sorunu çözebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir yönetici hesabı altında ya da çalıştırarak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Terminal Hizmetleri oturumu yerine sunucu konsolundan.

Bu geçici çözümlerden biri Mümkünse, üçüncü seçenek olmasına çalıştırarak işleme iliştirmek `vsjitdebugger.exe -p <ProcessId>` Windows komut satırından. *Tlist. exe*' yi kullanarak işlem kimliğini belirleyebilirsiniz. Edinme *tlist.exe*indir ve hata ayıklama araçları için Windows, kullanılabilir yükleme [WDK ve WinDbg yüklemeleri](/windows-hardware/drivers/download-the-wdk).

::: moniker range=">= vs-2019"

## <a name="BKMK_Docker_Attach"></a>Linux Docker kapsayıcısında çalışan bir işleme iliştirme

Visual Studio hata ayıklayıcısını, **Işleme Ekle** iletişim kutusunu kullanarak yerel veya uzak makinenizde Linux .NET Core Docker kapsayıcısında çalışan bir işleme ekleyebilirsiniz.

> [!IMPORTANT]
> Bu özelliği kullanmak için .NET Core platformlar arası geliştirme iş yükünü yüklemeli ve kaynak koda yerel erişim sahibi olmanız gerekir.

**Linux Docker kapsayıcısında çalışan bir işleme iliştirmek için:**

1. Visual Studio 'da, işleme **Ekle** iletişim kutusunu açmak Için **Hata Ayıkla > Işleme Ekle (Ctrl + Alt + P)** öğesini seçin.

![Işleme Ekle menüsü](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. **Bağlantı türünü** **Docker (Linux kapsayıcısı)** olarak ayarlayın.
3. **Docker kapsayıcısını Seç** iletişim kutusunu kullanarak **bağlantı hedefini** ayarlamak için **bul...** seçeneğini belirleyin.

    Bir Docker kapsayıcı işleminde yerel olarak veya uzaktan hata ayıklaması yapabilirsiniz.
    
    **Bir Docker kapsayıcı işleminde yerel olarak hata ayıklamak için:**
    1. **Docker CLI ana bilgisayarını** **yerel makineye**ayarlayın.
    1. Listeden eklemek için çalışan bir kapsayıcı seçin ve **Tamam 'a**basın.
    
    ![Docker kapsayıcı menüsünü seçin](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. bir Docker kapsayıcı işleminde uzaktan hata ayıklamak Için:**
    
    > [!NOTE] 
    > Bir Docker kapsayıcısında çalışan bir işleme uzaktan bağlanmak için iki seçenek vardır. SSH 'yi kullanmak için ilk seçenek, yerel makinenizde Docker Araçları yüklü değilse idealdir.  Yerel olarak Docker Araçları yüklüyse ve uzak istekleri kabul edecek şekilde yapılandırılmış bir Docker Daemon varsa, bir Docker Daemon kullanarak ikinci seçeneği deneyin.

    1. ***SSH aracılığıyla uzak makineye bağlanmak için:***
        1. Uzak bir sisteme bağlanmak için **Ekle...** öğesini seçin.<br/>
        ![Uzak bir sisteme bağlanma](../debugger/media/connect-remote-system.png "Uzak bir sisteme bağlanma")
        1. SSH veya Daemon 'e başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve **Tamam 'a**basın.

    
    1. ***Hedefi bir [Docker Daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla bir işlem çalıştıran uzak kapsayıcıya ayarlamak için***
        1. **Docker Konağı (Isteğe bağlı)** altında, Daemon ADRESINI (TCP, IP vb.) belirtin ve Yenile bağlantısına tıklayın.
        1. Daemon 'a başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve **Tamam 'a**basın.

4. **Kullanılabilir işlemler** listesinden karşılık gelen kapsayıcı işlemini seçin ve Visual Studio 'da C# kapsayıcı işleminizi hata ayıklamaya başlamak için **İliştir** ' i seçin!

    ![Docker Iliştirme menüsü tamamlandı](../debugger/media/docker-attach-complete.png "Docker Iliştirme menüsü tamamlandı")


::: moniker-end

## <a name="BKMK_reattach"></a> Bir İliştir

Hızlı, daha önce seçerek eklendiği işlemlere iliştirebilirsiniz **hata ayıklama** > **İliştir** (**Shift** + **Alt**+**P**). Bu komutu seçtiğinizde, son ilk önceki işlem kimliğini deneyerek bağlı işlemler iliştirmek hata ayıklayıcı hemen deneyecek ve bu, önceki eşleştirerek başarısız olursa adı işleyin. Herhangi bir eşleşme bulunursa veya çeşitli işlemlerin aynı ada sahipse **iliştirme** doğru işlemi seçebilmeniz için iletişim kutusu açılır.

> [!NOTE]
> **İşleme yeniden iliştir** komutu, Visual Studio 2017 ' den başlayarak kullanılabilir.

## <a name="BKMK_Scenarios"></a> Hata ayıklama senaryoları

Kullanılıp kullanılmayacağını belirlemenize yardımcı olmak üzere **iliştirme** ve hangi işlemin, aşağıdaki tabloda, daha fazla bilgi için bağlantılarla birlikte bazı yaygın hata ayıklama senaryoları gösterilmektedir. mevcut olduğunda ekleme. (Bu liste kapsamlı değildir.)

Evrensel Windows uygulamasında (UWP) uygulamaları gibi bazı uygulama türleri için doğrudan bir işlem adı iliştirme ancak kullanın **yüklenen uygulama paketinin hatalarını ayıklama** menü seçeneğini Visual Studio'da yerine (tabloya bakın).

C++ programında yazılan koda eklenmesi hata ayıklayıcı için kod yayması gerekir `DebuggableAttribute`. Bu, kodunuzu otomatik olarak ile bağlayarak ekleyebileceğiniz [assemblydebug](/cpp/build/reference/assemblydebug-add-debuggableattribute) bağlayıcı seçeneği.

İstemci tarafı betik hata ayıklama için betik hata ayıklamasını tarayıcıda etkinleştirilmelidir. Chrome üzerinde istemci tarafı betiklerinde hata ayıklamak için, kod türü olarak **Web seti** ' ni seçin ve uygulama türüne bağlı olarak, tüm Chrome örneklerini kapatmanız ve tarayıcıyı hata ayıklama modunda başlatmanız gerekebilir (bir komut satırından `chrome.exe --remote-debugging-port=9222` yazın).

Hızlı bir şekilde çalışan bir işleme eklemek, Visual Studio'da seçmek için türü **Ctrl**+**Alt**+**P**, ilk harflerini yazın işlem adı.

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|Uzaktan hata ayıklama ASP.NET 4 veya 4.5 üzerinde bir IIS sunucusu|Uzak Araçlar'ı kullanın ve **iliştirme**|*W3wp.exe*|Bkz: [uzaktan uzak bir IIS bilgisayarında ASP.NET hata ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Uzaktan hata ayıklamayı ASP.NET Core IIS sunucusu|Uzak Araçlar'ı kullanın ve **iliştirme**|*dotnet.exe*|Uygulama dağıtımı için bkz: [IIS Yayımla](https://docs.asp.net/en/latest/publishing/iis.html). Hata ayıklama için bkz: [uzak bir IIS bilgisayarda uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Desteklenen uygulama türleri için yerel bir IIS sunucusunda istemci tarafı betikte hata ayıklama |Kullanım **işleme**|*Chrome.exe*, *MicrosoftEdgeCP.exe*, veya *iexplore.exe*|Komut dosyası hata ayıklaması etkinleştirilmelidir. Chrome için ayrıca Chrome seçin ve hata ayıklama modu çalıştırmalısınız **Webkit kod** içinde **ekleme** alan.|
|Yerel makinede bir C#, Visual Basic veya C++ uygulamasında hata ayıklama|Standart hata ayıklama (**F5**) veya **İşleme İliştir**|*\<Appname > .exe*|Çoğu senaryoda, standart hata ayıklama kullanın ve **iliştirme**.|
|Uzaktan hata ayıklama bir Windows masaüstü uygulaması|Uzak Araçlar|YOK| Bkz: [uzaktan hata ayıklama, C# veya Visual Basic uygulama](../debugger/remote-debugging-csharp.md) veya [uzaktan hata ayıklama, C++ uygulama](../debugger/remote-debugging-cpp.md)|
|Hata Ayıklayıcı olmadan uygulamayı başlattıktan sonra yerel makine üzerinde bir ASP.NET uygulamasında hata ayıklama|Kullanım **işleme**|*iiexpress.exe*|Bu yük uygulamanızı hale getirmek yardımcı olabilecek daha hızlı gibi (örneğin) profili oluşturulurken. |
|Başka bir sunucu işlemi desteklenen uygulama türlerinde hata ayıklama|Sunucu uzak ise, uzak Araçlar kullanın ve **iliştirme**|*Chrome.exe*, *iexplore.exe*, veya diğer işlemler|Gerekirse, Kaynak İzleyicisi işlemi belirlemenize yardımcı olması için kullanın. Bkz: [uzaktan hata ayıklama](../debugger/remote-debugging.md).|
|Uzaktan hata ayıklama, bir evrensel Windows uygulamasında (UWP), OneCore, HoloLens ve IOT uygulaması|Yüklenen uygulama paketinin hatalarını ayıklama|YOK|Bkz: [yüklü uygulama paketinin hatalarını ayıklama](debug-installed-app-package.md) kullanmak yerine **iliştirme**|
|Visual Studio'dan başlatmamış bir evrensel Windows uygulamasında (UWP), OneCore, HoloLens ve IOT uygulamasında hata ayıklama|Yüklenen uygulama paketinin hatalarını ayıklama|YOK|Bkz: [yüklü uygulama paketinin hatalarını ayıklama](debug-installed-app-package.md) kullanmak yerine **iliştirme**|

## <a name="use-debugger-features"></a>Debugger özelliklerini kullanma

Visual Studio hata ayıklayıcı (kesme noktalarının isabet etmesi gibi) tam özelliklerini kullanmak için bir işleme iliştirirken uygulama tam olarak yerel kaynak ve simgeleri eşleşmelidir. Diğer bir deyişle, hata ayıklayıcı doğru yüklemek gereken [sembol (.pdb) dosyaları](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md). Varsayılan olarak, bu hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryoları için Visual Studio'da açık kaynak kodu (veya kaynak kodu bir kopyasını) sahip olmalıdır. Derlenmiş uygulama ikili dosyalarını uzak makinede gibi yerel makinede aynı derlemeden gelmelidir.

Uygulamayı doğru sembol dosyaları varsa bazı yerel hata ayıklama senaryolarında, Visual Studio'da kaynağına erişimi olmayan hata ayıklaması yapabilirsiniz. Varsayılan olarak, bu hata ayıklama derlemesi gerektirir. Daha fazla bilgi için [sembol ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a> Sorun giderme hataları iliştirme
 Çalışan bir işleme hata ayıklayıcı ekler, işlemi bir veya daha fazla kod türlerini içerebilir. Hata ayıklayıcının iliştirebileceği kod türleri görüntülenir ve seçili **kod türünü seç** iletişim kutusu.

 Bazen, hata ayıklayıcı başarıyla bir kod türüne, ancak başka bir kod türüne ekleyebilirsiniz. Uzak bir bilgisayarda çalışan bir işlem eklemeye çalışıyorsanız, bu durum oluşabilir. Uzak bilgisayarda uzaktan hata ayıklama bileşenleri belirli kod türleri için kullanılabilir ancak diğerleri yüklü olabilir. Doğrudan veritabanı hata ayıklamaya iki veya daha fazla işlem eklemeye çalışırsanız da meydana gelebilir. SQL hata ayıklama için yalnızca tek bir işlem eklemeyi destekler.

 Hata ayıklayıcı, ancak bazı değil tüm kod türlerine eklenebiliyorsa, hangi türlerin eklenemediğini tanımlayan bir ileti görürsünüz.

 Hata ayıklayıcı en az bir kod türüne başarıyla ekleniyorsa işlemin hatalarını ayıklamaya devam edebilirsiniz. Sadece başarıyla eklenen kod türlerinde hata ayıklama mümkün olacaktır. İşlem eklenmemiş kodu hala çalışır, ancak kesme noktaları ayarlayın, veri görüntüleyemez veya kod hata ayıklama diğer işlemleri mümkün olmayacaktır.

 Hata ayıklayıcının bir kod türünü başarısız olma nedenine ilişkin daha ayrıntılı bilgi isterseniz, yalnızca bu kod türüne yeniden deneyin.

 **Neden bir kod türü eklemenin başarısız hakkında ayrıntılı bilgi edinmek için:**

1. İşlemden ayırın. Üzerinde **hata ayıklama** menüsünde **tümünü Ayır**.

1. Eklenemeye kod türü seçerek işleme yeniden bağlayın.

    1. İçinde **iliştirme** iletişim kutusunda, işlemi seçin **kullanılabilir işlemler** listesi.

    2. Seçin **seçin**.

    3. İçinde **kod türünü seç** Seç iletişim kutusunda **bu tür kodlarda hata ayıklama** ve eklenemeye kod türü. Diğer kod türleri seçimini kaldırın.

    4. Seçin **Tamam**.

    5. İçinde **iliştirme** iletişim kutusunda **iliştirme**.

    Bu kez, iliştirme tümüyle başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)
- [Just-In-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
