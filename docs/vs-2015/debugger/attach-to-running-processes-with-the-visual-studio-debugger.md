---
title: Hata ayıklayıcı ile çalışan Işlemlere iliştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
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
- C++
- CSharp
- FSharp
- VB
- c++
helpviewer_keywords:
- remote debugging, attaching to programs
- processes, attaching to running processes
- Attach to Process dialog box
- debugging [Visual Studio], attaching to processes
- debugger, processes
ms.assetid: 27900e58-090c-4211-a309-b3e1496d5824
caps.latest.revision: 62
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf4d63d7d00e91daa2564992f801896075f73aab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918936"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio Hata Ayıklayıcısı ile Çalıştırma İşlemleri İliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcısını, yerel veya uzak bir bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalıştıktan sonra, işleme Ekle **/işleme** ' ya tıklayın (veya **Ctrl + Alt + P**tuşlarına basarak) **işleme Ekle** iletişim kutusunu açın.

Bu özelliği, yerel veya uzak bilgisayarda çalışan uygulamalarda hata ayıklamak, aynı anda birden çok işlemi hata ayıklamak veya Visual Studio 'da oluşturulmamış bir uygulamada hata ayıklamak için kullanabilirsiniz. Genellikle bir uygulamada hata ayıklamak istediğinizde, ancak (herhangi bir nedenle) uygulamayı Visual Studio 'dan hata ayıklayıcı ekli olarak başlatmadınız. Örneğin, uygulamayı hata ayıklayıcı olmadan çalıştırıyorsanız ve bir özel durumla karşılaşdıysanız, hata ayıklamaya başlamak için uygulamayı çalıştıran işleme ekleyebilirsiniz.

> [!TIP]
> Hata ayıklama senaryonuz için **iliştirme 'yi** kullanmak zorunda olduğunuzdan emin değil misiniz? Bkz. [yaygın hata ayıklama senaryoları](#BKMK_Scenarios). IIS 'ye dağıtılan ASP.NET uygulamalarında hata ayıklamak istiyorsanız, [uzak bır IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)bölümüne bakın.

