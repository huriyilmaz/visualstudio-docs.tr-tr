---
title: Hata ayıklayıcısı ile çalıştırma işlemleri iliştirme | Microsoft Docs
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
ms.openlocfilehash: 03cd890802e5563ce2daeb78438c56f4452d74f0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299510"
---
# <a name="attach-to-running-processes-with-the-visual-studio-debugger"></a>Visual Studio Hata Ayıklayıcısı ile Çalıştırma İşlemleri İliştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı bir yerel veya uzak bilgisayarda çalışan bir işleme ekleyebilirsiniz. İşlem çalıştıktan sonra, işleme Ekle **/işleme** ' ya tıklayın (veya **Ctrl + Alt + P**tuşlarına basarak) **işleme Ekle** iletişim kutusunu açın.

Bu özellik, bir yerel veya uzak bilgisayarda çalışan uygulamaların hata ayıklama, aynı anda birden çok işlemde hata ayıklama veya Visual Studio'da oluşturulmamış bir uygulamada hata ayıklamak için kullanabilirsiniz. Bir uygulamanın hatalarını ayıklamak istediğiniz zaman çoğunlukla yararlı olur ancak (herhangi bir nedenle), başlamadı uygulamayı Visual Studio'dan hata ayıklayıcısı ekli. Örneğin, hata ayıklayıcı olmadan uygulamayı çalıştırdığınız ve bir özel durum oluştu, hata ayıklamayı başlatmak için uygulama çalışan işlemi için daha sonra iliştirin.

> [!TIP]
> Hata ayıklama senaryonuz için **iliştirme 'yi** kullanmak zorunda olduğunuzdan emin değil misiniz? Bkz. [yaygın hata ayıklama senaryoları](#BKMK_Scenarios). IIS 'ye dağıtılan ASP.NET uygulamalarında hata ayıklamak istiyorsanız, [uzak bır IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)bölümüne bakın.

