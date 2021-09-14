---
title: Tanılama-Azure Cloud Services & VM 'Leri
ms.custom: SEO-VS-2020
description: Visual Studio 'de Azure bulut hizmetlerinde ve sanal makinelerde (VM) hata ayıklama için tanılamayı ayarlamayı öğrenin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.openlocfilehash: 454584df4f8a5254f538fa50b192be0193322878
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633145"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Azure Cloud Services ve sanal makineler için tanılamayı ayarlama
bir Azure bulut hizmetinde veya sanal makinede sorun gidermeniz gerektiğinde Azure Tanılama daha kolay bir şekilde kurmak için Visual Studio kullanabilirsiniz. Tanılama, bulut hizmetinizi çalıştıran sanal makinelerde ve sanal makine örneklerinde sistem verilerini ve günlük verilerini yakalar. Tanılama verileri, seçtiğiniz bir depolama hesabına aktarılır. Azure 'da tanılama günlüğü hakkında daha fazla bilgi için bkz. [Azure App Service Web Apps için tanılama günlüğünü etkinleştirme](/azure/app-service/web-sites-enable-diagnostic-log).

bu makalede, Azure Tanılama ve sonrasında dağıtımdan önce ve sonra kurulumu yapmak ve ayarlamak için Visual Studio nasıl kullanacağınızı göstereceğiz. Azure sanal makinelerinde tanılamayı ayarlamayı, toplanacak tanılama bilgilerinin türlerini seçmenizi ve toplandıktan sonra bilgilerin nasıl görüntüleneceğini öğrenin.

Azure Tanılama ayarlamak için aşağıdaki seçeneklerden birini kullanabilirsiniz:

* Tanılama **yapılandırması** iletişim kutusundaki tanılama ayarlarını değiştirin Visual Studio. Ayarlar, Diagnostics. wadcfgx adlı bir dosyaya kaydedilir (Azure SDK 2,4 ve önceki sürümlerde, dosya Diagnostics. wadcfg olarak adlandırılır). Ayrıca yapılandırma dosyasını doğrudan değiştirebilirsiniz. Dosyayı el ile güncelleştirirseniz, yapılandırma değişiklikleri bulut hizmetini Azure 'a bir sonraki dağıtışınızda veya hizmet öykünücüsünde çalıştırıldığında etkili olur.
* bir bulut hizmeti veya çalıştıran bir sanal makine için tanılama ayarlarını değiştirmek üzere Visual Studio bulut gezgini 'ni veya Sunucu Gezgini kullanın.

## <a name="azure-sdk-26-diagnostics-changes"></a>Azure SDK 2,6 tanılama değişiklikleri
Aşağıdaki değişiklikler Visual Studio Azure SDK 2,6 ve sonraki projeleri için geçerlidir:

* Yerel öykünücü artık tanılamayı desteklemektedir. Bu, tanılama verilerini toplayabileceğiniz ve Visual Studio geliştirme ve test ederken uygulamanızın doğru izlemeleri oluşturduğundan emin olmanızı sağlayan anlamına gelir. bağlantı dizesi, `UseDevelopmentStorage=true` Azure Depolama Emulator kullanarak Visual Studio ' de bulut hizmeti projenizi çalıştırırken tanılama veri toplamayı etkinleştirir. tüm tanılama verileri, geliştirme Depolama depolama hesabında toplanır.
* Tanılama depolama hesabı bağlantı dizesi, `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` hizmet yapılandırma (. cscfg) dosyasında depolanır. Azure SDK 2,5 ' de tanılama depolama hesabı, Diagnostics. wadcfgx dosyasında belirtilir.

Bağlantı dizesi, Azure SDK 2,6 ve üzeri sürümlerde Azure SDK 2,4 ve önceki sürümlerde bazı önemli yollarla farklı çalışır:

