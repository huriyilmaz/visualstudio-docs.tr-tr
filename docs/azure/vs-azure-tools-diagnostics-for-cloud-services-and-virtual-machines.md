---
title: Azure Cloud Services ve VM 'Ler için tanılama
description: Visual Studio 'da Azure bulut hizmetlerinde ve sanal makinelerde (VM) hata ayıklama için tanılamayı ayarlamayı öğrenin.
author: ghogen
manager: jillfra
ms.assetid: e70cd7b4-6298-43aa-adea-6fd618414c26
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 06/28/2018
ms.author: mikejo
ms.openlocfilehash: 7e0d261edfd946aed5d459ec732f652448fc46c0
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2020
ms.locfileid: "89740135"
---
# <a name="set-up-diagnostics-for-azure-cloud-services-and-virtual-machines"></a>Azure Cloud Services ve sanal makineler için tanılamayı ayarlama
Bir Azure bulut hizmetinde veya sanal makinede sorun gidermeniz gerektiğinde Azure Tanılama daha kolay bir şekilde kurmak için Visual Studio 'Yu kullanabilirsiniz. Tanılama, bulut hizmetinizi çalıştıran sanal makinelerde ve sanal makine örneklerinde sistem verilerini ve günlük verilerini yakalar. Tanılama verileri, seçtiğiniz bir depolama hesabına aktarılır. Azure 'da tanılama günlüğü hakkında daha fazla bilgi için bkz. [Azure App Service Web Apps için tanılama günlüğünü etkinleştirme](/azure/app-service/web-sites-enable-diagnostic-log).

Bu makalede, Visual Studio 'yu kullanarak Azure Tanılama, hem dağıtımdan önce hem de sonra kurulumu yapmak için nasıl kullanacağınızı göstereceğiz. Azure sanal makinelerinde tanılamayı ayarlamayı, toplanacak tanılama bilgilerinin türlerini seçmenizi ve toplandıktan sonra bilgilerin nasıl görüntüleneceğini öğrenin.

Azure Tanılama ayarlamak için aşağıdaki seçeneklerden birini kullanabilirsiniz:

* Tanılama ayarlarını, Visual Studio 'daki **Tanılama yapılandırması** iletişim kutusunda değiştirin. Ayarlar, Diagnostics. wadcfgx adlı bir dosyaya kaydedilir (Azure SDK 2,4 ve önceki sürümlerde, dosya Diagnostics. wadcfg olarak adlandırılır). Ayrıca yapılandırma dosyasını doğrudan değiştirebilirsiniz. Dosyayı el ile güncelleştirirseniz, yapılandırma değişiklikleri bulut hizmetini Azure 'a bir sonraki dağıtışınızda veya hizmet öykünücüsünde çalıştırıldığında etkili olur.
* Bulut hizmeti veya çalıştıran bir sanal makine için tanılama ayarlarını değiştirmek üzere Visual Studio 'da Cloud Explorer veya Sunucu Gezgini kullanın.

## <a name="azure-sdk-26-diagnostics-changes"></a>Azure SDK 2,6 tanılama değişiklikleri
Aşağıdaki değişiklikler, Visual Studio 'da Azure SDK 2,6 ve üzeri projeler için geçerlidir:

* Yerel öykünücü artık tanılamayı desteklemektedir. Bu, tanılama verilerini toplayabileceğiniz ve Visual Studio 'da geliştirme ve test yaparken uygulamanızın doğru izlemeleri oluşturduğundan emin olmanızı sağlayan anlamına gelir. `UseDevelopmentStorage=true`Azure Storage öykünücüsü ' nü kullanarak, Visual Studio 'da bulut hizmeti projenizi çalıştırırken, bağlantı dizesi tanılama veri toplamayı etkinleştirir. Tüm Tanılama verileri, geliştirme depolama depolama hesabında toplanır.
* Tanılama depolama hesabı bağlantı dizesi, `Microsoft.WindowsAzure.Plugins.Diagnostics.ConnectionString` hizmet yapılandırma (. cscfg) dosyasında depolanır. Azure SDK 2,5 ' de tanılama depolama hesabı, Diagnostics. wadcfgx dosyasında belirtilir.

Bağlantı dizesi, Azure SDK 2,6 ve üzeri sürümlerde Azure SDK 2,4 ve önceki sürümlerde bazı önemli yollarla farklı çalışır:

