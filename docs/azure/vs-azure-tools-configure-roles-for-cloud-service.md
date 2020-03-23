---
title: Azure bulut hizmeti için rolleri yapılandırma
description: Visual Studio'u kullanarak Azure bulut hizmetleri için rolleri nasıl ayarlayıp yapılandırabileceğinizi öğrenin.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.custom: seodec18
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: ded315917fb0e40159aed327ed98f747bb31c4b1
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301736"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti rollerini yapılandırma
Azure bulut hizmetinin bir veya daha fazla çalışanı veya web rolü olabilir. Her rol için, bu rolün nasıl ayarlandığını tanımlamanız ve bu rolün nasıl çalıştığını yapılandırmanız gerekir. Bulut hizmetlerindeki roller hakkında daha fazla bilgi edinmek için Azure [Bulut Hizmetlerine Giriş](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services)videosuna bakın.

Bulut hizmetinize ait bilgiler aşağıdaki dosyalarda depolanır:

- **ServiceDefinition.csdef** - Hizmet tanımı dosyası, bulut hizmetinizin çalışma zamanı ayarlarını, hangi rollerin gerekli olduğunu, uç noktaları ve sanal makine boyutunu tanımlar. Rolünüz çalışırken depolanan `ServiceDefinition.csdef` verilerin hiçbiri değiştirilemez.
- **ServiceConfiguration.cscfg** - Hizmet yapılandırma dosyası, bir rolün kaç örneğinin çalıştırıldığını ve bir rol için tanımlanan ayarların değerlerini yapılandırır. Rolünüz çalışırken `ServiceConfiguration.cscfg` depolanan veriler değiştirilebilir.

Bir rolün nasıl çalıştığını denetleyen ayarlar için farklı değerler depolamak için birden çok hizmet yapılandırması tanımlayabilirsiniz. Her dağıtım ortamı için farklı bir hizmet yapılandırması kullanabilirsiniz. Örneğin, depolama hesabı bağlantı dizenizi yerel bir hizmet yapılandırmasında yerel Azure depolama emülatörü kullanacak ve bulutta Azure depolamasını kullanmak için başka bir hizmet yapılandırması oluşturabilirsiniz.

