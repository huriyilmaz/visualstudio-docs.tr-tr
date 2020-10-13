---
title: Hata ayıklayıcı ile çalışan işlemlere iliştirme | Microsoft Docs
ms.custom: seodec18
ms.date: 06/12/2020
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
ms.openlocfilehash: 7decb23bb6d307732c1f675fb14a96c1fc0dcda1
ms.sourcegitcommit: 3e05bd4bfac6f0b8b3534d8c013388f67e288651
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91959867"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile çalıştırma işlemleri iliştirme

Visual Studio hata ayıklayıcısını, yerel veya uzak bir bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalıştıktan sonra, işleme Ekle **Hata Ayıkla**' yı seçin  >  **Attach to Process** veya **Ctrl** + **Alt** + Visual Studio 'da Ctrl alt**P** tuşlarına basın ve hata ayıklayıcıyı işleme eklemek için **İşleme İliştir** iletişim kutusunu kullanın.

Yerel veya uzak bilgisayarlarda çalışan uygulamalarda hata ayıklamak, aynı anda birden çok işlemi hata ayıklamak, Visual Studio 'da oluşturulmamış uygulamalarda hata ayıklamak veya Visual Studio 'da hata ayıklayıcı ekli olan herhangi bir uygulamada hata ayıklamak için **İliştir** ' i kullanabilirsiniz. Örneğin, hata ayıklayıcı olmadan bir uygulama çalıştırıyorsanız ve bir özel durumla karşılaşdıysanız, uygulamayı çalıştıran işleme hata ayıklayıcıyı iliştirebilir ve hata ayıklamaya başlayabilirsiniz.

> [!TIP]
> Hata ayıklama senaryonuz için **iliştirme** 'yi kullanıp kullanmayacağınızı bilmiyorsanız emin değil misiniz? Bkz. [yaygın hata ayıklama senaryoları](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Yerel makinenizde çalışan bir işleme iliştirme

