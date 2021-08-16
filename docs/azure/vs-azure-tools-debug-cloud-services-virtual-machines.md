---
title: Azure bulut hizmetinde veya sanal makinede hata ayıklama
description: Visual Studio'de Bulut Hizmeti veya Sanal Makinede Hata Ayıklama
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: aeaa6bf6230833a350fb2fe8d55178d6c838a5f1d014a5dcdbe959daf6d01838
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121364179"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Azure bulut hizmetinde veya sanal makinede hata ayıklama Visual Studio

Visual Studio Azure bulut hizmetleri ve sanal makinelerde hata ayıklamak için farklı seçenekler sunar.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Yerel bilgisayarınızda bulut hizmetinizin hata ayıklaması

Yerel makinede bulut hizmetinizin hata ayıklaması için Azure İşlem Emulator kullanarak zamandan ve paradan tasarruf edin. Hizmeti dağıtmadan önce yerel olarak hata ayıklarken, işlem süresi için ödeme yapmadan güvenilirliği ve performansı geliştirebilirsiniz. Ancak bazı hatalar yalnızca Azure'da bir bulut hizmeti çalıştırarak ortaya çıkabilir. Hizmetinizi yayımlarken uzaktan hata ayıklamayı etkinleştirir ve ardından hata ayıklayıcıyı bir rol örneğine iliştirersiniz.

