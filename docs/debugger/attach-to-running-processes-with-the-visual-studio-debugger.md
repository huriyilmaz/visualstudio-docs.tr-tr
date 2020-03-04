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
ms.openlocfilehash: f2f00cde0c2ea3fad79c0f5ef75f3c33ad7afc22
ms.sourcegitcommit: c98e0ccf236765b44e47095ee52836cb012e3854
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78257195"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile çalıştırma işlemleri iliştirme
Visual Studio hata ayıklayıcı bir yerel veya uzak bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalıştıktan sonra, **işleme** eklemek > **Hata Ayıkla** ' yı seçin ya da Visual Studio 'da **CTRL**+**alt**+**P** tuşlarına basın ve hata ayıklayıcıyı işleme eklemek için **İşleme İliştir** iletişim kutusunu kullanın.

Yerel veya uzak bilgisayarlarda çalışan uygulamalarda hata ayıklamak, aynı anda birden çok işlemi hata ayıklamak, Visual Studio 'da oluşturulmamış uygulamalarda hata ayıklamak veya Visual Studio 'da hata ayıklayıcı ekli olan herhangi bir uygulamada hata ayıklamak için **İliştir** ' i kullanabilirsiniz. Örneğin, hata ayıklayıcı olmadan bir uygulama çalıştırıyorsanız ve özel durumu ise, sonra uygulama çalışan işlemi için hata ayıklayıcının ve hata ayıklama başlayın.

> [!TIP]
> Hata ayıklama senaryonuz için **iliştirme** 'yi kullanıp kullanmayacağınızı bilmiyorsanız emin değil misiniz? Bkz. [yaygın hata ayıklama senaryoları](#BKMK_Scenarios).

## <a name="BKMK_Attach_to_a_running_process"></a>Yerel makinenizde çalışan bir işleme iliştirme

