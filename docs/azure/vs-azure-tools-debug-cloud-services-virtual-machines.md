---
title: Azure bulut hizmetinde veya sanal makinede hata ayıklama
description: Visual Studio bir bulut hizmetinde veya sanal makinede hata ayıklama
author: mikejo5000
manager: jmartens
ms.topic: how-to
ms.workload: azure-vs
ms.date: 1/24/2022
ms.author: mikejo
ms.technology: vs-ide-debug
ms.openlocfilehash: c507b8618f24eb76c6c7c3f2a75b85ac797efa35
ms.sourcegitcommit: 782992423db6e1cbbf206715c9b3b400c80052a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "138100975"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Visual Studio 'de Azure bulut hizmetinde veya sanal makinede hata ayıklama

Visual Studio, Azure cloud services ve sanal makinelerde hata ayıklama için kullanabileceğiniz farklı seçenekler sunar.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Yerel bilgisayarınızda bulut hizmetinizde hata ayıklayın

Azure işlem Emulator kullanarak, yerel bir makinedeki bulut hizmetinizde hata ayıklaması yapmak için zaman ve para tasarrufu yapabilirsiniz. Dağıtmadan önce bir hizmette yerel olarak hata ayıkladığında, işlem süresi için ödeme yapmadan güvenilirliği ve performansı artırabilirsiniz. Ancak bazı hatalar yalnızca Azure 'da bir bulut hizmeti çalıştırdığınızda gerçekleşebilir. Hizmetinizi yayımladığınızda uzaktan hata ayıklamayı etkinleştirirseniz ve ardından hata ayıklayıcıyı bir rol örneğine eklerseniz, bu hatalarda hata ayıklayabilirsiniz.

