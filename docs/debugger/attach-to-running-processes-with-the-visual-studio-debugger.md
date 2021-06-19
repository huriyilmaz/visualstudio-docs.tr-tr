---
title: Hata ayıklayıcısı ile çalıştırma işlemleri iliştirme
description: Visual Studio hata ayıklayıcısını, yerel veya uzak bir bilgisayarda çalışan bir işleme nasıl ekleyebilirim öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e3836403af80d06a2ecaa7f77cb7f49f0c6f0e8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389793"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcısı ile çalıştırma işlemleri iliştirme

Visual Studio hata ayıklayıcısını, yerel veya uzak bir bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalıştıktan sonra, işleme Ekle **Hata Ayıkla**' yı seçin  >   veya  +  + Visual Studio 'da Ctrl alt **p** tuşlarına basın ve hata ayıklayıcıyı işleme eklemek için **İşleme İliştir** iletişim kutusunu kullanın.

Yerel veya uzak bilgisayarlarda çalışan uygulamalarda hata ayıklamak, aynı anda birden çok işlemi hata ayıklamak, Visual Studio 'da oluşturulmamış uygulamalarda hata ayıklamak veya Visual Studio 'da hata ayıklayıcı ekli olan herhangi bir uygulamada hata ayıklamak için **İliştir** ' i kullanabilirsiniz. Örneğin, hata ayıklayıcı olmadan bir uygulama çalıştırıyorsanız ve bir özel durumla karşılaşdıysanız, uygulamayı çalıştıran işleme hata ayıklayıcıyı iliştirebilir ve hata ayıklamaya başlayabilirsiniz.

> [!TIP]
> Hata ayıklama senaryonuz için **iliştirme** 'yi kullanıp kullanmayacağınızı bilmiyorsanız emin değil misiniz? Bkz. [yaygın hata ayıklama senaryoları](#BKMK_Scenarios).

## <a name="attach-to-a-running-process-on-your-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Yerel makinenizde çalışan bir işleme iliştirme

