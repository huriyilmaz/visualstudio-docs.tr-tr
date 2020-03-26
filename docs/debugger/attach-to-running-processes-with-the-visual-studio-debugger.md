---
title: Hata ayıklama ile çalışan işlemlere ekleme | Microsoft Dokümanlar
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
ms.openlocfilehash: b5305be7615e426d7792d8dd3fefb2579e2ab6be
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233019"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile çalıştırma işlemleri iliştirme
Visual Studio hata ayıklayıcısını yerel veya uzak bir bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalışmaya devam ettikten **sonra,** > İşleme Hata**Ayıklama'yı** seçin veya Visual Studio'da **Ctrl**+**Alt**+**P** tuşuna basın ve hata ayıklayıcıyı işleme eklemek için **İşleme Ekle** iletişim kutusunu kullanın.

Yerel veya uzak bilgisayarlarda çalışan uygulamaları hata ayıklamak, aynı anda birden çok işlemi hata ayıklamak, Visual Studio'da oluşturulmamış uygulamaları hata ayıklamak veya Visual Studio'dan başlatmadığınız herhangi bir uygulamayı hata ayıklamak için **İşleme** Ekle'yi kullanabilirsiniz. Örneğin, hata ayıklama olmadan bir uygulama çalıştırıyorsanız ve bir özel durum isabet ediyorsanız, hata ayıklama işlemine uygulamayı çalıştıran ekleyebilir ve hata ayıklama başlar.

> [!TIP]
> Hata ayıklama senaryonuz için **İşleme Ekle'yi** kullanıp kullanmayacağınızkonusunda emin değil misiniz? [Bkz. Ortak hata ayıklama senaryoları.](#BKMK_Scenarios)

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a>Yerel makinenizde çalışan bir işleme ekleme