Öykünücü, Azure Işlem hizmetinin benzetimini yapar ve yerel ortamınızda çalışarak bulut hizmetinizi dağıtmadan önce test edebilir ve hata ayıklayabilirsiniz. Öykünücü, rol örneklerinizin yaşam döngüsünü işler ve yerel depolama gibi sanal kaynaklara erişim sağlar. Visual Studio bilgisayarınızdan hata ayıkladığınızda veya hizmetinizi çalıştırdığınızda, otomatik olarak öykünücü bir arka plan uygulaması olarak başlatılır ve sonra hizmetinizi öykünücüsüne dağıtır. Yerel ortamda çalıştırıldığında hizmetinizi görüntülemek için öykünücüsünü kullanabilirsiniz. Öykünücüsünün tam sürümünü veya Express sürümünü çalıştırabilirsiniz. (Azure 2,3 ' den itibaren, öykünücünün Express sürümü varsayılandır.) [bir bulut hizmetini yerel olarak çalıştırmak ve hata ayıklamak için Emulator Express kullanma](vs-azure-tools-emulator-express-debug-run.md)konusuna bakın.

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Yerel bilgisayarınızda bulut hizmetinizde hata ayıklamak için

1. Azure bulut hizmeti Projenizi çalıştırmak için menü çubuğunda **hata**  >  **ayıklamayı Başlat** ' ı seçin. Alternatif olarak F5 tuşuna basabilirsiniz. işlem Emulator başladığı bir ileti görürsünüz. Öykünücü başladığında, sistem tepsisi simgesi onu onaylar.

    ![Sistem tepsisinde Azure öykünücüsü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Bildirim alanında Azure simgesi için kısayol menüsünü açarak ve ardından **işlem Emulator Kullanıcı arabirimini göster**' i seçerek işlem öykünücüsünün Kullanıcı arabirimini görüntüleyin.

    Kullanıcı arabiriminin sol bölmesi, şu anda işlem öykünücüsüne ve her bir hizmetin çalıştığı rol örneklerine dağıtılan Hizmetleri gösterir. Sağ bölmedeki yaşam döngüsü, günlüğe kaydetme ve tanılama bilgilerini görüntüleyecek hizmeti veya rolleri seçebilirsiniz. Odağı eklenen pencerenin üst kenar boşluğuna yerleştirirseniz, sağ bölmeyi dolduracak şekilde genişler.

3. **Hata Ayıkla** menüsündeki komutları seçerek ve kodunuzda kesme noktaları ayarlayarak uygulamada ilerleyin. Hata ayıklayıcıda uygulamada ilerlerse, bölmeler uygulamanın geçerli durumuyla güncelleştirilir. Hata ayıklamayı durdurduğunuzda, uygulama dağıtımı silinir. uygulamanız bir web rolü içeriyorsa ve başlangıç eylemi özelliğini web tarayıcısını başlatacak şekilde ayarladıysanız, Visual Studio web uygulamanızı tarayıcıda başlatır. Hizmet yapılandırmasındaki bir rolün örnek sayısını değiştirirseniz, bulut hizmetinizi durdurmanız ve sonra rolün bu yeni örneklerine Hata ayıklayabilmeniz için hata ayıklamayı yeniden başlatmanız gerekir.

    > [!NOTE]
    > Çalıştırmayı veya hizmetinizi hata ayıklamayı durdurduğunuzda, yerel işlem öykünücüsü ve depolama öykünücüsü durdurulmaz. Bunları bildirim alanından açıkça durdurmanız gerekir.

## <a name="debug-a-cloud-service-in-azure"></a>Azure’daki bulut hizmetinde hata ayıklama

Bir bulut hizmetinde uzak bir makineden hata ayıklamak için, bulut hizmetinizi dağıtırken, rol örneklerinizi çalıştıran sanal makinelerde gerekli hizmetlerin (msvsmon.exe, örneğin) yüklü olması için bu işlevselliği açıkça etkinleştirmeniz gerekir. Hizmeti yayımladığınızda uzaktan hata ayıklamayı etkinleştirmezseniz, uzaktan hata ayıklama etkinken hizmeti yeniden yayımlamanız gerekir.

Bir bulut hizmeti için uzaktan hata ayıklamayı etkinleştirirseniz, performans düşebilir veya ek ücret uygulanır. Hizmeti kullanan istemciler olumsuz yönde etkilenmediğinden, bir üretim hizmetinde uzaktan hata ayıklama kullanmayın.

> [!NOTE]
> Visual Studio bir bulut hizmeti yayımladığınızda, söz konusu hizmette .NET Framework 4 veya .NET Framework 4,5 ' i hedefleyen tüm roller için **ıntellitrace** 'i etkinleştirebilirsiniz. **IntelliTrace** kullanarak, geçmişte bir rol örneğinde gerçekleşen olayları inceleyebilir ve bu zamandan bağlamı yeniden oluşturabilirsiniz. bkz. [ıntellitrace ve Visual Studio yayımlanmış bir bulut hizmetinde hata ayıklama](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md) ve [ıntellitrace kullanma](../debugger/intellitrace.md).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Bir bulut hizmeti için uzaktan hata ayıklamayı etkinleştirmek için

1. Azure projesi için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.

2. **Hazırlama** ortamını ve **hata ayıklama** yapılandırmasını seçin.

    Bu yalnızca bir kılavuz olur. Test ortamlarınızı bir üretim ortamında çalıştırmayı tercih edebilirsiniz. Ancak, üretim ortamında uzaktan hata ayıklamayı etkinleştirirseniz kullanıcıları olumsuz yönde etkileyebilirsiniz. Yayın yapılandırmasını seçebilirsiniz, ancak hata ayıklama yapılandırması hata ayıklamayı daha kolay hale getirir.

    ![Hata ayıklama yapılandırmasını seçin](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. olağan adımları izleyin, ancak **gelişmiş Ayarlar** sekmesindeki **tüm roller için uzaktan hata ayıklayıcıyı etkinleştir** onay kutusunu işaretleyin.

    ![Hata ayıklama yapılandırması](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Hata ayıklayıcıyı Azure 'daki bir bulut hizmetine eklemek için

1. Sunucu Gezgini, bulut hizmetinizin düğümünü genişletin.

2. Eklemek istediğiniz rol veya rol örneği için kısayol menüsünü açın ve ardından **hata ayıklayıcı Ekle**' yi seçin.

    bir rolde hata ayıklaması yaparsanız, Visual Studio hata ayıklayıcı bu rolün her örneğine iliştirir. Hata ayıklayıcı, bu kod satırını çalıştıran ve bu kesme noktasının tüm koşullarını karşılayan ilk rol örneği için bir kesme noktasına kesilir. Bir örnekte hata ayıklaması yaparsanız, hata ayıklayıcı yalnızca bu örneğe iliştirir ve yalnızca belirli bir örnek bu kod satırını çalıştırdığında kesme noktasının koşullarını karşıladığı zaman kesme noktasında kesilir.

    ![Hata ayıklayıcı Ekle](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Hata ayıklayıcı bir örneğe eklendikten sonra, her zamanki gibi hata ayıklayın. Hata ayıklayıcı, rolünüz için uygun ana bilgisayar işlemine otomatik olarak eklenir. Rolün ne olduğuna bağlı olarak, hata ayıklayıcı w3wp.exe, WaWorkerHost.exe veya WaIISHost.exe iliştirir. Hata ayıklayıcının eklendiği işlemi doğrulamak için Sunucu Gezgini ' deki örnek düğümünü genişletin. Azure işlemleriyle ilgili daha fazla bilgi için bkz. [Azure rol mimarisi](/archive/blogs/kwill/windows-azure-role-architecture) .

    ![Kod türünü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. hata ayıklayıcının eklendiği işlemi belirlemek için, menü çubuğunda **hata ayıkla**  >  **Windows**  >  **süreçler**' ı seçin ve **süreçler** iletişim kutusunu açın. (Klavye: Ctrl + Alt + Z) Belirli bir işlemi ayırmak için, kısayol menüsünü açın ve ardından **Işlemi ayır**' ı seçin. Ya da Sunucu Gezgini ' de örnek düğümünü bulun, işlemi bulun, kısayol menüsünü açın ve ardından **Işlemi ayır**' ı seçin.

    ![Hata Ayıklama İşlemleri](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Uzaktan hata ayıklama sırasında kesme noktalarında uzun durakları önleyin. Azure, birkaç dakikadan uzun süre sonra durdurulan bir işlemi yanıt vermemeye ve bu örneğe trafik göndermeyi durdurmaktadır. Çok uzun süre durdurursanız msvsmon.exe işlemden ayırır.

Hata ayıklayıcıyı örneğinizin veya rolünüzün tüm işlemlerinden ayırmak için, hata ayıklaması yaptığınız rol veya örnek için kısayol menüsünü açın ve ardından **hata ayıklayıcıyı ayır**' ı seçin.

## <a name="limitations-of-remote-debugging-in-azure"></a>Azure 'da uzaktan hata ayıklama sınırlamaları

Azure SDK 2,3 'de, uzaktan hata ayıklama aşağıdaki sınırlamalara sahiptir:

* Uzaktan hata ayıklama etkinken, herhangi bir rolün 25 ' ten fazla örneğe sahip olduğu bir bulut hizmeti yayımlayamazsınız.
* Hata ayıklayıcı 30400 ile 31400 30424 arasındaki bağlantı noktalarını 31424 ve 32400 32424 kullanır. Bu bağlantı noktalarından herhangi birini kullanmaya çalışırsanız, hizmetinizi yayımlayamayacaksınız ve Azure için etkinlik günlüğünde aşağıdaki hata iletilerinden biri görüntülenir:

  * . Cscfg dosyası. csdef dosyasına karşı doğrulanırken hata oluştu.
    ' Role ' rolünün Microsoft. WindowsAzure. eklenti. RemoteDebugger. Connector için ayrılmış bağlantı noktası aralığı ' Range ', zaten tanımlı bir bağlantı noktası veya aralıkla örtüşüyor.
  * Ayırma başarısız oldu. Lütfen daha sonra yeniden deneyin, VM boyutunu veya rol örneği sayısını azaltmayı deneyin ya da farklı bir bölgeye dağıtım yapmayı deneyin.

::: moniker range=">=vs-2022"

## <a name="debugging-azure-app-services"></a>Azure Uygulama hizmetlerinde hata ayıklama

Azure Uygulama hizmetlerinde çalışan programlarda, Visual Studio içinde Işleme Ekle iletişim kutusunu kullanarak hata ayıklaması yapabilirsiniz. 

> [!NOTE]
> bu yalnızca Azure uygulama hizmetleri Windows Visual Studio 2022 17,1 ' den başlayarak kullanılabilir. 

### <a name="to-debug-a-windows-azure-app-service"></a>Windows hata ayıklamak için Azure App Service

1. **Hata Ayıkla** altında, **İşleme İliştir**' i seçin.

2. **bağlantı türünü** **Microsoft Azure App Services** olarak değiştirip **bul..**. seçeneğini belirleyin.

3. Açılan iletişim kutusunda **abonelik adı**' nı seçin.

    ![Azure App Service Iletişim kutusu Seç](./media/vs-azure-tools-debug-cloud-services-virtual-machines/select-app-service.png)

> [!NOTE]
> Azure App Service içeren aboneliğe erişimi olan bir Microsoft hesabında oturum açmanız gerekir.

4. Görünümü kaynak grubu veya kaynak türüne göre filtreleyin ya da ada göre arama yapın.

5. Sonra, hata ayıklamak istediğiniz App Service seçin, sonra **Tamam**' ı seçin.

    Bu, App Service uzaktan hata ayıklamayı sağlar ve size iliştirilecek kullanılabilir işlemlerin bir listesini gösterir. 

    ![İşlem listeleme](./media/vs-azure-tools-debug-cloud-services-virtual-machines/attach-to-process.png)

6. Eklemek istediğiniz işlemi seçin ve ardından hata ayıklamayı başlatmak için **İliştir** ' i seçin. 

::: moniker-end

## <a name="debugging-azure-virtual-machines"></a>Azure sanal makinelerinde hata ayıklama

Visual Studio Sunucu Gezgini kullanarak Azure sanal makinelerinde çalışan programlarda hata ayıklaması yapabilirsiniz. Azure sanal makinesinde uzaktan hata ayıklamayı etkinleştirdiğinizde, Azure, uzaktan hata ayıklama uzantısını sanal makineye yüklenir. Daha sonra, sanal makine üzerinde işlemlere bağlanabilir ve normalde yaptığınız gibi hata ayıklayabilirsiniz.

> [!NOTE]
> Azure resource manager yığını üzerinden oluşturulan sanal makinelerin, Visual Studio 2015 ' de Cloud Explorer kullanılarak uzaktan hata ayıklaması yapılabilir. Daha fazla bilgi için bkz. [Cloud Explorer Ile Azure kaynaklarını yönetme](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Bir Azure sanal makinesinde hata ayıklamak için

1. Sunucu Gezgini ' de, sanal makineler düğümünü genişletin ve sanal makinenin hata ayıklamak istediğiniz düğümünü seçin.

2. Bağlam menüsünü açın ve **hata ayıklamayı etkinleştir**' i seçin. Sanal makinede hata ayıklamayı etkinleştirmek isteyip istemediğinizden emin olup olmadığınız sorulduğunda **Evet**' i seçin.

    Azure, hata ayıklamayı etkinleştirmek için sanal makinede uzaktan hata ayıklama uzantısı 'nı yüklüyor.

    ![Sanal makine hata ayıklamayı etkinleştir komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Uzaktan hata ayıklama uzantısı yüklemeyi tamamladıktan sonra, sanal makinenin bağlam menüsünü açın ve **hata ayıklayıcı Ekle...** seçeneğini belirleyin.

    Azure, sanal makinedeki işlemlerin bir listesini alır ve bunları **Işleme İliştir** iletişim kutusunda görüntüler.

    ![Hata ayıklayıcı komutu Ekle](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. **Işleme İliştir** iletişim kutusunda, sonuçlar listesini yalnızca hata ayıklamak istediğiniz kod türlerini gösterecek şekilde sınırlamak için **Seç** ' i seçin. 32 bit veya 64 bit yönetilen kodda, yerel kodda veya her ikisinde hata ayıklaması yapabilirsiniz.

    ![Kod türünü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Sanal makinede hata ayıklamak istediğiniz işlemi seçin ve ardından **Ekle**' yi seçin. Örneğin, sanal makinede bir Web uygulamasında hata ayıklamak istiyorsanız w3wp.exe işlemini seçebilirsiniz. daha fazla bilgi için bkz. Visual Studio ve [Azure rol mimarisinde](/archive/blogs/kwill/windows-azure-role-architecture) [bir veya daha fazla işlemde hata ayıklama](../debugger/debug-multiple-processes.md) .

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Hata ayıklama için bir Web projesi ve sanal makine oluşturma

Azure projenizi yayımlamadan önce, bunu hata ayıklama ve test senaryolarını destekleyen ve test ve izleme programlarını yükleyebileceğiniz bir kapsanan ortamda test etmeyi yararlı bulabilirsiniz. Bu tür testleri çalıştırmanın bir yolu, bir sanal makinede uygulamanızda uzaktan hata ayıklamanın bir yoludur.

Visual Studio ASP.NET projeler, uygulama testi için kullanabileceğiniz kullanışlı bir sanal makine oluşturma seçeneği sunar. Sanal makine, PowerShell, uzak masaüstü ve WebDeploy gibi yaygın olarak gereken uç noktaları içerir.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Hata ayıklama için bir Web projesi ve bir sanal makine oluşturmak için

1. Visual Studio, yeni bir ASP.NET Web uygulaması oluşturun.

2. yeni ASP.NET Project iletişim kutusunda, Azure bölümünde, açılan liste kutusunda **sanal makine** ' yi seçin. **Uzak kaynak oluştur** onay kutusunu seçili bırakın. Devam etmek için **Tamam ' ı** seçin.

    **Azure 'da sanal makine oluştur** iletişim kutusu görüntülenir.

    ![ASP.NET web projesi oluştur iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Henüz oturum açmadıysanız Azure hesabınızda oturum açmanız istenir.

3. Sanal makine için çeşitli ayarları seçin ve ardından **Tamam**' ı seçin. Daha fazla bilgi için bkz. [sanal makineler](/azure/virtual-machines/) .

    DNS adı için girdiğiniz ad, sanal makinenin adı olacaktır.

    ![Azure 'da sanal makine oluştur iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure, sanal makineyi oluşturur ve sonra uç noktaları (uzak masaüstü ve Web Dağıtımı gibi) hazırlar ve yapılandırır.

4. Sanal makine tam olarak yapılandırıldıktan sonra, Sunucu Gezgini sanal makinenin düğümünü seçin.

5. Bağlam menüsünü açın ve **hata ayıklamayı etkinleştir**' i seçin. Sanal makinede hata ayıklamayı etkinleştirmek isteyip istemediğinizden emin olup olmadığınız sorulduğunda **Evet**' i seçin.

    Azure, hata ayıklamayı etkinleştirmek için uzaktan hata ayıklama uzantısını sanal makineye yüklüyor.

    ![Sanal makine hata ayıklamayı etkinleştir komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. projeyi [nasıl yapılır: Visual Studio One-Click yayımlama kullanarak Web Project dağıtma](/previous-versions/aspnet/dd465337(v=vs.110))bölümünde özetlenen şekilde yayımlayın. sanal makinede hata ayıklamak istediğiniz için, **Web 'i yayımla** sihirbazının **Ayarlar** sayfasında, yapılandırma olarak **hata ayıkla** ' yı seçin. Bu, hata ayıklama sırasında kod simgelerinin kullanılabilir olmasını sağlar.

    ![Yayımlama ayarları](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. **Dosya yayımlama seçeneklerinde**, proje zaten daha önceki bir zamanda dağıtılmışsa, **Hedefteki ek dosyaları Kaldır** ' ı seçin.

8. Proje yayımlandıktan sonra, sanal makinenin Sunucu Gezgini içindeki bağlam menüsünde **hata ayıklayıcı Ekle...** seçeneğini belirleyin.

    Azure, sanal makinedeki işlemlerin bir listesini alır ve bunları **Işleme İliştir** iletişim kutusunda görüntüler.

    ![Hata ayıklayıcı komutu Ekle](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. **Işleme İliştir** iletişim kutusunda, sonuçlar listesini yalnızca hata ayıklamak istediğiniz kod türlerini gösterecek şekilde sınırlamak için **Seç** ' i seçin. 32 bit veya 64 bit yönetilen kodda, yerel kodda veya her ikisinde hata ayıklaması yapabilirsiniz.

    ![Kod türünü seç iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Sanal makinede hata ayıklamak istediğiniz işlemi seçin ve ardından **Ekle**' yi seçin. Örneğin, sanal makinede bir Web uygulamasında hata ayıklamak istiyorsanız w3wp.exe işlemini seçebilirsiniz. daha fazla bilgi için bkz. [Visual Studio bir veya daha fazla işlemde hata ayıklama](../debugger/debug-multiple-processes.md) .

## <a name="next-steps"></a>Sonraki adımlar

* **IntelliTrace** kullanarak bir yayın sunucusundan gelen çağrı ve olay günlüğünü toplayın. Bkz. [IntelliTrace ve Visual Studio yayımlanmış bir bulut hizmetinde hata ayıklama](vs-azure-tools-IntelliTrace-debug-published-cloud-services.md).

* Rollerin geliştirme ortamında veya Azure 'da çalışıp çalışmadığını, roller içinde çalışan koddan ayrıntılı bilgileri günlüğe kaydetmek için **Azure tanılama** kullanın. Bkz. [Azure Tanılama kullanarak günlük verilerini toplama](/azure/cloud-services/cloud-services-dotnet-diagnostics).
