---
title: Azure bulut hizmeti için rolleri yapılandırma
description: Azure bulut hizmetleri için rol ayarlamayı ve yapılandırmayı öğrenmek için Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: e7d775bcb87e38bb2628814327ef72d739ad5695
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633198"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti rollerini yapılandırma
Azure bulut hizmetinin bir veya daha fazla çalışan veya web rolü olabilir. Her rol için bu rolün nasıl ayar olduğunu tanımlamanız ve bu rolün nasıl çalıştırıldığında yapılandırmanız gerekir. Bulut hizmetlerinde roller hakkında daha fazla bilgi edinmek için bkz. [Azure Cloud Services.](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services)

Bulut hizmetinize ilişkin bilgiler aşağıdaki dosyalarda depolanır:

- **ServiceDefinition.csdef** - Hizmet tanımı dosyası hangi rollerin gerekli olduğu, uç noktalar ve sanal makine boyutu da dahil olmak üzere bulut hizmetinizin çalışma zamanı ayarlarını tanımlar. Rolünüz çalışıyorken `ServiceDefinition.csdef` içinde depolanan verilerin hiçbiri değiştirilemez.
- **ServiceConfiguration.cscfg** - Hizmet yapılandırma dosyası, bir rolün kaç örneğinin çalıştırıldığından ve bir rol için tanımlanan ayarların değerlerini yapılandırır. Rolünüz çalışırken `ServiceConfiguration.cscfg` içinde depolanan veriler değiştirilebilir.

Bir rolün nasıl çalıştırılır denetleme ayarlarına farklı değerler depolamak için birden çok hizmet yapılandırması tanımlayabilirsiniz. Her dağıtım ortamı için farklı bir hizmet yapılandırması kullanabilirsiniz. Örneğin, depolama hesabı bağlantı dizenizi yerel bir hizmet yapılandırmasında yerel Azure Depolama Emulator'i kullanmak üzere ayarlayın ve bulutta Azure depolamayı kullanmak için başka bir hizmet yapılandırması oluşturabilirsiniz.