Daha önce iliştirdiğiniz bir işleme hızla yeniden eklemek [için](#BKMK_reattach)bkz.

Uzak bir bilgisayardaki bir işlemi hata ayıklamak [için, uzak bir bilgisayardaki bir işleme ekle'ye](#BKMK_Attach_to_a_process_on_a_remote_computer)bakın.

::: moniker range=">= vs-2019"
Bir Linux Docker kapsayıcısı üzerinde bir .NET Core işlemini hata ayıklamak [için](#BKMK_Linux_Docker_Attach)bkz.
::: moniker-end

**Yerel bilgisayarınızdaki bir işleme eklemek için:**

1. Visual Studio'da, **İşleme Ekle** iletişim kutusunu açmak için **İşleme Hata** > **Ayıklama'yı** (veya **Ctrl**+**Alt**+**P**tuşuna basın) seçin.

   **Bağlantı türü** **Varsayılan**olarak ayarlanmalıdır. **Bağlantı hedefi** yerel makine adınız olmalıdır.

   ![DBG_Basics_Attach_To_Process](../debugger/media/DBG_Basics_Attach_To_Process.png "DBG_Basics_Attach_To_Process")

2. Kullanılabilir **süreçler** listesinde, eklemek istediğiniz işlemi veya işlemleri bulun ve seçin.

   - Bir işlemi hızlı bir şekilde seçmek için Filtre **işlemleri** kutusuna adını veya ilk harfini yazın.

   - İşlem adını bilmiyorsanız, listeye göz atın veya bazı yaygın işlem adları için [sık kullanılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın.

   >[!TIP]
   >**İşleme Ekle** iletişim kutusu açıkken işlemler arka planda başlayıp durabilir, bu nedenle çalışan işlemler listesi her zaman geçerli olmayabilir. Geçerli listeyi görmek için istediğiniz zaman **Yenile'yi** seçebilirsiniz.

3. Alana **Ekle'de** hata ayıklamayı planladığınız kod türünün listelenmiş olduğundan emin olun. Varsayılan **Otomatik** ayar çoğu uygulama türü için çalışır.

   Kod türlerini el ile seçmek için:
   1. **Seç'i**tıklatın.
   1. Kod **Türü Seç** iletişim kutusunda, **hata ayıklama bu kod türlerini**seçin.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. **Tamam'ı**seçin.

4. **Ekle'yi**seçin.

>[!NOTE]
>Hata ayıklama için birden çok uygulamaya eklenebilir, ancak hata ayıklayıcıda aynı anda yalnızca bir uygulama etkindir. Etkin uygulamayı Visual Studio Hata **Ayıklama Konumu** araç çubuğunda veya **İşlemler** penceresinde ayarlayabilirsiniz.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Uzak bir bilgisayardaki bir işleme ekleme

Ayrıca, **İşleme Ekle** iletişim kutusunda uzak bir bilgisayar seçebilir, o bilgisayarda çalışan kullanılabilir işlemlerin listesini görüntüleyebilir ve hata ayıklama işlemlerinden birine veya birkaçına ekleyebilirsiniz. Uzaktan hata ayıklama (*msvsmon.exe*) uzak bilgisayarda çalışıyor olmalıdır. Daha fazla bilgi için [Uzaktan hata ayıklama](../debugger/remote-debugging.md)bölümüne bakın.

IIS'ye dağıtılan ASP.NET uygulamaları nın hata ayıklanmasına ilişkin daha eksiksiz talimatlar [için, uzak bir IIS bilgisayarında uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)bakın.

**Uzak bir bilgisayarda çalışan bir işleme eklemek için:**

1. Visual Studio'da, **İşleme Ekle** iletişim kutusunu açmak için **İşleme Hata** > **Ayıklama'yı** (veya **Ctrl**+**Alt**+**P**tuşuna basın) seçin.

2. **Bağlantı türü** çoğu durumda **Varsayılan** olmalıdır. Bağlantı **hedef** kutusunda, aşağıdaki yöntemlerden birini kullanarak uzak bilgisayarı seçin:

   - **Bağlantı hedefinin**yanındaki açılır ok'u seçin ve açılan listeden bilgisayar adını seçin.
   - **Bağlantı hedef** kutusuna bilgisayar adını yazın ve **Enter**tuşuna basın.

     Visual Studio'nun bilgisayar adına gerekli bağlantı noktasını eklediğine ve biçimde görünen: ** \<uzak bilgisayar adı>:port**

     ::: moniker range=">= vs-2019"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini `123.45.678.9:4022`kullanmayı deneyin (örneğin, ). 4024 Visual Studio 2019 x64 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzak hata ayıklama bağlantı noktası atamaları [için, Uzaktan hata ayıklama bağlantı noktası atamalarına](remote-debugger-port-assignments.md)bakın.

     ::: moniker-end
     ::: moniker range="vs-2017"

     > [!NOTE]
     > Uzak bilgisayar adını kullanarak bağlanamıyorsanız, IP ve bağlantı noktası adresini `123.45.678.9:4022`kullanmayı deneyin (örneğin, ). 4022 Visual Studio 2017 x64 uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır. Diğer uzak hata ayıklama bağlantı noktası atamaları [için, Uzaktan hata ayıklama bağlantı noktası atamalarına](remote-debugger-port-assignments.md)bakın.

     ::: moniker-end

   - **Uzak Bağlantılar** iletişim kutusunu açmak için **Bağlantı hedef** kutusunun yanındaki **Bul** düğmesini seçin. **Uzak Bağlantılar** iletişim kutusu, yerel alt ağınızdaki veya doğrudan bilgisayarınıza bağlı olan tüm aygıtları listeler. Uzak aygıtları keşfetmek için sunucuda [UDP bağlantı noktası 3702'yi açmanız](../debugger/remote-debugger-port-assignments.md) gerekebilir. İstediğiniz bilgisayarı veya aygıtı seçin ve sonra **Seç'i**tıklatın.

   > [!NOTE]
   > **Bağlantı türü** ayarı hata ayıklama oturumları arasında devam eder. **Bağlantı hedef** ayarı, hata ayıklama oturumları arasında yalnızca bu hedefle başarılı bir hata ayıklama bağlantısı oluştuysa devam eder.

3. **Kullanılabilir süreçler** listesini doldurmak için **Yenile'yi** tıklatın.

    >[!TIP]
    >**İşleme Ekle** iletişim kutusu açıkken işlemler arka planda başlayıp durabilir, bu nedenle çalışan işlemler listesi her zaman geçerli olmayabilir. Geçerli listeyi görmek için istediğiniz zaman **Yenile'yi** seçebilirsiniz.

4. Kullanılabilir **süreçler** listesinde, eklemek istediğiniz işlemi veya işlemleri bulun ve seçin.

   - Bir işlemi hızlı bir şekilde seçmek için Filtre **işlemleri** kutusuna adını veya ilk harfini yazın.

   - İşlem adını bilmiyorsanız, listeye göz atın veya bazı yaygın işlem adları için [sık kullanılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın.

   - Tüm kullanıcı hesapları altında çalışan işlemleri bulmak için, tüm kullanıcı onay **kutusundan İşlemleri Göster'i** seçin.

     >[!NOTE]
     >Güvenilmeyen bir kullanıcı hesabına ait bir işleme iliştirmeye çalışırsanız, bir güvenlik uyarı iletişim kutusu onayı görüntülenir. Daha fazla bilgi için güvenlik [uyarısı: Güvenilmeyen bir kullanıcıya ait bir işleme bağlanmak tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme eklemeyin.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user.md)

5. Alana **Ekle'de** hata ayıklamayı planladığınız kod türünün listelenmiş olduğundan emin olun. Varsayılan **Otomatik** ayar çoğu uygulama türü için çalışır.

   Kod türlerini el ile seçmek için:
   1. **Seç'i**tıklatın.
   1. Kod **Türü Seç** iletişim kutusunda, **hata ayıklama bu kod türlerini**seçin.
   1. Hata ayıklamak istediğiniz kod türlerini seçin.
   1. **Tamam'ı**seçin.

6. **Ekle'yi**seçin.

>[!NOTE]
>Hata ayıklama için birden çok uygulamaya eklenebilir, ancak hata ayıklayıcıda aynı anda yalnızca bir uygulama etkindir. Etkin uygulamayı Visual Studio Hata **Ayıklama Konumu** araç çubuğunda veya **İşlemler** penceresinde ayarlayabilirsiniz.

Bazı durumlarda, Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıklama yaptığınızda, **Kullanılabilir işlemler** listesi kullanılabilir tüm işlemleri görüntülemez. Visual Studio'yu sınırlı bir kullanıcı hesabı olan bir kullanıcı olarak çalıştırıyorsanız, **Kullanılabilir süreçler** listesi Oturum 0'da çalışan işlemleri göstermez. Oturum 0 hizmetler ve *w3wp.exe*dahil olmak üzere diğer sunucu işlemleri için kullanılır. Sorunu bir yönetici hesabı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] altında çalıştırarak veya [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Terminal Hizmetleri oturumu yerine sunucu konsolundan çalıştırarak çözebilirsiniz.

Bu geçici çözümlerden hiçbiri mümkün değilse, üçüncü bir seçenek Windows `vsjitdebugger.exe -p <ProcessId>` komut satırından çalıştırarak işleme eklemektir. İşlem kimliğini *tlist.exe'yi*kullanarak belirleyebilirsiniz. *tlist.exe*almak için, [wdk ve WinDbg indirme](/windows-hardware/drivers/download-the-wdk)mevcuttur Windows için Hata Ayıklama Araçları indirin ve yükleyin.

::: moniker range=">= vs-2019"


## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH kullanarak Linux üzerinde çalışan bir .NET Core işlemine ekleme

Daha fazla bilgi için Bkz. [SSH kullanarak Linux'ta çalışan Uzaktan hata ayıklama .NET Core.](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a>Linux Docker kapsayıcısı üzerinde çalışan bir işleme ekleme

Visual Studio hata ayıklayıcısını, **İşleme Ekle** iletişim kutusunu kullanarak yerel veya uzak makinenizde linux .NET Core Docker kapsayıcısında çalışan bir işleme ekleyebilirsiniz.

> [!IMPORTANT]
> Bu özelliği kullanmak için .NET Çekirdek Çapraz Platform Geliştirme iş yükünü yüklemeniz ve kaynak koduna yerel erişime sahip olmalısınız.

**Linux Docker kapsayıcısında çalışan bir işleme eklemek için:**

1. Visual Studio'da, **İşleme Ekle** iletişim kutusunu açmak **için Hata Ayıklama > İşleme Ekle (CTRL+ALT+P)** seçeneğini belirleyin.

![İşlem Menüsüne Ekle](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Bağlantı **türünü** **Docker (Linux Container)** olarak ayarlayın.
3. **Bağlantı hedefini,** **Docker Konteyneri Seç** iletişim kutusu aracılığıyla ayarlamak için **Bul...** seçeneğini belirleyin.

    Docker kapsayıcı işlemini yerel veya uzaktan hata ayıklayabilirsiniz.
    
    **Docker kapsayıcı işlemini yerel olarak hata ayıklamak için:**
    1. **Docker CLI ana bilgisayarı** **Yerel Makine'ye**ayarlayın.
    1. Listeden eklemek için çalışan bir kapsayıcı seçin ve **Tamam'a**vurun.
    
    ![Docker Konteyner Menüsü'nü seçin](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")
 
    **B. Docker konteyner işlemini uzaktan hata ayıklamak için:**
    
    > [!NOTE] 
    > Docker kapsayıcısında çalışan bir işleme uzaktan bağlanmak için iki seçenek vardır. SSH'yi kullanmak için ilk seçenek, yerel makinenizde Docker araçları yüklü değilse idealdir.  Docker araçları yerel olarak yüklüyse ve uzaktan istekleri kabul etmek üzere yapılandırılan bir Docker daemon'una sahipseniz, docker daemon kullanarak ikinci seçeneği deneyin.

    1. ***SSH üzerinden uzak bir makineye bağlanmak için:***
        1. Uzak bir sisteme bağlanmak için **Ekle...** seçeneğini belirleyin.<br/>
        ![Uzaktan Sisteme Bağlanma](../debugger/media/connect-remote-system.png "Uzaktan Sisteme Bağlanma")
        1. SSH veya daemon'a başarıyla bağlandıktan sonra takmak için çalışan bir kapsayıcı seçin ve **Tamam tuşuna**basın.

    
    1. ***Hedefi [Docker daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) üzerinden işlem yürüten uzak bir kapsayıcıya ayarlamak için***
        1. **Docker ana bilgisayarı (İsteğe bağlı)** altındaki daemon adresini (örneğin TCP, IP, vb. yoluyla) belirtin ve yenileme bağlantısını tıklayın.
        1. Daemon'a başarıyla bağlandıktan sonra takacak çalışan bir kapsayıcı seçin ve **Tamam'a**çarptı.

4. **Kullanılabilir süreçler** listesinden ilgili kapsayıcı işlemini seçin ve Visual Studio'da C# konteyner işleminizin hata ayıklamaya başlamak için **Ekle'yi** seçin!

    ![Tamamlanmış Docker Ekle Menüsü](../debugger/media/docker-attach-complete.png "Tamamlanmış Linux Docker Ekle Menüsü")
    

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a><a name="BKMK_Windows_Docker_Attach"></a>Windows Docker kapsayıcısı üzerinde çalışan bir işleme ekleme

**İşleme Ekle** iletişim kutusunu kullanarak Visual Studio hata ayıklama işlemini yerel makinenizdeki Windows Docker kapsayıcısında çalışan bir işleme ekleyebilirsiniz.

> [!IMPORTANT]
> Bu özelliği .NET Core işlemiyle kullanmak için .NET Çekirdek Çapraz Platform Geliştirme iş yükünü yüklemeniz ve kaynak koduna yerel erişime sahip olmalısınız.

**Windows Docker kapsayıcısında çalışan bir işleme eklemek için:**

1. Visual Studio'da, İşleme Ekle iletişim kutusunu açmak **için Hata Ayıklama > İşleme (veya** **CTRL+ALT+P)** **ekle'yi** seçin.

   ![İşlem Menüsüne Ekle](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Bağlantı **türünü** **Docker (Windows Kapsayıcısı)** olarak ayarlayın.
3. **Docker Konteyneri Seç** iletişim kutusunu kullanarak **Bağlantı hedefini** ayarlamak için **Bul...** seçeneğini belirleyin.

    > [!IMPORTANT]
    > Hedef işlem, üzerinde çalıştığı Docker Windows kapsayıcısı ile aynı işlemci mimarisine sahip olmalıdır.
    
   Hedefi SSH üzerinden uzak bir kapsayıcıya ayarlamak şu anda kullanılamıyor ve yalnızca Docker daemon kullanılarak yapılabilir.
    
    ***Hedefi [Docker daemon](https://docs.docker.com/engine/reference/commandline/dockerd/) üzerinden işlem yürüten uzak bir kapsayıcıya ayarlamak için***
    1. **Docker ana bilgisayarı (İsteğe bağlı)** altındaki daemon adresini (örneğin TCP, IP, vb. yoluyla) belirtin ve yenileme bağlantısını tıklayın. 

    1. Daemon'a başarıyla bağlandıktan sonra takmak için çalışan bir kapsayıcı seçin ve Tamam'ı seçin.
    
4. **Kullanılabilir işlemler** listesinden ilgili kapsayıcı işlemini seçin ve C# konteyner işleminizin hata ayıklamaya başlamak için **Ekle'yi** seçin.

    ![Tamamlanmış Docker Ekle Menüsü](../debugger/media/docker-attach-complete-windows.png "Tamamlanmış Windows Docker Ekle Menüsü")
    

5.  Kullanılabilir işlemler listesinden ilgili kapsayıcı işlemini seçin ve C# konteyner işleminizin hata ayıklamaya başlamak için **Ekle'yi** seçin.


::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a>İşleme yeniden iliştirme

**Hata Ayıklama** > **Reattach to Process** **(Shift**+**Alt**+**P)** seçeneğini seçerek daha önce bağlı olduğunuz işlemlere hızla yeniden ekleyebilirsiniz. Bu komutu seçtiğinizde, hata ayıklama işlemi, önceki işlem kimliğini eşleştirmeye çalışırken ve bu başarısız olursa, önceki işlem adı ile eşleştirerek bağlı olduğunuz son işlemlere hemen eklemeyi dener. Eşler bulunmazsa veya birden çok işlem aynı ada sahipse, doğru işlemi seçebilmeniz **için İşleme Ekle** iletişim kutusu açılır.

> [!NOTE]
> **Reattach to Process** komutu Visual Studio 2017'den itibaren kullanılabilir.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a>Sık kullanılan hata ayıklama senaryoları

**İşleme Ekle'yi** kullanıp kullanmayacağını ve hangi işleme eklenmeyeceğini belirlemenize yardımcı olmak için, aşağıdaki tabloda kullanılabilir durumda daha fazla yönergeye bağlantılar içeren birkaç yaygın hata ayıklama senaryosu gösterilmektedir. (Liste ayrıntılı değildir.)

Evrensel Windows Uygulaması (UWP) uygulamaları gibi bazı uygulama türleri için doğrudan bir işlem adına iliştirmezsiniz, ancak Bunun yerine Visual Studio'da **Hata Ayıklama Yüklü Uygulama Paketi** menüsü seçeneğini kullanabilirsiniz (tabloya bakın).

Hata ayıklayıcının C++'da yazılmış koda eklemesi için `DebuggableAttribute`kodun . [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) bağlantı seçeneğine bağlanarak bunu kodunuza otomatik olarak ekleyebilirsiniz.

İstemci tarafı komut dosyası hata ayıklama için tarayıcıda komut dosyası hata ayıklama etkinolmalıdır. Chrome'da istemci tarafındaki komut dosyasının hata ayıklama için kod türü olarak **Web kitini** seçin ve uygulama türünüze bağlı olarak, tüm Chrome `chrome.exe --remote-debugging-port=9222` örneklerini kapatmanız ve tarayıcıyı hata ayıklama modunda başlatmanız gerekebilir (komut satırından yazın).

Visual Studio'da eklenecek bir çalıştırma işlemini hızlı bir şekilde seçmek için **Ctrl**+**Alt**+**P**yazın ve ardından işlem adının ilk harfini yazın.

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|IIS sunucusunda 4 veya 4,5 ASP.NET uzaktan hata ayıklama|Uzak araçları kullanın ve **İşleme Ekle**|*w3wp.exe*|[Uzak bir IIS bilgisayarında uzaktan hata ayıklama ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) bakın|
|IIS sunucusunda Core ASP.NET uzaktan hata ayıklama|Uzak araçları kullanın ve **İşleme Ekle**|*dotnet.exe* veya *appname.exe*|Uygulama dağıtımı için [bkz.](https://docs.asp.net/en/latest/publishing/iis.html) Hata ayıklama için, [uzak bir IIS bilgisayarında Uzaktan hata ayıklama ASP.NET Core](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md) bölümüne bakın|
|Desteklenen uygulama türleri için yerel bir IIS sunucusunda istemci tarafındaki komut dosyası hata ayıklama |**İşleme Ekle'yi** Kullan|*chrome.exe*, *MicrosoftEdgeCP.exe*, veya *iexplore.exe*|Komut dosyası hata ayıklama etkin olmalıdır. Chrome için, Chrome'u hata ayıklama modunda çalıştırmanız ve alana **Ekle'de** **Webkit kodunu** seçmeniz gerekir.|
|Yerel makinede C#, Visual Basic veya C++ uygulamasını hata ayıklama|Standart hata ayıklama **(F5**) veya **İşleme Ekleme'yi** kullanın|*\<appname>.exe*|Çoğu senaryoda, standart hata ayıklama kullanın ve **İşleme Eklemeyin.**|
|Windows masaüstü uygulamasını uzaktan hata ayıklama|Uzak araçlar|Yok| [C# veya Visual Basic uygulamasını uzaktan hata ayıklama veya](../debugger/remote-debugging-csharp.md) [C++ uygulamasını uzaktan hata ayıklama](../debugger/remote-debugging-cpp.md)|
|Linux'ta Hata Ayıklama .NET Core|**İşleme Ekle'yi** Kullan|*dotnet.exe*|SSH'yi kullanmak için, [SSH kullanarak Linux üzerinde çalışan Uzaktan hata ayıklama .NET Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)bölümüne bakın. |
|Hata ayıklama olmadan uygulamayı başlattıktan sonra yerel makinede ASP.NET bir uygulama hata ayıklama|**İşleme Ekle'yi** Kullan|*iiexpress.exe*|Bu, (örneğin) profil oluşturma gibi uygulamanızın daha hızlı yüklenmesini sağlamak için yararlı olabilir. |
|Sunucu işleminde desteklenen diğer uygulama türlerini hata ayıklama|Sunucu uzaksa, uzak araçları kullanın ve **İşleme Ekle**|*chrome.exe*, *iexplore.exe*, veya diğer işlemler|Gerekirse, işlemi belirlemeye yardımcı olmak için Kaynak İzleyici'yi kullanın. Bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md).|
|Evrensel Windows Uygulaması (UWP), OneCore, HoloLens veya IoT uygulamasını uzaktan hata ayıklama|Hata ayıklama yüklü uygulama paketi|Yok|İşleme Ekle'yi kullanmak yerine [yüklü bir uygulama paketini hata](debug-installed-app-package.md) **ayıklama**|
|Visual Studio'dan başlamadığınız Evrensel Windows Uygulaması (UWP), OneCore, HoloLens veya IoT uygulamasını hata ayıklama|Hata ayıklama yüklü uygulama paketi|Yok|İşleme Ekle'yi kullanmak yerine [yüklü bir uygulama paketini hata](debug-installed-app-package.md) **ayıklama**|

## <a name="use-debugger-features"></a>Hata ayıklama özelliklerini kullanma

Visual Studio hata ayıklamanın (kesme noktalarına vurmak gibi) tüm özelliklerini bir işleme eklerken kullanmak için uygulamanın yerel kaynağınızla ve sembollerinizle tam olarak eşleşmesi gerekir. Diğer bir diğer olarak, hata ayıklama doğru [simge (.pdb) dosyalarını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)yükleyebilmeli. Varsayılan olarak, bu bir hata ayıklama oluşturma gerektirir.

Uzaktan hata ayıklama senaryoları için, kaynak kodu (veya kaynak kodun bir kopyası) Zaten Visual Studio açık olması gerekir. Uzak makinede derlenmiş uygulama ikilileri yerel makinedekiyle aynı yapıdan gelmelidir.

Bazı yerel hata ayıklama senaryolarında, uygulamayla birlikte doğru sembol dosyaları varsa, kaynağa erişmeden Visual Studio'da hata ayıklama yapabilirsiniz. Varsayılan olarak, bu bir hata ayıklama oluşturma gerektirir. Daha fazla bilgi için [bkz.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a>Sorun giderme ekleme hataları
 Hata ayıklayıcı çalışan bir işleme eklendiğinde, işlem bir veya daha fazla kod türü içerebilir. Hata ayıklayıcının ekebileceği kod türleri görüntülenir ve **Kod Türünü Seç** iletişim kutusunda seçilir.

 Bazen hata ayıklayıcı bir kod türüne başarıyla bağlanabilir, ancak başka bir kod türüne ekleyebilir. Uzak bir bilgisayarda çalışan bir işleme eklemeye çalışıyorsanız bu oluşabilir. Uzak bilgisayarda bazı kod türleri için yüklü, ancak diğerleri için yüklü olmayan uzaktan hata ayıklama bileşenleri olabilir. Doğrudan veritabanı hata ayıklama için iki veya daha fazla işlem eklemeye çalışırsanız da oluşabilir. SQL hata ayıklama yalnızca tek bir işleme eklemeyi destekler.

 Hata ayıklayıcı, tüm kod türlerine değil, bazılarına eklenebilirse, hangi türlerin eklenmediğini tanımlayan bir ileti görürsünüz.

 Hata ayıklayıcı en az bir kod türüne başarıyla bağlanırsa, işlemi hata ayıklama işlemine devam edebilirsiniz. Yalnızca başarıyla iliştirilen kod türlerini hata ayıklama nız mümkün olacaktır. İşlemdeki eklenmemiş kod yine de çalışır, ancak kesme noktaları ayarlayamazsınız, verileri görüntüleyemezsiniz veya bu koddaki diğer hata ayıklama işlemlerini gerçekleştiremezsiniz.

 Hata ayıklayıcının neden bir kod türüne eklenmediği hakkında daha ayrıntılı bilgi istiyorsanız, yalnızca bu kod türüne yeniden eklemeyi deneyin.

 **Kod türünün neden eklenmediği hakkında belirli bilgiler edinmek için:**

1. İşlemden ayırın. Hata **Ayıklama** menüsünde **Tümünü Ayır'ı**seçin.

1. Yalnızca eklenemeyen kod türünü seçerek işleme yeniden ekin.

    1. **İşleme Ekle** iletişim kutusunda, **Kullanılabilir İşlemler** listesindeki işlemi seçin.

    2. **Seç**’i seçin.

    3. Kod **Türü Seç** iletişim kutusunda, **hata ayıklama bu kod türleri** ve eklemek için başarısız kod türü seçin. Diğer kod türlerinin select'ini seçin.

    4. **Tamam'ı**seçin.

    5. **İşleme Ekle** iletişim kutusunda **Ekle'yi**seçin.

    Bu kez, eklemek tamamen başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca bkz.

- [Birden çok işlemde hata ayıklama](../debugger/debug-multiple-processes.md)
- [Just-In-Time hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md)
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
