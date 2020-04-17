---
title: Azure bulut hizmetiveya sanal makine hata ayıklama
description: Visual Studio'da Bulut Hizmeti veya Sanal Makine Hata Ayıklama
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: 2536a56f76a048cab6a3bf9a5ec026d22fe112a7
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489746"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Visual Studio'da Azure bulut hizmeti veya sanal makine hata ayıklama

Visual Studio, Azure bulut hizmetlerini ve sanal makineleri hata ayıklama nız için farklı seçenekler sunar.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Yerel bilgisayarınızdaki bulut hizmetinizi hata ayıklama

Bulut hizmetinizi yerel bir makinede hata ayıklamak için Azure hesaplama emülatörü kullanarak zamandan ve paradan tasarruf edebilirsiniz. Bir hizmeti dağıtmadan önce yerel olarak hata ayıklayarak, işlem süresi için ödeme yapmadan güvenilirliği ve performansı artırabilirsiniz. Ancak, bazı hatalar yalnızca Azure'da bir bulut hizmeti çalıştırdığınızda oluşabilir. Hizmetinizi yayımladığınızda uzaktan hata ayıklamayı etkinleştirip hata ayıklamayı bir rol örneğine bağlarsanız bu hataları ayıklayabilirsiniz.

Emülatör Azure İşlem hizmetini simüle eder ve bulut hizmetinizi dağıtmadan önce test edip hata ayıklamanız için yerel ortamınızda çalışır. Emülatör rol örneklerinizin yaşam döngüsünü işler ve yerel depolama gibi benzetimli kaynaklara erişim sağlar. Visual Studio'dan hizmetinizi ayıklama veya çalıştırdığınızda, emülatörotomatik olarak arka plan uygulaması olarak çalıştırır ve ardından hizmetinizi emülatöre dağıtır. Emülatör, yerel ortamda çalıştığında hizmetinizi görüntülemek için kullanabilirsiniz. Emülatörün tam sürümünü veya ekspres sürümünü çalıştırabilirsiniz. (Azure 2.3 ile başlayarak, emülatörün ekspres sürümü varsayılandır.) Bulut [Hizmetini Yerel Olarak Çalıştırmak ve Hata Ayıklamak için Emülatör Ekspresini Kullanma'ya](vs-azure-tools-emulator-express-debug-run.md)bakın.

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Yerel bilgisayarınızdaki bulut hizmetinizi hata ayıklamak için

