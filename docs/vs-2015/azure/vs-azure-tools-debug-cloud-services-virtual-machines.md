---
title: Bir Azure bulut hizmeti ya da sanal makineyi hata ayıklama
description: Bir bulut hizmeti veya sanal makine Visual Studio'da hata ayıklama
author: mikejo5000
manager: jillfra
ms.assetid: 945e06e0-2100-41af-b218-72347367ddab
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: 2185641d5e3f9facf416e6ea999a1e8dcec0b37b
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294208"
---
# <a name="debugging-an-azure-cloud-service-or-virtual-machine-in-visual-studio"></a>Bir Azure bulut hizmeti veya sanal makinesinde Visual Studio'da hata ayıklama

Visual Studio, Azure bulut Hizmetleri ve sanal makineler hata ayıklama için farklı seçenekler sunar.

## <a name="debug-your-cloud-service-on-your-local-computer"></a>Yerel bilgisayarınızda, bir bulut hizmetinde hata ayıklama

Zamandan tasarruf edebilirsiniz ve Azure kullanarak para işlem bulut hizmetinizi yerel bir makinede hata ayıklamak için öykünücü. Dağıtmadan önce bir hizmet yerel olarak hata ayıklama tarafından güvenilirlik ve performans işlem süresi için ödeme yapmadan artırabilir. Ancak, bazı hatalar yalnızca bir bulut hizmeti Azure'da çalıştırıldığında meydana gelebilir kendisi. Hizmetinizi yayımlayın ve ardından bir rol örneği için hata ayıklayıcının uzak hata ayıklama etkinleştirirseniz, bu hataları ayıklayabilirsiniz.

