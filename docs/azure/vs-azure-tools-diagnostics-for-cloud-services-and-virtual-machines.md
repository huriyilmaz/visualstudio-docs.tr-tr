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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122122637"
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
* PowerShell kullanarak tanılama uzantısını ayarlama sürecini basitleştirmek için, Visual Studio paket çıktısı her bir rol için tanılama uzantısının ortak yapılandırma XML 'sini içerir. Visual Studio, genel yapılandırmadaki depolama hesabı bilgilerini doldurmak için tanılama bağlantı dizesini kullanır. Ortak yapılandırma dosyaları uzantılar klasöründe oluşturulur. Ortak yapılandırma dosyaları, PaaSDiagnostics adlandırma düzenlerini kullanır. &lt; rol adı \>.PubConfig.xml. Herhangi bir PowerShell tabanlı dağıtımlar, her yapılandırmayı bir rolle eşlemek için bu kalıbı kullanabilir.
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
Visual Studio, Azure sanal makineleri için tanılama verileri toplayabilirsiniz.

### <a name="to-turn-on-diagnostics-on-azure-virtual-machines"></a>Azure sanal makinelerinde tanılamayı açmak için

1. Sunucu Gezgini ' de, Azure düğümünü seçin ve henüz bağlı değilseniz Azure aboneliğinize bağlanın.
2. **Sanal makineler** düğümünü genişletin. Yeni bir sanal makine oluşturabilir veya var olan bir düğümü seçebilirsiniz.
3. İstediğiniz sanal makinenin kısayol menüsünde **Yapılandır**' ı seçin. Sanal makine yapılandırması iletişim kutusu görüntülenir.

    ![Azure sanal makinesini yapılandırma](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796663.png)