1. Menü çubuğunda, Azure bulut hizmeti projenizi çalıştırmak için **Hata Ayıklama**, **Hata Ayıklama'yı başlat'ı** seçin. Alternatif olarak F5 tuşuna basabilirsiniz. İşlem Emülatörü'nün başladığına dair bir ileti görürsünüz. Emülatör başladığında, sistem tepsisi simgesi bunu onaylar.

    ![Sistem tepsisinde azure emülatörü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Bildirim alanındaki Azure simgesinin kısayol menüsünü açarak bilgi işlem emülatörü için kullanıcı arabirimini görüntüleyin ve ardından **Bilgi İşlem Emülatör Kullanıcı Arabirimi'ni göster'i**seçin.

    UI'nin sol bölmesi, şu anda işlem emülatöre dağıtılan hizmetleri ve her hizmetin çalıştırdığı rol örneklerini gösterir. Yaşam döngüsünü, günlüğe kaydetmeyi ve tanılama bilgilerini doğru bölmede görüntülemek için hizmeti veya rolleri seçebilirsiniz. Odağı, dahil edilmiş bir pencerenin üst kenar boşluğuna koyarsanız, sağ bölmeyi doldurmak için genişler.

3. **Hata Ayıklama** menüsündeki komutları seçerek ve kodunuzda kesme noktaları ayarlayarak uygulamada adım atın. Hata ayıklamadaki uygulamanın içinden geçerken, bölmeler uygulamanın geçerli durumuyla güncelleştirilir. Hata ayıklamayı durdurunca, uygulama dağıtımı silinir. Uygulamanız bir web rolü içeriyorsa ve Web tarayıcısını başlatmak için Başlangıç eylem özelliğini ayarladıysanız, Visual Studio web uygulamanızı tarayıcıda başlatır. Hizmet yapılandırmasındaki bir rolün örneklerinin sayısını değiştirirseniz, bu yeni rolü hata ayıklamak için bulut hizmetinizi durdurmanız ve sonra hata ayıklamayı yeniden başlatmanız gerekir.

    > [!NOTE]
    > Hizmetinizi çalıştırmayı veya hata ayıklamayı bıraktığınızda, yerel işlem emülatörü ve depolama emülatörü durdurulamaz. Bildirim alanından açıkça durdurmanız gerekir.

## <a name="debug-a-cloud-service-in-azure"></a>Azure’daki bulut hizmetinde hata ayıklama

Bir bulut hizmetini uzak bir makineden ayıklamak için, bulut hizmetinizi dağıtTığınızda bu işlevselliği açıkça etkinleştirmeniz gerekir, böylece gerekli hizmetler (örneğin msvsmon.exe) rol örneklerinizi çalıştıran sanal makinelere yüklenir. Hizmeti yayımladığınızda uzaktan hata ayıklamayı etkinleştirmediyseniz, uzaktan hata ayıklama etkinleştirilmiş şekilde hizmeti yeniden yayımlamanız gerekir.

Bir bulut hizmeti için uzaktan hata ayıklamayı etkinleştiriyorsanız, bozulmuş performans göstermez veya ek ücrete tabi değildir. Hizmeti kullanan istemciler olumsuz etkilenebileceğinden, bir üretim hizmetinde uzaktan hata ayıklama kullanmayın.

> [!NOTE]
> Visual Studio'dan bir bulut hizmeti yayımladığınızda, .NET Framework 4 veya .NET Framework 4.5'i hedefleyen bu hizmetteki tüm roller için **IntelliTrace'i** etkinleştirebilirsiniz. **IntelliTrace'i**kullanarak, geçmişte bir rol örneğinde meydana gelen olayları inceleyebilir ve o zamana ait bağlamı yeniden oluşturabilirsiniz. [IntelliTrace ve Visual Studio ile yayınlanan bir bulut hizmetini hata ayıklama ve](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) [IntelliTrace'i kullanma bölümüne](../debugger/intellitrace.md)bakın.

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Bulut hizmeti için uzaktan hata ayıklamayı etkinleştirmek için

1. Azure projesiiçin kısayol menüsünü açın ve ardından **Yayımla'yı**seçin.

2. **Hazırlama** ortamını ve **Hata Ayıklama** yapılandırmasını seçin.

    Bu sadece bir kılavuzdur. Test ortamlarınızı üretim ortamında çalıştırmayı tercih edebilirsiniz. Ancak, Üretim ortamında uzaktan hata ayıklama yı etkinleştiriseniz kullanıcıları olumsuz etkileyebilirsiniz. Sürüm yapılandırmasını seçebilirsiniz, ancak Hata Ayıklama yapılandırması hata ayıklamayı kolaylaştırır.

    ![Hata Ayıklama yapılandırmasını seçin](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Her zamanki adımları izleyin, ancak **Gelişmiş Ayarlar** sekmesindeki tüm roller için Uzaktan **Hata Ayıklama'yı Etkinleştir'i** seçin.

    ![Hata Ayıklama Yapılandırması](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Hata ayıklamayı Azure'daki bir bulut hizmetine eklemek için

1. Sunucu Gezgini'nde bulut hizmetinizin düğümunu genişletin.

2. Eklemek istediğiniz rol veya rol örneği için kısayol menüsünü açın ve ardından **Hata Ayıklayıcı'yı takın'ı**seçin.

    Bir rolü hata ayıklama ederseniz, Visual Studio hata ayıklama bu rolün her örneğine bağlanır. Hata ayıklayıcı, bu kod satırını çalıştıran ve bu kesme noktasının tüm koşullarını karşılayan ilk rol örneği için bir kesme noktası üzerinde kırılır. Bir örneği hata ayıklama ederseniz, hata ayıklayıcı yalnızca bu örne bağlanır ve yalnızca belirli bir örnek bu kod satırını çalıştırdığında ve kesme noktasının koşullarını karşıladığında kesme noktası üzerinde kırılır.

    ![Hata Ayıklama tak](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Hata ayıklama bir örne bağlandıktan sonra, her zamanki gibi hata ayıklama. Hata ayıklama, rolünüz için uygun ana bilgisayar işlemine otomatik olarak bağlanır. Rolün ne olduğuna bağlı olarak, hata ayıklayıcı w3wp.exe, WaWorkerHost.exe veya WaIISHost.exe bağlanır. Hata ayıklayıcının bağlı olduğu işlemi doğrulamak için Sunucu Gezgini'ndeki örnek düğümlerini genişletin. Azure işlemleri hakkında daha fazla bilgi için [Azure Rol Mimarisi'ne](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) bakın.

    ![Kod türü iletişim kutusunu seçin](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Hata ayıklamanın bağlı olduğu işlemleri tanımlamak için, Hata Ayıklama, Windows, İşlemler'i seçerek menü çubuğunda İşlemler iletişim kutusunu açın. (Klavye: Ctrl+Alt+Z) Belirli bir işlemi ayırmak için kısayol menüsünü açın ve ardından **İşlemi Ayırma'yı**seçin. Veya Sunucu Gezgini'ndeki örnek düğümünü bulun, işlemi bulun, kısayol menüsünü açın ve ardından **İşlemi Ayır'ı**seçin.

    ![Hata Ayıklama İşlemleri](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Uzaktan hata ayıklama sırasında kesme noktalarında uzun duraklardan kaçının. Azure, birkaç dakikadan uzun süre durdurulan bir işlemi yanıt vermiyormuş gibi davranır ve bu örne trafik göndermeyi durdurur. Eğer çok uzun süre durursanız, msvsmon.exe işlemden ayrılır.

Hata ayıklayıcıyı örneğinizdeki veya rolünüzdeki tüm işlemlerden ayırmak için hata ayıklama yıktığınız rol veya örnek için kısayol menüsünü açın ve ardından **Detach Debugger'ı**seçin.

## <a name="limitations-of-remote-debugging-in-azure"></a>Azure'da uzaktan hata ayıklama sınırlamaları

Azure SDK 2.3'ten uzaktan hata ayıklamanın aşağıdaki sınırlamaları vardır:

* Uzaktan hata ayıklama etkinken, herhangi bir rolün 25'ten fazla örneği olan bir bulut hizmeti yayımlayamazsınız.
* Hata ayıklama 30400-30424, 31400-31424 ve 32400-32424 bağlantı noktalarını kullanır. Bu bağlantı noktalarından herhangi birini kullanmaya çalışırsanız, hizmetinizi yayımlayamazsınız ve Azure etkinlik günlüğünde aşağıdaki hata iletilerinden biri görünür:

  * .cscfg dosyasına karşı .cscfg dosyasını doğrulama hatası.
    Son nokta Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector rolü 'rol' için ayrılmış bağlantı noktası aralığı 'aralığı' zaten tanımlanmış bir bağlantı noktası veya aralığı ile çakışıyor.
  * Ayırma başarısız oldu. Lütfen daha sonra yeniden deneyin, VM boyutunu veya rol örneklerinin sayısını azaltmayı deneyin veya farklı bir bölgeye dağıtmayı deneyin.

## <a name="debugging-azure-virtual-machines"></a>Azure sanal makinelerin hata ayıklama

Visual Studio'da Server Explorer'ı kullanarak Azure sanal makinelerinde çalışan programları hata ayıklayabilirsiniz. Azure sanal makinede uzaktan hata ayıklamayı etkinleştirdiğinizde, Azure uzaktan hata ayıklama uzantısını sanal makineye yükler. Ardından, sanal makinedeki işlemlere ekleyebilir ve normalde yaptığınız gibi hata ayıklama yapabilirsiniz.

> [!NOTE]
> Azure kaynak yöneticisi yığını üzerinden oluşturulan sanal makineler Visual Studio 2015'te Cloud Explorer kullanılarak uzaktan debuğa alınabilir. Daha fazla bilgi için bkz: [Bulut Gezgini ile Azure Kaynaklarını Yönetme.](vs-azure-tools-resources-managing-with-cloud-explorer.md)

### <a name="to-debug-an-azure-virtual-machine"></a>Azure sanal makinesini hata ayıklamak için

1. Sunucu Gezgini'nde, Sanal Makineler düğümünü genişletin ve hata ayıklamak istediğiniz sanal makinenin düğümünü seçin.

2. Bağlam menüsünü açın ve **Hata Ayıklama'yı etkinleştir'i**seçin. Sanal makinede hata ayıklamayı etkinleştirmek isteyip istemediğiniz sorulduğunda **Evet'i**seçin.

    Azure, hata ayıklamayı etkinleştirmek için sanal makineye uzaktan hata ayıklama uzantısı yükler.

    ![Sanal makine hata ayıklama komutunu etkinleştirme](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Uzaktan hata ayıklama uzantısı yüklemeyi bitirdikten sonra, sanal makinenin bağlam menüsünü açın ve **Hata Ayıklama Ekle'yi seçin...**

    Azure, sanal makinedeki işlemlerin bir listesini alır ve bunları İşleme Ekle iletişim kutusunda gösterir.

    ![Hata ayıklama komutunu ekleme](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. **İşleme Ekle** iletişim kutusunda, yalnızca hata ayıklamak istediğiniz kod türlerini göstermek için sonuç listesini sınırlamak için **Seç'i** seçin'i seçin. 32 bit veya 64-bit yönetilen kod, yerel kod veya her ikisini birden hata ayıklayabilirsiniz.

    ![Kod türü iletişim kutusunu seçin](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Sanal makinede hata ayıklamak istediğiniz işlemleri seçin ve sonra **Ekle'yi**seçin. Örneğin, sanal makinede bir web uygulamasını hata ayıklamak istiyorsanız w3wp.exe işlemini seçebilirsiniz. Daha fazla bilgi için Visual Studio ve [Azure Rol Mimarisinde](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) [Hata Ayıklama Bir veya Daha Fazla İşleme](https://msdn.microsoft.com/library/jj919165.aspx) bakın.

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Hata ayıklama için bir web projesi ve sanal bir makine oluşturun

Azure projenizi yayımlamadan önce, hata ayıklama ve test senaryolarını destekleyen ve test ve izleme programlarını yükleyebileceğiniz bir ortamda test etmeyi yararlı bulabilirsiniz. Bu tür testleri çalıştırmanın bir yolu, uygulamanızı sanal bir makinede uzaktan hata ayıklamaktır.

Visual Studio ASP.NET projeleri, uygulama testi için kullanabileceğiniz kullanışlı bir sanal makine oluşturma seçeneği sunar. Sanal makine PowerShell, Uzak Masaüstü ve WebDeploy gibi yaygın olarak gereken uç noktaları içerir.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Bir web projesi ve hata ayıklama için sanal bir makine oluşturmak için

1. Visual Studio'da yeni bir web uygulaması ASP.NET oluşturun.

2. Yeni ASP.NET Projesi iletişim kutusunda, Azure bölümünde açılan liste kutusunda **Sanal Makine'yi** seçin. Uzak **kaynakları oluştur** onay kutusunu seçili bırakın. Devam etmek için **Tamam'ı** seçin.

    Azure iletişim kutusunda **sanal makine oluştur** görüntülenir.

    ![ASP.NET web projesi iletişim kutusu oluşturma](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Oturum açmamışsanız Azure hesabınızda oturum açmanız istenir.

3. Sanal makine için çeşitli ayarları seçin ve sonra **Tamam'ı**seçin. Daha fazla bilgi için [Sanal Makineler'e](/azure/virtual-machines/) bakın.

    DNS adı için girdiğiniz ad, sanal makinenin adı olacaktır.

    ![Azure iletişim kutusunda sanal makine oluşturma](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure sanal makineyi oluşturur ve ardından Uzak Masaüstü ve Web Dağıtımı gibi uç noktaları hükümler ve yapılandırmalar

4. Sanal makine tamamen yapılandırıldıktan sonra, Sunucu Gezgini'nde sanal makinenin düğümünü seçin.

5. Bağlam menüsünü açın ve **Hata Ayıklama'yı etkinleştir'i**seçin. Sanal makinede hata ayıklamayı etkinleştirmek isteyip istemediğiniz sorulduğunda **Evet'i**seçin.

    Azure, hata ayıklamayı etkinleştirmek için uzaktan hata ayıklama uzantısını sanal makineye yükler.

    ![Sanal makine hata ayıklama komutunu etkinleştirme](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Projenizi Nasıl Ana Hatlarıyla [Yayınla: Visual Studio'da Tek Tıklamayla Yayınla'yı Kullanarak Bir Web Projesini Dağıtın.](https://msdn.microsoft.com/library/dd465337.aspx) Sanal makinede hata ayıklamak istediğiniziçin, **Web Yayımla** sihirbazının **Ayarlar** sayfasında yapılandırma olarak **Hata Ayıklama'yı** seçin. Bu, hata ayıklama sırasında kod simgelerinin kullanılabilir olmasını sağlar.

    ![Yayımlama ayarları](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. Dosya **Yayımlama**Seçenekleri'nde, proje daha önceki bir zamanda zaten dağıtıldıysa, **hedefteki ek dosyaları kaldır'ı** seçin.

8. Proje yayımladıktan sonra, Sunucu Gezgini'ndeki sanal makinenin bağlam menüsünde **Hata Ayıklama Ekle'yi seçin...**

    Azure, sanal makinedeki işlemlerin bir listesini alır ve bunları İşleme Ekle iletişim kutusunda gösterir.

    ![Hata ayıklama komutunu ekleme](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. **İşleme Ekle** iletişim kutusunda, yalnızca hata ayıklamak istediğiniz kod türlerini göstermek için sonuç listesini sınırlamak için **Seç'i** seçin'i seçin. 32 bit veya 64-bit yönetilen kod, yerel kod veya her ikisini birden hata ayıklayabilirsiniz.

    ![Kod türü iletişim kutusunu seçin](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Sanal makinede hata ayıklamak istediğiniz işlemleri seçin ve sonra **Ekle'yi**seçin. Örneğin, sanal makinede bir web uygulamasını hata ayıklamak istiyorsanız w3wp.exe işlemini seçebilirsiniz. Daha fazla bilgi için [Visual Studio'da Hata Ayıklama Bir veya Daha Fazla İşleme](https://msdn.microsoft.com/library/jj919165.aspx) bakın.

## <a name="next-steps"></a>Sonraki adımlar

* Bir sürüm sunucusundan aramaların ve olayların günlüğünü toplamak için **IntelliTrace'i** kullanın. [IntelliTrace ve Visual Studio ile Yayınlanan Bulut Hizmetini Hata Ayıklama'ya](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md)bakın.

* Rollerin geliştirme ortamında veya Azure'da çalışıp çalışmadığı, roller içinde çalışan kodlardan ayrıntılı bilgileri günlüğe kaydetmek için **Azure Diagnostics'i** kullanın. Bkz. [Azure Tanılama'yı kullanarak günlük verilerini toplama.](/azure/cloud-services/cloud-services-dotnet-diagnostics)