Daha önce eklediğiniz bir işleme hızlıca yeniden iliştirmek için bkz. [bir işleme yeniden bağlama](#BKMK_reattach).

**Yerel bilgisayarınızdaki bir işleme eklemek için:**

1. Visual Studio 'da, işleme Ekle  >    +  + iletişim kutusunu açmak  için işleme Ekle hata ayıkla (veya Ctrl alt **P** tuşlarına basın) seçeneğini belirleyin.

1. **Bağlantı türünü** denetleyin.

   Çoğu senaryoda **varsayılan**'ı kullanabilirsiniz. Bazı senaryolar, farklı bir bağlantı türü gerektirebilir. Daha fazla bilgi için, bu makaledeki diğer bölümlere veya [ortak hata ayıklama senaryolarına](#BKMK_Scenarios)bakın.

1. Yerel makine adınızla **bağlantı hedefini** ayarlayın.

   ![Işleme Iliştir iletişim kutusunun, bağlantı hedefi yerel makine adına ayarlanmış olan ekran görüntüsü.](../debugger/media/DBG_Basics_Attach_To_Process.png)

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

1. Visual Studio 'da, işleme Ekle  >    +  + iletişim kutusunu açmak  için işleme Ekle hata ayıkla (veya Ctrl alt **P** tuşlarına basın) seçeneğini belirleyin.

1. **Bağlantı türünü** denetleyin.

   Çoğu senaryoda **varsayılan**'ı kullanabilirsiniz. Linux veya kapsayıcılı bir uygulama için hata ayıklama gibi bazı senaryolar, farklı bir bağlantı türü gerektirir. Daha fazla bilgi için, bu makaledeki diğer bölümlere veya [ortak hata ayıklama senaryolarına](#BKMK_Scenarios)bakın.

1. **Bağlantı hedefi** kutusunda, aşağıdaki yöntemlerden birini kullanarak uzak bilgisayarı seçin:

   - **Bağlantı hedefi**' nin yanındaki açılan oku seçin ve açılan listeden bilgisayar adını seçin.
   - Bilgisayar adını **bağlantı hedefi** kutusuna yazın ve **ENTER** tuşuna basın.

     Visual Studio 'Nun gerekli bağlantı noktasını bilgisayar adına eklediğini doğrulayın ve şu biçimde görünür: **\<remote computer name> :p ort**

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

Bazı durumlarda, Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıkladığınızda, **kullanılabilir süreçler** listesinde tüm kullanılabilir süreçler görüntülenmez. Visual Studio 'Yu sınırlı bir kullanıcı hesabına sahip olan bir kullanıcı olarak çalıştırıyorsanız, **kullanılabilir süreçler** listesinde, oturum 0 ' da çalışan süreçler gösterilmez. Oturum 0, *w3wp.exe* dahil olmak üzere Hizmetler ve diğer sunucu işlemlerinde kullanılır. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Bir yönetici hesabı altında veya bir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Terminal Hizmetleri oturumu yerine sunucu konsolundan çalıştırarak sorunu çözebilirsiniz.

Bu geçici çözümlerin hiçbiri mümkün değilse, üçüncü bir seçenek `vsjitdebugger.exe -p <ProcessId>` Windows komut satırından çalıştırılarak işleme eklemektir. *tlist.exe* kullanarak işlem kimliğini belirleyebilirsiniz. *tlist.exe* edinmek Için, Windows Için hata ayıklama araçları 'nı indirip yükleyin [ve ardından, WDK ve WinDbg indirmelerinde](/windows-hardware/drivers/download-the-wdk)kullanılabilir.

## <a name="attach-to-a-net-core-process-running-on-linux-using-ssh"></a>SSH kullanarak Linux üzerinde çalışan bir .NET Core işlemine iliştirme

Daha fazla bilgi için bkz. [SSH kullanarak Linux üzerinde çalışan uzaktan hata ayıklama .NET Core](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md).

::: moniker range=">= vs-2019"

## <a name="attach-to-a-process-running-on-a-docker-container"></a><a name="BKMK_Linux_Docker_Attach"></a> Docker kapsayıcısında çalışan bir işleme iliştirme

Visual Studio 2019 ' den başlayarak, Visual Studio hata ayıklayıcısını bir Docker kapsayıcısında çalışan bir işleme ekleyebilirsiniz. Linux .NET Core Docker kapsayıcısı için bkz. [Linux Docker kapsayıcısında çalışan bir Işleme iliştirme](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container). Windows Docker kapsayıcısı için, bkz. [Windows Docker kapsayıcısında çalışan bir Işleme iliştirme](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-windows-docker-container).

::: moniker-end

## <a name="reattach-to-a-process"></a><a name="BKMK_reattach"></a> Bir işleme yeniden iliştir

Daha önce iliştirmiş olduğunuz işlemlere hızlı bir şekilde **yeniden iliştirebilirsiniz**  >    +  + . Bu komutu seçtiğiniz zaman, hata ayıklayıcı ilk olarak önceki işlem kimliğiyle eşleşmeyi deneyerek ve başarısız olursa, önceki işlem adıyla eşleştirerek, ekli son işlemlere hemen eklemeye dener. Eşleşme bulunamıyorsa veya birden çok işlem aynı adı  alıyorsa, doğru işlemi seçerek İşleme Ekle iletişim kutusu açılır.

> [!NOTE]
> 2017'den itibaren İşleme Yeniden Visual Studio kullanılabilir. 

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Yaygın hata ayıklama senaryoları

İşleme Ekle'nin kullanıp kullanmayıp kullanmamanıza ve hangi işleme ekli olunacaklarını belirlemenize yardımcı olmak için, aşağıdaki tabloda bazı yaygın hata ayıklama senaryoları ve varsa daha fazla yönergelerin bağlantıları yer almaktadır.  (Liste kapsamlı değildir.)

Evrensel Windows Uygulaması (UWP) uygulamaları gibi bazı uygulama türleri için doğrudan bir işlem  adına eklemezsiniz, ancak bunun yerine Visual Studio uygulamasında Hata Ayıklama Yüklü Uygulama Paketi menü seçeneğini kullanırsınız (tabloya bakın).

Hata ayıklayıcının C++ ile yazılmış koda eklemesi için kodun yayma ihtiyacı `DebuggableAttribute` vardır. [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute) linker seçeneğiyle bağlantı kullanarak bunu kodunuza otomatik olarak ekebilirsiniz.

İstemci tarafı betik hata ayıklaması için tarayıcıda betik hata ayıklama etkinleştirilmelidir. Chrome'da istemci tarafı betiğinde hata ayıklamak için kod türü olarak **JavaScript (Chrome)** veya **JavaScript (Microsoft Edge - Chromium)** seçin ve uygulama türünüze bağlı olarak tüm Chrome örneklerini kapatmanız ve tarayıcıyı hata ayıklama modunda başlatmanız (bir komut satırıyla yazın) `chrome.exe --remote-debugging-port=9222` gerekir. Visual Studio'nin önceki sürümlerinde Chrome için betik hata ayıklayıcısı **Web seti'dir.**

Hızla iliştirilen bir işlemi seçmek için, Visual Studio **Ctrl** Alt P yazın ve ardından işlem adının ilk +  + harfini yazın.

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|IIS sunucusunda ASP.NET 4 veya 4.5'te uzaktan hata ayıklama|Uzak araçları kullanma ve **İşleme Ekleme**|*w3wp.exe*|Bkz. [Uzak IIS ASP.NET uzaktan hata ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS sunucusunda ASP.NET Core'da uzaktan hata ayıklama|Uzak araçları kullanma ve **İşleme Ekleme**|*w3wp.exe* veya *dotnet.exe*|.NET Core 3'te *w3wp.exe,* varsayılan uygulama içinde barındırma [modeli için kullanılır.](/aspnet/core/host-and-deploy/aspnet-core-module?view=aspnetcore-3.1&preserve-view=true#hosting-models) Uygulama dağıtımı için bkz. [IIS'de yayımlama.](/aspnet/core/host-and-deploy/iis/) Daha ayrıntılı bilgi için [bkz. Uzak iis ASP.NET çekirdekte uzaktan hata ayıklama](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md#BKMK_attach)|
|Desteklenen uygulama türleri için yerel IIS sunucusunda istemci tarafı betiği hata ayıklama |İşleme **Ekle'nin kullanımı**|*chrome.exe*, *MicrosoftEdgeCP.exe* veya *iexplore.exe*|Betik hata ayıklama etkinleştirilmelidir. Chrome için Chrome'u hata ayıklama modunda da çalıştırmalı (komut satırına yazın) ve Ekle alanında `chrome.exe --remote-debugging-port=9222` **JavaScript (Chrome)** **seçeneğini de seçmeniz** gerekir.|
|Yerel makinede C#, Visual Basic veya C++ uygulamasında hata ayıklama|Standart hata ayıklama (**F5**) veya İşleme **Ekleme kullanma**|*\<appname>.exe*|Çoğu senaryoda, İşleme Ekle değil standart hata **ayıklama kullanın.**|
|Windows masaüstü uygulamasında uzaktan hata ayıklama|Uzak araçlar|Yok| Bkz. [C# veya Visual Basic uzaktan](../debugger/remote-debugging-csharp.md) hata ayıklama veya [C++](../debugger/remote-debugging-cpp.md) uygulamasında uzaktan hata ayıklama|
|Linux’ta .NET Core hatalarını ayıklama|İşleme **Ekle'nin kullanımı**|*dotnet.exe* işlem adı veya benzersiz bir işlem adı|SSH kullanmak için [bkz. SSH kullanarak Linux](../debugger/remote-debugging-dotnet-core-linux-with-ssh.md)üzerinde çalışan uzaktan hata ayıklama .NET Core. Kapsayıcılı uygulamalar için [bkz. Docker kapsayıcısı içinde çalışan bir işleme ekleme.](../debugger/attach-to-process-running-in-docker-container.md#attach-to-a-process-running-on-a-linux-docker-container)|
|Kapsayıcılı uygulamada hata ayıklama|İşleme **Ekle'nin kullanımı**|*dotnet.exe* işlem adı veya benzersiz bir işlem adı|Bkz. [Docker kapsayıcısı içinde çalışan işleme ekleme](../debugger/attach-to-process-running-in-docker-container.md)|
|Linux üzerinde Python'da uzaktan hata ayıklama|İşleme **Ekle'nin kullanımı**|*hata ayıklama*|Bkz. [Python Araçlarından uzaktan ekleme](../python/debugging-python-code-on-remote-linux-machines.md#attach-remotely-from-python-tools)|
|Hata ayıklayıcı ASP.NET sonra yerel makinede bir uygulamanın hata ayıklamasını ayıklama|İşleme **Ekle'nin kullanımı**|*iiexpress.exe*|Bu, profil oluşturma gibi (örneğin) uygulama yüklemenizi daha hızlı hale toplamaya yardımcı olabilir. |
|Sunucu işlemi üzerinde desteklenen diğer uygulama türlerinde hata ayıklama|Sunucu uzaksa uzak araçlar kullanın ve İşleme **Ekle'ye**|*chrome.exe*, *iexplore.exe* veya diğer işlemler|Gerekirse, işlemi Kaynak İzleyicisi yardımcı olmak için Kaynak İzleyicisi kullanın. Bkz. [Uzaktan hata ayıklama.](../debugger/remote-debugging.md)|
|Evrensel Windows Uygulaması (UWP), OneCore, HoloLens veya IoT uygulamasında uzaktan hata ayıklama|Yüklü uygulama paketinde hata ayıklama|Yok|Bkz. [İşleme Ekle kullanmak yerine yüklü](debug-installed-app-package.md) bir uygulama **paketinde hata ayıklama**|
|Evrensel Windows Uygulaması (UWP), OneCore, HoloLens veya IoT uygulamasında Visual Studio|Yüklü uygulama paketinde hata ayıklama|Yok|Bkz. [İşleme Ekle kullanmak yerine yüklü](debug-installed-app-package.md) bir uygulama **paketinde hata ayıklama**|

## <a name="use-debugger-features"></a>Hata ayıklayıcı özelliklerini kullanma

Bir işleme ekleme sırasında Visual Studio hata ayıklayıcısının (kesme noktalarına isabet etmek gibi) tüm özelliklerini kullanmak için uygulamanın yerel kaynağınız ve simgeleriniz ile tam olarak eşleşmesi gerekir. Diğer bir nedenle, hata ayıklayıcı doğru sembol [(.pdb) dosyalarını yükleyemedi.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryoları için kaynak kodun (veya kaynak kodun bir kopyasının) önceden açık olması Visual Studio. Uzak makinede derlenmiş uygulama ikilileri, yerel makineyle aynı derlemeden gelbelir.

Bazı yerel hata ayıklama senaryolarında, uygulamada doğru sembol Visual Studio kaynak erişimine sahip değilken hata ayıklama sırasında hata ayıkabilirsiniz. Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir. Daha fazla bilgi için [bkz. Sembol ve kaynak dosyalarını belirtme.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> Ekleme hatalarını giderme

Bazı senaryolarda, hata ayıklayıcının hata ayıklamak için kod türünü doğru şekilde tanımlaması için yardıma ihtiyacı olabilir. Bağlantı değerleri doğru şekilde ayarlanmışsa (Kullanılabilir işlemler listesinde  doğru işlemi görüntülebilirsiniz) ancak hata ayıklayıcı eklenemezse, Bağlantı  türü listesinden en uygun bağlantı türünü seçmeyi deneyin. Bu tür bir Linux veya Python uygulamasında hata ayıklarken gerekli olabilir. Varsayılan bağlantı türünü kullanıyorsanız, bu bölümün ilerleyen kısımlarında açıklandığı gibi, alternatif olarak bağlanmak istediğiniz kod türünü de kullanabilirsiniz.

Hata ayıklayıcı çalışan bir işleme ekli olduğunda, işlem bir veya daha fazla kod türü içerebilir. Hata ayıklayıcının eklenemiyor kod türleri Kod Türünü Seç [iletişim kutusunda görüntülenir ve](../debugger/select-code-type-dialog-box.md) seçilir.

Bazen, hata ayıklayıcı bir kod türüne başarıyla iliştirebilirsiniz, ancak başka bir kod türüne ekleyemez. Bu durum genellikle aşağıdakiler olduğunda gerçekleşir:

- Uzak bilgisayarda çalışan bir işleme eklemeye çalışıyorsanız. Uzak bilgisayarda bazı kod türleri için uzaktan hata ayıklama bileşenleri yüklü olabilir, ancak diğerleri için yüklenmez.
- Doğrudan veritabanı hata ayıklaması için iki veya daha fazla işleme eklemeye çalışabilirsiniz. SQL hata ayıklaması yalnızca tek bir işleme iliştirme desteği sağlar.

Hata ayıklayıcısı kod türlerinin bazılarını (ancak hepsini değil) ekleyemediyse, hangi türlerin eklenemedi olduğunu belirten bir iletiyle karşılaşabilirsiniz.

Hata ayıklayıcı en az bir kod türüne başarıyla eklense, işlemde hata ayıklamaya geçebilirsiniz. Yalnızca başarıyla eklenmiş kod türlerinde hata ayıkabileceksiniz. İşlemde eksiz kod yine de çalıştırılmaz, ancak kesme noktaları ayar devredilemez, veriler görüntüilemez veya bu kod üzerinde başka hata ayıklama işlemleri gerçekleştirilemez.

Hata ayıklayıcının bir kod türüne neden eklenemedikleri hakkında daha ayrıntılı bilgi almak için yalnızca bu kod türüne yeniden eklemeyi deneyin.

**Bir kod türünün neden eklenemedikleri hakkında belirli bilgiler almak için:**

1. İşlemden ayırma. Hata **Ayıkla menüsünde,** Tüm Öğeleri **Ayır'ı seçin.**

1. Yalnızca eklenemedi kod türünü seçerek işleme yeniden iliştirin.

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