4. zaten yüklenmemişse Microsoft Monitoring Agent tanılama uzantısını ekleyin. Bu uzantıyla birlikte Azure sanal makinesi için tanılama verileri toplayabilirsiniz. **yüklü uzantılar** altında, **kullanılabilir uzantı seç** aşağı açılan liste kutusunda **Microsoft Monitoring Agent tanılama**' yı seçin.

    ![Azure sanal makine uzantısı 'nı yükler](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766024.png)

    > [!NOTE]
   > Diğer tanılama uzantıları, sanal makineleriniz için kullanılabilir. Daha fazla bilgi için bkz. [sanal makine uzantıları ve Windows özellikleri](/azure/virtual-machines/windows/extensions-features).
   >
   >
5. Uzantıyı eklemek ve **Tanılama yapılandırması** iletişim kutusunu görüntülemek için **Ekle**' yi seçin.
6. Bir depolama hesabı belirtmek için **Yapılandır**' ı seçin ve ardından **Tamam**' ı seçin.

    Her sekme ( **genel** ve **günlük dizinleri** hariç), toplayacağınız bir tanılama veri kaynağını temsil eder.

    ![Azure tanılama ve yapılandırmasını etkinleştirme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC758144.png)

    Varsayılan sekmesi olan **genel**, aşağıdaki tanılama veri toplama seçeneklerini sunar: **Yalnızca hatalar**, **tüm bilgiler** ve **özel plan**. Varsayılan seçenek olan **Yalnızca hatalar**, uyarıları veya izleme iletilerini aktarmadığından en az depolama alanı miktarını alır. **Tüm bilgiler** seçeneği, en fazla bilgiyi aktarır ve bu nedenle depolama açısından en pahalı seçenektir.
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
Windows olay günlüklerini yakalamak için, **Windows olay günlüklerinin aktarımını etkinleştir** onay kutusunu işaretleyin. Olay günlüklerinin depolama hesabınıza aktarılması arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin. İzlemek istediğiniz olay türlerinin onay kutularını seçin.

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
günlük dizinleri, Internet Information Services (ııs) istekleri, başarısız istekler veya seçtiğiniz klasörler için günlük dizinlerinden toplanan verilere sahiptir. Günlük dizinlerini yakalamak için, **günlük dizinlerinin aktarımını etkinleştir** onay kutusunu seçin. Depolama hesabınıza günlüklerin aktarımı arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin.

Toplamak istediğiniz günlüklerin onay kutularını seçin; örneğin, **IIS günlükleri** ve **başarısız istek** günlükleri. Varsayılan depolama kapsayıcısı adları sağlanır, ancak adları değiştirebilirsiniz.

Herhangi bir klasörden günlükleri yakalayabilirsiniz. Yolu, **mutlak dizinden günlük** bölümünde belirtin ve ardından **Dizin Ekle**' yi seçin. Günlükler belirtilen kapsayıcılar içinde yakalanır.

![Günlük dizinleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796665.png)

### <a name="etw-logs"></a>ETW günlükleri
Windows (etw) [için olay izlemeyi](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) kullanıyorsanız ve etw günlüklerini yakalamak istiyorsanız, **etw günlüklerinin aktarımını etkinleştir** onay kutusunu seçin. Depolama hesabınıza günlüklerin aktarımı arasındaki aralığı artırmak veya azaltmak için, **aktarım süresi (dk)** değerini değiştirin.

Olaylar, belirttiğiniz olay kaynaklarından ve olay bildirimlerinden yakalanır. Bir olay kaynağı belirtmek için, **olay kaynakları** bölümünde, bir ad girin ve **olay kaynağı Ekle**' yi seçin. Benzer şekilde, olay **bildirimleri** bölümünde bir olay bildirimi belirtebilir ve ardından **olay bildirimi Ekle**' yi seçebilirsiniz.

![ETW günlükleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766025.png)

ETW çerçevesi, [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) ad alanındaki sınıflar aracılığıyla ASP.NET desteklenir. Standart [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) sınıflarını devralan ve genişleten Microsoft. WindowsAzure. Diagnostics ad alanı, Azure ortamında bir günlük oluşturma çerçevesi olarak [System. Diagnostics. aspx](/dotnet/api/system.diagnostics) kullanımını mümkün kılar. daha fazla bilgi için bkz. [Microsoft Azure 'da günlüğe kaydetme ve izleme denetimi yapın](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) ve [Azure Cloud Services ve sanal makinelerde tanılamayı etkinleştirin](/azure/cloud-services/cloud-services-dotnet-diagnostics).

### <a name="crash-dumps"></a>Kilitlenme bilgi dökümleri
Bir rol örneğinin çöktüğü hakkında bilgi yakalamak için **kilitlenme dökümlerinin aktarımını etkinleştir** onay kutusunu seçin. (ASP.NET çoğu özel durumu işleyeceğinden, bu genellikle yalnızca çalışan rolleri için yararlıdır.) Kilitlenme dökümlerinde ayrılan depolama alanı yüzdesini artırmak veya azaltmak için **Dizin kotası (%)** değerini değiştirin. Kilitlenme dökümlerinin depolandığı depolama kapsayıcısını değiştirebilir ve **tam** ya da **mini** döküm yakalamak isteyip istemediğinizi seçebilirsiniz.

Şu anda izlenmekte olan süreçler bir sonraki ekran görüntüsünde listelenmiştir. Yakalamak istediğiniz işlemlerin onay kutularını seçin. Listeye başka bir işlem eklemek için işlem adını girip **Işlem Ekle**' yi seçin.

![Kilitlenme bilgi dökümleri](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766026.png)

daha fazla bilgi için bkz. [Microsoft Azure 'de günlüğe kaydetme ve izleme denetimi alma](/archive/msdn-magazine/2010/june/msdn-magazine-cloud-diagnostics-take-control-of-logging-and-tracing-in-windows-azure) ve [Microsoft Azure tanılama bölüm 4: özel günlük bileşenleri ve Azure Tanılama 1,3 değişiklikleri](https://www.red-gate.com/simple-talk/cloud/platform-as-a-service/microsoft-azure-diagnostics-part-4-custom-logging-components-and-azure-diagnostics-1.3-changes/).

## <a name="view-the-diagnostics-data"></a>Tanılama verilerini görüntüle
Bir bulut hizmeti veya sanal makine için tanılama verilerini topladıktan sonra, bunu görüntüleyebilirsiniz.

### <a name="to-view-cloud-service-diagnostics-data"></a>Bulut hizmeti Tanılama verilerini görüntülemek için
1. Bulut hizmetinizi her zamanki gibi dağıtın ve ardından çalıştırın.
2. tanılama verilerini Visual Studio oluşturduğu bir raporda ya da depolama hesabınızdaki tablolarda görüntüleyebilirsiniz. Bir raporda verileri görüntülemek için Bulut Gezgini'ni Sunucu Gezgini, istediğiniz rolün kısayol menüsünü açın ve tanılama verilerini **görüntüle'yi seçin.**

    ![Tanılama verilerini görüntüleme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748912.png)

    Kullanılabilir verileri gösteren bir rapor görüntülenir.

    ![Microsoft Azure Visual Studio'da tanılama raporu](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796666.png)

    En son veriler gösterilmezse, aktarım döneminin devamını beklemelisiniz.

    Verileri hemen güncelleştirmek için Yenile **bağlantısını** seçin. Verilerin otomatik olarak güncelleştirilen bir aralık seçerek Otomatik **Yenile** açılan listesi kutusundan seçin. Hata verilerini dışarı aktarma için **CSV'ye** Aktar düğmesini seçerek bir çalışma sayfasında açabilirsiniz virgülle ayrılmış bir değer Excel oluşturun.

    Bulut Gezgini'Sunucu Gezgini dağıtımla ilişkili depolama hesabını açın.
3. Tablo görüntüleyicisinde tanılama tablolarını açın ve toplanmış verileri gözden geçirme. IIS günlükleri ve özel günlükler için bir blob kapsayıcısı açabilirsiniz. Aşağıdaki tabloda, farklı günlük dosyalarının verilerini içeren tablolar veya blob kapsayıcıları liste bulunmaktadır. Tablo girdileri, bu günlük dosyasının verilerine ek olarak, verileri hangi sanal makinenin ve rolün ne zaman üretmiş olduğunu tanımlamanıza yardımcı olmak için **EventTickCount**, **DeploymentId**, **Role** **ve RoleInstance**'i içerir.

   | Tanılama verileri | Açıklama | Konum |
   | --- | --- | --- |
   | Uygulama günlükleri |**System.Diagnostics.Trace** sınıfının yöntemlerini çağırarak kodunuzun ürettiklerini günlüğe kaydeder. |WADLogsTable |
   | Olay günlükleri |Sanal makinelerde Windows günlüklerinden veriler. Windows bu günlüklerde depolar, ancak uygulamalar ve hizmetler hataları veya günlük bilgilerini rapor etmek için günlükleri de kullanır. |WADWindowsEventLogsTable |
   | Performans sayaçları |Sanal makinede bulunan herhangi bir performans sayacında veri toplayabilirsiniz. İşletim sistemi, bellek kullanımı ve işlemci zamanı gibi birçok istatistik içeren performans sayaçları sağlar. |WADPerformanceCountersTable |
   | Altyapı günlükleri |Tanılama altyapısından oluşturulan günlükler. |WADDiagnosticInfrastructureLogsTable |
   | IIS günlükleri |Web isteklerini kaydeden günlükler. Bulut hizmetiniz önemli miktarda trafik alıyorsa bu günlükler uzun olabilir. Bu verileri yalnızca ihtiyacınız olduğunda toplamak ve depolamak iyi bir fikirdir. |Başarısız istek günlüklerini blob kapsayıcısında wad-iis-failedreqlogs altındaki dağıtım, rol ve örnek yolunun altında bulabilirsiniz. Tam günlükleri wad-iis-logfiles altında bulabilirsiniz. Her dosyanın girdileri WADDirectories tablosunda yapılır. |
   | Kilitlenme bilgi dökümleri |Bulut hizmetinizin işleminin ikili görüntülerini sağlar (genellikle çalışan rolü). |wad-crush-dumps blob kapsayıcısı |
   | Özel günlük dosyaları |Önceden tanımlanmış veri günlükleri. |Kodda depolama hesabındaki özel günlük dosyalarının konumunu belirtebilirsiniz. Örneğin, özel bir blob kapsayıcısı belirtabilirsiniz. |
4. Herhangi bir türde veriler kesilirse, bu veri türü için arabelleği artırmayı veya sanal makineden depolama hesabınıza veri aktarımları arasındaki aralığı kısaltmayı denemeniz gerekir.
5. (İsteğe bağlı) Genel depolama maliyetlerini azaltmak için depolama hesabından verileri ara sıra temizleme.
6. Tam dağıtım yaptığınız zaman Diagnostics.cscfg dosyası (Azure SDK 2.5 için .wadcfgx) Azure'da güncelleştirilir ve bulut hizmetiniz tanılama yapılandırmanıza yapılan değişiklikleri alır. Bunun yerine mevcut bir dağıtımı güncelleştiriyorsanız.cscfg dosyası Azure'da güncelleştirilmez. Ancak bir sonraki bölümde yer alan adımları takip edin ve tanılama ayarlarını değiştirebilirsiniz. Tam dağıtım gerçekleştirme ve mevcut dağıtımı güncelleştirme hakkında daha fazla bilgi için bkz. [Azure Uygulama Yayımlama Sihirbazı.](vs-azure-tools-publish-azure-application-wizard.md)

### <a name="to-view-virtual-machine-diagnostics-data"></a>Sanal makine tanılama verilerini görüntülemek için
1. Sanal makinenin kısayol menüsünde Tanılama Verilerini **Görüntüle'yi seçin.**

    ![Azure sanal makinesinde tanılama verilerini görüntüleme](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC766027.png)

    Tanılama **özeti iletişim** kutusu görüntülenir.

    ![Azure sanal makine tanılama özeti](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC796667.png)

    En son veriler gösterilmezse, aktarım döneminin devamını beklemelisiniz.

    Verileri hemen güncelleştirmek için Yenile **bağlantısını** seçin. Verilerin otomatik olarak güncelleştirilen bir aralık seçerek Otomatik **Yenile** açılan listesi kutusundan seçin. Hata verilerini dışarı aktarma için **CSV'ye** Aktar düğmesini seçerek bir çalışma sayfasında açabilirsiniz virgülle ayrılmış bir değer Excel oluşturun.

## <a name="set-up-cloud-service-diagnostics-after-deployment"></a>Dağıtımdan sonra bulut hizmeti tanılamasını ayarlama
Zaten çalışan bir bulut hizmetiyle ilgili bir sorunu araştırıyorsanız, rolü ilk olarak dağıtmadan önce belirtmeden verileri toplamak istiyor olabilir. Bu durumda, veri kaynağında ayarları değiştirerek bu verileri toplamaya Sunucu Gezgini. Tanılamayı tek bir örnek için veya bir rolde yer alan tüm örnekler için  ayarlayabilirsiniz. Tanılama Yapılandırması iletişim kutusunu örneğin kısayol menüsünden mi yoksa rol için mi açabilirsiniz? Rol düğümünü yapılandırıyorsanız, yaptığınız tüm değişiklikler tüm örneklere uygulanır. Örnek düğümünü yapılandırdısanız, yaptığınız tüm değişiklikler yalnızca bu örnek için geçerlidir.

### <a name="to-set-up-diagnostics-for-a-running-cloud-service"></a>Çalışan bir bulut hizmeti için tanılama ayarlamak için
1. Bu Sunucu Gezgini, **Cloud Services** düğümünü genişletin ve ardından araştırmak istediğiniz rolü veya örneği (veya her ikisini birden) bulmak için düğüm listesini genişletin.

    ![Tanılama yapılandırma](./media/vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines/IC748913.png)
2. Örnek düğümünün veya rol düğümünün kısayol menüsünde Tanılamayı **Güncelleştir'i Ayarlar** seçin ve ardından toplamak istediğiniz tanılama ayarlarını seçin.

    Yapılandırma ayarları hakkında bilgi için bu makaledeki **Tanılama veri kaynaklarını ayarlama** bölümüne bakın. Tanılama verilerini görüntüleme hakkında bilgi için bu makaledeki **Tanılama verilerini görüntüleme** bölümüne bakın.

    Veri toplamayı bulutta Sunucu Gezgini, siz bulut hizmetinizi tamamen yeniden Sunucu Gezgini kadar değişiklikler devam ediyor olur. Varsayılan yayımlama ayarlarını kullanırsanız değişikliklerin üzerine yazılmaz. Varsayılan yayımlama ayarı, tam bir yeniden dağıtım yapmak yerine mevcut dağıtımı güncelleştirmektir. Ayarların dağıtım zamanında temiz olduğundan emin olmak için **Yayımla sihirbazında Gelişmiş** Ayarlar sekmesine gidin ve dağıtım güncelleştirmesi **onay kutusunun** işaretini kaldırın. Bu onay kutusu temizlendi olarak yeniden yayınlasanız, ayarlar rol için Özellikler düzenleyicisi aracılığıyla ayarlanacak şekilde .wadcfgx (veya .wadcfg) dosyasındaki ayarlara geri döner.  Dağıtımınızı güncelleştirin, Azure önceki ayarları tutar.

## <a name="troubleshoot-azure-cloud-service-issues"></a>Azure bulut hizmeti sorunlarını giderme
"Meşgul" durumda takılı kalan, tekrar tekrar geri dönüştüren veya iç sunucu hatasına neden olan bir rol gibi bulut hizmeti projelerinde sorun yaşamanız durumunda, sorunu tanılamak ve düzeltmek için kullanabileceğiniz araçlar ve teknikler vardır. Yaygın sorunların ve çözümlerin belirli örnekleri ve bu hataları tanılamak ve düzeltmek için kullanabileceğiniz kavramlara ve araçlara genel bir bakış için [bkz. Azure PaaS işlem tanılama verileri.](/archive/blogs/kwill/windows-azure-paas-compute-diagnostics-data)

## <a name="q--a"></a>Soru-Cevap
**Arabellek boyutu nedir ve ne kadar büyük olmalı?**

Her sanal makine örneğinde kotalar, yerel dosya sisteminde ne kadar tanılama verisi depolayabileceklerini sınırlandırır. Ayrıca, kullanılabilen her tanılama verisi türü için bir arabellek boyutu belirtirsiniz. Bu arabellek boyutu, bu tür veriler için ayrı bir kota görevi görür. Genel kotayı ve kalan bellek miktarını belirlemek için tanılama veri türünün iletişim kutusunun en altına bakın. Daha büyük arabellekler veya daha fazla veri türü belirtirsiniz, genel kotaya yaklaşabilirsiniz. Diagnostics.wadcfg veya .wadcfgx yapılandırma dosyasını değiştirerek genel kotayı değiştirebilirsiniz. Tanılama verileri, uygulamanın verileriyle aynı dosya sisteminde depolanır. Uygulamanız büyük miktarda disk alanı kullanıyorsa, genel tanılama kotasını artırmamanız gerekir.

**Aktarım süresi nedir ve ne kadar süreyle olması gerekir?**

Aktarım dönemi, veri yakalamaları arasında geçen süredir. Her aktarım döneminden sonra, veriler sanal makinede yerel dosya sisteminden depolama hesabı tablolarına taşınır. Toplanan veri miktarı, aktarım süresi sona ermeden önce kotayı aşarsa eski veriler atılır. Verilerinizin arabellek boyutunu veya genel kotayı aşması nedeniyle veri kaybınız varsa aktarım dönemini azaltmak iyi olabilir.

**Zaman damgaları hangi saat diliminde?**

Zaman damgaları, bulut hizmetinizi barındıran veri merkezi yerel saat dilimindedir. Günlük tablolarında aşağıdaki üç zaman damgası sütunu kullanılır:

* **PreciseTimeStamp:** Olayın ETW zaman damgası. Başka bir ifadeyle, olayın istemciden günlüğe kaydedile zamanı.
* **Zaman damgası**: ön IO **zaman damgası** değeri, karşıya yükleme sıklığı sınırına yuvarlanır. Örneğin, karşıya yükleme sıklığınızdan 5 dakika ve olay saati 00:17:12 ise, zaman DAMGASı 00:15:00 ' dir.
* **Zaman damgası**: varlığın Azure tablosunda oluşturulduğu zaman damgası.

**Tanılama bilgilerini toplamada Nasıl yaparım? maliyetleri yönetmek istiyor musunuz?**

Varsayılan ayarlar (**günlük düzeyi** **hata** olarak ayarlanır ve **aktarım süresi** **1 dakikaya** ayarlanır) maliyetleri en aza indirmek için tasarlanmıştır. Daha fazla tanılama verisi topladığınızda veya aktarım süresini azaltırsanız işlem maliyetleriniz artar. İhtiyaç duymadan daha fazla veri toplamayın ve artık ihtiyacınız kalmadığında veri toplamayı devre dışı bırakmayı unutmayın. Bu makalenin önceki kısımlarında açıklandığı gibi, çalışma zamanında bile her zaman yeniden etkinleştirebilirsiniz.

**Nasıl yaparım? başarısız-istek günlükleri IIS 'den toplansın mı?**

IIS, varsayılan olarak başarısız-istek günlüklerini toplamaz. Web rolünüzün web.config dosyasını düzenleyerek, IIS 'yi başarısız istek günlüklerini toplayacak şekilde ayarlayabilirsiniz.

**OnStart gibi RoleEntryPoint yöntemlerinden izleme bilgileri alamıyorum. Ne oldu?**

**Roleentrypoint** yöntemleri IIS 'de değil WAIISHost.exe bağlamında çağrılır. Normal olarak izlemeyi sağlayan web.config içindeki yapılandırma bilgileri uygulanmaz. Bu sorunu çözmek için, Web rolü projenize bir .config dosyası ekleyin ve dosyayı **Roleentrypoint** kodunu içeren çıkış derlemesiyle eşleşecek şekilde adlandırın. Varsayılan Web rolü projesinde .config dosyanın adı WAIISHost.exe.config olmalıdır. Aşağıdaki satırları bu dosyaya ekleyin:

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

**Özellikler** penceresinde, **Çıkış Dizinine Kopyala** özelliğini **her zaman Kopyala** olarak ayarlayın.

## <a name="next-steps"></a>Sonraki adımlar
Azure 'da tanılama günlüğü hakkında daha fazla bilgi edinmek için bkz. [azure Cloud Services ve sanal makinelerde tanılamayı etkinleştirme](/azure/cloud-services/cloud-services-dotnet-diagnostics) ve [Azure App Service Web Apps Için tanılama günlüğünü etkinleştirme](/azure/app-service/web-sites-enable-diagnostic-log).