Daha önce eklediğiniz bir işleme hızlıca yeniden iliştirmek için bkz. [bir işleme yeniden bağlama](#BKMK_reattach).

**Yerel bilgisayarınızdaki bir işleme eklemek için:**

1. Visual Studio 'da, işleme **Debug**Ekle  >  **Attach to Process** **Ctrl** + **Alt** + iletişim kutusunu açmak **Attach to Process** için işleme Ekle hata ayıkla (veya Ctrl alt**P**tuşlarına basın) seçeneğini belirleyin.

1. **Bağlantı türünü**denetleyin.

   Çoğu senaryoda **varsayılan**'ı kullanabilirsiniz. Bazı senaryolar, farklı bir bağlantı türü gerektirebilir. Daha fazla bilgi için, bu makaledeki diğer bölümlere veya [ortak hata ayıklama senaryolarına](#BKMK_Scenarios)bakın.

1. Yerel makine adınızla **bağlantı hedefini** ayarlayın.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

1. **Kullanılabilir işlemler** listesinde, eklemek istediğiniz işlem veya işlemleri bulun ve seçin.

   - Bir işlemi hızlıca seçmek için, **filtre işlemleri** kutusuna adını veya ilk harfini yazın.

   - İşlem adını bilmiyorsanız, listeye göz atın veya bazı yaygın işlem adları için [sık karşılaşılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın.

   >[!TIP]
   >İşlemler, **Işleme İliştir** iletişim kutusu açıkken arka planda başlayabilir ve durabilir, böylece çalışan işlemlerin listesi her zaman güncel olmayabilir. Geçerli listeyi görmek için istediğiniz zaman **Yenile** seçeneğini belirleyebilirsiniz.

1. **Ekle** alanına, hata ayıklamayı planladığınız kodun türünün listelendiğinden emin olun. Varsayılan **Otomatik** ayar, çoğu uygulama türü için geçerlidir.

   **Varsayılan** bağlantı türünü kullanıyorsanız, eklemek istediğiniz kod türünü el ile seçebilirsiniz. Aksi takdirde, **Select** seçeneği devre dışı bırakılabilir.

   Kod türlerini el ile seçmek için:
   1. **Seç**’e tıklayın.
   1. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinde hata ayıkla**' yı seçin.
      Listedeki bir işleme iliştirmeye çalıştığınızda bir hata yaşarsanız, sorunu [gidermeye](#BKMK_Troubleshoot_attach_errors) yardımcı olması Için [kod türünü seç](../debugger/select-code-type-dialog-box.md) iletişim kutusunu kullanabilirsiniz.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. **Tamam**’ı seçin.

1. **Ekle**' yi seçin.

>[!NOTE]
>Hata ayıklama için birden çok uygulamaya iliştirilebilecek, ancak aynı anda hata ayıklayıcıda yalnızca bir uygulama etkin olur. Etkin uygulamayı Visual Studio **hata ayıklama konumu** araç çubuğunda veya **süreçler** penceresinde ayarlayabilirsiniz.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Uzak bilgisayardaki bir işleme iliştirme

Ayrıca, **Işleme İliştir** iletişim kutusunda bir uzak bilgisayar seçebilir, bu bilgisayarda çalışan kullanılabilir işlemlerin listesini görüntüleyebilir ve hata ayıklama için bir veya daha fazla işleme ekleyebilirsiniz. Uzak bilgisayarda uzaktan hata ayıklayıcı (*msvsmon.exe*) çalışıyor olmalıdır. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).

IIS 'ye dağıtılan ASP.NET uygulamalarında hata ayıklama hakkında daha fazla yönerge için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md).

**Uzak bir bilgisayarda çalışan bir işleme eklemek için:**

1. Visual Studio 'da, işleme **Debug**Ekle  >  **Attach to Process** **Ctrl** + **Alt** + iletişim kutusunu açmak **Attach to Process** için işleme Ekle hata ayıkla (veya Ctrl alt**P**tuşlarına basın) seçeneğini belirleyin.

1. **Bağlantı türünü**denetleyin.

   Çoğu senaryoda **varsayılan**'ı kullanabilirsiniz. Linux veya kapsayıcılı bir uygulama için hata ayıklama gibi bazı senaryolar, farklı bir bağlantı türü gerektirir. Daha fazla bilgi için, bu makaledeki diğer bölümlere veya [ortak hata ayıklama senaryolarına](#BKMK_Scenarios)bakın.

1. **Bağlantı hedefi** kutusunda, aşağıdaki yöntemlerden birini kullanarak uzak bilgisayarı seçin:

   - **Bağlantı hedefi**' nin yanındaki açılan oku seçin ve açılan listeden bilgisayar adını seçin.
   - Bilgisayar adını **bağlantı hedefi** kutusuna yazın ve **ENTER**tuşuna basın.

     Visual Studio 'Nun gerekli bağlantı noktasını bilgisayar adına eklediğini doğrulayın ve şu biçimde görünür: ** \<remote computer name> :p ort**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız IP ve bağlantı noktası adresini (örneğin,) kullanmayı deneyin `123.45.678.9:4022` . 4024, Visual Studio 2019 x64 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](remote-debugger-port-assignments.md).

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız IP ve bağlantı noktası adresini (örneğin,) kullanmayı deneyin `123.45.678.9:4022` . 4022, Visual Studio 2017 x64 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzaktan hata ayıklayıcı bağlantı noktası atamaları için bkz. [Uzaktan hata ayıklayıcı bağlantı noktası atamaları](remote-debugger-port-assignments.md).

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
     >Güvenilmeyen bir kullanıcı hesabına ait bir işleme iliştirmeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görüntülenir. Daha fazla bilgi için bkz [. güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir Işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)eklemeyin.

5. **Ekle** alanına, hata ayıklamayı planladığınız kodun türünün listelendiğinden emin olun. Varsayılan **Otomatik** ayar, çoğu uygulama türü için geçerlidir.

   **Varsayılan** bağlantı türünü kullanıyorsanız, eklemek istediğiniz kod türünü el ile seçebilirsiniz. Aksi takdirde, **Select** seçeneği devre dışı bırakılabilir.

   Kod türlerini el ile seçmek için:
   1. **Seç**’e tıklayın.
   1. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinde hata ayıkla**' yı seçin.
      Listedeki bir işleme iliştirmeye çalıştığınızda bir hata yaşarsanız, sorunu [gidermeye](#BKMK_Troubleshoot_attach_errors) yardımcı olması Için [kod türünü seç](../debugger/select-code-type-dialog-box.md) iletişim kutusunu kullanabilirsiniz.
   1. **Tamam**’ı seçin.

6. **Ekle**' yi seçin.

>[!NOTE]
>Hata ayıklama için birden çok uygulamaya iliştirilebilecek, ancak aynı anda hata ayıklayıcıda yalnızca bir uygulama etkin olur. Etkin uygulamayı Visual Studio **hata ayıklama konumu** araç çubuğunda veya **süreçler** penceresinde ayarlayabilirsiniz.

Bazı durumlarda, Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıkladığınızda, **kullanılabilir süreçler** listesinde tüm kullanılabilir süreçler görüntülenmez. Visual Studio 'Yu sınırlı bir kullanıcı hesabına sahip olan bir kullanıcı olarak çalıştırıyorsanız, **kullanılabilir süreçler** listesinde, oturum 0 ' da çalışan süreçler gösterilmez. Oturum 0, *w3wp.exe*dahil olmak üzere Hizmetler ve diğer sunucu işlemlerinde kullanılır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Bir yönetici hesabı altında veya bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Terminal Hizmetleri oturumu yerine sunucu konsolundan çalıştırarak sorunu çözebilirsiniz.

Bu geçici çözümlerin hiçbiri mümkün değilse, üçüncü bir seçenek `vsjitdebugger.exe -p <ProcessId>` Windows komut satırından çalıştırılarak işleme eklemektir. *tlist.exe*kullanarak işlem kimliğini belirleyebilirsiniz. *tlist.exe*edinmek Için, Windows Için hata ayıklama araçları 'nı indirip yükleyin [ve ardından, WDK ve WinDbg indirmelerinde](/windows-hardware/drivers/download-the-wdk)kullanılabilir.

::: moniker range=">= vs-2019"

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH kullanarak Linux üzerinde çalışan bir .NET Core işlemine iliştirme

Daha fazla bilgi için bkz. [SSH kullanarak Linux üzerinde çalışan uzaktan hata ayıklama .NET Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Linux Docker kapsayıcısında çalışan bir işleme iliştirme

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

    **Kenarı. Bir Docker kapsayıcı işleminde uzaktan hata ayıklamak için:**

    > [!NOTE]
    > Bir Docker kapsayıcısında çalışan bir işleme uzaktan bağlanmak için iki seçenek vardır. SSH 'yi kullanmak için ilk seçenek, yerel makinenizde Docker Araçları yüklü değilse idealdir.  Yerel olarak Docker Araçları yüklüyse ve uzak istekleri kabul edecek şekilde yapılandırılmış bir Docker Daemon varsa, bir Docker Daemon kullanarak ikinci seçeneği deneyin.

    1. ***SSH aracılığıyla uzak makineye bağlanmak için:***
        1. Uzak bir sisteme bağlanmak için **Ekle...** öğesini seçin.<br/>
        ![Uzak bir sisteme bağlanma](../debugger/media/connect-remote-system.png "Uzak bir sisteme bağlanma")
        1. SSH veya Daemon 'e başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve **Tamam 'a**basın.

    1. ***Hedefi bir [Docker Daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla bir işlem çalıştıran uzak kapsayıcıya ayarlamak için***
        1. **Docker Konağı (Isteğe bağlı)** altında, Daemon ADRESINI (TCP, IP vb.) belirtin ve Yenile bağlantısına tıklayın.
        1. Daemon 'a başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve **Tamam 'a**basın.

4. **Kullanılabilir işlemler** listesinden karşılık gelen kapsayıcı işlemini seçin ve Visual Studio 'Da C# kapsayıcı işleminizi hata ayıklamaya başlamak için **İliştir** ' i seçin!

    ![Docker Iliştirme menüsü tamamlandı](../debugger/media/docker-attach-complete.png "Tamamlanmış Linux Docker Iliştirme menüsü")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a> Windows Docker kapsayıcısında çalışan bir işleme iliştirme

Visual Studio hata ayıklayıcısını, **Işleme Ekle** iletişim kutusunu kullanarak yerel makinenizde bir Windows Docker kapsayıcısında çalışan bir işleme ekleyebilirsiniz.

> [!IMPORTANT]
> Bu özelliği bir .NET Core işlemiyle birlikte kullanmak için .NET Core platformlar arası geliştirme iş yükünü yüklemeli ve kaynak koda yerel erişim sahibi olmanız gerekir.

**Bir Windows Docker kapsayıcısında çalışan bir işleme iliştirmek için:**

1. Visual Studio 'da, işleme **Ekle** iletişim kutusunu açmak Için **Hata Ayıkla > işleme Ekle** (veya **Ctrl + Alt + P**) öğesini seçin.

   ![Işleme Ekle menüsü](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. **Bağlantı türünü** **Docker (Windows container)** olarak ayarlayın.
3. **Docker kapsayıcısını Seç** iletişim kutusunu kullanarak **bağlantı hedefini** ayarlamak için **bul...** seçeneğini belirleyin.

    > [!IMPORTANT]
    > Hedef işlem, üzerinde çalıştığı Docker Windows kapsayıcısı ile aynı işlemci mimarisine sahip olmalıdır.

   Hedefin SSH aracılığıyla uzak bir kapsayıcıya ayarlanması şu anda kullanılamıyor ve yalnızca bir Docker Daemon kullanılarak yapılabilir.

    ***Hedefi bir [Docker Daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) aracılığıyla bir işlem çalıştıran uzak kapsayıcıya ayarlamak için***
    1. **Docker Konağı (Isteğe bağlı)** altında, Daemon ADRESINI (TCP, IP vb.) belirtin ve Yenile bağlantısına tıklayın.

    1. Daemon 'a başarıyla bağlandıktan sonra eklemek için çalışan bir kapsayıcı seçin ve Tamam ' ı seçin.

4. **Kullanılabilir işlemler** listesinden karşılık gelen kapsayıcı işlemini seçin ve C# kapsayıcı işleminizi hata ayıklamaya başlamak için **İliştir** ' i seçin.

    ![Docker Iliştirme menüsü tamamlandı](../debugger/media/docker-attach-complete-windows.png "Windows Docker Iliştirme menüsü tamamlandı")

5.  Kullanılabilir işlemler listesinden karşılık gelen kapsayıcı işlemini seçin ve C# kapsayıcı işleminizi hata ayıklamaya başlamak için **İliştir** ' i seçin.

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Bir işleme yeniden iliştir

Daha önce iliştirmiş olduğunuz işlemlere hızlı bir şekilde **yeniden iliştirebilirsiniz**  >  **Reattach to Process** **Shift** + **Alt** + **P**. Bu komutu seçtiğinizde, hata ayıklayıcı, ilk olarak önceki işlem KIMLIĞIYLE eşleştirmeye çalışırken ve başarısız olursa, önceki işlem adıyla eşleşen son işlemler için iliştirmeye çalışacaktır. Eşleşme bulunmazsa veya birkaç işlem aynı ada sahip ise, doğru işlemi seçebilmeniz **Için Işleme İliştir** iletişim kutusu açılır.

> [!NOTE]
> **İşleme yeniden iliştir** komutu, Visual Studio 2017 ' den başlayarak kullanılabilir.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Ortak hata ayıklama senaryoları

**Işleme eklemeyi** ve hangi işlemin iliştirileyeceğini belirlemenize yardımcı olmak için, aşağıdaki tabloda, mevcut yerlerde daha fazla yönergelerin bağlantılarıyla birlikte birkaç ortak hata ayıklama senaryosu gösterilmektedir. (Liste kapsamlı değildir.)

Evrensel Windows uygulaması (UWP) uygulamaları gibi bazı uygulama türlerinde doğrudan bir işlem adına iliştiremezsiniz, ancak Visual Studio 'da **yüklü uygulama paketini hata ayıkla** menü seçeneğini kullanın (bkz. tablo).

Hata ayıklayıcının C++ dilinde yazılmış koda eklemesi için kodun bir yayma yapması gerekir `DebuggableAttribute` . [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) bağlayıcı seçeneğiyle bağlantı kurarak bunu kodunuza otomatik olarak ekleyebilirsiniz.

İstemci tarafında komut dosyası hata ayıklaması için, tarayıcıda betik hata ayıklaması etkinleştirilmelidir. Chrome üzerinde istemci tarafı komut dosyasında hata ayıklamak için, kod türü olarak **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge-kmıum)** seçeneğini belirleyin ve uygulama türüne bağlı olarak, tüm Chrome örneklerini kapatmanız ve tarayıcıyı hata ayıklama modunda başlatmanız gerekebilir ( `chrome.exe --remote-debugging-port=9222` bir komut satırından yazın). Visual Studio 'nun önceki sürümlerinde Chrome için betik hata ayıklayıcısı **Web paketi**idi.

Eklemek üzere bir çalışan işlemi hızlı bir şekilde seçmek için, Visual Studio 'da **CTRL** + **alt** + **P**yazın ve ardından işlem adının ilk harfini yazın.

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|IIS sunucusunda uzaktan hata ayıklama ASP.NET 4 veya 4,5|Uzak araçları kullanma ve **Işleme iliştirme**|*w3wp.exe*|Bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS sunucusunda uzaktan hata ayıklama ASP.NET Core|Uzak araçları kullanma ve **Işleme iliştirme**|*w3wp.exe* veya *dotnet.exe*|.NET Core 3 ' te başlayarak, *w3wp.exe* işlemi varsayılan [uygulama içi barındırma modelinde](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models)kullanılır. Uygulama dağıtımı için bkz. [IIS 'de yayımlama](/aspnet/core/host-and-deploy/iis/). Daha ayrıntılı bilgi için bkz. uzaktan [hata ayıklama ASP.NET Core uzak bır IIS bilgisayarında](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach) .|
|Desteklenen uygulama türleri için yerel bir IIS sunucusunda istemci tarafı komut dosyasında hata ayıkla |**İşlemek Için İliştir** kullanın|*chrome.exe*, *MicrosoftEdgeCP.exe*veya *iexplore.exe*|Betik hata ayıklaması etkinleştirilmelidir. Chrome için Ayrıca, hata ayıklama modunda ( `chrome.exe --remote-debugging-port=9222` bir komut satırından tür) Chrome 'u çalıştırmanız ve **Iliştirme** alanında **JavaScript (Chrome)** öğesini seçmeniz gerekir.|
|Yerel makinede bir C#, Visual Basic veya C++ uygulamasında hata ayıklama|Standart hata ayıklama (**F5**) veya **İşleme İliştir**|*\<appname>]*|Çoğu senaryoda standart hata ayıklama kullanın ve **Işleme iliştirilemiyor**.|
|Windows masaüstü uygulamasında uzaktan hata ayıklama|Uzak araçlar|YOK| Bkz. [bir C# veya Visual Basic uygulamasında uzaktan hata ayıklama](../debugger/remote-debugging-csharp.md) veya [C++ uygulamasında uzaktan hata ayıklama](../debugger/remote-debugging-cpp.md)|
|Linux 'ta .NET Core hatalarını ayıklama|**İşlemek Için İliştir** kullanın|*dotnet.exe*|SSH kullanmak için bkz. [SSH kullanarak Linux üzerinde çalışan uzaktan hata ayıklama .NET Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md). Kapsayıcılı uygulamalar için, bu makaledeki önceki bölümlere bakın.|
|Linux üzerinde uzaktan hata ayıklama Python|**İşlemek Için İliştir** kullanın|*hata ayıklama GPY*|Bkz. [Python araçlarından uzaktan iliştirme](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Uygulamayı hata ayıklayıcı olmadan başlattıktan sonra yerel makinede bir ASP.NET uygulamasında hata ayıklayın|**İşlemek Için İliştir** kullanın|*iiexpress.exe*|Bu, uygulamanızın profil oluşturma sırasında (örneğin) daha hızlı yüklenmesini sağlamak için yararlı olabilir. |
|Sunucu işlemindeki desteklenen diğer uygulama türlerinde hata ayıkla|Sunucu uzakta ise uzak Araçlar 'ı kullanın ve **Işleme ekleyin**|*chrome.exe*, *iexplore.exe*veya diğer süreçler|Gerekirse, işlemi tanımlamada yardımcı olması için Kaynak İzleyicisi kullanın. Bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).|
|Evrensel Windows uygulaması (UWP), OneCore, HoloLens veya IoT uygulamasında uzaktan hata ayıklama|Yüklü uygulama paketinin hatalarını ayıkla|YOK|Bkz. **Işleme İliştir** kullanmak yerine [yüklü uygulama paketinin hatalarını ayıkla](debug-installed-app-package.md)|
|Visual Studio 'da başlatmadığınız bir Evrensel Windows uygulaması (UWP), OneCore, HoloLens veya IoT uygulamasında hata ayıklama|Yüklü uygulama paketinin hatalarını ayıkla|YOK|Bkz. **Işleme İliştir** kullanmak yerine [yüklü uygulama paketinin hatalarını ayıkla](debug-installed-app-package.md)|

## <a name="use-debugger-features"></a>Hata ayıklayıcı özelliklerini kullanma

Bir işleme eklenirken Visual Studio hata ayıklayıcının (kesme noktaları gibi) tam özelliklerini kullanmak için, uygulamanın yerel kaynak ve sembolleriyle tam olarak eşleşmesi gerekir. Diğer bir deyişle, hata ayıklayıcı doğru [sembol (. pdb) dosyalarını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)yükleyebilmelidir. Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryolarında, Visual Studio 'da zaten açık olan kaynak kodu (veya kaynak kodun bir kopyası) olmalıdır. Uzak makinedeki derlenen uygulama ikilileri, yerel makineyle aynı derlemeden gelmelidir.

Bazı yerel hata ayıklama senaryolarında, uygulamayla ilgili doğru sembol dosyaları varsa, Visual Studio 'da kaynağa erişim olmadan hata ayıklaması yapabilirsiniz. Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir. Daha fazla bilgi için bkz. [sembol ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> İliştirme hatalarını giderme

Bazı senaryolarda hata ayıklayıcı, hata ayıklamanın kod türünü doğru şekilde belirlemek için yardıma ihtiyaç duyuyor olabilir. Bağlantı değerleri doğru ayarlandıysa ( **kullanılabilir işlemler** listesinde doğru işlemi görüntüleyebilirsiniz), ancak hata ayıklayıcı Iliştirilemezse **bağlantı türü** listesinde en uygun bağlantı türünü seçmeyi deneyin, örneğin bir Linux veya Python uygulamasında hata ayıklaması yapıyorsanız, bu gerekli olabilir. Varsayılan bağlantı türünü kullanıyorsanız, bu bölümün ilerleyen kısımlarında açıklandığı gibi, bağlanmak üzere belirli bir kod türünü seçebilirsiniz.

Hata ayıklayıcı çalışan bir işleme iliştirayarlandığında, işlem bir veya daha fazla kod türü içerebilir. Hata ayıklayıcının iliştirebilecek kod türleri [kod türü seç](../debugger/select-code-type-dialog-box.md) iletişim kutusunda görüntülenir ve seçilir.

Bazen hata ayıklayıcı, bir kod türüne başarıyla eklenebilir, ancak başka bir kod türüne eklenemez. Genellikle bu durum şu durumlarda oluşur:

- Uzak bir bilgisayarda çalışan bir işleme iliştirmeye çalışırsınız. Uzak bilgisayarda, bazı kod türleri için yüklenmiş uzaktan hata ayıklama bileşenleri bulunabilir, ancak diğerleri için kullanılamaz.
- Doğrudan veritabanı hata ayıklaması için iki veya daha fazla işleme eklemeye çalışırsınız. SQL hata ayıklaması yalnızca tek bir işleme eklemeyi destekler.

Hata ayıklayıcı bazı kod türlerine iliştirilemiyor, ancak bunların tümüne değil, hangi türlerin iliştirileyemedi tanımlayan bir ileti görürsünüz.

Hata ayıklayıcı en az bir kod türüne başarıyla iliştirmesine devam ederseniz işlemde hata ayıklaması yapabilirsiniz. Yalnızca başarıyla eklenmiş kod türlerinde hata ayıklayabileceksiniz. İşlemdeki eklenmemiş kod çalışmaya devam eder, ancak kesme noktaları ayarlayabilir, verileri görüntüleyemez veya bu kodda başka hata ayıklama işlemleri gerçekleştiremezsiniz.

Hata ayıklayıcının neden bir kod türüne eklenemediğini öğrenmek için, yalnızca bu kod türüne yeniden iliştirmeyi deneyin.

**Bir kod türünün neden eklenemediğini öğrenmek için:**

1. İşlemden ayırın. **Hata Ayıkla** menüsünde **Tümünü Ayır**' ı seçin.

1. Yalnızca iliştirilemedi kod türünü seçerek işleme yeniden iliştirme.

    1. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinde işlemi seçin.

    2. **Seç**’i seçin.

    3. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinin** ve Iliştirilemedi kod türünün hatalarını ayıkla ' yı seçin. Diğer kod türlerinin seçimini kaldırın.

    4. **Tamam**’ı seçin.

    5. **Işleme İliştir** Iletişim kutusunda **Ekle**' yi seçin.

    Bu kez, iliştirme tamamen başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)
- [Tam zamanında hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