## <a name="attach-to-a-running-process-on-the-local-machine"></a><a name="BKMK_Attach_to_a_running_process"></a> Yerel makinede çalışan bir işleme iliştirme
 Bir işleme iliştirmek için işlemin adını bilmeniz gerekir (bazı yaygın işlem adları için [sık karşılaşılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın).

1. Visual Studio 'da **Hata Ayıkla/Işleme İliştir** ' i seçin (veya **Ctrl + Alt + P**tuşlarına basın).

2. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinden eklemek istediğiniz programı bulun.

     İstediğiniz işlemi hızlıca seçmek için, işlem adının ilk harfini yazın. İşlem adını bilmiyorsanız bkz. [ortak hata ayıklama senaryoları](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     İşlem farklı bir kullanıcı hesabı altında çalışıyorsa, **tüm kullanıcılardan Işlemleri göster** onay kutusunu seçin.

3. **Ekle** kutusunda, hata ayıklamanızı istediğiniz kod türünün listelendiğinden emin olun. Varsayılan **Otomatik** ayar, hata ayıklamak istediğiniz kod türünü belirlemeyi dener. Kod türünü el ile ayarlamak için şunları yapın

    1. **Ekle** kutusunda **Seç**' e tıklayın.

    2. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinde hata ayıkla** ' ya tıklayın ve hata ayıklaması yapılacak türleri seçin.

    3. **Tamam**’a tıklayın.

4. **Ekle**' ye tıklayın.

## <a name="attach-to-a-process-on-a-remote-computer"></a><a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a> Uzak bilgisayardaki bir işleme iliştirme
 Bir işleme iliştirmek için işlemin adını bilmeniz gerekir (bazı yaygın işlem adları için [sık karşılaşılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın). IIS 'ye dağıtılan ASP.NET uygulamalarına yönelik daha kapsamlı yönergeler için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Diğer uygulamalar için, Görev Yöneticisi 'nde işlemin adını bulabilirsiniz.

 **Işleme İliştir** iletişim kutusunu kullandığınızda, uzaktan hata ayıklama için ayarlanmış başka bir bilgisayar seçebilirsiniz. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Uzak bir bilgisayar seçtiğinizde, o bilgisayarda çalışan kullanılabilir işlemlerin listesini görüntüleyebilir ve hata ayıklama için bir veya daha fazla işleme ekleyebilirsiniz.

 **Uzak bir bilgisayar seçmek için:**

1. Visual Studio 'da **Hata Ayıkla/Işleme İliştir** ' i seçin (veya **Ctrl + Alt + P**tuşlarına basın).

2. **Işleme İliştir** iletişim kutusunda, **Aktarım** listesinden uygun bağlantı türünü seçin. **Varsayılan değer** çoğu durumda doğru ayardır.

   **Aktarım** ayarı, hata ayıklama oturumları arasında devam ettirir.

3. Aşağıdaki yöntemlerden birini kullanarak uzak bilgisayar adını seçmek için **niteleyici** liste kutusunu kullanın:

   1. **Niteleyici** liste kutusuna adı yazın.

      > [!NOTE]
      > Daha sonraki adımlarda, uzak bilgisayar adını kullanarak bağlanamıyorsanız IP adresini kullanın. (Bağlantı noktası numarası işlem seçildikten sonra otomatik olarak görünebilir. Ayrıca, el ile de girebilirsiniz. Aşağıdaki çizimde, 4020, uzaktan hata ayıklayıcı için varsayılan bağlantı noktasıdır.)

   2. **Niteleyici** liste kutusuna eklenen aşağı açılan oka tıklayın ve açılan listeden bilgisayar adını seçin.

   3. **Niteleyici** listesinin yanındaki **bul** düğmesine tıklayarak **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusunu açın. **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu, yerel alt ağınızdaki tüm cihazları ve Ethernet kablosu üzerinden bilgisayarınıza doğrudan bağlı olan tüm cihazları listeler. İstediğiniz bilgisayara veya cihaza tıklayın ve ardından **Seç**' e tıklayın.

      **Niteleyici** ayarı, yalnızca bu niteleyici ile başarılı bir hata ayıklama bağlantısı meydana gelirse hata ayıklama oturumları arasında devam sürdürülür.

4. **Yenile**'ye tıklayın.

     **İşler** iletişim kutusunu açtığınızda **kullanılabilir süreçler** listesi otomatik olarak görüntülenir. İletişim kutusu açıkken, işlem arka planda başlayabilir ve durabilir. Ancak, içerikler her zaman geçerli değildir. **Yenile**' ye tıklayarak, geçerli işlem listesini görmek için listeyi dilediğiniz zaman yenileyebilirsiniz.

5. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinden eklemek istediğiniz programı bulun.

    İşlem farklı bir kullanıcı hesabı altında çalışıyorsa, **tüm kullanıcılardan Işlemleri göster** onay kutusunu seçin.

6. **Ekle**' ye tıklayın.

## <a name="additional-info"></a>Ek bilgiler

Hata ayıklarken birden çok programa iliştirilebilir, ancak herhangi bir zamanda hata ayıklayıcıda yalnızca bir program etkin hale getirebilirsiniz. Etkin programı **hata ayıklama konumu** araç çubuğunda veya **süreçler** penceresinde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: geçerli programı ayarlama](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Güvenilmeyen bir kullanıcı hesabına ait bir işleme iliştirmeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görüntülenir. Daha fazla bilgi için bkz [. güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir Işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)eklemeyin.

Bazı durumlarda, Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıkladığınızda, **kullanılabilir süreçler** listesinde tüm kullanılabilir süreçler gösterilmez. Farklı bir kullanıcı hesabı olan bir kullanıcı olarak Visual Studio çalıştırıyorsanız, **kullanılabilir süreçler** listesi, w3wp.exe dahil olmak üzere Hizmetler ve diğer sunucu Işlemlerinde kullanılan oturum 0 ' da çalışan işlem göstermez. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bir yönetici hesabı altında veya bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Terminal Hizmetleri oturumu yerine sunucu konsolundan çalıştırarak sorunu çözebilirsiniz. Bu geçici çözümlerin hiçbiri mümkün değilse, üçüncü bir seçenek, `vsjitdebugger.exe -p` Windows komut satırından *İşlemKimliği* çalıştırılarak işleme eklemektir. tlist.exe kullanarak işlem kimliğini belirleyebilirsiniz. tlist.exe edinmek için, Windows için hata ayıklama araçları 'nı indirip yükleyin  [ve ardından, WDK ve WinDbg indirmelerinde](/windows-hardware/drivers/dashboard/)kullanılabilir.

## <a name="common-debugging-scenarios"></a><a name="BKMK_Scenarios"></a> Ortak hata ayıklama senaryoları

**Işleme İliştir** ve ne tür bir işleme kullanacağınızı belirlemenize yardımcı olmak için, burada yaygın olarak karşılaşılan birkaç hata ayıklama senaryosu gösterilir (liste ayrıntılı değildir). Daha fazla yönerge varsa, bağlantılar sağlıyoruz.

Bazı uygulama türleri (örneğin, Windows Mağazası uygulamaları gibi) için doğrudan bir işlem adına iliştiremezsiniz, ancak bunun yerine **yüklü uygulama paketini hata ayıkla** menü seçeneğini kullanın (bkz. tablo).

> [!NOTE]
> Visual Studio 'da temel hata ayıklama hakkında daha fazla bilgi için bkz. [hata ayıklayıcıyla çalışmaya başlama](../debugger/getting-started-with-the-debugger.md).

|Senaryo|Hata ayıklama yöntemi|İşlem adı|Notlar ve bağlantılar|
|-|-|-|-|
|Yerel makinede yönetilen veya yerel bir uygulamada hata ayıklama|İşlemek veya [Standart hata ayıklamak](../debugger/getting-started-with-the-debugger.md) için İliştir kullanın|*appname*. exe|İletişim kutusuna hızlıca erişmek için **Ctrl + Alt + P** tuşlarını kullanın ve ardından işlem adının ilk harfini yazın.|
|Uygulamayı hata ayıklayıcı olmadan başlattıktan sonra yerel makinede ASP.NET uygulamalarda hata ayıklayın|İşlemek için İliştir kullanın|iiexpress.exe|Bu, uygulamanızın profil oluşturma sırasında (örneğin) daha hızlı yüklenmesini sağlamak için yararlı olabilir. |
|IIS sunucusunda uzaktan hata ayıklama ASP.NET 4 veya 4,5|Uzak araçları kullanma ve işleme iliştirme|w3wp.exe|Bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|IIS sunucusunda uzaktan hata ayıklama ASP.NET Core|Uzak araçları kullanma ve işleme iliştirme|dnx.exe|Uygulama dağıtımı için bkz. [IIS 'de yayımlama](https://docs.asp.net/en/latest/publishing/iis.html). Hata ayıklama için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Sunucu işlemindeki desteklenen diğer uygulama türlerinde hata ayıkla|Uzak araçları kullan (sunucu uzakta ise) ve işleme iliştir|iexplore.exe veya diğer süreçler|Gerekirse, işlemin tanımlanmasına yardımcı olması için Görev Yöneticisi 'ni kullanın. Bu konunun [Uzaktan hata ayıklama](../debugger/remote-debugging.md) ve üzeri bölümlerine bakın|
|Windows masaüstü uygulamasında uzaktan hata ayıklama|Uzak Araçlar ve F5|Yok| Bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Windows Universal (UWP), OneCore, HoloLens veya IoT uygulamasında uzaktan hata ayıklama|Yüklü uygulama paketinin hatalarını ayıkla|Yok|**Hata ayıklama/diğer hata ayıklama hedeflerini kullan/** **Işleme Iliştir** yerine yüklü uygulama paketini Ayıkla|
|Visual Studio 'dan başlatmadığınız bir Windows Universal (UWP), OneCore, HoloLens veya IoT uygulamasında hata ayıklama|Yüklü uygulama paketinin hatalarını ayıkla|Yok|**Hata ayıklama/diğer hata ayıklama hedeflerini kullan/** **Işleme Iliştir** yerine yüklü uygulama paketini Ayıkla|

> [!WARNING]
> JavaScript 'te yazılmış bir Windows Evrensel uygulamasına eklemek için, önce uygulama için hata ayıklamayı etkinleştirmeniz gerekir. Bkz. Windows Geliştirme Merkezi 'nde [hata ayıklayıcıyı iliştirme](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) .

> [!NOTE]
> Hata ayıklayıcının C++ dilinde yazılmış koda eklemesi için kodun bir yayma yapması gerekir `DebuggableAttribute` . [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) bağlayıcı seçeneğiyle bağlantı kurarak bunu kodunuza otomatik olarak ekleyebilirsiniz.

## <a name="what-debugger-features-can-i-use"></a>Hangi hata ayıklayıcı özelliklerini kullanabilirim?

Bir işleme eklenirken Visual Studio hata ayıklayıcının (kesme noktaları gibi) tam özelliklerini kullanmak için, yürütülebilir dosya yerel kaynak ve sembollerle tam olarak eşleşmelidir (yani, hata ayıklayıcı doğru [sembol (. pbd) dosyalarını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)yükleyebilmelidir). Varsayılan olarak, bu bir hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryolarında, Visual Studio 'da zaten açık olan kaynak kodu (veya kaynak kodun bir kopyası) olmalıdır. Uzak makinedeki derlenen uygulama ikilileri, yerel makineyle aynı derlemeden gelmelidir.

Bazı yerel hata ayıklama senaryolarında, uygulamayla ilgili doğru sembol dosyaları varsa, Visual Studio 'da kaynağa erişim olmadan hata ayıklama yapabilirsiniz (varsayılan olarak, bu, bir hata ayıklama derlemesi gerektirir). Daha fazla bilgi için bkz. [sembol ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="troubleshoot-attach-errors"></a><a name="BKMK_Troubleshoot_attach_errors"></a> İliştirme hatalarını giderme
 Hata ayıklayıcı çalışan bir işleme iliştirayarlandığında, işlem bir veya daha fazla kod türü içerebilir. Hata ayıklayıcının iliştirebilecek kod türleri **kod türü seç** iletişim kutusunda görüntülenir ve seçilir.

 Bazen hata ayıklayıcı, bir kod türüne başarıyla eklenebilir, ancak başka bir kod türüne eklenemez. Bu durum, uzak bir bilgisayarda çalışan bir işleme eklemeye çalışıyorsanız oluşabilir. Uzak bilgisayarda, bazı kod türleri için yüklenmiş uzaktan hata ayıklama bileşenleri bulunabilir, ancak diğerleri için kullanılamaz. Doğrudan veritabanı hata ayıklaması için iki veya daha fazla işleme eklemeye çalıştığınızda da bu durum oluşabilir. SQL hata ayıklaması yalnızca tek bir işleme eklemeyi destekler.

 Hata ayıklayıcı bazı kod türlerine iliştirilemiyor, ancak bunların tümüne değil, hangi türlerin iliştirileyemedi tanımlayan bir ileti görürsünüz.

 Hata ayıklayıcı en az bir kod türüne başarıyla iliştirmesine devam ederseniz işlemde hata ayıklaması yapabilirsiniz. Yalnızca başarıyla eklenmiş kod türlerinde hata ayıklayabileceksiniz. Yukarıdaki örnek ileti, komut dosyası kodu türünün iliştirilemedi olduğunu gösterir. Bu nedenle, işlem içindeki komut dosyası kodu hatalarını ayıklayamazsınız. İşlemdeki betik kodu hala çalışmaya devam eder, ancak komut dosyasında kesme noktaları ayarlayabilir, verileri görüntüleyemez veya diğer hata ayıklama işlemlerini gerçekleştiremeyeceksiniz.

 Hata ayıklayıcının neden bir kod türüne eklenemediğini belirten daha özel bilgiler istiyorsanız, yalnızca bu kod türüne yeniden iliştirmeyi deneyebilirsiniz.

 **Kod türünün neden iliştirilemedi hakkında belirli bilgiler elde etmek için**

1. İşlemden ayırın. **Hata Ayıkla** menüsünde **Tümünü Ayır**' a tıklayın.

2. Yalnızca tek bir kod türü seçerek işleme yeniden iliştirin.

   1. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinde işlemi seçin.

   2. **Seç**’e tıklayın.

   3. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinin** ve Iliştirilemedi kod türünün hatalarını ayıkla ' yı seçin. Diğer tüm kodları temizleyin.

   4. **Tamam**’a tıklayın. **Kod türünü seç** iletişim kutusu kapanır.

   5. **Işleme İliştir** Iletişim kutusunda **İliştir**' e tıklayın.

      Bu kez, iliştirme tamamen başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca Bkz.
 [Birden çok Işlemi hata ayıklama](../debugger/debug-multiple-processes.md) [hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) [Uzaktan hata](../debugger/remote-debugging.md) ayıklama