* Azure SDK 2,4 ve önceki sürümlerde, bağlantı dizesi, tanılama günlüklerini aktarmaya yönelik depolama hesabı bilgilerini almak için tanılama eklentisi tarafından bir çalışma zamanı olarak kullanılır.
* Azure SDK 2,6 ve sonrasında Visual Studio, Azure Tanılama uzantısını yayımlama sırasında uygun depolama hesabı bilgileriyle ayarlamak için tanılama bağlantı dizesini kullanır. Visual Studio, yayımlama sırasında kullandığı farklı hizmet yapılandırmalarına yönelik farklı depolama hesapları tanımlamak için bağlantı dizesini kullanabilirsiniz. Ancak, tanılama eklentisi Azure SDK 2,5 sonrasında kullanılamadığından,. cscfg dosyası kendisi için tanılama uzantısını ayarlayamayabilir. uzantıyı Visual Studio veya PowerShell gibi araçları kullanarak ayrı olarak ayarlamanız gerekir.
* PowerShell kullanarak tanılama uzantısını ayarlama sürecini basitleştirmek için, Visual Studio paket çıktısı her bir rol için tanılama uzantısının ortak yapılandırma XML 'sini içerir. Visual Studio, genel yapılandırmadaki depolama hesabı bilgilerini doldurmak için tanılama bağlantı dizesini kullanır. Ortak yapılandırma dosyaları uzantılar klasöründe oluşturulur. Ortak yapılandırma dosyaları, PaaSDiagnostics adlandırma düzenlerini kullanır. &lt; rol adı \> . PubConfig.xml. Herhangi bir PowerShell tabanlı dağıtımlar, her yapılandırmayı bir rolle eşlemek için bu kalıbı kullanabilir.
* [Azure Portal](https://portal.azure.com) , tanılama verilerine erişmek için. cscfg dosyasındaki bağlantı dizesini kullanır. Veriler **izleme** sekmesinde görüntülenir. Bağlantı dizesi, hizmeti portalda ayrıntılı izleme verilerini gösterecek şekilde ayarlamak için gereklidir.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Projeleri Azure SDK 2,6 ve üzeri sürümlere geçirme
Azure SDK 2,5 ' den Azure SDK 2,6 veya sonraki bir sürüme geçirdiğinizde,. wadcfgx dosyasında belirtilen bir tanılama depolama hesabınız varsa, depolama hesabı bu dosyada kalır. Farklı depolama yapılandırmalarının farklı depolama hesaplarını kullanma esnekliğinden faydalanmak için bağlantı dizesini projenize el ile ekleyin. Bir projeyi Azure SDK 2,4 veya önceki sürümlerden Azure SDK 2,6 ' ye geçiriyorsanız, tanılama bağlantı dizeleri korunur. Bununla birlikte, önceki bölümde açıklanan şekilde, bağlantı dizelerinin Azure SDK 2,6 ' de nasıl ele alındığına ilişkin değişikliklere göz önüne alın.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>tanılama depolama hesabını Visual Studio nasıl belirler
* . cscfg dosyasında bir tanılama bağlantı dizesi belirtilmişse, Visual Studio yayımlama sırasında tanılama uzantısını ayarlamak için ve paketleme sırasında ortak yapılandırma XML dosyalarını oluşturduğunda bunu kullanır.
* . cscfg dosyasında bir tanılama bağlantı dizesi belirtilmemişse, Visual Studio yayımlama için tanılama uzantısını ayarlamak ve paketleme sırasında ortak yapılandırma XML dosyalarını oluşturmak için. wadcfgx dosyasında belirtilen depolama hesabını kullanmaya geri döner.
* . Cscfg dosyasındaki tanılama bağlantı dizesi. wadcfgx dosyasındaki depolama hesabından önceliklidir. . cscfg dosyasında bir tanılama bağlantı dizesi belirtilirse, Visual Studio bu bağlantı dizesini kullanır ve. wadcfgx içindeki depolama hesabını yoksayar.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>"Geliştirme depolama bağlantı dizelerini güncelleştir..." onay kutusu yapılsın mı?
**tanılama için güncelleştirme geliştirme depolama bağlantı dizeleri, Microsoft Azure 'de yayımlarken Microsoft Azure depolama hesabı kimlik bilgileriyle Önbelleğe Alma** , tüm geliştirme depolama hesabı bağlantı dizelerini yayımlama sırasında belirttiğiniz Azure depolama hesabıyla güncelleştirmenin kolay bir yoludur.

örneğin, bu onay kutusunu seçerseniz ve tanılama bağlantı dizesi belirtiyorsa `UseDevelopmentStorage=true` , projeyi Azure 'da yayımladığınızda, Visual Studio tanılama bağlantı dizesini yayımlama sihirbazında belirttiğiniz depolama hesabıyla otomatik olarak güncelleştirir. Ancak, tanılama bağlantı dizesi olarak gerçek bir depolama hesabı belirtilmişse, bunun yerine bu hesap kullanılır.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Azure SDK 2,4 ve önceki sürümlerinde ve Azure SDK 2,5 ve üzeri ile tanılama işlevselliği farklılıkları
Projenizi Azure SDK 2,4 ve önceki sürümlerden Azure SDK 2,5 veya sonraki bir sürüme yükseltiyorsanız aşağıdaki tanılama işlevselliği farklarını aklınızda bulundurun:

* **Yapılandırma API 'leri kullanım dışıdır**. Tanılamayı programsal olarak yapılandırma, Azure SDK 2,4 ve önceki sürümlerde kullanılabilir, ancak Azure SDK 2,5 ve sonraki sürümlerde kullanım dışıdır. Tanılama yapılandırmanız Şu anda kodda tanımlıysa, tanılama 'nın çalışmaya devam etmesini sağlamak için, geçirilen projedeki bu ayarları sıfırdan yeniden yapılandırmanız gerekir. Azure SDK 2,4 için tanılama yapılandırma dosyası, Diagnostics. wadcfg ' dir. Azure SDK 2,5 ve üzeri için tanılama yapılandırma dosyası, Diagnostics. wadcfgx ' dir.
* **Bulut hizmeti uygulamalarına yönelik Tanılamalar yalnızca rol düzeyinde yapılandırılabilir**. Azure SDK 2,5 ve üzeri sürümlerde, örnek düzeyinde bulut hizmeti uygulamaları için tanılamayı ayarlayamazsınız.
* **Uygulamanızı her dağıttığınız zaman tanılama yapılandırması güncelleştirilir**. tanılama yapılandırmanızı Visual Studio Sunucu Gezgini değiştirirseniz ve sonra uygulamanızı yeniden dağıtırsanız, bu, eşlik sorunlarına neden olabilir.
* **Azure SDK 2,5 ve üzeri sürümlerde kilitlenme dökümleri, kodda değil, tanılama yapılandırma dosyasında yapılandırılır**. Kod içinde yapılandırılmış kilitlenme dökümlerinden sahipseniz, yapılandırmayı koddan yapılandırma dosyasına el ile aktarmanız gerekir. Kilitlenme dökümü, Azure SDK 2,6 ' e geçiş sırasında aktarılmaz.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Bulut hizmeti projelerinde tanılamayı dağıtmadan önce etkinleştirin
Visual Studio ' de, dağıtımdan önce hizmet öykünücüsünde hizmeti çalıştırdığınızda Azure 'da çalışan roller için tanılama verileri toplayabilirsiniz. Visual Studio tanılama ayarlarındaki tüm değişiklikler, diagnostics. wadcfgx yapılandırma dosyasına kaydedilir. Bu ayarlar, bulut hizmetinizi dağıtırken tanılama verilerinin kaydedildiği depolama hesabını belirtir.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>dağıtımdan önce Visual Studio tanılamayı açmak için

1. Rolün kısayol menüsünde, **Özellikler**' i seçin. Rolün **Özellikler** Iletişim kutusunda **yapılandırma** sekmesini seçin.
2. **Tanılama** bölümünde, **tanılamayı etkinleştir** onay kutusunun seçili olduğundan emin olun.

    ![Tanılamayı etkinleştir seçeneğine erişin](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Tanılama verilerine yönelik depolama hesabı belirtmek için üç nokta (...) düğmesini seçin.

    ![Kullanılacak depolama hesabını belirtin](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. **Depolama bağlantı dizesi oluştur** iletişim kutusunda azure Depolama Emulator, bir azure aboneliğini veya el ile girilen kimlik bilgilerini kullanarak bağlanmak isteyip istemediğinizi belirtin.

    ![Depolama hesabı iletişim kutusu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * **Microsoft Azure Depolama Emulator** seçeneğini belirlerseniz bağlantı dizesi olarak ayarlanır `UseDevelopmentStorage=true` .
   * **Aboneliğinizi** seçerseniz, kullanmak istediğiniz Azure aboneliğini seçip hesap adını girebilirsiniz. Azure aboneliklerinizi yönetmek için **hesapları Yönet**' i seçin.
   * **El ile girilen kimlik bilgilerini** seçerseniz, kullanmak istediğiniz Azure hesabının adını ve anahtarını girin.
5. **Tanılama yapılandırması** iletişim kutusunu görüntülemek için **Yapılandır**' ı seçin. **Genel** ve **günlük dizinleri** hariç her sekme, toplayacağınız bir tanılama veri kaynağını temsil eder. Varsayılan **genel** sekmesi aşağıdaki tanılama veri toplama seçeneklerini sunar: **Yalnızca hatalar**, **tüm bilgiler** ve **özel plan**. Yalnızca varsayılan **hatalar** seçeneği, uyarıları veya izleme iletilerini aktarmadığı için en az depolama alanı miktarını kullanır. **Tüm bilgi** seçeneği en çok bilgiyi aktarır, en çok depolama alanını kullanır ve bu nedenle en pahalı seçenektir.

   > [!NOTE]
   > "MB cinsinden disk kotası" için desteklenen minimum boyut 50MB ve varsayılan boyut 4 GB 'tır. Ancak, bellek dökümlerini topluyorsanız, bunu 10 GB gibi daha yüksek bir değere yükseltin.
   >

    ![Azure tanılama ve yapılandırmasını etkinleştirme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Bu örnekte, toplanan verileri özelleştirebilmeniz için **özel plan** seçeneğini belirleyin.
7. **Disk KOTASı MB olarak** kutusunda, tanılama verileri için depolama hesabınızda ne kadar alan ayrılacağını belirleyebilirsiniz. Varsayılan değeri değiştirebilir veya kabul edebilirsiniz.
8. Toplamak istediğiniz tanılama verilerinin her sekmesinde, **aktarımını \<log type\> Etkinleştir** onay kutusunu seçin. Örneğin, uygulama günlüklerini toplamak istiyorsanız **, uygulama günlükleri sekmesinde** **uygulama günlüklerinin aktarımını etkinleştir** onay kutusunu seçin. Ayrıca, her bir tanılama veri türü için gereken diğer bilgileri de belirtin. Her bir sekmeye ait yapılandırma bilgileri için, bu makalenin ilerleyen bölümlerinde **Tanılama veri kaynaklarını ayarlama** bölümüne bakın.
9. İstediğiniz tüm tanılama verilerinin toplanmasını etkinleştirdikten sonra **Tamam**' ı seçin.
10. Azure bulut hizmeti projenizi Visual Studio her zamanki gibi çalıştırın. Uygulamanızı kullanırken, etkinleştirdiğiniz günlük bilgileri belirttiğiniz Azure depolama hesabına kaydedilir.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Azure sanal makinelerinde tanılamayı açma
Bu Visual Studio Azure sanal makineleri için tanılama verilerini toplayabilirsiniz.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Azure sanal makinelerde tanılamayı açmak için

1. Bu Sunucu Gezgini Azure düğümünü seçin ve henüz bağlı değilken Azure aboneliğinize bağlanın.
2. Sanal Makineler **düğümünü** genişletin. Yeni bir sanal makine oluşturabilir veya var olan bir düğümü seçin.
3. İstediğiniz sanal makinenin kısayol menüsünde Yapılandır'ı **seçin.** Sanal makine yapılandırması iletişim kutusu görüntülenir.

    ![Azure sanal makinesi yapılandırma](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Henüz yüklenmemişse, Microsoft Monitoring Agent Tanılama uzantısını ekleyin. Bu uzantıyla Azure sanal makinesi için tanılama verilerini topabilirsiniz. Yüklü **Uzantılar altında,** Kullanılabilir bir **uzantı seçin** açılan listesinde Tanılama'yı Microsoft Monitoring Agent **seçin.**

    ![Azure sanal makine uzantısı yükleme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > Sanal makineleriniz için diğer tanılama uzantıları kullanılabilir. Daha fazla bilgi için [bkz. Sanal makine uzantıları ve özellikleri Windows.](/azure/virtual-machines/windows/extensions-features)
   >
   >
5. Uzantıyı eklemek ve Tanılama yapılandırması **iletişim kutusunu görüntülemek için** Ekle'yi **seçin.**
6. Depolama hesabı belirtmek için Yapılandır'ı **ve** ardından Tamam'ı **seçin.**

    Her sekme (Genel **ve Günlük** **Dizinleri dışında),** toplayabilirsiniz bir tanılama veri kaynağını temsil eder.

    ![Azure tanılama ve yapılandırmasını etkinleştirme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    Varsayılan sekme olan **Genel,** şu tanılama veri toplama seçeneklerini sunar: **Yalnızca hatalar,** **Tüm bilgiler** ve **Özel plan.** Varsayılan seçenek olan **Yalnızca hatalar**, uyarıları veya izleme iletilerini aktarmayarak en az depolama alanını alır. Tüm **bilgiler seçeneği** en fazla bilgiyi iletir ve bu nedenle depolama açısından en pahalı seçenektir.
7. Bu örnekte, toplanan **verileri özelleştirebileceğiniz** Özel plan seçeneğini belirleyin.
8. **MB olarak Disk Kotası** kutusu, tanılama verileri için depolama hesabınıza ne kadar alan ayırmak istediğinizi belirtir. 5. varsayılan değeri değiştirebilirsiniz.
9. Toplamak istediğiniz tanılama verileri sekmesinde Aktarımı Etkinleştir **onay kutusunu \<log type\>** seçin.

    Örneğin, uygulama günlüklerini toplamak için Uygulama **Günlükleri** sekmesindeKi Uygulama Günlüklerinin aktarımını etkinleştir onay **kutusunu** seçin. Ayrıca, her tanılama veri türü için gereken diğer tüm bilgileri belirtin. Her sekmeye ilişkin yapılandırma bilgileri için bu **makalenin ilerleyen kısımlarında Tanılama veri** kaynaklarını ayarlama bölümüne bakın.
10. İstediğiniz tüm tanılama verilerini toplamayı etkinleştirdikten sonra Tamam'ı **seçin.**
11. Güncelleştirilmiş projeyi kaydedin.

    Microsoft Azure Etkinlik **Günlüğü penceresindeki** bir ileti, sanal makinenin güncelleştirilmiş olduğunu gösterir.

## <a name="set-up-diagnostics-data-sources"></a>Tanılama veri kaynaklarını ayarlama
Tanılama veri toplamayı etkinleştirdikten sonra, tam olarak hangi veri kaynaklarını toplamak istediğinizi ve hangi bilgilerin toplanmış olduğunu seçebilirsiniz. Sonraki bölümlerde Tanılama yapılandırması iletişim kutusundaki **sekmeler ve** her yapılandırma seçeneğinin anlamı açıklanmaktadır.

### <a name="application-logs"></a>Uygulama günlükleri
Uygulama günlüklerinde bir web uygulaması tarafından üretilen tanılama bilgileri vardır. Uygulama günlüklerini yakalamak için Uygulama Günlüklerinin **aktarımını etkinleştir onay** kutusunu seçin. Uygulama günlüklerinin depolama hesabınıza aktarımı arasındaki aralığı artırmak veya azaltmak için Aktarım Dönemi **(dk) değerini** değiştirebilirsiniz. Günlük düzeyi değerini ayarerek günlükte yakalanan bilgi miktarını **da değiştirebilirsiniz.** Örneğin, daha fazla **bilgi almak için Ayrıntılı'ya** veya yalnızca kritik hataları **yakalamak** için Kritik'i seçin. Uygulama günlüklerini yayana belirli bir tanılama sağlayıcınız varsa, Sağlayıcı GUID kutusuna sağlayıcının GUID'ini ekleyerek **günlükleri yakalayabilirsiniz.**

  ![Uygulama günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Uygulama günlükleri hakkında daha fazla bilgi için [bkz. Web Apps'de tanılama Azure App Service.](/azure/app-service/web-sites-enable-diagnostic-log)

### <a name="windows-event-logs"></a>Windows olay günlükleri
Olay günlüklerini Windows için Olay Günlüklerinin aktarımını **Windows onay** kutusunu seçin. Olay günlüklerinin depolama hesabınıza aktarımı arasındaki aralığı artırmak veya azaltmak için Aktarım Dönemi **(min) değerini** değiştirebilirsiniz. Izlemek istediğiniz olay türlerinin onay kutularını seçin.

![Olay günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Azure SDK 2.6 veya sonraki bir sürümü kullanıyorsanız ve özel bir veri kaynağı belirtmek için metin kutusuna girin ve **\<Data source name\>** Ekle'yi **seçin.** Veri kaynağı diagnostics.cfcfg dosyasına eklenir.

Azure SDK 2.5 kullanıyorsanız ve özel bir veri kaynağı belirtmek istiyorsanız, bunu aşağıdaki örnekte olduğu gibi `WindowsEventLog` diagnostics.wadcfgx dosyasının bölümüne ebilirsiniz:

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>Performans sayaçları
Performans sayacı bilgileri, sistem performans sorunlarını bulup sistem ve uygulama performansında ince ayarlamalar yardımcı olabilir. Daha fazla bilgi için [bkz. Azure uygulamasında performans sayaçları oluşturma ve kullanma.](/azure/cloud-services/diagnostics-performance-counters) Performans sayaçlarını yakalamak için Performans **Sayaçlarının aktarımını etkinleştir onay** kutusunu seçin. Olay günlüklerinin depolama hesabınıza aktarımı arasındaki aralığı artırmak veya azaltmak için Aktarım Dönemi **(min) değerini** değiştirebilirsiniz. Izlemek istediğiniz performans sayaçları için onay kutularını seçin.

![Performans sayaçları](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Listede olmayan bir performans sayacını izlemek için önerilen söz dizimlerini kullanarak performans sayacını girin. ve ardından **Ekle'yi seçin.** Sanal makinede işletim sistemi, hangi performans sayaçlarını iz izley oIabilirsiniz belirler. Söz dizimi hakkında daha fazla bilgi [için bkz. Bir sayaç yolu belirtme.](/windows/win32/perfctrs/specifying-a-counter-path)

### <a name="infrastructure-logs"></a>Altyapı günlükleri
Altyapı günlüklerinde Azure tanılama altyapısı, RemoteAccess modülü ve RemoteForwarder modülü hakkında bilgiler bulunur. Altyapı günlükleri hakkında bilgi toplamak için Altyapı **Günlüklerinin aktarımını etkinleştir onay** kutusunu seçin. Altyapı günlüklerinin depolama hesabınıza aktarımı arasındaki aralığı artırmak veya azaltmak için Aktarım Dönemi **(dk) değerini** değiştirebilirsiniz.

![Tanılama altyapısı günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Daha fazla bilgi için [bkz. Günlük verilerini Azure Tanılama.](/azure/cloud-services/cloud-services-dotnet-diagnostics)

### <a name="log-directories"></a>Günlük dizinleri
Günlük dizinleri, seçtiğiniz Internet Information Services (IIS) istekleri, başarısız istekler veya klasörler için günlük dizinlerinden toplanan verilere sahip olur. Günlük dizinlerini yakalamak için Günlük **Dizinlerinin aktarımını etkinleştir onay** kutusunu seçin. Günlüklerin depolama hesabınıza aktarımı arasındaki aralığı artırmak veya azaltmak için Aktarım Dönemi **(dk) değerini** değiştirebilirsiniz.

IIS Günlükleri ve Başarısız İstek günlükleri gibi toplamak istediğiniz **günlüklerin onay** **kutularını** seçin. Varsayılan depolama kapsayıcısı adları sağlanır, ancak adları değiştirebilirsiniz.

Günlükleri herhangi bir klasörden yakalayabilirsiniz. Mutlak Dizinden Günlük **bölümünde yolu belirtin ve** ardından Dizin **Ekle'yi seçin.** Günlükler belirtilen kapsayıcılarda yakalanır.

![Günlük dizinleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>ETW günlükleri
[Windows](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) için Olay İzleme'yi kullanıyorsanız ve ETW günlüklerini yakalamak istiyorsanız ETW Günlüklerinin **aktarımını etkinleştir onay** kutusunu işaretleyin. Günlüklerin depolama hesabınıza aktarımı arasındaki aralığı artırmak veya azaltmak için Aktarım Dönemi **(dk) değerini** değiştirebilirsiniz.

Olaylar, belirttiğiniz olay kaynaklarından ve olay bildirimlerinden yakalanır. Olay kaynağı belirtmek için Olay Kaynakları **bölümünde bir ad** girin ve Olay Kaynağı **Ekle'yi seçin.** Benzer şekilde, Olay Bildirimleri bölümünde bir olay bildirimi **belirtebilirsiniz** ve ardından Olay Bildirimi **Ekle'yi seçin.**

![ETW günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

ETW çerçevesi, [System.Diagnostics.aspx](/dotnet/api/system.diagnostics) ASP.NET sınıfları aracılığıyla bu çerçevede de desteklemektedir. Standart [System.Diagnostics.aspx](/dotnet/api/system.diagnostics) sınıflarından devralan ve sınıflarını genişleten Microsoft.WindowsAzure.Diagnostics ad alanı, [System.Diagnostics.aspx'in](/dotnet/api/system.diagnostics) Azure ortamında günlüğe kaydetme çerçevesi olarak kullanımını sağlar. Daha fazla bilgi için [bkz.](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) Sanal makinelerde günlüğe kaydetme ve Microsoft Azure denetimi alma ve Azure Cloud Services [makinelerde tanılamayı etkinleştirme.](/azure/cloud-services/cloud-services-dotnet-diagnostics)

### <a name="crash-dumps"></a>Kilitlenme bilgi dökümleri
Rol örneği kilitleniyorsa ilgili bilgileri yakalamak için Kilitlenme Bilgi Dökümlerinin **aktarımını etkinleştir onay kutusunu** seçin. (Bu ASP.NET çoğu özel durumu işlemesi nedeniyle, bu genellikle yalnızca çalışan rolleri için yararlıdır.) Kilitlenme dökümleri için ayrılmış depolama alanı yüzdesini artırmak veya azaltmak için Dizin Kotası **(%) değerini** seçin. Kilitlenme dökümlerini depolandığı depolama kapsayıcısı değiştirebilir ve Tam döküm veya Mini döküm yakalamak **isteyip** **istemediklerini** seçin.

İzlenmiş olan işlemler sonraki ekran görüntüsünde listelenmiştir. Yakalamak istediğiniz işlemler için onay kutularını seçin. Listeye başka bir işlem eklemek için işlem adını girin ve İşlem **Ekle'yi seçin.**

![Kilitlenme bilgi dökümleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Daha fazla bilgi için bkz. Microsoft Azure ve [Microsoft Azure](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) Tanılama Bölüm 4: Özel günlük bileşenleri ve Azure Tanılama [1.3 değişikliklerini denetleme.](https://www.red-gate.com/simple-talk/cloud/platform-as-a-service/microsoft-azure-diagnostics-part-4-custom-logging-components-and-azure-diagnostics-1.3-changes/)

## <a name="view-the-diagnostics-data"></a>Tanılama verilerini görüntüleme
Bir bulut hizmeti veya sanal makine için tanılama verilerini topdikten sonra görüntüebilirsiniz.

### <a name="to-view-cloud-service-diagnostics-data"></a>Bulut hizmeti tanılama verilerini görüntülemek için
1. Bulut hizmetinizi her zamanki gibi dağıtın ve çalıştırın.
2. Tanılama verilerini, oluşturulan bir raporda veya Visual Studio tablolarda görüntüebilirsiniz. Verileri bir raporda görüntülemek için Cloud Explorer veya Sunucu Gezgini açın, istediğiniz rolün düğüm kısayol menüsünü açın ve ardından **tanılama verilerini görüntüle**' yi seçin.

    ![Tanılama verilerini görüntüle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Kullanılabilir verileri gösteren bir rapor görüntülenir.

    ![Microsoft Azure Visual Studio tanılama raporu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    En son veriler gösterilmemişse, aktarım süresinin geçmesini beklemeniz gerekebilir.

    Verileri hemen güncelleştirmek için **Yenile** bağlantısını seçin. Verilerin otomatik olarak güncelleştirilmesini sağlamak için **Otomatik Yenile** açılan liste kutusunda bir Aralık seçin. hata verilerini dışarı aktarmak için, Excel çalışma sayfasında açabileceğiniz bir virgülle ayrılmış değer dosyası oluşturmak üzere **CSV 'ye aktar** düğmesini seçin.

    Bulut Gezgini ' nde veya Sunucu Gezgini, dağıtımla ilişkili depolama hesabını açın.
3. Tablo görüntüleyicisinde tanılama tablolarını açın ve ardından topladığınız verileri gözden geçirin. IIS günlükleri ve özel Günlükler için bir blob kapsayıcısı açabilirsiniz. Aşağıdaki tabloda, farklı günlük dosyaları için verileri içeren tablolar veya blob kapsayıcıları listelenmektedir. Bu günlük dosyası için verilere ek olarak, tablo girişleri **Eventtickcount**, **DeploymentId**, **rol** ve **roleınstance**, verileri hangi sanal makine ve rolün oluşturulduğunu belirlemenize yardımcı olur.

   | Tanılama verileri | Description | Konum |
   | --- | --- | --- |
   | Uygulama günlükleri |**System. Diagnostics. Trace** sınıfının yöntemlerini çağırarak kodunuzun oluşturduğu Günlükler. |WADLogsTable |
   | Olay günlükleri |sanal makinelerdeki Windows olay günlüklerinden alınan veriler. Windows bilgileri bu günlüklere depolar, ancak uygulamalar ve hizmetler, hataları veya günlük bilgilerini raporlamak için günlükleri de kullanır. |WADWindowsEventLogsTable |
   | Performans sayaçları |Sanal makinede bulunan herhangi bir performans sayacı üzerinde veri toplayabilirsiniz. İşletim sistemi, bellek kullanımı ve işlemci zamanı gibi birçok istatistiği içeren performans sayaçlarını sağlar. |WADPerformanceCountersTable |
   | Altyapı günlükleri |Tanılama altyapısının kendisinden oluşturulan Günlükler. |WADDiagnosticInfrastructureLogsTable |
   | IIS günlükleri |Web isteklerini kaydeden Günlükler. Bulut hizmetiniz önemli miktarda trafik alırsa, bu Günlükler uzun olabilir. Bu verileri yalnızca ihtiyacınız olduğunda toplamak ve depolamak iyi bir fikirdir. |Başarısız-istek günlüklerini, bu dağıtım, rol ve örnek için bir yol altında wad-IIS-failedreqlogs altında bulunan BLOB kapsayıcısında bulabilirsiniz. Tüm günlükleri wad-IIS-LogFiles altında bulabilirsiniz. Her bir dosyanın girişleri Waddizinler tablosunda yapılır. |
   | Kilitlenme bilgi dökümleri |Bulut hizmetinizin işleminin (genellikle bir çalışan rolü) ikili görüntülerini sağlar. |WAD-Crush-blob kapsayıcısı dökümünü alır |
   | Özel günlük dosyaları |Önceden tanımlamış olduğunuz verilerin günlükleri. |Depolama hesabınızdaki özel günlük dosyalarının konumunu kod içinde belirtebilirsiniz. Örneğin, özel bir blob kapsayıcısı belirtebilirsiniz. |
4. Herhangi bir türün verileri kesilmişse, bu veri türü için arabelleği artırmayı deneyebilir veya sanal makineden depolama hesabınıza veri aktarımları arasındaki aralığı kısaltaştırın.
5. Seçim Genel depolama maliyetlerini azaltmak için depolama hesabından verileri her zaman temizleyin.
6. Tam bir dağıtım yaptığınızda, tanılama. cscfg dosyası (Azure SDK 2,5 için. wadcfgx) Azure 'da güncelleştirilir ve bulut hizmetiniz, tanılama yapılandırmanızda yapılan tüm değişiklikleri seçer. Bunun yerine var olan bir dağıtımı güncelleştirirseniz,. cscfg dosyası Azure 'da güncellenmez. Yine de, sonraki bölümdeki adımları izleyerek tanılama ayarlarını değiştirebilirsiniz. Tam dağıtım gerçekleştirme ve var olan bir dağıtımı güncelleştirme hakkında daha fazla bilgi için bkz. [Azure Uygulama Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-view-virtual-machine-diagnostics-data"></a>Sanal makine tanılama verilerini görüntülemek için
1. Sanal makinenin kısayol menüsünde **tanılama verilerini görüntüle**' yi seçin.

    ![Azure sanal makinesinde tanılama verilerini görüntüleme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    **Tanılama Özeti** iletişim kutusu görüntülenir.

    ![Azure sanal makine tanılama Özeti](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    En son veriler gösterilmemişse, aktarım süresinin geçmesini beklemeniz gerekebilir.

    Verileri hemen güncelleştirmek için **Yenile** bağlantısını seçin. Verilerin otomatik olarak güncelleştirilmesini sağlamak için **Otomatik Yenile** açılan liste kutusunda bir Aralık seçin. hata verilerini dışarı aktarmak için, Excel çalışma sayfasında açabileceğiniz bir virgülle ayrılmış değer dosyası oluşturmak üzere **CSV 'ye aktar** düğmesini seçin.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Dağıtımdan sonra bulut hizmeti tanılamayı ayarla
Zaten çalışmakta olan bir bulut hizmetiyle ilgili bir sorunu araştırıyorsanız, rolü ilk olarak dağıtmadan önce belirtmediğiniz verileri toplamak isteyebilirsiniz. Bu durumda, Sunucu Gezgini ayarları değiştirerek bu verileri toplamaya başlayabilirsiniz. Tanılama **yapılandırması** iletişim kutusunu, örneğin veya rol için kısayol menüsünden açıp açdığınıza bağlı olarak, tek bir örnek veya bir roldeki tüm örnekler için tanılamayı ayarlayabilirsiniz. Rol düğümünü yapılandırırsanız, yaptığınız tüm değişiklikler tüm örneklere uygulanır. Örnek düğümünü yapılandırırsanız, yaptığınız tüm değişiklikler yalnızca bu örnek için geçerlidir.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Çalışan bir bulut hizmeti için tanılamayı ayarlamak için
1. Sunucu Gezgini ' de, **Cloud Services** düğümünü genişletin ve ardından araştırmak istediğiniz rolü veya örneği (ya da her ikisini) bulmak için düğüm listesini genişletin.

    ![Tanılama yapılandırma](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. örnek düğümü veya rol düğümünün kısayol menüsünde, **tanılama Ayarlar güncelleştir**' i seçin ve ardından toplamak istediğiniz tanılama ayarlarını seçin.

    Yapılandırma ayarları hakkında daha fazla bilgi için bu makaledeki **Tanılama veri kaynaklarını ayarlama** bölümüne bakın. Tanılama verilerini görüntüleme hakkında daha fazla bilgi için bu makaledeki **tanılama verilerini görüntüleyin** bölümüne bakın.

    Sunucu Gezgini ' de veri toplamayı değiştirirseniz, bulut hizmetinizi tamamen yeniden dağıtana kadar değişiklikler etkin kalır. Varsayılan yayımlama ayarlarını kullanırsanız, değişikliklerin üzerine yazılmaz. Varsayılan yayımlama ayarı, tam yeniden dağıtım yapmak yerine mevcut dağıtımı güncelleştirmedir. dağıtım zamanında ayarların açık olduğundan emin olmak için, yayımla sihirbazındaki **gelişmiş Ayarlar** sekmesine gidin ve ardından **dağıtım güncelleştirmesi** onay kutusunu temizleyin. Bu onay kutusu temizlenerek, ayarlar. wadcfgx (veya. wadcfg) dosyasında, rol için **Özellikler** Düzenleyicisi aracılığıyla ayarlanmış olanlarla döndürülür. Dağıtımınızı güncelleştirirseniz, Azure önceki ayarları tutar.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Azure bulut hizmeti sorunlarını giderme
Bulut hizmeti projelerinizle ilgili sorunlar yaşıyorsanız ("meşgul" durumunda kalmış olan bir rol ya da bir iç sunucu hatası oluşturursa, sorunu tanılamak ve onarmak için kullanabileceğiniz araçlar ve teknikler vardır. Yaygın sorunların ve çözümlerin belirli örnekleri için ve bu hataları tanılamak ve onarmak üzere kullanabileceğiniz kavram ve araçlara genel bir bakış için bkz. [Azure PaaS işlem Tanılama verileri](/archive/blogs/kwill/windows-azure-paas-compute-diagnostics-data).

## <a name="q--a"></a>Soru-Cevap
**Arabellek boyutu nedir ve ne kadar çok olmalıdır?**

Her bir sanal makine örneğinde, kotalar, yerel dosya sisteminde ne kadar tanılama verisi depolanabileceğini sınırlandırır. Ayrıca, kullanılabilir her bir tanılama verileri türü için bir arabellek boyutu belirtirsiniz. Bu arabellek boyutu, bu tür veriler için tek bir kota gibi davranır. Genel kotayı ve kalan bellek miktarını öğrenmek için tanılama veri türü iletişim kutusunun alt bölümüne bakın. Daha büyük arabellekler veya daha fazla veri türü belirtirseniz, genel kotayı değiştireceksiniz. Diagnostics. wadcfg veya. wadcfgx yapılandırma dosyasını değiştirerek genel kotayı değiştirebilirsiniz. Tanılama verileri, uygulamanızın verileriyle aynı dosya sisteminde depolanır. Uygulamanız büyük miktarda disk alanı kullanıyorsa, genel tanılama kotasını artırmanız gerekmez.

**Aktarım dönemi nedir ve ne kadar süreyle olmalıdır?**

Aktarım süresi, veri yakalamaları arasında geçen sürenin miktarıdır. Her aktarım süresinden sonra, veriler sanal bir makinedeki yerel dosya sisteminden Depolama hesabınızdaki tablolara taşınır. Toplanan veri miktarı, aktarım döneminin sonundan önce kotayı aşarsa, eski veriler atılır. Verileriniz arabellek boyutunu veya genel kotayı aştığından verileri kaybetmeniz durumunda, aktarım süresini azaltmak isteyebilirsiniz.

**Zaman damgaları hangi saat dilimlidir?**

Zaman damgaları, bulut hizmetinizi barındıran veri merkezinin yerel saat dilimlidir. Günlük tablolarındaki aşağıdaki üç zaman damgası sütunu kullanılır:

* **Ön IBU zaman damgası**: etkinliğin ETW zaman damgası. Diğer bir deyişle, olayın istemciden günlüğe kaydedildiği zaman.
* **TIMESTAMP:** **PreciseTimeStamp** değeri, karşıya yükleme sıklığı sınırına yuvarlanır. Örneğin, karşıya yükleme sıklığınız 5 dakika ve olay saati 00:17:12 ise TIMESTAMP 00:15:00 olur.
* **Zaman damgası:** Varlığın Azure tablosunda oluşturulmuş olduğu zaman damgası.

**Nasıl yaparım? bilgileri toplarken maliyetleri nasıl yönetebilirsiniz?**

Varsayılan ayarlar (**Günlük düzeyi Hata** olarak ayarlanır **ve** **Aktarım dönemi** 1 dakika olarak **ayarlanır)** maliyetleri en aza indirmek için tasarlanmıştır. Daha fazla tanılama verisi toplayan veya aktarım dönemini azaltan işlem maliyetleriniz artar. Size gerekenden fazla veri toplamayın ve artık ihtiyacınız kalmadan veri toplamayı devre dışı bırakmayı unutmayın. Bu makalenin başlarında açıklandığı gibi, çalışma zamanında bile her zaman yeniden etkinleştirabilirsiniz.

**Nasıl yaparım? istek günlüklerini IIS'den mi toplayabilirsiniz?**

Varsayılan olarak, IIS başarısız istek günlüklerini toplamaz. Web rolünüz için web.config dosyasını düzenleyerek başarısız istek günlüklerini toplamak için IIS'yi kurabilirsiniz.

**OnStart gibi RoleEntryPoint yöntemlerinden izleme bilgileri al değilim. Ne oldu?**

**RoleEntryPoint yöntemleri,** IIS'de değil WAIISHost.exe bağlamında çağrılır. normalde izlemeyi web.config yapılandırma bilgileri geçerli değildir. Bu sorunu çözmek için web .config projenize bir dosya ekleyin ve **dosyayı RoleEntryPoint** kodunu içeren çıkış derlemesi ile eş olacak şekilde adlaştırabilirsiniz. Varsayılan web rolü projesinde, .config dosyasının adı WAIISHost.exe.config. Bu dosyaya aşağıdaki satırları ekleyin:

```xml
<system.diagnostics>
  <trace>
      <listeners>
          <add name “AzureDiagnostics” type=”Microsoft.WindowsAzure.Diagnostics.DiagnosticMonitorTraceListener”>
              <filter type=”” />
          </add>
      </listeners>
  </trace>
</system.diagnostics>
```

Özellikler penceresinde **Çıkış** Dizinine Kopyala **özelliğini Her zaman** kopyala olarak **ayarlayın.**

## <a name="next-steps"></a>Sonraki adımlar
Azure'da tanılama günlüğü hakkında daha fazla bilgi edinmek için bkz. [Azure Cloud Services](/azure/cloud-services/cloud-services-dotnet-diagnostics) ve sanal makinelerde tanılamayı etkinleştirme ve Web Apps için [tanılama Azure App Service.](/azure/app-service/web-sites-enable-diagnostic-log)