## <a name="BKMK_Attach_to_a_running_process"></a>Yerel makinede çalışan bir işleme iliştirme
 Bir işleme iliştirmek için işlemin adını bilmeniz gerekir (bazı yaygın işlem adları için [sık karşılaşılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın).

1. Visual Studio 'da **Hata Ayıkla/Işleme İliştir** ' i seçin (veya **Ctrl + Alt + P**tuşlarına basın).

2. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinden eklemek istediğiniz programı bulun.

     İstediğiniz işlemi hızla seçmek için işlem adı ilk harflerini yazın. İşlem adını bilmiyorsanız bkz. [ortak hata ayıklama senaryoları](#BKMK_Scenarios).

     ![DBG_Basics_Attach_To_Process](../debugger/media/dbg-basics-attach-to-process.png "DBG_Basics_Attach_To_Process")

     İşlem farklı bir kullanıcı hesabı altında çalışıyorsa, **tüm kullanıcılardan Işlemleri göster** onay kutusunu seçin.

3. **Ekle** kutusunda, hata ayıklamanızı istediğiniz kod türünün listelendiğinden emin olun. Varsayılan **Otomatik** ayar, hata ayıklamak istediğiniz kod türünü belirlemeyi dener. Kod türünü el ile ayarlamak için aşağıdakileri yapın

    1. **Ekle** kutusunda **Seç**' e tıklayın.

    2. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinde hata ayıkla** ' ya tıklayın ve hata ayıklaması yapılacak türleri seçin.

    3. **Tamam**'a tıklayın.

4. **Ekle**' ye tıklayın.

## <a name="BKMK_Attach_to_a_process_on_a_remote_computer"></a>Uzak bilgisayardaki bir işleme iliştirme
 Bir işleme iliştirmek için işlemin adını bilmeniz gerekir (bazı yaygın işlem adları için [sık karşılaşılan hata ayıklama senaryolarına](#BKMK_Scenarios) bakın). IIS 'ye dağıtılan ASP.NET uygulamalarına yönelik daha kapsamlı yönergeler için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md). Diğer uygulamalar için Görev Yöneticisi'nde işleminin adını bulma mümkün olabilir.

 **Işleme İliştir** iletişim kutusunu kullandığınızda, uzaktan hata ayıklama için ayarlanmış başka bir bilgisayar seçebilirsiniz. Daha fazla bilgi için bkz. [Uzaktan hata ayıklama](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c). Bir uzak bilgisayar seçtiğinizde, bu bilgisayar üzerinde çalışan kullanılabilir süreçlerin listesini görüntüleyebilir ve bir veya daha fazla hata ayıklama için iliştirin.

 **Uzak bir bilgisayar seçmek için:**

1. Visual Studio 'da **Hata Ayıkla/Işleme İliştir** ' i seçin (veya **Ctrl + Alt + P**tuşlarına basın).

2. **Işleme İliştir** iletişim kutusunda, **Aktarım** listesinden uygun bağlantı türünü seçin. **Varsayılan değer** çoğu durumda doğru ayardır.

   **Aktarım** ayarı, hata ayıklama oturumları arasında devam ettirir.

3. Aşağıdaki yöntemlerden birini kullanarak uzak bilgisayar adını seçmek için **niteleyici** liste kutusunu kullanın:

   1. **Niteleyici** liste kutusuna adı yazın.

      > [!NOTE]
      > Daha sonraki adımlarda, uzak bilgisayar adını kullanarak bağlanamıyorsanız IP adresini kullanın. (Bağlantı noktası numarasını otomatik olarak işlem seçtikten sonra görünebilir. Da onu el ile girebilirsiniz. Aşağıdaki çizimde, 4020 uzaktan hata ayıklayıcı için varsayılan bağlantı noktası var.)

   2. **Niteleyici** liste kutusuna eklenen aşağı açılan oka tıklayın ve açılan listeden bilgisayar adını seçin.

   3. **Niteleyici** listesinin yanındaki **bul** düğmesine tıklayarak **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusunu açın. **Uzaktan hata ayıklayıcı bağlantısı Seç** iletişim kutusu, yerel alt ağınızdaki tüm cihazları ve Ethernet kablosu üzerinden bilgisayarınıza doğrudan bağlı olan tüm cihazları listeler. İstediğiniz bilgisayara veya cihaza tıklayın ve ardından **Seç**' e tıklayın.

      **Niteleyici** ayarı, yalnızca bu niteleyici ile başarılı bir hata ayıklama bağlantısı meydana gelirse hata ayıklama oturumları arasında devam sürdürülür.

4. **Yenile**' ye tıklayın.

     **İşler** iletişim kutusunu açtığınızda **kullanılabilir süreçler** listesi otomatik olarak görüntülenir. İşlemler başlatabilir ve iletişim kutusu açıkken arka planda durdurabilirsiniz. Ancak, içeriği her zaman geçerli değildir. **Yenile**' ye tıklayarak, geçerli işlem listesini görmek için listeyi dilediğiniz zaman yenileyebilirsiniz.

5. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinden eklemek istediğiniz programı bulun.

    İşlem farklı bir kullanıcı hesabı altında çalışıyorsa, **tüm kullanıcılardan Işlemleri göster** onay kutusunu seçin.

6. **Ekle**' ye tıklayın.

## <a name="additional-info"></a>Ek bilgi

Birden çok programları için hata ayıklama, ancak herhangi bir anda yalnızca bir programı hata ayıklayıcıda etkin eklenebilir. Etkin programı **hata ayıklama konumu** araç çubuğunda veya **süreçler** penceresinde ayarlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: geçerli programı ayarlama](https://msdn.microsoft.com/7e1d7fa5-0e40-44cf-8c41-d3dba31c969e).

Güvenilmeyen bir kullanıcı tarafından sahip olunan bir işlem eklemeye çalışırsanız, bir güvenlik uyarısı iletişim kutusu onayı görünecektir. Daha fazla bilgi için bkz [. güvenlik uyarısı: güvenilmeyen bir kullanıcının sahip olduğu bir Işleme ekleme tehlikeli olabilir. Aşağıdaki bilgiler şüpheli görünüyorsa veya emin değilseniz, bu işleme](/visualstudio/debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user?view=vs-2015)eklemeyin.

Bazı durumlarda, Uzak Masaüstü (Terminal Hizmetleri) oturumunda hata ayıkladığınızda, **kullanılabilir süreçler** listesinde tüm kullanılabilir süreçler gösterilmez. Farklı bir kullanıcı hesabı olan bir kullanıcı olarak Visual Studio çalıştırıyorsanız, **kullanılabilir süreçler** listesi, W3wp. exe dahil olmak üzere Hizmetler ve diğer sunucu Işlemlerinde kullanılan oturum 0 ' da çalışan işlemi göstermez. Bir yönetici hesabı altında [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çalıştırarak veya bir Terminal Hizmetleri oturumu yerine sunucu konsolundan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] çalıştırarak sorunu çözebilirsiniz. Bu geçici çözümlerin hiçbiri mümkün değilse, üçüncü bir seçenek Windows komut satırından `vsjitdebugger.exe -p` *İşlemKimliği* çalıştırılarak işleme eklemektir. Tlist.exe kullanarak işlem kimliğini belirleyebilirsiniz. Tlist. exe ' yi edinmek için, Windows için hata ayıklama araçları 'nı indirip yükleyin [ve ardından, WDK ve WinDbg indirmelerinde](https://go.microsoft.com/fwlink/?LinkId=168279)kullanılabilir.

## <a name="BKMK_Scenarios"></a>Ortak hata ayıklama senaryoları

**Işleme İliştir** ve ne tür bir işleme kullanacağınızı belirlemenize yardımcı olmak için, burada yaygın olarak karşılaşılan birkaç hata ayıklama senaryosu gösterilir (liste ayrıntılı değildir). Daha fazla yönerge kullanılabiliyorsa, bağlantılar sağlıyoruz.

Bazı uygulama türleri (örneğin, Windows Mağazası uygulamaları gibi) için doğrudan bir işlem adına iliştiremezsiniz, ancak bunun yerine **yüklü uygulama paketini hata ayıkla** menü seçeneğini kullanın (bkz. tablo).

> [!NOTE]
> Visual Studio 'da temel hata ayıklama hakkında daha fazla bilgi için bkz. [hata ayıklayıcıyla çalışmaya başlama](../debugger/getting-started-with-the-debugger.md).

|Senaryo|Hata ayıklama yöntemi|İşlem Adı|Notlar ve bağlantılar|
|-|-|-|-|
|Yerel makinede bir yönetilen veya yerel uygulamasında hata ayıklama|İşlemek veya [Standart hata ayıklamak](../debugger/getting-started-with-the-debugger.md) için İliştir kullanın|*appname*. exe|İletişim kutusuna hızlıca erişmek için **Ctrl + Alt + P** tuşlarını kullanın ve ardından işlem adının ilk harfini yazın.|
|Hata Ayıklayıcı olmadan uygulamayı başlattıktan sonra yerel makinede uygulamaları ASP.NET hata ayıklama|Kullanım iliştirme|iiexpress.exe|Bu yük uygulamanızı hale getirmek yardımcı olabilecek daha hızlı gibi (örneğin) profili oluşturulurken. |
|Uzaktan hata ayıklama ASP.NET 4 veya 4.5 üzerinde bir IIS sunucusu|Uzak Araçlar'ı kullanın ve işleme|w3wp.exe|Bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Uzaktan hata ayıklamayı ASP.NET Core IIS sunucusu|Uzak Araçlar'ı kullanın ve işleme|dnx.exe|Uygulama dağıtımı için bkz. [IIS 'de yayımlama](https://docs.asp.net/en/latest/publishing/iis.html). Hata ayıklama için bkz. uzak [IIS bilgisayarında uzaktan hata ayıklama ASP.net](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md)|
|Başka bir sunucu işlemi desteklenen uygulama türlerinde hata ayıklama|Uzak Araçlar (sunucu uzaktaysa) kullanın ve işleme|iexplore.exe veya diğer işlemler|Gerekirse, işlem belirlemenize yardımcı olması için Görev Yöneticisi'ni kullanın. Bu konunun [Uzaktan hata ayıklama](../debugger/remote-debugging.md) ve üzeri bölümlerine bakın|
|Uzaktan hata ayıklama bir Windows masaüstü uygulaması|Uzak Araçlar ve F5|YOK| Bkz. [Uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Uzaktan hata ayıklama, bir Windows Evrensel (UWP), OneCore, HoloLens ve IOT uygulaması|Yüklenen uygulama paketinin hatalarını ayıklama|YOK|**Hata ayıklama/diğer hata ayıklama hedeflerini kullan/** **Işleme Iliştir** yerine yüklü uygulama paketini Ayıkla|
|Visual Studio'dan başlatmamış bir Windows Evrensel (UWP), OneCore, HoloLens ve IOT uygulamasında hata ayıklama|Yüklenen uygulama paketinin hatalarını ayıklama|YOK|**Hata ayıklama/diğer hata ayıklama hedeflerini kullan/** **Işleme Iliştir** yerine yüklü uygulama paketini Ayıkla|

> [!WARNING]
> JavaScript'te yazılmış bir Windows Evrensel uygulaması iliştirmek için önce uygulama için hata ayıklamayı etkinleştirmeniz gerekir. Bkz. Windows Geliştirme Merkezi 'nde [hata ayıklayıcıyı iliştirme](../debugger/start-a-debugging-session-for-store-apps-in-visual-studio-javascript.md#BKMK_Attach_the_debugger) .

> [!NOTE]
> Hata ayıklayıcının ' de C++yazılan koda eklemesi için, kodun `DebuggableAttribute`yayması gerekir. [/ASSEMBLYDEBUG](https://msdn.microsoft.com/library/94443af3-470c-41d7-83a0-7434563d7982) bağlayıcı seçeneğiyle bağlantı kurarak bunu kodunuza otomatik olarak ekleyebilirsiniz.

## <a name="what-debugger-features-can-i-use"></a>Hangi hata ayıklayıcısı özellikleri kullanabilir miyim?

Bir işleme eklenirken Visual Studio hata ayıklayıcının (kesme noktaları gibi) tam özelliklerini kullanmak için, yürütülebilir dosya yerel kaynak ve sembollerle tam olarak eşleşmelidir (yani, hata ayıklayıcı doğru [sembol (. pbd) dosyalarını](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)yükleyebilmelidir). Varsayılan olarak, bu hata ayıklama derlemesi gerektirir.

Uzaktan hata ayıklama senaryoları için Visual Studio'da açık kaynak kodu (veya kaynak kodu bir kopyasını) sahip olmalıdır. Derlenmiş uygulama ikili dosyalarını uzak makinede gibi yerel makinede aynı derlemeden gelmelidir.

Uygulamayı doğru sembol dosyaları varsa bazı yerel hata ayıklama senaryolarında, Visual Studio'da kaynağına erişimi olmayan hata ayıklaması yapabilirsiniz (varsayılan olarak, bu, hata ayıklama derlemesi'gerektirir). Daha fazla bilgi için bkz. [sembol ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="BKMK_Troubleshoot_attach_errors"></a>İliştirme hatalarını giderme
 Çalışan bir işleme hata ayıklayıcı ekler, işlemi bir veya daha fazla kod türlerini içerebilir. Hata ayıklayıcının iliştirebilecek kod türleri **kod türü seç** iletişim kutusunda görüntülenir ve seçilir.

 Bazen, hata ayıklayıcı başarıyla bir kod türüne, ancak başka bir kod türüne ekleyebilirsiniz. Uzak bir bilgisayarda çalışan bir işlem eklemeye çalışıyorsanız, bu durum oluşabilir. Uzak bilgisayarda uzaktan hata ayıklama bileşenleri belirli kod türleri için kullanılabilir ancak diğerleri yüklü olabilir. Doğrudan veritabanı hata ayıklamaya iki veya daha fazla işlem eklemeye çalışırsanız da meydana gelebilir. SQL hata ayıklama için yalnızca tek bir işlem eklemeyi destekler.

 Hata ayıklayıcı, ancak bazı değil tüm kod türlerine eklenebiliyorsa, hangi türlerin eklenemediğini tanımlayan bir ileti görürsünüz.

 Hata ayıklayıcı en az bir kod türüne başarıyla ekleniyorsa işlemin hatalarını ayıklamaya devam edebilirsiniz. Sadece başarıyla eklenen kod türlerinde hata ayıklama mümkün olacaktır. Yukarıdaki örnek ileti, komut dosyası kodu türü eklemenin başarısız olduğunu gösterir. Bu nedenle, işlem içinde komut satırı kodunda hata ayıklamanız mümkün olmaz. İşlemdeki komut dosyası kodu hala çalışır, ancak kesme noktaları ayarlayın, veri görüntüleyemez veya komut dosyasında başka hata ayıklama işlemleri gerçekleştirmek mümkün olmaz.

 Hata ayıklayıcının bir kod türünü başarısız olma nedenine ilişkin daha ayrıntılı bilgi isterseniz, yalnızca bu kod türüne yeniden deneyebilirsiniz.

 **Kod türünün neden iliştirilemedi hakkında belirli bilgiler elde etmek için**

1. İşlemden ayırın. **Hata Ayıkla** menüsünde **Tümünü Ayır**' a tıklayın.

2. Yalnızca tek bir kod türü seçerek işleme yeniden bağlayın.

   1. **Işleme İliştir** iletişim kutusunda, **kullanılabilir işlemler** listesinde işlemi seçin.

   2. **Seç**' e tıklayın.

   3. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerinin** ve Iliştirilemedi kod türünün hatalarını ayıkla ' yı seçin. Diğer kodları temizleyin.

   4. **Tamam**'a tıklayın. **Kod türünü seç** iletişim kutusu kapanır.

   5. **Işleme İliştir** Iletişim kutusunda **İliştir**' e tıklayın.

      Bu kez, iliştirme tümüyle başarısız olur ve belirli bir hata iletisi alırsınız.

## <a name="see-also"></a>Ayrıca Bkz.
 [Birden çok Işlemi hata ayıklama](../debugger/debug-multiple-processes.md) [hata ayıklama](../debugger/just-in-time-debugging-in-visual-studio.md) [Uzaktan hata](../debugger/remote-debugging.md) ayıklama