Öykünücü, Azure işlem hizmetini taklit eder ve test ve bulut hizmetinizi dağıtmadan önce hata ayıklama için yerel ortamınızda çalışır. Öykünücü, rol örneklerinizin yaşam döngüsü işler ve yerel depolama gibi sanal kaynaklara erişim sağlar. Hata ayıklama veya hizmetinizi Visual Studio'dan çalıştırma öykünücü bir arka plan uygulama otomatik olarak başlatılır ve sonra hizmetinizi öykünücüye dağıtır. Öykünücüyü hizmetinizi yerel ortamda çalıştığında görüntülemek için kullanabilirsiniz. Tam sürümünü ya da öykünücüsü'nün express sürümü çalıştırabilirsiniz. (Azure 2,3 ' den itibaren, öykünücünün Express sürümü varsayılandır.) [Bulut hizmetini yerel olarak çalıştırmak ve hata ayıklamak Için öykünücü Express kullanma](vs-azure-tools-emulator-express-debug-run.md)konusuna bakın.

### <a name="to-debug-your-cloud-service-on-your-local-computer"></a>Bulut hizmetinizi yerel bilgisayarınızda hata ayıklamak için

1. Azure bulut hizmeti Projenizi çalıştırmak için menü çubuğunda **Hata Ayıkla**, **hata ayıklamayı Başlat** ' ı seçin. Alternatif olarak, F5 tuşuna basabilirsiniz. İşlem öykünücüsü başlatılıyor bir ileti görürsünüz. Öykünücü başlatıldığında sistem tepsisi simgesi, onaylar.

    ![Sistem tepsisindeki Azure öykünücüsü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC783828.png)

2. Bildirim alanında Azure simgesi için kısayol menüsünü açarak ve ardından **Işlem öykünücüsü Kullanıcı arabirimini göster**' i seçerek işlem öykünücüsünün Kullanıcı arabirimini görüntüleyin.

    Sol bölmede kullanıcı arabiriminin işlem öykünücüsü ve her hizmet çalışan rolü örnekleri için şu anda dağıtılan hizmetler gösterilmektedir. Hizmet veya yaşam döngüsü, günlüğe kaydetme ve tanılama bilgileri sağ bölmede gösterilecek roller seçebilirsiniz. Odağı dahil penceresinin üst kenar boşluğunda yerleştirirseniz, sağ bölmede doldurmak üzere genişletir.

3. **Hata Ayıkla** menüsündeki komutları seçerek ve kodunuzda kesme noktaları ayarlayarak uygulamada ilerleyin. Uygulama hata ayıklayıcı adım adım olarak bölmeleri uygulamanın geçerli durumuyla güncelleştirilir. Uygulama dağıtımı hata ayıklamayı durdurduğunuzda silinir. Uygulamanız bir web rolü içerir ve web tarayıcı başlatmak için başlatma eylemi özelliğini ayarladınız, Visual Studio web uygulamanızı tarayıcıda başlatır. Hizmet yapılandırmasının bir rolün örnekleri sayısını değiştirirseniz, bulut hizmetinizi durdurmak ve ardından bu yeni rol örneklerini ayıklayabilirsiniz, hata ayıklamayı yeniden başlatın.

    > [!NOTE]
    > Çalıştırmayı veya hizmetinizi hata ayıklamayı durdurduğunuzda, yerel işlem öykünücüsü ve depolama öykünücüsü durdurulmaz. Bunları açıkça bildirim alanından durdurmanız gerekir.

## <a name="debug-a-cloud-service-in-azure"></a>Azure bulut hizmetinde hata ayıklama

Bulut hizmetinizi böylece gerekli hizmetlerinin (örneğin, msvsmon.exe) rol örneklerinizin çalışan sanal makineleri üzerinde yüklü olduğu dağıttığınızda bir bulut hizmeti uzak bir makineden hata ayıklamak için bu işlevi açıkça etkinleştirmeniz gerekir. Hizmet yayımlandığında, uzaktan hata ayıklama etkinleştirmediyseniz, uzaktan hata ayıklama etkin olan hizmet yeniden yayımlamanız gerekir.

Bir bulut hizmeti için uzaktan hata ayıklama etkinleştirirseniz, performans göstermesi veya ek ücrete tabi değildir. Hizmeti kullanan istemciler olumsuz yönde etkilenebilir, çünkü bir üretim hizmetine üzerinde uzaktan hata ayıklama kullanmayın.

> [!NOTE]
> Visual Studio 'dan bir bulut hizmeti yayımladığınızda, söz konusu hizmette .NET Framework 4 ' ü veya .NET Framework 4,5 ' i hedefleyen herhangi bir rol için **IntelliTrace** 'i etkinleştirebilirsiniz. **IntelliTrace**kullanarak, geçmişte bir rol örneğinde gerçekleşen olayları inceleyebilir ve bu zamandan bağlamı yeniden oluşturabilirsiniz. Bkz. [IntelliTrace ve Visual Studio ile yayımlanmış bir bulut hizmetinde hata ayıklama](https://go.microsoft.com/fwlink/?LinkID=623016) ve [IntelliTrace kullanma](https://msdn.microsoft.com/library/dd264915.aspx).

### <a name="to-enable-remote-debugging-for-a-cloud-service"></a>Bir bulut hizmeti için uzaktan hata ayıklamayı etkinleştirmek için

1. Azure projesi için kısayol menüsünü açın ve ardından **Yayımla**' yı seçin.

2. **Hazırlama** ortamını ve **hata ayıklama** yapılandırmasını seçin.

    Yalnızca bir kılavuz budur. Bir üretim ortamında test ortamlarınızı çalıştırmayı seçebilirsiniz. Ancak, üretim ortamına uzaktan hata ayıklama etkinleştirirseniz kullanıcılar olumsuz yönde etkileyebilir. Sürüm yapılandırmasını seçebilirsiniz, ancak hata ayıklama yapılandırması hata ayıklamayı kolaylaştırır.

    ![Hata ayıklama yapılandırmasını seçin](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746717.gif)

3. Olağan adımları izleyin, ancak **Gelişmiş ayarlar** sekmesinde **tüm roller Için uzaktan hata ayıklayıcıyı etkinleştir** onay kutusunu işaretleyin.

    ![Hata Ayıklama Yapılandırması](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746718.gif)

### <a name="to-attach-the-debugger-to-a-cloud-service-in-azure"></a>Azure'daki bir bulut hizmeti eklemek için

1. Sunucu Gezgini'nde, bulut hizmetinizin düğümünü genişletin.

2. Eklemek istediğiniz rol veya rol örneği için kısayol menüsünü açın ve ardından **hata ayıklayıcı Ekle**' yi seçin.

    Rol hatalarını ayıklıyorsanız Visual Studio hata ayıklayıcı bu rolün her örneğine ekler. Hata ayıklayıcı, kodun o satırına çalıştırır ve bu Kesme noktasının koşulları karşılayan ilk rol örneği için bir kesme noktasında keser. Örneği, yalnızca bu örneği ve yalnızca o belirli örnekte bu kod satırı çalıştırır ve kesme noktasının koşullara uyan bir kesme noktasında sonları hata ayıklayıcı iliştirileceği hata ayıklama durumunda.

    ![Hata Ayıklayıcı Ekle](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746719.gif)

3. Hata ayıklayıcı örneğine ekler sonra zamanki gibi hata ayıklayın. Hata ayıklayıcı, uygun ana bilgisayar işlemine rolünüz için otomatik olarak ekler. Rolü nedir bağlı olarak, hata ayıklayıcı, w3wp.exe, WaWorkerHost.exe veya WaIISHost.exe ekler. Hata ayıklayıcının bağlı olduğu işlemini doğrulamak için Sunucu Gezgininde örneği genişletin. Azure işlemleriyle ilgili daha fazla bilgi için bkz. [Azure rol mimarisi](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) .

    ![Kod türünü seçin iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

4. Hata ayıklayıcının bağlı olduğu işlemleri tanımlamak için seçme hata ayıklama, Windows, işlemleri menü çubuğunda, işlemleri iletişim kutusunu açın. (Klavye: Ctrl + Alt + Z) Belirli bir işlemi ayırmak için, kısayol menüsünü açın ve ardından **Işlemi ayır**' ı seçin. Ya da Sunucu Gezgini ' de örnek düğümünü bulun, işlemi bulun, kısayol menüsünü açın ve ardından **Işlemi ayır**' ı seçin.

    ![Hata Ayıklama İşlemleri](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC690787.gif)

> [!WARNING]
> Uzun kesme noktaları uzak durur önlemek hata ayıklama. Azure işlem yanıt vermiyor olarak birkaç dakikadan fazla durdurulur ve bu örneğe trafik göndermeyi durdurur değerlendirir. Uzun süre durdurursanız, msvsmon.exe işlemden ayırır.

Hata ayıklayıcıyı örneğinizin veya rolünüzün tüm işlemlerinden ayırmak için, hata ayıklaması yaptığınız rol veya örnek için kısayol menüsünü açın ve ardından **hata ayıklayıcıyı ayır**' ı seçin.

## <a name="limitations-of-remote-debugging-in-azure"></a>Azure'da uzaktan hata ayıklama sınırlamaları

Azure SDK 2.3 ' uzaktan hata ayıklama aşağıdaki sınırlamalara sahiptir:

* Uzaktan hata ayıklama etkin olan, herhangi bir rol 25 örnekten daha fazlasını olan bir bulut hizmeti yayımlanamıyor.
* Hata ayıklayıcı için 30400 30424, 31400 için 31424 ve 32400 için 32424 bağlantı noktalarını kullanır. Bu bağlantı noktalarından birini kullanmayı denerseniz, hizmetinizi yayımlama mümkün olmayacaktır ve aşağıdaki hata iletilerinden biri için Azure etkinlik günlüğü'nde görünür:

  * .Cscfg dosyası .csdef dosyası karşı doğrulanırken bir hata oluştu.
    Uç noktası için ayrılmış bir bağlantı noktası aralığı 'range' Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector 'role' rolünün bir zaten tanımlı bir bağlantı veya aralığı ile çakışıyor.
  * Ayırma başarısız oldu. Lütfen daha sonra yeniden deneyin, VM boyutunu veya rol örneklerinin sayısını azaltmayı deneyin veya farklı bir bölgeye dağıtmayı deneyin.

## <a name="debugging-azure-virtual-machines"></a>Azure sanal makineleri hata ayıklama

Visual Studio'da Sunucu Gezgini kullanarak Azure sanal makinelerinde çalışan programlar ayıklayabilirsiniz. Azure sanal makinesinde uzaktan hata ayıklama etkinleştirdiğinizde, Azure sanal makinede uzaktan hata ayıklama uzantısı yükler. Ardından, sanal makine üzerindeki işlemleri ekleyin ve normalde yaptığınız gibi hata ayıklama.

> [!NOTE]
> Azure resource manager yığınından oluşturulan sanal makineler, Visual Studio 2015'te Cloud Explorer'ı kullanarak uzaktan ayıklanabilir. Daha fazla bilgi için bkz. [Cloud Explorer Ile Azure kaynaklarını yönetme](vs-azure-tools-resources-managing-with-cloud-explorer.md).

### <a name="to-debug-an-azure-virtual-machine"></a>Bir Azure sanal makinesi hata ayıklamak için

1. Sunucu Gezgini'nde, sanal makine düğümünü genişletin ve sanal makinenin hata ayıklamak istediğiniz düğümü seçin.

2. Bağlam menüsünü açın ve **hata ayıklamayı etkinleştir**' i seçin. Sanal makinede hata ayıklamayı etkinleştirmek isteyip istemediğinizden emin olup olmadığınız sorulduğunda **Evet**' i seçin.

    Azure uzaktan hata ayıklama uzantısı hata ayıklamayı etkinleştirmek için sanal makineye yükler.

    ![Sanal makine hata ayıklamayı etkinleştir komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

3. Uzaktan hata ayıklama uzantısı yüklemeyi tamamladıktan sonra, sanal makinenin bağlam menüsünü açın ve **hata ayıklayıcı Ekle...** seçeneğini belirleyin.

    Azure sanal makinede işlemlerin bir listesini alır ve bunları işleme İliştir işlem iletişim kutusu gösterir.

    ![Hata ayıklayıcısı ekle komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

4. **Işleme İliştir** iletişim kutusunda, sonuçlar listesini yalnızca hata ayıklamak istediğiniz kod türlerini gösterecek şekilde sınırlamak için **Seç** ' i seçin. 32 bit veya 64 bit yönetilen kod, yerel kod veya her ikisi de ayıklayabilirsiniz.

    ![Kod türünü seçin iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

5. Sanal makinede hata ayıklamak istediğiniz işlemi seçin ve ardından **Ekle**' yi seçin. Örneğin, w3wp.exe işlemi, sanal makinede bir web uygulamasında hata ayıklamak istiyorsanız seçebilirsiniz. Daha fazla bilgi için bkz. Visual Studio ve [Azure rol mimarisinde](https://blogs.msdn.microsoft.com/kwill/2011/05/05/windows-azure-role-architecture/) [bir veya daha fazla işlemde hata ayıklama](https://msdn.microsoft.com/library/jj919165.aspx) .

## <a name="create-a-web-project-and-a-virtual-machine-for-debugging"></a>Bir web projesi ve hata ayıklama için bir sanal makine oluşturma

Azure projenizi yayımlamadan önce hata ayıklama ve test senaryolarını destekleyen ve test etme ve programları izleme yükleyebileceği bağımsız bir ortamda test etmek yararlı. Bu tür testler yollarından biri, uygulamanızı bir sanal makinede uzaktan hata ayıklama sağlamaktır.

Visual Studio ASP.NET projeleri uygulamayı test etmek için kullanabileceğiniz yararlı bir sanal makine oluşturmak için bir seçenek sunar. Sanal makine, PowerShell, Uzak Masaüstü ve WebDeploy gibi yaygın olarak gerekli uç noktaları içerir.

### <a name="to-create-a-web-project-and-a-virtual-machine-for-debugging"></a>Bir web projesi ve hata ayıklama için bir sanal makine oluşturmak için

1. Visual Studio'da yeni bir ASP.NET Web uygulaması oluşturun.

2. Yeni ASP.NET projesi iletişim kutusunda, Azure bölümünde, açılan liste kutusundan **sanal makine** ' yi seçin. **Uzak kaynak oluştur** onay kutusunu seçili bırakın. Devam etmek için **Tamam ' ı** seçin.

    **Azure 'da sanal makine oluştur** iletişim kutusu görüntülenir.

    ![ASP.NET web projesi oluştur iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746723.png)

    > [!NOTE]
    > Henüz oturum açmadıysanız Azure hesabınızda oturum açmanız istenir.

3. Sanal makine için çeşitli ayarları seçin ve ardından **Tamam**' ı seçin. Daha fazla bilgi için bkz. [sanal makineler](https://go.microsoft.com/fwlink/?LinkId=623033) .

    DNS adı için girdiğiniz ad, sanal makinenin adı olacaktır.

    ![Azure'da sanal makine oluştur iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746724.png)

    Azure sanal makine ve ardından hükümlerine oluşturur ve Uzak Masaüstü ve Web dağıtımı gibi uç noktaları yapılandırır

4. Sanal makine tam olarak yapılandırdıktan sonra sunucu Gezgini'nde sanal makinenin düğümünü seçin.

5. Bağlam menüsünü açın ve **hata ayıklamayı etkinleştir**' i seçin. Sanal makinede hata ayıklamayı etkinleştirmek isteyip istemediğinizden emin olup olmadığınız sorulduğunda **Evet**' i seçin.

    Azure uzaktan hata ayıklama uzantısı hata ayıklamayı etkinleştirmek için sanal makineye yükler.

    ![Sanal makine hata ayıklamayı etkinleştir komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746720.png)

    ![Azure etkinlik günlüğü](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746721.png)

6. Projenizi [nasıl yapılır: Visual Studio 'Da tek tıklamayla yayımlama kullanarak Web projesi dağıtma](https://msdn.microsoft.com/library/dd465337.aspx)bölümünde açıklandığı şekilde yayımlayın. Sanal makinede hata ayıklamak istediğiniz için, **Web 'ı Yayımla** sihirbazının **Ayarlar** sayfasında, yapılandırma olarak **Hata Ayıkla** ' yı seçin. Bu hata ayıklama sırasında kod sembollerinin kullanılabilir olduğundan emin olur.

    ![Yayımlama ayarları](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718349.png)

7. **Dosya yayımlama seçeneklerinde**, proje zaten daha önceki bir zamanda dağıtılmışsa, **Hedefteki ek dosyaları Kaldır** ' ı seçin.

8. Proje yayımlandıktan sonra, sanal makinenin Sunucu Gezgini içindeki bağlam menüsünde **hata ayıklayıcı Ekle...** seçeneğini belirleyin.

    Azure sanal makinede işlemlerin bir listesini alır ve bunları işleme İliştir işlem iletişim kutusu gösterir.

    ![Hata ayıklayıcısı ekle komutu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC746722.png)

9. **Işleme İliştir** iletişim kutusunda, sonuçlar listesini yalnızca hata ayıklamak istediğiniz kod türlerini gösterecek şekilde sınırlamak için **Seç** ' i seçin. 32 bit veya 64 bit yönetilen kod, yerel kod veya her ikisi de ayıklayabilirsiniz.

    ![Kod türünü seçin iletişim kutusu](./media/vs-azure-tools-debug-cloud-services-virtual-machines/IC718346.png)

10. Sanal makinede hata ayıklamak istediğiniz işlemi seçin ve ardından **Ekle**' yi seçin. Örneğin, w3wp.exe işlemi, sanal makinede bir web uygulamasında hata ayıklamak istiyorsanız seçebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'Da bir veya daha fazla Işlemde hata ayıklama](https://msdn.microsoft.com/library/jj919165.aspx) .

## <a name="next-steps"></a>Sonraki adımlar

* **IntelliTrace** kullanarak bir yayın sunucusundan gelen çağrı ve olay günlüğünü toplayın. Bkz. [IntelliTrace ve Visual Studio Ile yayınlanmış bir bulut hizmetinde hata ayıklama](https://go.microsoft.com/fwlink/?LinkID=623016).

* Rollerin geliştirme ortamında veya Azure 'da çalışıp çalışmadığını, roller içinde çalışan koddan ayrıntılı bilgileri günlüğe kaydetmek için **Azure tanılama** kullanın. Bkz. [Azure Tanılama kullanarak günlük verilerini toplama](https://go.microsoft.com/fwlink/p/?LinkId=400450).