Visual Studio'da bir Azure bulut hizmeti oluşturduğunuzda, otomatik olarak oluşturulur ve Azure projenize eklenir:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Azure bulut hizmetini yapılandırma
Aşağıdaki adımlarda gösterildiği gibi Visual Studio'daki Solution Explorer'dan bir Azure bulut hizmeti yapılandırabilirsiniz:

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde**projeyi sağ tıklatın ve bağlam menüsünden **Özellikler'i**seçin.

    ![Çözüm Explorer proje bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Projenin özellikleri sayfasında **Geliştirme** sekmesini seçin.

    ![Proje özellikleri sayfası - geliştirme sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. Hizmet **Yapılandırmalistesinde,** düzenlemek istediğiniz hizmet yapılandırmasının adını seçin. (Bu rol için tüm hizmet yapılandırmalarında değişiklik yapmak istiyorsanız, **Tüm Yapılandırmalar'ı**seçin.)

    > [!IMPORTANT]
    > Belirli bir hizmet yapılandırması seçerseniz, yalnızca tüm yapılandırmalar için ayarlanabildiklerinden bazı özellikler devre dışı bırakılır. Bu özellikleri düzenlemek için **Tüm Yapılandırmaları**seçmeniz gerekir.

    ![Azure bulut hizmeti için Hizmet Yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Rol örneklerinin sayısını değiştirme
Bulut hizmetinizin performansını artırmak için, kullanıcı sayısına veya belirli bir rol için beklenen yüke bağlı olarak çalışan bir rolün örnek sayısını değiştirebilirsiniz. Bulut hizmeti Azure'da çalıştığında, rolün her örneği için ayrı bir sanal makine oluşturulur. Bu, bu bulut hizmetinin dağıtımı için faturalandırmayı etkiler. Faturalandırma hakkında daha fazla bilgi için [bkz.](/azure/billing/billing-understand-your-bill)

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde**proje düğümlerini genişletin. **Roller** düğümüaltında, güncelleştirmek istediğiniz rolü sağ tıklatın ve bağlam menüsünden **Özellikler'i**seçin.

    ![Çözüm Gezgini Azure rol bağlamı menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Yapılandırma** sekmesini seçin.

    ![Yapılandırma sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. Hizmet **Yapılandırma** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet Yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. Örnek **sayısı** metin kutusuna, bu rol için başlamak istediğiniz örnek sayısını girin. Bulut hizmetini Azure'da yayımladığınızda her örnek ayrı bir sanal makinede çalışır.

    ![Örnek Sayısının Güncellenmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Visual Studio, araç çubuğundan **Kaydet'i**seçin.

## <a name="manage-connection-strings-for-storage-accounts"></a>Depolama hesapları için bağlantı dizelerini yönetme
Hizmet yapılandırmalarınız için bağlantı dizeleri ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Örneğin, `UseDevelopmentStorage=true`değeri . Azure'da bir depolama hesabı kullanan bir bulut hizmeti yapılandırmasını da yapılandırmak isteyebilirsiniz.

> [!WARNING]
> Bir depolama hesabı bağlantı dizesi için Azure depolama hesabı anahtar bilgilerini girdiğinizde, bu bilgiler hizmet yapılandırma dosyasında yerel olarak depolanır. Ancak, bu bilgiler şu anda şifreli metin olarak depolanmaz.
>
>

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetinizde farklı bağlantı dizeleri kullanmanız veya bulut hizmetinizi Azure'da yayımladığınızda kodunuzu değiştirmeniz gerekmez. Kodunuzda bağlantı dizesi için aynı adı kullanabilirsiniz ve bulut hizmetinizi oluştururken veya yayımlarken seçtiğiniz hizmet yapılandırmasını temel alan değer farklıdır.

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde**proje düğümlerini genişletin. **Roller** düğümüaltında, güncelleştirmek istediğiniz rolü sağ tıklatın ve bağlam menüsünden **Özellikler'i**seçin.

    ![Çözüm Gezgini Azure rol bağlamı menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Ayarlar** sekmesini seçin.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Hizmet **Yapılandırma** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet Yapılandırması](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Bağlantı dizesi eklemek için **Ayar Ekle'yi**seçin.

    ![Bağlantı dizesi ekleme](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Yeni ayar listeye eklendikten sonra, listedeki satırı gerekli bilgilerle güncelleştirin.

    ![Yeni bağlantı dizesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** - Bağlantı dizesi için kullanmak istediğiniz adı girin.
    - **Tür -** Açılan listeden **Bağlantı Dizesi'ni** seçin.
    - **Değer** - Bağlantı dizesini doğrudan **Değer** hücresine girebilir veya **Depolama Bağlantısı String** oluştur iletişim kutusunda çalışmak üzere elipsleri (...) seçebilirsiniz.

1. Depolama **Bağlantısı String oluştur** iletişim kutusunda, **kullanarak Bağlan**seçeneği ni seçin. Ardından seçtiğiniz seçenek için yönergeleri izleyin:

    - **Microsoft Azure depolama emülatörü** - Bu seçeneği seçerseniz, iletişim kutusundaki kalan ayarlar yalnızca Azure için geçerli olduğu için devre dışı bırakılır. **Tamam'ı**seçin.
    - **Aboneliğiniz** - Bu seçeneği seçerseniz, bir Microsoft hesabı seçmek ve oturum açmak veya bir Microsoft hesabı eklemek için açılır listeyi kullanın. Bir Azure aboneliği ve depolama hesabı seçin. **Tamam'ı**seçin.
    - **El ile girilen kimlik bilgileri** - Depolama hesabı adını ve birincil veya ikinci anahtarı girin. **Bağlantı** için bir seçenek seçin (çoğu senaryo için HTTPS önerilir.) **Tamam'ı**seçin.

1. Bağlantı dizesini silmek için bağlantı dizesini seçin ve ardından **Ayar'ı Kaldır'ı**seçin.

1. Visual Studio, araç çubuğundan **Kaydet'i**seçin.

## <a name="programmatically-access-a-connection-string"></a>Bir bağlantı dizesi programlı olarak erişin

Aşağıdaki adımlar, C# kullanarak bir bağlantı dizesine nasıl programlı olarak erişeceğimize gösterin.

1. Ayarı kullanacağınız c# dosyasına yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod, bağlantı dizesine nasıl erişilene ilişkin bir örneği göstermektedir. ConnectionStringName> yer tutucuyu &lt;uygun değerle değiştirin.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Azure bulut hizmetinizde kullanmak üzere özel ayarlar ekleme
Hizmet yapılandırma dosyasındaki özel ayarlar, belirli bir hizmet yapılandırması için bir dize için bir ad ve değer eklemenize izin verir. Bu ayarı, ayarın değerini okuyarak ve kodunızdaki mantığı denetlemek için bu değeri kullanarak bulut hizmetinizdeki bir özelliği yapılandırmak için kullanmayı seçebilirsiniz. Bu hizmet yapılandırma değerlerini, hizmet paketinizi yeniden oluşturmanıza gerek kalmadan veya bulut hizmetiniz çalışırken değiştirebilirsiniz. Kodunuz, ayar ne zaman değişebileceğine dair bildirimleri denetleyebilir. Bkz. [RoleEnvironment.Changing Event](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Hizmet yapılandırmalarınız için özel ayarlar ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Farklı hizmet yapılandırmaları için bu dizeleri için farklı değerler isteyebilirsiniz.

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetinizde farklı dizeleri kullanmanız veya bulut hizmetinizi Azure'da yayımladığınızda kodunuzu değiştirmeniz gerekmez. Bulut hizmetinizi oluştururken veya yayımlarken seçtiğiniz hizmet yapılandırmasını temel alan, kodunızdaki dize için aynı adı kullanabilirsiniz ve değer farklıdır.

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde**proje düğümlerini genişletin. **Roller** düğümüaltında, güncelleştirmek istediğiniz rolü sağ tıklatın ve bağlam menüsünden **Özellikler'i**seçin.

    ![Çözüm Gezgini Azure rol bağlamı menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Ayarlar** sekmesini seçin.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. Hizmet **Yapılandırma** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet Yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Özel ayar eklemek için **Ayar Ekle'yi**seçin.

    ![Özel ayar ekleme](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Yeni ayar listeye eklendikten sonra, listedeki satırı gerekli bilgilerle güncelleştirin.

    ![Yeni özel ayar](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** - Ayarın adını girin.
    - **Türü** - Açılan listeden **String'i** seçin.
    - **Değer** - Ayarın değerini girin. Değeri doğrudan **Değer** hücresine girebilir veya **Edit String** iletişim kutusundaki değeri girmek için elipsleri (...) seçebilirsiniz.

1. Özel bir ayarı silmek için, ayarı seçin ve ardından **Ayar'ı Kaldır'ı**seçin.

1. Visual Studio, araç çubuğundan **Kaydet'i**seçin.

## <a name="programmatically-access-a-custom-settings-value"></a>Özel bir ayarın değerine programlı olarak erişin

Aşağıdaki adımlar, C#'ı kullanarak özel bir ayara nasıl programlı olarak erişilenleri gösterir.

1. Ayarı kullanacağınız c# dosyasına yönergeleri kullanarak aşağıdakileri ekleyin:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod, özel bir ayara nasıl erişilene kadar erişilene ilgili bir örneği göstermektedir. SettingName &lt;> yer tutucuyu uygun değerle değiştirin.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Her rol örneği için yerel depolama yı yönetme
Bir rolün her örneği için yerel dosya sistemi depolama sı ekleyebilirsiniz. Bu depolama alanında depolanan verilere, verilerin depolandığı rolün diğer örnekleri veya diğer roller erişilemez.

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde**proje düğümlerini genişletin. **Roller** düğümüaltında, güncelleştirmek istediğiniz rolü sağ tıklatın ve bağlam menüsünden **Özellikler'i**seçin.

    ![Çözüm Gezgini Azure rol bağlamı menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. Yerel **Depolama** sekmesini seçin.

    ![Yerel depolama sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. Hizmet **Yapılandırmalistesinde,** tüm hizmet yapılandırmaları için yerel depolama ayarları uygulandığından **tüm Yapılandırmaların** seçildiğinden emin olun. Diğer değerler, sayfadaki tüm giriş alanlarının devre dışı edilmesiyle sonuçlanır.

    ![Hizmet Yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Yerel depolama alanı girişi eklemek için **Yerel Depolama Alanı Ekle'yi**seçin.

    ![Yerel depolama alanı ekleme](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Yeni yerel depolama girişi listeye eklendikten sonra, listedeki satırı gerekli bilgilerle güncelleştirin.

    ![Yeni yerel depolama girişi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Ad** - Yeni yerel depolama alanı için kullanmak istediğiniz adı girin.
    - **Boyut (MB)** - Yeni yerel depolama için ihtiyacınız olan boyutu MB'ye girin.
    - **Rol geri dönüşümünü temizle** - Rol için sanal makine geri dönüştürüldüğünde yeni yerel depolama alanında verileri kaldırmak için bu seçeneği belirleyin.

1. Yerel bir depolama girişini silmek için, girişi seçin ve ardından **Yerel Depolama alanını kaldır'ı**seçin.

1. Visual Studio, araç çubuğundan **Kaydet'i**seçin.

## <a name="programmatically-accessing-local-storage"></a>Yerel depolamaya programlı olarak erişme

Bu bölümde, bir test metni dosyası `MyLocalStorageTest.txt`yazarak C# kullanarak yerel depolamaya nasıl programlı olarak erişilenler gösteriş.

### <a name="write-a-text-file-to-local-storage"></a>Yerel depolama alanına metin dosyası yazma

Aşağıdaki kod, yerel depolama alanına metin dosyası nın nasıl yazılalacak nasıl yazılalacak nasıl bir örnek gösterir. LocalStorageName> yer tutucuyu &lt;uygun değerle değiştirin.

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

### <a name="find-a-file-written-to-local-storage"></a>Yerel depolama alanına yazılmış bir dosya bulma

Önceki bölümde kod tarafından oluşturulan dosyayı görüntülemek için aşağıdaki adımları izleyin:

1. Windows bildirim alanında Azure simgesine sağ tıklayın ve bağlam menüsünden **Bilgi İşlem Emülatör Ünü'nü göster'i**seçin.

    ![Azure işlem emülatörü göster](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Web rolünü seçin.

    ![Azure işlem emülatörü](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. Microsoft **Azure İşlem Emülatörü** menüsünde, **Araçlar** > **Açık yerel mağazayı**seçin.

    ![Yerel mağaza menü öğeni açma](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Windows Gezgini penceresi açıldığında, **Arama** metin kutusuna 'MyLocalStorageTest.txt' girin ve aramayı başlatmak için **Enter'u** seçin.

## <a name="next-steps"></a>Sonraki adımlar
[Azure Projesi Yapılandırma'yı](vs-azure-tools-configuring-an-azure-project.md)okuyarak Visual Studio'daki Azure projeleri hakkında daha fazla bilgi edinin. [Şema Referans'ı](https://msdn.microsoft.com/library/azure/dd179398)okuyarak bulut hizmeti şeması hakkında daha fazla bilgi edinin.