* Azure SDK 2,4 ve önceki sürümlerde, bağlantı dizesi, tanılama günlüklerini aktarmaya yönelik depolama hesabı bilgilerini almak için tanılama eklentisi tarafından bir çalışma zamanı olarak kullanılır.
* Azure SDK 2,6 ve sonraki sürümlerinde, Visual Studio, yayımlama sırasında uygun depolama hesabı bilgileriyle Azure Tanılama uzantısını ayarlamak için tanılama bağlantı dizesini kullanır. Visual Studio 'Nun yayımlama sırasında kullandığı farklı hizmet yapılandırmalarına yönelik farklı depolama hesapları tanımlamak için bağlantı dizesini kullanabilirsiniz. Ancak, tanılama eklentisi Azure SDK 2,5 sonrasında kullanılamadığından,. cscfg dosyası kendisi için tanılama uzantısını ayarlayamayabilir. Uzantıyı Visual Studio veya PowerShell gibi araçları kullanarak ayrı olarak ayarlamanız gerekir.
* PowerShell kullanarak tanılama uzantısını ayarlama sürecini basitleştirmek için, Visual Studio 'daki paket çıktısı her rolün tanılama uzantısının ortak yapılandırma XML 'sini içerir. Visual Studio, genel yapılandırmadaki depolama hesabı bilgilerini doldurmak için tanılama bağlantı dizesini kullanır. Ortak yapılandırma dosyaları uzantılar klasöründe oluşturulur. Ortak yapılandırma dosyaları, PaaSDiagnostics adlandırma düzenlerini kullanır. &lt; rol adı \>.PubConfig.xml. Herhangi bir PowerShell tabanlı dağıtımlar, her yapılandırmayı bir rolle eşlemek için bu kalıbı kullanabilir.
* [Azure Portal](https://portal.azure.com) , tanılama verilerine erişmek için. cscfg dosyasındaki bağlantı dizesini kullanır. Veriler **izleme** sekmesinde görüntülenir. Bağlantı dizesi, hizmeti portalda ayrıntılı izleme verilerini gösterecek şekilde ayarlamak için gereklidir.

## <a name="migrate-projects-to-azure-sdk-26-and-later"></a>Projeleri Azure SDK 2,6 ve üzeri sürümlere geçirme
Azure SDK 2,5 ' den Azure SDK 2,6 veya sonraki bir sürüme geçirdiğinizde,. wadcfgx dosyasında belirtilen bir tanılama depolama hesabınız varsa, depolama hesabı bu dosyada kalır. Farklı depolama yapılandırmalarının farklı depolama hesaplarını kullanma esnekliğinden faydalanmak için bağlantı dizesini projenize el ile ekleyin. Bir projeyi Azure SDK 2,4 veya önceki sürümlerden Azure SDK 2,6 ' ye geçiriyorsanız, tanılama bağlantı dizeleri korunur. Bununla birlikte, önceki bölümde açıklanan şekilde, bağlantı dizelerinin Azure SDK 2,6 ' de nasıl ele alındığına ilişkin değişikliklere göz önüne alın.

### <a name="how-visual-studio-determines-the-diagnostics-storage-account"></a>Visual Studio 'Nun tanılama depolama hesabını nasıl belirlediği
* . Cscfg dosyasında bir tanılama bağlantı dizesi belirtilmişse, Visual Studio bunu yayınlama sırasında ve paketleme sırasında ortak yapılandırma XML dosyalarını oluşturduğunda, tanılama uzantısını ayarlamak için kullanır.
* . Cscfg dosyasında bir tanılama bağlantı dizesi belirtilmemişse, Visual Studio, yayımlama için tanılama uzantısını ayarlamak ve paketleme sırasında ortak yapılandırma XML dosyalarını oluşturmak için. wadcfgx dosyasında belirtilen depolama hesabını kullanmaya geri döner.
* . Cscfg dosyasındaki tanılama bağlantı dizesi. wadcfgx dosyasındaki depolama hesabından önceliklidir. . Cscfg dosyasında bir tanılama bağlantı dizesi belirtilirse, Visual Studio bu bağlantı dizesini kullanır ve. wadcfgx içindeki depolama hesabını yoksayar.

### <a name="what-does-the-update-development-storage-connection-strings-check-box-do"></a>"Geliştirme depolama bağlantı dizelerini güncelleştir..." onay kutusu yapılsın mı?
**Microsoft Azure 'de yayımlarken Microsoft Azure depolama hesabı kimlik bilgileriyle tanılama ve önbelleğe alma Için güncelleştirme geliştirme depolama bağlantı dizeleri** , yayımlama sırasında belirttiğiniz Azure depolama hesabı ile tüm geliştirme depolama hesabı bağlantı dizelerini güncelleştirmenin kolay bir yoludur.

Örneğin, bu onay kutusunu seçerseniz ve tanılama bağlantı dizesi belirtiyorsa `UseDevelopmentStorage=true` , projeyi Azure 'da yayımladığınızda, Visual Studio otomatik olarak tanılama bağlantı dizesini Yayımla sihirbazında belirttiğiniz depolama hesabıyla güncelleştirir. Ancak, tanılama bağlantı dizesi olarak gerçek bir depolama hesabı belirtilmişse, bunun yerine bu hesap kullanılır.

## <a name="diagnostics-functionality-differences-in-azure-sdk-24-and-earlier-vs-azure-sdk-25-and-later"></a>Azure SDK 2,4 ve önceki sürümlerinde ve Azure SDK 2,5 ve üzeri ile tanılama işlevselliği farklılıkları
Projenizi Azure SDK 2,4 ve önceki sürümlerden Azure SDK 2,5 veya sonraki bir sürüme yükseltiyorsanız aşağıdaki tanılama işlevselliği farklarını aklınızda bulundurun:

* **Yapılandırma API 'leri kullanım dışıdır**. Tanılamayı programsal olarak yapılandırma, Azure SDK 2,4 ve önceki sürümlerde kullanılabilir, ancak Azure SDK 2,5 ve sonraki sürümlerde kullanım dışıdır. Tanılama yapılandırmanız Şu anda kodda tanımlıysa, tanılama 'nın çalışmaya devam etmesini sağlamak için, geçirilen projedeki bu ayarları sıfırdan yeniden yapılandırmanız gerekir. Azure SDK 2,4 için tanılama yapılandırma dosyası, Diagnostics. wadcfg ' dir. Azure SDK 2,5 ve üzeri için tanılama yapılandırma dosyası, Diagnostics. wadcfgx ' dir.
* **Bulut hizmeti uygulamalarına yönelik Tanılamalar yalnızca rol düzeyinde yapılandırılabilir**. Azure SDK 2,5 ve üzeri sürümlerde, örnek düzeyinde bulut hizmeti uygulamaları için tanılamayı ayarlayamazsınız.
* **Uygulamanızı her dağıttığınız zaman tanılama yapılandırması güncelleştirilir**. Bu, tanılama yapılandırmanızı Visual Studio Sunucu Gezgini değiştirirseniz ve sonra uygulamanızı yeniden dağıtırsanız eşlik sorunlarına neden olabilir.
* **Azure SDK 2,5 ve üzeri sürümlerde kilitlenme dökümleri, kodda değil, tanılama yapılandırma dosyasında yapılandırılır**. Kod içinde yapılandırılmış kilitlenme dökümlerinden sahipseniz, yapılandırmayı koddan yapılandırma dosyasına el ile aktarmanız gerekir. Kilitlenme dökümü, Azure SDK 2,6 ' e geçiş sırasında aktarılmaz.

## <a name="turn-on-diagnostics-in-cloud-service-projects-before-you-deploy-them"></a>Bulut hizmeti projelerinde tanılamayı dağıtmadan önce etkinleştirin
Visual Studio 'da, dağıtımdan önce hizmet öykünücüsünde hizmeti çalıştırdığınızda Azure 'da çalışan roller için tanılama verileri toplayabilirsiniz. Visual Studio 'da tanılama ayarlarındaki tüm değişiklikler, Diagnostics. wadcfgx yapılandırma dosyasına kaydedilir. Bu ayarlar, bulut hizmetinizi dağıtırken tanılama verilerinin kaydedildiği depolama hesabını belirtir.

[!INCLUDE [cloud-services-wad-warning](./includes/cloud-services-wad-warning.md)]

### <a name="to-turn-on-diagnostics-in-visual-studio-before-deployment"></a>Dağıtımdan önce Visual Studio 'da tanılamayı açmak için

1. Rolün kısayol menüsünde, **Özellikler**' i seçin. Rolün **Özellikler** Iletişim kutusunda **yapılandırma** sekmesini seçin.
2. **Tanılama** bölümünde, **tanılamayı etkinleştir** onay kutusunun seçili olduğundan emin olun.

    ![Tanılamayı etkinleştir seçeneğine erişin](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796660.png)
3. Tanılama verilerine yönelik depolama hesabı belirtmek için üç nokta (...) düğmesini seçin.

    ![Kullanılacak depolama hesabını belirtin](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796661.png)
4. **Depolama bağlantı dizesi oluştur** iletişim kutusunda, Azure depolama öykünücüsü, bir Azure aboneliği veya el ile girilen kimlik bilgilerini kullanarak bağlanmak isteyip istemediğinizi belirtin.

    ![Depolama hesabı iletişim kutusu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796662.png)

   * **Microsoft Azure depolama öykünücüsü**' yi seçerseniz bağlantı dizesi olarak ayarlanır `UseDevelopmentStorage=true` .
   * **Aboneliğinizi**seçerseniz, kullanmak istediğiniz Azure aboneliğini seçip hesap adını girebilirsiniz. Azure aboneliklerinizi yönetmek için **hesapları Yönet**' i seçin.
   * **El ile girilen kimlik bilgilerini**seçerseniz, kullanmak istediğiniz Azure hesabının adını ve anahtarını girin.
5. **Tanılama yapılandırması** iletişim kutusunu görüntülemek için **Yapılandır**' ı seçin. **Genel** ve **günlük dizinleri**hariç her sekme, toplayacağınız bir tanılama veri kaynağını temsil eder. Varsayılan **genel** sekmesi aşağıdaki tanılama veri toplama seçeneklerini sunar: **Yalnızca hatalar**, **tüm bilgiler**ve **özel plan**. Yalnızca varsayılan **hatalar** seçeneği, uyarıları veya izleme iletilerini aktarmadığı için en az depolama alanı miktarını kullanır. **Tüm bilgi** seçeneği en çok bilgiyi aktarır, en çok depolama alanını kullanır ve bu nedenle en pahalı seçenektir.

   > [!NOTE]
   > "MB cinsinden disk kotası" için desteklenen minimum boyut 50MB ve varsayılan boyut 4 GB 'tır. Ancak, bellek dökümlerini topluyorsanız, bunu 10 GB gibi daha yüksek bir değere yükseltin.
   >

    ![Azure tanılama ve yapılandırmasını etkinleştirme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)
6. Bu örnekte, toplanan verileri özelleştirebilmeniz için **özel plan** seçeneğini belirleyin.
7. **Disk KOTASı MB olarak** kutusunda, tanılama verileri için depolama hesabınızda ne kadar alan ayrılacağını belirleyebilirsiniz. Varsayılan değeri değiştirebilir veya kabul edebilirsiniz.
8. Toplamak istediğiniz tanılama verilerinin her sekmesinde, **aktarımını \<log type\> Etkinleştir** onay kutusunu seçin. Örneğin, uygulama günlüklerini toplamak istiyorsanız **, uygulama günlükleri sekmesinde** **uygulama günlüklerinin aktarımını etkinleştir** onay kutusunu seçin. Ayrıca, her bir tanılama veri türü için gereken diğer bilgileri de belirtin. Her bir sekmeye ait yapılandırma bilgileri için, bu makalenin ilerleyen bölümlerinde **Tanılama veri kaynaklarını ayarlama** bölümüne bakın.
9. İstediğiniz tüm tanılama verilerinin toplanmasını etkinleştirdikten sonra **Tamam**' ı seçin.
10. Azure bulut hizmeti projenizi her zamanki gibi Visual Studio 'da çalıştırın. Uygulamanızı kullanırken, etkinleştirdiğiniz günlük bilgileri belirttiğiniz Azure depolama hesabına kaydedilir.

## <a name="turn-on-diagnostics-on-azure-virtual-machines"></a>Azure sanal makinelerinde tanılamayı açma
Visual Studio 'da Azure sanal makineleri için tanılama verileri toplayabilirsiniz.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Azure sanal makinelerinde tanılamayı açmak için

1. Sunucu Gezgini ' de, Azure düğümünü seçin ve henüz bağlı değilseniz Azure aboneliğinize bağlanın.
2. **Sanal makineler** düğümünü genişletin. Yeni bir sanal makine oluşturabilir veya var olan bir düğümü seçebilirsiniz.
3. İstediğiniz sanal makinenin kısayol menüsünde **Yapılandır**' ı seçin. Sanal makine yapılandırması iletişim kutusu görüntülenir.

    ![Azure sanal makinesini yapılandırma](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. Zaten yüklenmemişse Microsoft Monitoring Agent tanılama uzantısını ekleyin. Bu uzantıyla birlikte Azure sanal makinesi için tanılama verileri toplayabilirsiniz. **Yüklü uzantılar**altında, **kullanılabilir uzantı Seç** aşağı açılan liste kutusunda **Microsoft Monitoring Agent tanılama**' yı seçin.

    ![Azure sanal makine uzantısı 'nı yükler](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > Diğer tanılama uzantıları, sanal makineleriniz için kullanılabilir. Daha fazla bilgi için bkz. [Windows Için sanal makine uzantıları ve özellikleri](/azure/virtual-machines/windows/extensions-features).
   >
   >
5. Uzantıyı eklemek ve **Tanılama yapılandırması** iletişim kutusunu görüntülemek için **Ekle**' yi seçin.
6. Bir depolama hesabı belirtmek için **Yapılandır**' ı seçin ve ardından **Tamam**' ı seçin.

    Her sekme ( **genel** ve **günlük dizinleri**hariç), toplayacağınız bir tanılama veri kaynağını temsil eder.

    ![Azure tanılama ve yapılandırmasını etkinleştirme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    Varsayılan sekmesi olan **genel**, aşağıdaki tanılama veri toplama seçeneklerini sunar: **Yalnızca hatalar**, **tüm bilgiler**ve **özel plan**. Varsayılan seçenek olan **Yalnızca hatalar**, uyarıları veya izleme iletilerini aktarmadığından en az depolama alanı miktarını alır. **Tüm bilgiler** seçeneği, en fazla bilgiyi aktarır ve bu nedenle depolama açısından en pahalı seçenektir.
7. Bu örnekte, toplanan verileri özelleştirebilmeniz için **özel plan** seçeneğini belirleyin.
8. **MB cinsinden disk kotası** kutusunda, tanılama verileri için depolama hesabınızda ne kadar alan tahsis etmek istediğinizi belirtir. İsterseniz varsayılan değeri değiştirebilirsiniz.
9. Toplamak istediğiniz tanılama verilerinin her sekmesinde, onay kutusunun **aktarımını \<log type\> Etkinleştir** ' i seçin.

    Örneğin, uygulama günlüklerini toplamak istiyorsanız **uygulama** günlükleri sekmesinde **uygulama günlüklerinin aktarımını etkinleştir** onay kutusunu seçin. Ayrıca, her bir tanılama veri türü için gereken diğer bilgileri de belirtin. Her bir sekmeye ait yapılandırma bilgileri için, bu makalenin ilerleyen bölümlerinde **Tanılama veri kaynaklarını ayarlama** bölümüne bakın.
10. İstediğiniz tüm tanılama verilerinin toplanmasını etkinleştirdikten sonra **Tamam**' ı seçin.
11. Güncelleştirilmiş projeyi kaydedin.

    **Microsoft Azure etkinlik günlüğü** penceresinde bir ileti, sanal makinenin güncelleştirildiğini gösterir.

## <a name="set-up-diagnostics-data-sources"></a>Tanılama veri kaynaklarını ayarlama
Tanılama veri toplamayı etkinleştirdikten sonra, tam olarak hangi veri kaynaklarını toplamak istediğinizi ve hangi bilgilerin toplandığını seçebilirsiniz. Sonraki bölümlerde, **Tanılama yapılandırması** iletişim kutusundaki sekmeler ve her yapılandırma seçeneğinin anlamı açıklanır.

### <a name="application-logs"></a>Uygulama günlükleri
Uygulama günlüklerinde bir Web uygulaması tarafından üretilen tanılama bilgileri vardır. Uygulama günlüklerini yakalamak istiyorsanız, **uygulama günlüklerinin aktarımını etkinleştir** onay kutusunu seçin. Uygulama günlüklerinin depolama hesabınıza aktarılması arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin. Günlük **düzeyi** değerini ayarlayarak günlükte yakalanan bilgi miktarını da değiştirebilirsiniz. Örneğin, daha fazla bilgi almak için **verbose** ' i seçin veya yalnızca kritik hataları yakalamak için **kritik** ' i seçin. Uygulama günlüklerini gösteren belirli bir tanılama sağlayıcısına sahipseniz **, sağlayıcı GUID kutusuna SAĞLAYıCıNıN** GUID 'sini ekleyerek günlükleri yakalayabilirsiniz.

  ![Uygulama günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758145.png)

Uygulama günlükleri hakkında daha fazla bilgi için bkz. [Azure App Service Web Apps için tanılama günlüğünü etkinleştirme](/azure/app-service/web-sites-enable-diagnostic-log).

### <a name="windows-event-logs"></a>Windows olay günlükleri
Windows olay günlüklerini yakalamak için **Windows olay günlüklerinin aktarımını etkinleştir** onay kutusunu seçin. Olay günlüklerinin depolama hesabınıza aktarılması arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin. İzlemek istediğiniz olay türlerinin onay kutularını seçin.

![Olay günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796664.png)

Azure SDK 2,6 veya sonraki bir sürümünü kullanıyorsanız ve özel bir veri kaynağı belirtmek istiyorsanız, **\<Data source name\>** metin kutusuna girin ve ardından **Ekle**' yi seçin. Veri kaynağı Diagnostics. cfcfg dosyasına eklenir.

Azure SDK 2,5 kullanıyorsanız ve özel bir veri kaynağı belirtmek istiyorsanız, bunu `WindowsEventLog` Aşağıdaki örnekte olduğu gibi Diagnostics. wadcfgx dosyasının bölümüne ekleyebilirsiniz:

```xml
<WindowsEventLog scheduledTransferPeriod="PT1M">
   <DataSource name="Application!*" />
   <DataSource name="CustomDataSource!*" />
</WindowsEventLog>
```

### <a name="performance-counters"></a>Performans sayaçları
Performans sayacı bilgileri, sistem performans sorunlarını bulmanıza ve sistem ve uygulama performansını ayarlamanıza yardımcı olabilir. Daha fazla bilgi için bkz. [Azure uygulamasında performans sayaçlarını oluşturma ve kullanma](/azure/cloud-services/diagnostics-performance-counters). Performans sayaçlarını yakalamak için, **performans sayaçlarını aktarmayı etkinleştir** onay kutusunu seçin. Olay günlüklerinin depolama hesabınıza aktarılması arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin. İzlemek istediğiniz performans sayaçlarının onay kutularını seçin.

![Performans sayaçları](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758147.png)

Listelenmeyen bir performans sayacını izlemek için önerilen sözdizimini kullanarak performans sayacını girin. sonra **Ekle**' yi seçin. Sanal makinedeki işletim sistemi, hangi performans sayaçlarını izleyebileceğinizi belirler. Sözdizimi hakkında daha fazla bilgi için bkz. [sayaç yolu belirtme](/windows/win32/perfctrs/specifying-a-counter-path).

### <a name="infrastructure-logs"></a>Altyapı günlükleri
Altyapı günlüklerinde Azure tanılama altyapısı, RemoteAccess modülü ve RemoteForwarder modülü hakkında bilgiler vardır. Altyapı günlükleri hakkında bilgi toplamak için, **altyapı günlüklerinin aktarımını etkinleştir** onay kutusunu seçin. Altyapı günlüklerinin depolama hesabınıza aktarılması arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin.

![Tanılama altyapı günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758148.png)

Daha fazla bilgi için bkz. [Azure Tanılama kullanarak günlük verilerini toplama](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="log-directories"></a>Günlük dizinleri
Günlük dizinleri, Internet Information Services (IIS) istekleri, başarısız istekler veya seçtiğiniz klasörler için günlük dizinlerinden toplanan verilere sahiptir. Günlük dizinlerini yakalamak için, **günlük dizinlerinin aktarımını etkinleştir** onay kutusunu seçin. Depolama hesabınıza günlüklerin aktarımı arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin.

Toplamak istediğiniz günlüklerin onay kutularını seçin; örneğin, **IIS günlükleri** ve **başarısız istek** günlükleri. Varsayılan depolama kapsayıcısı adları sağlanır, ancak adları değiştirebilirsiniz.

Herhangi bir klasörden günlükleri yakalayabilirsiniz. Yolu, **mutlak dizinden günlük** bölümünde belirtin ve ardından **Dizin Ekle**' yi seçin. Günlükler belirtilen kapsayıcılar içinde yakalanır.

![Günlük dizinleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>ETW günlükleri
[Windows Için olay izleme](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) (ETW) KULLANıYORSANıZ ve ETW günlüklerini yakalamak ISTIYORSANıZ, **ETW günlüklerinin aktarımını etkinleştir** onay kutusunu seçin. Depolama hesabınıza günlüklerin aktarımı arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin.

Olaylar, belirttiğiniz olay kaynaklarından ve olay bildirimlerinden yakalanır. Bir olay kaynağı belirtmek için, **olay kaynakları** bölümünde, bir ad girin ve **olay kaynağı Ekle**' yi seçin. Benzer şekilde, olay **bildirimleri** bölümünde bir olay bildirimi belirtebilir ve ardından **olay bildirimi Ekle**' yi seçebilirsiniz.

![ETW günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

ETW çerçevesi, [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) ad alanındaki sınıflar aracılığıyla ASP.net desteklenir. Standart [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) sınıflarını devralan ve genişleten Microsoft. WindowsAzure. Diagnostics ad alanı, Azure ortamında bir günlük oluşturma çerçevesi olarak [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) kullanımını mümkün kılar. Daha fazla bilgi için bkz. [Microsoft Azure 'da günlüğe kaydetme ve izleme denetimi yapın](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) ve [Azure Cloud Services ve sanal makinelerde tanılamayı etkinleştirin](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Kilitlenme bilgi dökümleri
Bir rol örneğinin çöktüğü hakkında bilgi yakalamak için **kilitlenme dökümlerinin aktarımını etkinleştir** onay kutusunu seçin. (ASP.NET çoğu özel durumu işleyeceğinden, bu genellikle yalnızca çalışan rolleri için yararlıdır.) Kilitlenme dökümlerinde ayrılan depolama alanı yüzdesini artırmak veya azaltmak için **Dizin kotası (%)** değerini değiştirin. Kilitlenme dökümlerinin depolandığı depolama kapsayıcısını değiştirebilir ve **tam** ya da **mini** döküm yakalamak isteyip istemediğinizi seçebilirsiniz.

Şu anda izlenmekte olan süreçler bir sonraki ekran görüntüsünde listelenmiştir. Yakalamak istediğiniz işlemlerin onay kutularını seçin. Listeye başka bir işlem eklemek için işlem adını girip **Işlem Ekle**' yi seçin.

![Kilitlenme bilgi dökümleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

Daha fazla bilgi için bkz. [Microsoft Azure 'da günlüğe kaydetme ve izleme denetimi alma](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) ve [Bölüm 4: özel günlük bileşenleri ve Azure Tanılama 1,3 değişiklikleri Microsoft Azure tanılama](https://www.red-gate.com/simple-talk/cloud/platform-as-a-service/microsoft-azure-diagnostics-part-4-custom-logging-components-and-azure-diagnostics-1.3-changes/).

## <a name="view-the-diagnostics-data"></a>Tanılama verilerini görüntüle
Bir bulut hizmeti veya sanal makine için tanılama verilerini topladıktan sonra, bunu görüntüleyebilirsiniz.

### <a name="to-view-cloud-service-diagnostics-data"></a>Bulut hizmeti Tanılama verilerini görüntülemek için
1. Bulut hizmetinizi her zamanki gibi dağıtın ve ardından çalıştırın.
2. Tanılama verilerini, Visual Studio 'Nun oluşturduğu bir raporda ya da Depolama hesabınızdaki tablolarda görüntüleyebilirsiniz. Verileri bir raporda görüntülemek için Cloud Explorer veya Sunucu Gezgini açın, istediğiniz rolün düğüm kısayol menüsünü açın ve ardından **tanılama verilerini görüntüle**' yi seçin.

    ![Tanılama verilerini görüntüle](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Kullanılabilir verileri gösteren bir rapor görüntülenir.

    ![Visual Studio 'da Microsoft Azure Tanılama raporu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    En son veriler gösterilmemişse, aktarım süresinin geçmesini beklemeniz gerekebilir.

    Verileri hemen güncelleştirmek için **Yenile** bağlantısını seçin. Verilerin otomatik olarak güncelleştirilmesini sağlamak için **Otomatik Yenile** açılan liste kutusunda bir Aralık seçin. Hata verilerini dışarı aktarmak için, bir Excel çalışma sayfasında açabileceğiniz bir virgülle ayrılmış değer dosyası oluşturmak üzere **CSV 'ye aktar** düğmesini seçin.

    Bulut Gezgini ' nde veya Sunucu Gezgini, dağıtımla ilişkili depolama hesabını açın.
3. Tablo görüntüleyicisinde tanılama tablolarını açın ve ardından topladığınız verileri gözden geçirin. IIS günlükleri ve özel Günlükler için bir blob kapsayıcısı açabilirsiniz. Aşağıdaki tabloda, farklı günlük dosyaları için verileri içeren tablolar veya blob kapsayıcıları listelenmektedir. Bu günlük dosyası için verilere ek olarak, tablo girişleri **Eventtickcount**, **DeploymentId**, **rol**ve **roleınstance**, verileri hangi sanal makine ve rolün oluşturulduğunu belirlemenize yardımcı olur.

   | Tanılama verileri | Açıklama | Konum |
   | --- | --- | --- |
   | Uygulama günlükleri |**System. Diagnostics. Trace** sınıfının yöntemlerini çağırarak kodunuzun oluşturduğu Günlükler. |WADLogsTable |
   | Olay günlükleri |Sanal makinelerdeki Windows olay günlüklerinden alınan veriler. Windows, bilgileri bu günlüklerde depolar, ancak uygulamalar ve hizmetler, hataları veya günlük bilgilerini raporlamak için günlükleri de kullanır. |WADWindowsEventLogsTable |
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

    Verileri hemen güncelleştirmek için **Yenile** bağlantısını seçin. Verilerin otomatik olarak güncelleştirilmesini sağlamak için **Otomatik Yenile** açılan liste kutusunda bir Aralık seçin. Hata verilerini dışarı aktarmak için, bir Excel çalışma sayfasında açabileceğiniz bir virgülle ayrılmış değer dosyası oluşturmak üzere **CSV 'ye aktar** düğmesini seçin.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Dağıtımdan sonra bulut hizmeti tanılamayı ayarla
Zaten çalışmakta olan bir bulut hizmetiyle ilgili bir sorunu araştırıyorsanız, rolü ilk olarak dağıtmadan önce belirtmediğiniz verileri toplamak isteyebilirsiniz. Bu durumda, Sunucu Gezgini ayarları değiştirerek bu verileri toplamaya başlayabilirsiniz. Tanılama **yapılandırması** iletişim kutusunu, örneğin veya rol için kısayol menüsünden açıp açdığınıza bağlı olarak, tek bir örnek veya bir roldeki tüm örnekler için tanılamayı ayarlayabilirsiniz. Rol düğümünü yapılandırırsanız, yaptığınız tüm değişiklikler tüm örneklere uygulanır. Örnek düğümünü yapılandırırsanız, yaptığınız tüm değişiklikler yalnızca bu örnek için geçerlidir.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Çalışan bir bulut hizmeti için tanılamayı ayarlamak için
1. Sunucu Gezgini ' de, **Cloud Services** düğümünü genişletin ve ardından araştırmak istediğiniz rolü veya örneği (ya da her ikisini) bulmak için düğüm listesini genişletin.

    ![Tanılama yapılandırma](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. Örnek düğümü veya rol düğümünün kısayol menüsünde, **tanılama ayarlarını Güncelleştir**' i seçin ve ardından toplamak istediğiniz tanılama ayarlarını seçin.

    Yapılandırma ayarları hakkında daha fazla bilgi için bu makaledeki **Tanılama veri kaynaklarını ayarlama** bölümüne bakın. Tanılama verilerini görüntüleme hakkında daha fazla bilgi için bu makaledeki **tanılama verilerini görüntüleyin** bölümüne bakın.

    Sunucu Gezgini ' de veri toplamayı değiştirirseniz, bulut hizmetinizi tamamen yeniden dağıtana kadar değişiklikler etkin kalır. Varsayılan yayımlama ayarlarını kullanırsanız, değişikliklerin üzerine yazılmaz. Varsayılan yayımlama ayarı, tam yeniden dağıtım yapmak yerine mevcut dağıtımı güncelleştirmedir. Dağıtım zamanında ayarların açık olduğundan emin olmak için, yayımlama sihirbazındaki **Gelişmiş ayarlar** sekmesine gidin ve ardından **dağıtım güncelleştirmesi** onay kutusunu temizleyin. Bu onay kutusu temizlenerek, ayarlar. wadcfgx (veya. wadcfg) dosyasında, rol için **Özellikler** Düzenleyicisi aracılığıyla ayarlanmış olanlarla döndürülür. Dağıtımınızı güncelleştirirseniz, Azure önceki ayarları tutar.

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
* **Zaman damgası**: ön IO **zaman damgası** değeri, karşıya yükleme sıklığı sınırına yuvarlanır. Örneğin, karşıya yükleme sıklığınızdan 5 dakika ve olay saati 00:17:12 ise, zaman DAMGASı 00:15:00 ' dir.
* **Zaman damgası**: varlığın Azure tablosunda oluşturulduğu zaman damgası.

**Tanılama bilgilerini toplamada Nasıl yaparım? maliyetleri yönetmek istiyor musunuz?**

Varsayılan ayarlar (**günlük düzeyi** **hata**olarak ayarlanır ve **aktarım süresi** **1 dakikaya**ayarlanır) maliyetleri en aza indirmek için tasarlanmıştır. Daha fazla tanılama verisi topladığınızda veya aktarım süresini azaltırsanız işlem maliyetleriniz artar. İhtiyaç duymadan daha fazla veri toplamayın ve artık ihtiyacınız kalmadığında veri toplamayı devre dışı bırakmayı unutmayın. Bu makalenin önceki kısımlarında açıklandığı gibi, çalışma zamanında bile her zaman yeniden etkinleştirebilirsiniz.

**Nasıl yaparım? başarısız-istek günlükleri IIS 'den toplansın mı?**

IIS, varsayılan olarak başarısız-istek günlüklerini toplamaz. Web rolünüzün web.config dosyasını düzenleyerek, IIS 'yi başarısız istek günlüklerini toplayacak şekilde ayarlayabilirsiniz.

**OnStart gibi RoleEntryPoint yöntemlerinden izleme bilgileri alamıyorum. Ne oldu?**

**Roleentrypoint** yöntemleri IIS 'de değil WAIISHost.exe bağlamında çağrılır. Normal olarak izlemeyi sağlayan web.config içindeki yapılandırma bilgileri uygulanmaz. Bu sorunu çözmek için web rolü projenize bir. config dosyası ekleyin ve dosyayı **Roleentrypoint** kodunu içeren çıkış derlemesiyle eşleşecek şekilde adlandırın. Varsayılan Web rolü projesinde,. config dosyasının adı WAIISHost.exe.config olmalıdır. Aşağıdaki satırları bu dosyaya ekleyin:

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

**Özellikler** penceresinde, **Çıkış Dizinine Kopyala** özelliğini **her zaman Kopyala**olarak ayarlayın.

## <a name="next-steps"></a>Sonraki adımlar
Azure 'da tanılama günlüğü hakkında daha fazla bilgi edinmek için bkz. [azure Cloud Services ve sanal makinelerde tanılamayı etkinleştirme](/azure/cloud-services/cloud-services-dotnet-diagnostics) ve [Azure App Service Web Apps Için tanılama günlüğünü etkinleştirme](/azure/app-service/web-sites-enable-diagnostic-log).