Azure'da bir Azure bulut hizmeti Visual Studio iki hizmet yapılandırması otomatik olarak oluşturulur ve Azure projenize eklenir:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Azure bulut hizmetini yapılandırma
Aşağıdaki adımlarda gösterildiği gibi azure Çözüm Gezgini Visual Studio azure bulut hizmetini yapılandırabilirsiniz:

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini,** projeye sağ tıklayın ve bağlam menüsünden Özellikler'i **seçin.**

    ![Çözüm Gezgini proje bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Projenin özellikler sayfasında Geliştirme **sekmesini** seçin.

    ![Project özellikler sayfası - geliştirme sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Hizmet **Yapılandırması listesinde,** düzenlemek istediğiniz hizmet yapılandırmasının adını seçin. (Bu rol için tüm hizmet yapılandırmalarında değişiklik yapmak için Tüm **Yapılandırmalar'ı seçin.)**

    > [!IMPORTANT]
    > Belirli bir hizmet yapılandırmasını seçerseniz, bazı özellikler yalnızca tüm yapılandırmalar için ayarlanabiliyor olduğundan devre dışı bırakılır. Bu özellikleri düzenlemek için Tüm Yapılandırmalar'ı **seçmeniz gerekir.**

    ![Azure bulut hizmeti için Hizmet Yapılandırması listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Rol örneklerinin sayısını değiştirme
Bulut hizmetinizin performansını artırmak için, çalışan bir rolün örnek sayısını kullanıcı sayısına veya belirli bir rol için beklenen yüke göre değiştirebilirsiniz. Bulut hizmeti Azure'da çalıştırılan her rol örneği için ayrı bir sanal makine oluşturulur. Bu, bu bulut hizmetinin dağıtımının faturalarını etkiler. Faturalama hakkında daha fazla bilgi için [bkz. Faturanızı anlama Microsoft Azure.](/azure/billing/billing-understand-your-bill)

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini** proje düğümünü genişletin. Roller **düğümü** altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünde Özellikler'i **seçin.**

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Yapılandırma** sekmesini seçin.

    ![Yapılandırma sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Hizmet **Yapılandırması listesinde,** güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet Yapılandırması listesi 1](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Örnek **sayısı** metin kutusuna bu rol için başlatmak istediğiniz örnek sayısını girin. Bulut hizmetini Azure'da yayımlarken her örnek ayrı bir sanal makinede çalışır.

    ![Örnek Sayısını Güncelleştirme](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Araç çubuğundan Visual Studio'yi **seçin.**

## <a name="manage-connection-strings-for-storage-accounts"></a>Depolama hesapları için bağlantı dizelerini yönetme
Hizmet yapılandırmalarınız için bağlantı dizelerini ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Örneğin, değerine sahip bir yerel hizmet yapılandırması için yerel bağlantı dizesine sahip olmak istiyor `UseDevelopmentStorage=true` olabilir. Ayrıca, Azure'da depolama hesabı kullanan bir bulut hizmeti yapılandırması yapılandırmak da istiyor olabilir.

> [!WARNING]
> Depolama hesabı bağlantı dizesi için Azure depolama hesabı anahtar bilgilerini girerken, bu bilgiler hizmet yapılandırma dosyasında yerel olarak depolanır. Ancak, bu bilgiler şu anda şifrelenmiş metin olarak depolanmaz.
>
>

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetinizi Azure'da yayımlarken bulut hizmetinizin farklı bağlantı dizelerini kullanmak veya kodunuzu değiştirmek zorunda olmaznız. Kodda bağlantı dizesi için aynı adı kullanabilirsiniz ve değer, bulut hizmetinizi derlemek için veya yayımlarken seçen hizmet yapılandırmasına bağlı olarak farklıdır.

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini** proje düğümünü genişletin. Roller **düğümü** altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünde Özellikler'i **seçin.**

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Ayarlar** sekmesini seçin.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Hizmet **Yapılandırması listesinde,** güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet Yapılandırması](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Bağlantı dizesi eklemek için Ayar **Ekle'yi seçin.**

    ![Bağlantı dizesi ekleme](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Yeni ayar listeye eklendiktan sonra, listede yer alan satırı gerekli bilgilerle güncelleştirin.

    ![Yeni bağlantı dizesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** - Bağlantı dizesi için kullanmak istediğiniz adı girin.
    - **Tür** - **Açılan listeden** Bağlantı Dizesi'ne tıklayın.
    - **Değer** - Bağlantı dizesini doğrudan **Değer** hücresine girebilirsiniz veya Bağlantı Dizesi Oluştur iletişim kutusunda çalışmak için üç noktayı (...) **Depolama belirleyebilirsiniz.**

1. Bağlantı **Dizesi Depolama iletişim kutusunda,** kullanarak bağlantı Bağlan **seçin.** Ardından, seçenenenle ilgili yönergeleri izleyin:

    - **Microsoft Azure Depolama Emulator** - Bu seçeneği kullanırsanız, iletişim kutusundaki diğer ayarlar yalnızca Azure için geçerli olduğu için devre dışı bırakılır. **Tamam**’ı seçin.
    - **Aboneliğiniz** - Bu seçeneği kullanırsanız açılan listeyi kullanarak bir abonelik seçin ve Microsoft hesabı oturum Microsoft hesabı. Bir Azure aboneliği ve depolama hesabı seçin. **Tamam**’ı seçin.
    - **El ile girilen kimlik** bilgileri - Depolama hesabı adını ve birincil veya ikinci anahtarı girin. Bağlantı için bir **seçenek belirleyin** (çoğu senaryo için HTTPS önerilir.) **Tamam'ı seçin.**

1. Bir bağlantı dizesini silmek için bağlantı dizesini ve ardından Ayarı **Kaldır'ı seçin.**

1. Araç çubuğundan Visual Studio'yi **seçin.**

## <a name="programmatically-access-a-connection-string"></a>Program aracılığıyla bir bağlantı dizesine erişme

Aşağıdaki adımlarda, C# kullanarak bir bağlantı dizesine program aracılığıyla nasıl erişin?

1. Aşağıdaki using yönergelerini, ayarını kullanmak üzere bir C# dosyasına ekleyin:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod, bağlantı dizesine nasıl erişilene bir örnek gösterir. &lt;ConnectionStringName> uygun değerle değiştirin.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Azure bulut hizmetinize kullanmak üzere özel ayarlar ekleme
Hizmet yapılandırma dosyasındaki özel ayarlar, belirli bir hizmet yapılandırması için bir dize için ad ve değer eklemenize olanak sağlar. Ayarın değerini okuyarak ve kodundaki mantığı kontrol etmek için bu değeri kullanarak bulut hizmetinize bir özellik yapılandırmak için bu ayarı kullanmayı seçebilirsiniz. Bu hizmet yapılandırma değerlerini, hizmet paketinizi yeniden oluşturmanıza gerek kalmadan veya bulut hizmetiniz çalışıyorken değiştirebilirsiniz. Kodunuz, bir ayarın ne zaman değiştiklerinin bildirimlerini kontrol ediyor olabilir. Bkz. [RoleEnvironment.Changing Olayı.](/previous-versions/azure/reference/ee758134(v=azure.100))

Hizmet yapılandırmaları için özel ayarlar ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Farklı hizmet yapılandırmaları için bu dizeler için farklı değerlere sahip olmak istiyor olabilir.

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetinizi Azure'da yayımlarken bulut hizmetinizi farklı dizeler kullanmak veya kodunuzu değiştirmek zorunda olmaznız. Kodundaki dize için aynı adı kullanabilirsiniz ve değer, bulut hizmetinizi derlemek veya yayımlarken seçen hizmet yapılandırmasına bağlı olarak farklıdır.

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini** proje düğümünü genişletin. Roller **düğümü** altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünde Özellikler'i **seçin.**

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Ayarlar** sekmesini seçin.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Hizmet **Yapılandırması listesinde,** güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet Yapılandırması listesi 2](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Özel ayar eklemek için Ayar **Ekle'yi seçin.**

    ![Özel ayar ekleme](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Yeni ayar listeye eklendiktan sonra, listede yer alan satırı gerekli bilgilerle güncelleştirin.

    ![Yeni özel ayar](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** - Ayarın adını girin.
    - **Tür** - **Açılan** listeden Dize'yi seçin.
    - **Değer** - Ayarın değerini girin. Değeri doğrudan Değer hücresine **girebilirsiniz** veya üç noktayı (...) seçerek Dizeyi Düzenle iletişim **kutusuna değeri girebilirsiniz.**

1. Özel bir ayarı silmek için ayarı seçin ve ardından Ayarı **Kaldır'ı seçin.**

1. Araç çubuğundan Visual Studio'yi **seçin.**

## <a name="programmatically-access-a-custom-settings-value"></a>Program aracılığıyla özel bir ayarın değerine erişme

Aşağıdaki adımlarda, C# kullanarak program aracılığıyla özel bir ayara nasıl erişebilirsiniz?

1. Aşağıdaki using yönergelerini, ayarını kullanmak üzere bir C# dosyasına ekleyin:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod, özel bir ayara nasıl erişilene bir örnek göstermektedir. &lt;SettingName> yer tutucusunu uygun değerle değiştirin.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Her rol örneği için yerel depolamayı yönetme
Bir rolün her örneği için yerel dosya sistemi depolama alanı ekebilirsiniz. Bu depolamada depolanan verilere, verilerin depolandığı rolün diğer örnekleri veya diğer roller tarafından erişilemez.

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini** proje düğümünü genişletin. Roller **düğümü** altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünde Özellikler'i **seçin.**

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Yerel veri **Depolama** seçin.

    ![Yerel depolama sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Hizmet Yapılandırması **listesinde,** yerel depolama ayarları **tüm** hizmet yapılandırmalarına uygulanırken Tüm Yapılandırmalar'ın seçildiğinden emin olun. Diğer herhangi bir değer, sayfada yer alan tüm giriş alanlarının devre dışı bırakılmıştır.

    ![Hizmet Yapılandırması listesi 3](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Yerel depolama girişi eklemek için Yerel Depolama Alanı **Ekle'yi Depolama.**

    ![Yerel depolama ekleme](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Listeye yeni yerel depolama girdisi eklendiktan sonra, listede satırı gerekli bilgilerle güncelleştirin.

    ![Yeni yerel depolama girişi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Ad** - Yeni yerel depolama için kullanmak istediğiniz adı girin.
    - **Boyut (MB)** - Yeni yerel depolama için ihtiyacınız olan boyutu MB olarak girin.
    - **Rol geri dönüşümünde** temizle - Rolün sanal makinesi geri dönüştür olduğunda yeni yerel depolama alanı verilerini kaldırmak için bu seçeneği belirleyin.

1. Yerel depolama girişini silmek için girdiyi seçin ve sonra Yerel Depolama Alanını **Kaldır'ı Depolama.**

1. Araç çubuğundan Visual Studio'yi **seçin.**

## <a name="programmatically-accessing-local-storage"></a>Program aracılığıyla yerel depolamaya erişme

Bu bölümde, bir test metin dosyası yazarak C# kullanarak yerel depolamaya program aracılığıyla nasıl erişilenler `MyLocalStorageTest.txt` göstermektedir.

### <a name="write-a-text-file-to-local-storage"></a>Yerel depolama alanına metin dosyası yazma

Aşağıdaki kod, yerel depolama alanına metin dosyası yazma örneği gösterir. &lt;LocalStorageName> yer tutucusunu uygun değerle değiştirin.

```csharp
// Retrieve an object that points to the local storage resource
LocalResource localResource = RoleEnvironment.GetLocalResource("<LocalStorageName>");

//Define the file name and path
string[] paths = { localResource.RootPath, "MyLocalStorageTest.txt" };
String filePath = Path.Combine(paths);

using (FileStream writeStream = File.Create(filePath))
{
    Byte[] textToWrite = new UTF8Encoding(true).GetBytes("Testing Web role storage");
    writeStream.Write(textToWrite, 0, textToWrite.Length);
}
```

### <a name="find-a-file-written-to-local-storage"></a>Yerel depolamaya yazılmış bir dosya bulma

Önceki bölümde kod tarafından oluşturulan dosyayı görüntülemek için şu adımları izleyin:

1. Yeni Windows alanında Azure simgesine sağ tıklayın ve bağlam menüsünden İşlem Ve Kullanıcı Arabirimini **Göster'Emulator seçin.**

    ![Azure işlem öykünücüsünü gösterme](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Web rolünü seçin.

    ![Azure işlem öykünücüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. İşlem Microsoft Azure **menüsünde Araçlar Emulator** yerel **mağazayı**  >  **aç'ı seçin.**

    ![Yerel mağaza menü öğesini açma](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Windows Gezgini penceresi açıldığında, Arama metin kutusuna ''MyLocalStorageTest.txt '' yazın ve Enter'ı  seçerek arama başlatın.

## <a name="next-steps"></a>Sonraki adımlar
Azure'da Azure projeleri hakkında daha fazla Visual Studio [için Azure Project.](vs-azure-tools-configuring-an-azure-project.md) Şema Başvurusu'larını okuyarak bulut hizmeti şeması hakkında daha [fazla bilgi edinin.](/previous-versions/azure/dd179398(v=azure.100))