Öykünücü, Azure İşlem hizmetinin benzetimini sağlar ve dağıtmadan önce bulut hizmetinizi test etmek ve hata ayıklamak için yerel ortamınız içinde çalışır. Öykünücü rol örneklerinizin yaşam döngüsünü ele almaktadır ve yerel depolama gibi sanal kaynaklara erişim sağlar. Hata ayıklar veya hizmetinizi Visual Studio, öykünücü otomatik olarak bir arka plan uygulaması olarak başlatır ve ardından hizmetinizi öykünücüye dağıtır. Hizmetinizi yerel ortamda çalıştırarak görüntülemek için öykünücüsü kullanabilirsiniz. Öykünücüsünün tam sürümünü veya hızlı sürümünü çalıştırarak. (Azure 2.3'den başlayarak öykünücüsünün hızlı sürümü varsayılandır.) Bkz. Emulator Hizmeti Yerel Olarak Çalıştırmak ve Hata Ayıklamak için [Express Kullanma.](vs-azure-tools-emulator-express-debug-run.md)

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Yerel bilgisayarınızda bulut hizmetinizin hata ayıklaması için

1. Menü çubuğunda Hata Ayıklama Hata **AyıklamaYı**  >  **Başlat'ı seçerek** Azure bulut hizmeti projenizi çalıştırın. Alternatif olarak, F5 tuşuna basarak da basın. İşlem oluşturmanın başlat olduğunu Emulator alırsınız. Öykünücü başlatıldığında sistem tepsisi simgesi bunu onaylar.

    ![Sistem tepsisinde Azure öykünücüsü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Bildirim alanında Azure simgesinin kısayol menüsünü açarak işlem öykünücüsü için kullanıcı arabirimini görüntüler ve ardından kullanıcı arabiriminde İşlem **göster'Emulator seçin.**

    Kullanıcı arabiriminin sol bölmesinde, şu anda işlem öykünücüsünü dağıtan hizmetler ve her hizmetin çalıştırılan rol örnekleri gösterilir. Yaşam döngüsü, günlüğe kaydetme ve tanılama bilgilerini sağ bölmede görüntülemek için hizmeti veya rolleri seçebilirsiniz. Odağı dahil edilen bir pencerenin üst kenar boşluğuna koyarak sağ bölmeyi dolduracak şekilde genişler.

3. Hata Ayıkla menüsündeki komutları seçerek **ve kodunda** kesme noktaları ayarerek uygulamada adım adım inin. Hata ayıklayıcıda uygulamada adım adım ilerlediğinde, bölmeler uygulamanın geçerli durumuyla güncelleştirilir. Hata ayıklamayı durdurarak uygulama dağıtımı silinir. Uygulamanız bir web rolü içerirse ve Başlangıç eylemi özelliğini web tarayıcısını başlatmak için Visual Studio web uygulamasını tarayıcıda başlatır. Hizmet yapılandırmasında rol örneklerinin sayısını değiştirirsanız, rolün bu yeni örneklerde hata ayıklaması için bulut hizmetinizi durdurmanız ve ardından hata ayıklamayı yeniden başlatmanız gerekir.

    > [!NOTE]
    > Hizmetinizi çalıştırmayı veya hata ayıklamayı durdurarak yerel işlem öykünücüsü ve depolama öykünücüsü durdurulamaz. Bunları bildirim alanında açıkça durdurmalısınız.

## <a name="debug-a-cloud-service-in-azure"></a>Azure’daki bulut hizmetinde hata ayıklama

Uzak makineden bir bulut hizmetinin hata ayıklaması yapmak için, gerekli hizmetlerin (örneğin, msvsmon.exe) rol örneklerinizi çalıştıran sanal makinelere yüklensin diye bulut hizmetinizi dağıtırken bu işlevi açıkça etkinleştirmeniz gerekir. Hizmeti yayımlarken uzaktan hata ayıklamayı etkinleştirmediyseniz, uzaktan hata ayıklama etkinleştirildiğinde hizmeti yeniden yayımlamak gerekir.

Bir bulut hizmeti için uzaktan hata ayıklamayı etkinleştirirsanız, performans düşük olmaz veya ek ücret uygulanmaz. Bir üretim hizmetinde uzaktan hata ayıklamayı kullanmayın çünkü hizmeti kullanan istemciler olumsuz etkilenebilir.

> [!NOTE]
> Visual Studio'dan bir bulut hizmeti yayımlarken, bu hizmette .NET Framework 4 veya .NET Framework 4.5'i hedef alan roller için **IntelliTrace'i** etkinleştirabilirsiniz. **IntelliTrace kullanarak,** geçmişte bir rol örneğinde meydana gelen olayları inceler ve o zaman bağlamı yeniden üretin. Bkz. [IntelliTrace ve Visual Studio](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) ile yayımlanmış bir bulut hizmetinde hata ayıklama ve [IntelliTrace kullanma.](../debugger/intellitrace.md)

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Bulut hizmeti için uzaktan hata ayıklamayı etkinleştirmek için

1. Azure projesinin kısayol menüsünü açın ve Yayımla'yı **seçin.**

2. Hazırlama **ortamını ve** Hata ayıklama **yapılandırmasını** seçin.

    Bu yalnızca bir kılavuzdur. Test ortamlarınızı üretim ortamında çalıştırmayı tercih edersiniz. Ancak Üretim ortamında uzaktan hata ayıklamayı etkinleştirirsanız kullanıcıları olumsuz etkileyebilirsiniz. Yayın yapılandırmasını seçebilirsiniz, ancak Hata ayıklama yapılandırması hata ayıklamayı kolaylaştırır.

    ![Hata ayıklama yapılandırmasını seçin](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Normal adımları izleyin, ancak Gelişmiş Hata Ayıklayıcı **sekmesindeki** Tüm roller için Uzaktan Hata Ayıklayıcıyı Etkinleştir **onay Ayarlar** seçin.

    ![Hata Ayıklama Yapılandırması](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Hata ayıklayıcıyı Azure'daki bir bulut hizmetine eklemek için

1. Bu Sunucu Gezgini, bulut hizmetinizin düğümünü genişletin.

2. Eklemek istediğiniz rol veya rol örneğinin kısayol menüsünü açın ve Ardından Hata Ayıklayıcıyı **Ekle'yi seçin.**

    Bir rolde hata ayıklarsanız, Visual Studio hata ayıklayıcısı bu rolün her örneğine iliştirer. Hata ayıklayıcı, bu kod satırı çalıştıran ve bu kesme noktası koşullarını karşılar ilk rol örneği için bir kesme noktası üzerinde kesme noktası olur. Bir örnekte hata ayıklarsanız, hata ayıklayıcı yalnızca bu örneği iliştirer ve kesme noktası üzerinde yalnızca ilgili örnek bu kod satırı çalıştırılıyorsa ve kesme noktası koşullarını karşılarsa kesme noktası üzerinde sonlanır.

    ![Hata Ayıklayıcı ekleme](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Hata ayıklayıcı bir örneğine iliştirdikten sonra her zamanki gibi hata ayıklar. Hata ayıklayıcı, rolünüz için uygun konak işlemini otomatik olarak iliştirer. Rolün ne olduğu bağlı olarak, hata ayıklayıcı w3wp.exe, WaWorkerHost.exe veya WaIISHost.exe. Hata ayıklayıcının ekli olduğu işlemi doğrulamak için, hata ayıklayıcısında örnek Sunucu Gezgini. [Azure işlemleri hakkında daha fazla](/archive/blogs/kwill/windows-azure-role-architecture) bilgi için bkz. Azure Rol Mimarisi.

    ![Kod türü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Hata ayıklayıcının ekli olduğu işlemleri belirlemek için menü çubuğunda İşlemler'de hata  >    >  **Windows'ı** seçin ve **İşlemler iletişim** kutusunu açın. (Klavye: Ctrl+Alt+Z) Belirli bir işlemi ayırmak için kısayol menüsünü açın ve İşlemleri **Ayır'ı seçin.** Veya örnek düğümünü uygulamanın Sunucu Gezgini, işlemi bulun, kısayol menüsünü açın ve ardından işlemi **ayır'ı seçin.**

    ![Hata Ayıklama İşlemleri](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Uzaktan hata ayıklama sırasında kesme noktalarında uzun duraklardan kaçının. Azure, birkaç dakikadan uzun süre durdurulan bir işlemi yanıt vermemeye alır ve bu örnek için trafik göndermeyi durdurur. Çok uzun süre durursanız msvsmon.exe ayırır.

Hata ayıklayıcıyı örneğinizin veya rolünüzle ilgili tüm işlemlerden ayırmak için, hata ayıklarken rol veya örneğin kısayol menüsünü açın ve Hata Ayıklayıcıyı **Ayır'ı seçin.**

## <a name="limitations-of-remote-debugging-in-azure"></a>Azure'da uzaktan hata ayıklama sınırlamaları

Azure SDK 2.3'te uzaktan hata ayıklama aşağıdaki sınırlamalara sahiptir:

* Uzaktan hata ayıklama etkinleştirildiğinde, herhangi bir rolün 25'den fazla örneğin olduğu bir bulut hizmetini yayımlayamzın.
* Hata ayıklayıcısı 30400 ile 30424, 31400 - 31424 ve 32400 ile 32424 arasında bağlantı noktalarını kullanır. Bu bağlantı noktalarından herhangi birini kullanmayı denersanız hizmetinizi yayımamazsınız ve Azure için etkinlik günlüğünde aşağıdaki hata iletilerinden biri görüntülenir:

  * .cscfg dosyasını .csdef dosyasıyla doğrulama hatası.
    'role' rolünün Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector uç noktası için ayrılmış bağlantı noktası aralığı 'range' zaten tanımlanmış bir bağlantı noktası veya aralık ile çakışıyor.
  * Ayırma başarısız oldu. Lütfen daha sonra yeniden deneyin, VM boyutunu veya rol örneği sayısını azaltmayı deneyin veya farklı bir bölgeye dağıtmayı deneyin.

## <a name="debugging-azure-virtual-machines"></a>Azure sanal makinelerde hata ayıklama

Azure sanal makinelerde çalıştıran programlarda hata ayıklamak için Sunucu Gezgini Visual Studio. Azure sanal makinesi üzerinde uzaktan hata ayıklamayı etkinleştirerek sanal makineye uzaktan hata ayıklama uzantısını yükleyebilirsiniz. Ardından, sanal makinede işlemlere iliştirin ve normalde olduğu gibi hata ayıklarsanız.

> [!NOTE]
> Azure Resource Manager yığını aracılığıyla oluşturulan sanal makineler, 2015'te Cloud Explorer kullanılarak Visual Studio ayıklanır. Daha fazla bilgi için [bkz. Cloud Explorer ile Azure Kaynaklarını Yönetme.](vs-azure-tools-resources-managing-with-cloud-explorer.md)

### <a name="to-debug-an-azure-virtual-machine"></a>Azure sanal makinede hata ayıklamak için

1. Bu Sunucu Gezgini Sanal Makineler düğümünü genişletin ve hata ayıklamak istediğiniz sanal makinenin düğümünü seçin.

2. Bağlam menüsünü açın ve Hata Ayıklamayı **Etkinleştir'i seçin.** Sanal makinede hata ayıklamayı etkinleştirmek istediğinizden emin olup değilken Evet'i **seçin.**

    Azure, hata ayıklamayı etkinleştirmek için sanal makineye uzaktan hata ayıklama uzantısını yüklür.

    ![Sanal makine hata ayıklamayı etkinleştir komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Uzaktan hata ayıklama uzantısının yüklemesi tamam olduktan sonra sanal makinenin bağlam menüsünü açın ve Hata Ayıklayıcı **ekle... öğesini seçin.**

    Azure, sanal makinede işlemlerin listesini alır ve bunları İşleme Ekle **iletişim kutusunda** gösterir.

    ![Hata ayıklayıcı ekle komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. İşleme **Ekle iletişim kutusunda,** sonuçlar listesini **yalnızca hata** ayıklamak istediğiniz kod türlerini gösterecek şekilde sınırlamak için Seç'i seçin. 32 bit veya 64 bit yönetilen kodda, yerel kodda veya her ikisinde de hata ayıkabilirsiniz.

    ![Kod türü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Sanal makinede hata ayıklamak istediğiniz işlemleri seçin ve ardından Ekle'yi **seçin.** Örneğin, sanal makinede bir web w3wp.exe hata ayıklamak istediyebilirsiniz. Daha [fazla bilgi için bkz.](../debugger/debug-multiple-processes.md) Visual Studio ve Azure Rol [Mimarisinde Bir veya Daha Fazla](/archive/blogs/kwill/windows-azure-role-architecture) İşlemde Hata Ayıklama.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Hata ayıklama için web projesi ve sanal makine oluşturma

Azure projenizi yayımlamadan önce, hata ayıklama ve test senaryolarını destekleyen ve test ve izleme programlarını yükleyip yükleyip yüklemeyilen bir ortamda test etmek yararlı olabilir. Bu tür testleri çalıştırmanın bir yolu, sanal makinede uygulama hata ayıklamayı uzaktan yapmaktır.

Visual Studio ASP.NET projeleri, uygulama testi için kullanabileceğiniz kullanışlı bir sanal makine oluşturma seçeneği sağlar. Sanal makine PowerShell, Uzak Masaüstü ve WebDeploy gibi yaygın olarak gereken uç noktaları içerir.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Hata ayıklama için bir web projesi ve sanal makine oluşturmak için

1. Bu Visual Studio Web Uygulaması için yeni ASP.NET oluşturun.

2. Yeni ASP.NET Project iletişim kutusundaki Azure bölümünde, açılan **liste kutusunda** Sanal Makine'yi seçin. Uzak kaynaklar **oluştur onay kutusunu** seçili bırakın. Devam etmek **için Tamam'ı** seçin.

    **Azure'da sanal makine oluştur** iletişim kutusu görüntülenir.

    ![Web ASP.NET oluştur iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Henüz oturum açmadıysanız Azure hesabınızla oturum açmanız istener.

3. Sanal makine için çeşitli ayarları seçin ve ardından Tamam'ı **seçin.** Daha [fazla bilgi için](/azure/virtual-machines/) bkz. Sanal Makineler.

    DNS adı için girersiniz ad, sanal makinenin adıdır.

    ![Azure'da sanal makine oluştur iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure sanal makineyi oluşturur, ardından Uzak Masaüstü ve Sanal Makine Gibi uç noktaları sağlar ve Web Dağıtımı.

4. Sanal makine tam olarak yapılandırıldığında, sanal makinenin düğümünü Sunucu Gezgini.

5. Bağlam menüsünü açın ve Hata Ayıklamayı **Etkinleştir'i seçin.** Sanal makinede hata ayıklamayı etkinleştirmek istediğinizden emin olup değilken Evet'i **seçin.**

    Azure, hata ayıklamayı etkinleştirmek için sanal makineye uzaktan hata ayıklama uzantısını yüklür.

    ![Sanal makine hata ayıklamayı etkinleştir komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Projenizi nasıl yayımla: Web Uygulaması [Dağıtma Project One-Click'de Yayımlama Visual Studio.](/previous-versions/aspnet/dd465337(v=vs.110)) Sanal makinede hata ayıklamak istediğiniz için, **Web'Ayarlar Yayımla** sihirbazının Ayarlar sayfasında yapılandırma olarak **Hata Ayıkla'yı** seçin.  Bu, hata ayıklama sırasında kod sembollerinin kullanılabilir olduğundan emin olur.

    ![Yayımlama ayarları](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. Proje **daha önce dağıtılmışsa** Dosya **Yayımlama Seçenekleri'nde** Hedefte ek dosyaları kaldır'ı seçin.

8. Proje yayımlandıktan sonra, Sanal makinede yer alan sanal makinenin bağlam menüsünde Sunucu Gezgini **Ekle... öğesini seçin.**

    Azure, sanal makinede işlemlerin listesini alır ve bunları İşleme Ekle **iletişim kutusunda** gösterir.

    ![Hata ayıklayıcı ekle komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. İşleme **Ekle iletişim kutusunda,** sonuçlar listesini **yalnızca hata** ayıklamak istediğiniz kod türlerini gösterecek şekilde sınırlamak için Seç'i seçin. 32 bit veya 64 bit yönetilen kodda, yerel kodda veya her ikisinde de hata ayıkabilirsiniz.

    ![Kod türü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Sanal makinede hata ayıklamak istediğiniz işlemleri seçin ve ardından Ekle'yi **seçin.** Örneğin, sanal makinede bir web w3wp.exe hata ayıklamak istediyebilirsiniz. Daha [fazla bilgi için bkz.](../debugger/debug-multiple-processes.md) Bir veya daha Visual Studio İşlemde Hata Ayıklama.

## <a name="next-steps"></a>Sonraki adımlar

* **IntelliTrace'i** kullanarak bir yayın sunucusundan çağrı ve olay günlüğünü toplayın. Bkz. [IntelliTrace ve Visual Studio ile Yayımlanan Bulut Hizmetinde Hata Ayıklama.](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md)

* Rollerin **Azure Tanılama** veya Azure'da çalışan rollerde çalışan koddan ayrıntılı bilgileri günlüğe almak için Azure Tanılama'i kullanın. Bkz. [Azure Tanılama kullanarak günlük verileri toplama.](/azure/cloud-services/cloud-services-dotnet-diagnostics)