Daha önce eklediğiniz bir işleme hızlıca yeniden iliştirmek için bkz. [bir işleme yeniden bağlama](#BKMK_reattach).

Uzak bilgisayardaki bir işlemde hata ayıklamak için bkz. [uzak bilgisayarda bir Işleme iliştirme](#BKMK_Attach_to_a_process_on_a_remote_computer).

::: moniker range=">= vs-2019"
Bir Linux Docker kapsayıcısında .NET Core işleminde hata ayıklamak için bkz. [bir Linux Docker kapsayıcısına iliştirme](#BKMK_Docker_Attach).
::: moniker-end

**Yerel bilgisayarınızdaki bir işleme eklemek için:**

1. Visual Studio **'da işleme ekle > ** **Hata Ayıkla** ' yı seçin (veya **CTRL**+**alt**+**P**) tuşlarına basarak **İşleme İliştir** iletişim kutusunu açın.

   **Bağlantı türü** **varsayılan**olarak ayarlanmalıdır. **Bağlantı hedefi** yerel makinenizin adı olmalıdır.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. **Kullanılabilir işlemler** listesinde, eklemek istediğiniz işlem veya işlemleri bulun ve seçin.

   - Bir işlemi hızlıca seçmek için, **filtre işlemleri** kutusuna adını veya ilk harfini yazın.

   - İşlem adını bilmiyorsanız, listeye göz atın veya bazı yaygın işlem adları için [sık karşılaşılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın.

   >[!TIP]
   >İşlemler, **Işleme İliştir** iletişim kutusu açıkken arka planda başlayabilir ve durabilir, böylece çalışan işlemlerin listesi her zaman güncel olmayabilir. Geçerli listeyi görmek için istediğiniz zaman **Yenile** seçeneğini belirleyebilirsiniz.

3. **Ekle** alanına, hata ayıklamayı planladığınız kodun türünün listelendiğinden emin olun. Varsayılan **Otomatik** ayar, çoğu uygulama türü için geçerlidir.

   Kod türleri el ile seçmek için:
   1. **Seç**'e tıklayın.
   1. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinde hata ayıkla**' yı seçin.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. **Tamam**’ı seçin.

4. **Ekle**' yi seçin.

>[!NOTE]
>Hata ayıklama için birden fazla uygulama için bağlı, ancak bir kerede yalnızca bir uygulama hata ayıklayıcıda etkin olur. Etkin uygulamayı Visual Studio **hata ayıklama konumu** araç çubuğunda veya **süreçler** penceresinde ayarlayabilirsiniz.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Uzak bilgisayardaki bir işleme iliştirme

Ayrıca, **Işleme İliştir** iletişim kutusunda bir uzak bilgisayar seçebilir, bu bilgisayarda çalışan kullanılabilir işlemlerin listesini görüntüleyebilir ve hata ayıklama için bir veya daha fazla işleme ekleyebilirsiniz. Uzak bilgisayarda uzaktan hata ayıklayıcı (*Msvsmon. exe*) çalışıyor olmalıdır. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

IIS 'ye dağıtılan ASP.NET uygulamalarında hata ayıklama hakkında daha fazla yönerge için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Uzak bir bilgisayarda çalışan bir işleme eklemek için:**

1. Visual Studio **'da işleme ekle > ** **Hata Ayıkla** ' yı seçin (veya **CTRL**+**alt**+**P**) tuşlarına basarak **İşleme İliştir** iletişim kutusunu açın.

2. Çoğu durumda **bağlantı türü** **varsayılan** olmalıdır. **Bağlantı hedefi** kutusunda, aşağıdaki yöntemlerden birini kullanarak uzak bilgisayarı seçin:

   - **Bağlantı hedefi**' nin yanındaki açılan oku seçin ve açılan listeden bilgisayar adını seçin.
   - Bilgisayar adını **bağlantı hedefi** kutusuna yazın ve **ENTER**tuşuna basın.

     Visual Studio 'Nun gerekli bağlantı noktasını, şu biçimde görünen bilgisayar adına eklediğinden emin olun: **\<uzak bilgisayar adı >:p ort**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini (örneğin, `123.45.678.9:4022`) kullanmayı deneyin. 4024, Visual Studio 2019 x64 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini (örneğin, `123.45.678.9:4022`) kullanmayı deneyin. 4022 x64 Visual Studio 2017 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](remote-debugger-port-assignments.md).

     ::: moniker-end

   - **Uzaktan bağlantılar** iletişim kutusunu açmak için **bağlantı hedefi** kutusunun yanındaki **bul** düğmesini seçin. **Uzak bağlantılar** iletişim kutusu, yerel alt ağınızdaki veya doğrudan bilgisayarınıza bağlı olan tüm cihazları listeler. Uzak cihazları bulmaya yönelik sunucuda [UDP bağlantı noktası 3702](../debugger/remote-debugger-port-assignments.md) ' i açmanız gerekebilir. İstediğiniz bilgisayarı veya cihazı seçin ve ardından **Seç**' e tıklayın.

   > [!NOTE]
   > **Bağlantı türü** ayarı hata ayıklama oturumları arasında devam ettirir. **Bağlantı hedefi** ayarı, yalnızca bu hedefle başarılı bir hata ayıklama bağlantısı oluştuysa hata ayıklama oturumları arasında devam ettirir.

3. **Kullanılabilir süreçler** listesini doldurmak için **Yenile** ' ye tıklayın.

    >[!TIP]
    >İşlemler, **Işleme İliştir** iletişim kutusu açıkken arka planda başlayabilir ve durabilir, böylece çalışan işlemlerin listesi her zaman güncel olmayabilir. Geçerli listeyi görmek için istediğiniz zaman **Yenile** seçeneğini belirleyebilirsiniz.

4. **Kullanılabilir işlemler** listesinde, eklemek istediğiniz işlem veya işlemleri bulun ve seçin.

   - Bir işlemi hızlıca seçmek için, **filtre işlemleri** kutusuna adını veya ilk harfini yazın.

   - İşlem adını bilmiyorsanız, listeye göz atın veya bazı yaygın işlem adları için [sık karşılaşılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın.

   - Tüm Kullanıcı hesapları altında çalışan süreçler bulmak için **tüm kullanıcılardan Işlem göster** onay kutusunu seçin.

     >[!NOTE]
     >Güvenilmeyen bir kullanıcı tarafından sahip olunan bir işlem eklemeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görünecektir. Daha fazla bilgi için bkz [. güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir Işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)eklemeyin.

5. **Ekle** alanına, hata ayıklamayı planladığınız kodun türünün listelendiğinden emin olun. Varsayılan **Otomatik** ayar, çoğu uygulama türü için geçerlidir.

   Kod türleri el ile seçmek için:
   1. **Seç**'e tıklayın.
   1. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinde hata ayıkla**' yı seçin.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. **Tamam**’ı seçin.

6. **Ekle**' yi seçin.

>[!NOTE]
>Hata ayıklama için birden fazla uygulama için bağlı, ancak bir kerede yalnızca bir uygulama hata ayıklayıcıda etkin olur. Etkin uygulamayı Visual Studio **hata ayıklama konumu** araç çubuğunda veya **süreçler** penceresinde ayarlayabilirsiniz.

Bazı durumlarda, Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıkladığınızda, **kullanılabilir süreçler** listesinde tüm kullanılabilir süreçler görüntülenmez. Visual Studio 'Yu sınırlı bir kullanıcı hesabına sahip olan bir kullanıcı olarak çalıştırıyorsanız, **kullanılabilir süreçler** listesinde, oturum 0 ' da çalışan süreçler gösterilmez. Oturum 0, *W3wp. exe*dahil olmak üzere Hizmetler ve diğer sunucu işlemlerinde kullanılır. Bir yönetici hesabı altında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştırarak veya bir Terminal Hizmetleri oturumu yerine sunucu konsolundan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çalıştırarak sorunu çözebilirsiniz.

Bu geçici çözümlerin hiçbiri mümkün değilse, üçüncü bir seçenek, Windows komut satırından `vsjitdebugger.exe -p <ProcessId>` çalıştırarak işleme iliştirmeye yönelik bir seçenektir. *Tlist. exe*' yi kullanarak işlem kimliğini belirleyebilirsiniz. *Tlist. exe*' yi edinmek Için, Windows Için hata ayıklama araçları 'nı indirip yükleyin [ve ardından, WDK ve WinDbg indirmelerinde](/windows-hardware/drivers/download-the-wdk)kullanılabilir.

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH kullanarak Linux üzerinde çalışan bir .NET Core işlemine iliştirme

Daha fazla bilgi için bkz. [SSH kullanarak Linux üzerinde çalışan uzaktan hata ayıklama .NET Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

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

## <a name="BKMK_reattach"></a>Bir işleme yeniden iliştir

**Hata ayıkla** > **işleme yeniden iliştir** ' i seçerek (**SHIFT**+**alt**+**P**), daha önce eklediğiniz işlemlere hızlıca yeniden iliştirebilirsiniz. Bu komutu seçtiğinizde, son ilk önceki işlem kimliğini deneyerek bağlı işlemler iliştirmek hata ayıklayıcı hemen deneyecek ve bu, önceki eşleştirerek başarısız olursa adı işleyin. Eşleşme bulunmazsa veya birkaç işlem aynı ada sahip ise, doğru işlemi seçebilmeniz **Için Işleme İliştir** iletişim kutusu açılır.

> [!NOTE]
> **İşleme yeniden iliştir** komutu, Visual Studio 2017 ' den başlayarak kullanılabilir.

## <a name="BKMK_Scenarios"></a>Ortak hata ayıklama senaryoları

**Işleme eklemeyi** ve hangi işlemin iliştirileyeceğini belirlemenize yardımcı olmak için, aşağıdaki tabloda, mevcut yerlerde daha fazla yönergelerin bağlantılarıyla birlikte birkaç ortak hata ayıklama senaryosu gösterilmektedir. (Bu liste kapsamlı değildir.)

Evrensel Windows uygulaması (UWP) uygulamaları gibi bazı uygulama türlerinde doğrudan bir işlem adına iliştiremezsiniz, ancak Visual Studio 'da **yüklü uygulama paketini hata ayıkla** menü seçeneğini kullanın (bkz. tablo).

Hata ayıklayıcının ' de C++yazılan koda eklemesi için, kodun `DebuggableAttribute`yayması gerekir. [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) bağlayıcı seçeneğiyle bağlantı kurarak bunu kodunuza otomatik olarak ekleyebilirsiniz.

İstemci tarafı betik hata ayıklama için betik hata ayıklamasını tarayıcıda etkinleştirilmelidir. Chrome üzerinde istemci tarafı betiklerinde hata ayıklamak için, kod türü olarak **Web seti** ' ni seçin ve uygulama türüne bağlı olarak, tüm Chrome örneklerini kapatmanız ve tarayıcıyı hata ayıklama modunda başlatmanız gerekebilir (bir komut satırından `chrome.exe --remote-debugging-port=9222` yazın).

Eklemek üzere bir çalışan işlemi hızlı bir şekilde seçmek için, Visual Studio 'da **Ctrl**+**alt**+**P**yazın ve ardından işlem adının ilk harfini yazın.

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|Uzaktan hata ayıklama ASP.NET 4 veya 4.5 üzerinde bir IIS sunucusu|Uzak araçları kullanma ve **Işleme iliştirme**|*W3wp.exe*|Bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Uzaktan hata ayıklamayı ASP.NET Core IIS sunucusu|Uzak araçları kullanma ve **Işleme iliştirme**|*DotNet. exe* veya *appname. exe*|Uygulama dağıtımı için bkz. [IIS 'de yayımlama](https://docs.asp.net/en/latest/publishing/iis.html). Hata ayıklama için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)|
|Desteklenen uygulama türleri için yerel bir IIS sunucusunda istemci tarafı betikte hata ayıklama |**İşlemek Için İliştir** kullanın|*Chrome. exe*, *microsoftedgecp. exe*veya *iexplore. exe*|Komut dosyası hata ayıklaması etkinleştirilmelidir. Chrome için Ayrıca, hata ayıklama modunda Chrome ' ı çalıştırmanız ve **iliştirme** alanında **WebKit Code** ' u seçmeniz gerekir.|
|Yerel makinede bir C#, Visual Basic veya C++ uygulamasında hata ayıklama|Standart hata ayıklama (**F5**) veya **İşleme İliştir**|*\<AppName >. exe*|Çoğu senaryoda standart hata ayıklama kullanın ve **Işleme iliştirilemiyor**.|
|Uzaktan hata ayıklama bir Windows masaüstü uygulaması|Uzak Araçlar|Yok| Bkz. [Uzaktan hata C# ayıklama a veya Visual Basic uygulaması](../debugger/remote-debugging-csharp.md) veya [bir C++ uygulamada uzaktan hata ayıklama](../debugger/remote-debugging-cpp.md)|
|Linux 'ta .NET Core hatalarını ayıklama|**İşlemek Için İliştir** kullanın|*DotNet. exe*|SSH kullanmak için bkz. [SSH kullanarak Linux üzerinde çalışan uzaktan hata ayıklama .NET Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). |
|Hata Ayıklayıcı olmadan uygulamayı başlattıktan sonra yerel makine üzerinde bir ASP.NET uygulamasında hata ayıklama|**İşlemek Için İliştir** kullanın|*ııexpress. exe*|Bu yük uygulamanızı hale getirmek yardımcı olabilecek daha hızlı gibi (örneğin) profili oluşturulurken. |
|Başka bir sunucu işlemi desteklenen uygulama türlerinde hata ayıklama|Sunucu uzakta ise uzak Araçlar 'ı kullanın ve **Işleme ekleyin**|*Chrome. exe*, *iexplore. exe*veya diğer süreçler|Gerekirse, Kaynak İzleyicisi işlemi belirlemenize yardımcı olması için kullanın. Bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).|
|Uzaktan hata ayıklama, bir evrensel Windows uygulamasında (UWP), OneCore, HoloLens ve IOT uygulaması|Yüklenen uygulama paketinin hatalarını ayıklama|Yok|Bkz. **Işleme İliştir** kullanmak yerine [yüklü uygulama paketinin hatalarını ayıkla](debug-installed-app-package.md)|
|Visual Studio'dan başlatmamış bir evrensel Windows uygulamasında (UWP), OneCore, HoloLens ve IOT uygulamasında hata ayıklama|Yüklenen uygulama paketinin hatalarını ayıklama|Yok|Bkz. **Işleme İliştir** kullanmak yerine [yüklü uygulama paketinin hatalarını ayıkla](debug-installed-app-package.md)|

## <a name="use-debugger-features"></a>Debugger özelliklerini kullanma

Visual Studio hata ayıklayıcı (kesme noktalarının isabet etmesi gibi) tam özelliklerini kullanmak için bir işleme iliştirirken uygulama tam olarak yerel kaynak ve simgeleri eşleşmelidir. Diğer bir deyişle, hata ayıklayıcı doğru [sembol (. pdb) dosyalarını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)yükleyebilmelidir. Varsayılan olarak, bu hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryoları için Visual Studio'da açık kaynak kodu (veya kaynak kodu bir kopyasını) sahip olmalıdır. Derlenmiş uygulama ikili dosyalarını uzak makinede gibi yerel makinede aynı derlemeden gelmelidir.

Uygulamayı doğru sembol dosyaları varsa bazı yerel hata ayıklama senaryolarında, Visual Studio'da kaynağına erişimi olmayan hata ayıklaması yapabilirsiniz. Varsayılan olarak, bu hata ayıklama derlemesi gerektirir. Daha fazla bilgi için bkz. [sembol ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a>İliştirme hatalarını giderme
 Çalışan bir işleme hata ayıklayıcı ekler, işlemi bir veya daha fazla kod türlerini içerebilir. Hata ayıklayıcının iliştirebilecek kod türleri **kod türü seç** iletişim kutusunda görüntülenir ve seçilir.

 Bazen, hata ayıklayıcı başarıyla bir kod türüne, ancak başka bir kod türüne ekleyebilirsiniz. Uzak bir bilgisayarda çalışan bir işlem eklemeye çalışıyorsanız, bu durum oluşabilir. Uzak bilgisayarda uzaktan hata ayıklama bileşenleri belirli kod türleri için kullanılabilir ancak diğerleri yüklü olabilir. Doğrudan veritabanı hata ayıklamaya iki veya daha fazla işlem eklemeye çalışırsanız da meydana gelebilir. SQL hata ayıklama için yalnızca tek bir işlem eklemeyi destekler.

 Hata ayıklayıcı, ancak bazı değil tüm kod türlerine eklenebiliyorsa, hangi türlerin eklenemediğini tanımlayan bir ileti görürsünüz.

 Hata ayıklayıcı en az bir kod türüne başarıyla ekleniyorsa işlemin hatalarını ayıklamaya devam edebilirsiniz. Sadece başarıyla eklenen kod türlerinde hata ayıklama mümkün olacaktır. İşlem eklenmemiş kodu hala çalışır, ancak kesme noktaları ayarlayın, veri görüntüleyemez veya kod hata ayıklama diğer işlemleri mümkün olmayacaktır.

 Hata ayıklayıcının bir kod türünü başarısız olma nedenine ilişkin daha ayrıntılı bilgi isterseniz, yalnızca bu kod türüne yeniden deneyin.

 **Bir kod türünün neden eklenemediğini öğrenmek için:**

1. İşlemden ayırın. **Hata Ayıkla** menüsünde **Tümünü Ayır**' ı seçin.

1. Eklenemeye kod türü seçerek işleme yeniden bağlayın.

    1. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinde işlemi seçin.

    2. **Seç**' i seçin.

    3. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinin** ve Iliştirilemedi kod türünün hatalarını ayıkla ' yı seçin. Diğer kod türleri seçimini kaldırın.

    4. **Tamam**’ı seçin.

    5. **Işleme İliştir** Iletişim kutusunda **Ekle**' yi seçin.

    Bu kez, iliştirme tümüyle başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)
- [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
