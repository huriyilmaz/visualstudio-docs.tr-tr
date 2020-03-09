---
title: Azure bulut hizmeti rollerini yapılandırma
description: Ayarlama ve rolleri Visual Studio kullanarak Azure bulut Hizmetleri için yapılandırma hakkında bilgi edinin.
author: ghogen
manager: jillfra
assetId: d397ef87-64e5-401a-aad5-7f83f1022e16
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 810ebfcfb4cb4354c3df4c0d9892a37ca1624256
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410052"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti rollerini yapılandırma
Azure bulut hizmeti çalışan veya web rollerinin bir veya daha fazla olabilir. Her rol için bu rolü nasıl ayarlandığı tanımlayın ve bu rolü nasıl çalıştığını da yapılandırmanız gerekir. Bulut hizmetlerindeki roller hakkında daha fazla bilgi edinmek için bkz. [Azure 'A giriş videosu Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

Bulut hizmetiniz için bilgiler aşağıdaki dosyalarda saklanır:

- **ServiceDefinition. csdef** -hizmet tanımı dosyası, gerekli rollerin, uç noktaların ve sanal makine boyutunun yanı sıra bulut hizmetiniz için çalışma zamanı ayarlarını tanımlar. Rolünüzde `ServiceDefinition.csdef` depolanan verilerin hiçbiri, rolünüz çalışırken değiştirilebilir.
- **ServiceConfiguration. cscfg** -hizmet yapılandırma dosyası, bir rolün kaç örneğinin çalıştırılacağını ve bir rol için tanımlanan ayarların değerlerini yapılandırır. `ServiceConfiguration.cscfg` depolanan veriler, rolünüzün çalıştığı sırada değiştirilebilir.

Farklı değerler için bir rol nasıl çalıştığını denetleyen ayarları depolamak için birden çok hizmet yapılandırmaları tanımlayabilirsiniz. Her dağıtım ortamı için farklı hizmet yapılandırmasını kullanabilirsiniz. Örneğin, bir yerel hizmet yapılandırmasında yerel Azure depolama öykünücüsü kullanma ve bulutta Azure depolamanızı kullanmak için başka bir hizmet yapılandırması oluşturmak için depolama hesabı bağlantı dizesi ayarlayabilirsiniz.

Visual Studio'da bir Azure bulut hizmeti oluşturduğunuzda, iki hizmet yapılandırması otomatik olarak oluşturulur ve Azure projenize eklenir:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Azure bulut hizmeti yapılandırın
Visual Studio'da Çözüm Gezgini'nden bir Azure bulut hizmeti aşağıdaki adımlarda gösterildiği gibi yapılandırabilirsiniz:

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Çözüm Gezgini proje bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Projenin Özellikler sayfasında **geliştirme** sekmesini seçin.

    ![Proje Özellikleri sayfası - geliştirme sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. **Hizmet yapılandırması** listesinde, düzenlemek istediğiniz hizmet yapılandırmasının adını seçin. (Bu rolün tüm hizmet yapılandırmalarında değişiklik yapmak istiyorsanız, **Tüm Konfigürasyonlar**' ı seçin.)

    > [!IMPORTANT]
    > Belirli hizmet yapılandırması seçerseniz, bazı özellikler tüm yapılandırmalar için yalnızca ayarlanabilir için devre dışı bırakıldı. Bu özellikleri düzenlemek için **Tüm Konfigürasyonlar**' ı seçmeniz gerekir.
    >
    >

    ![Azure bulut hizmeti için hizmet yapılandırması listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Rol örnekleri sayısını değiştirin
Bulut hizmetinizin performansını artırmak için kullanıcı ya da belirli bir rol için beklenen yük sayısına dayalı olarak çalıştırılan bir rolün örnekleri sayısını değiştirebilirsiniz. Bulut hizmeti Azure içinde çalıştığında her bir rol örneği için ayrı bir sanal makine oluşturulur. Bu, bu bulut hizmeti dağıtımı için faturalandırma etkiler. Faturalandırma hakkında daha fazla bilgi için bkz. [Microsoft Azure Faturanızı Anlama](/azure/billing/billing-understand-your-bill).

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin. **Roller** düğümü altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Yapılandırma** sekmesini seçin.

    ![Yapılandırma sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. **Hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. **Örnek sayısı** metin kutusunda, bu rol için başlamasını istediğiniz örneklerin sayısını girin. Bulut hizmeti Azure'da yayımlarken her örneği ayrı bir sanal makinede çalışır.

    ![Örnek sayısını güncelleştiriliyor](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Visual Studio araç çubuğundan **Kaydet**' i seçin.

## <a name="manage-connection-strings-for-storage-accounts"></a>Depolama hesapları için bağlantı dizelerini Yönet
Ekleyin, kaldırın veya bağlantı dizeleri, hizmet yapılandırması için değiştirin. Örneğin, `UseDevelopmentStorage=true`değerine sahip bir yerel hizmet yapılandırması için yerel bir bağlantı dizesi isteyebilirsiniz. Azure'da bir depolama hesabını kullanan bir bulut hizmeti yapılandırması yapılandırmak isteyebilirsiniz.

> [!WARNING]
> Bir depolama hesabı bağlantı dizesi için Azure depolama hesabı anahtar bilgilerini girdiğinizde, bu bilgiler hizmet yapılandırma dosyasında yerel olarak depolanır. Ancak, bu bilgileri şu anda şifreli metin olarak depolanmaz.
>
>

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetinizin farklı bağlantı dizelerini kullanma veya Bulut hizmetinizi Azure'da yayımlarken, kodunuzu değiştirmeniz gerekmez. Kodunuzda bağlantı dizesi için aynı adı kullanabilirsiniz ve bulut hizmetinizi oluşturma sırasında veya uygulamayı yayımladığınızda seçtiğiniz hizmet yapılandırmasına göre farklı değerdir.

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin. **Roller** düğümü altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Ayarlar** sekmesini seçin.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. **Hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet yapılandırması](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Bir bağlantı dizesi eklemek için, **Ayar ekle**' yi seçin.

    ![Bağlantı dizesi Ekle](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Yeni ayar listesine eklendikten sonra listedeki satıra gerekli bilgilerle güncelleştirin.

    ![Yeni bağlantı dizesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** -bağlantı dizesi için kullanmak istediğiniz adı girin.
    - **Yazın** -açılan listeden **bağlantı dizesini** seçin.
    - **Değer** -bağlantı dizesini doğrudan **değer** hücresine girebilir veya **depolama bağlantı dizesi oluştur** iletişim kutusunda çalışmak için üç nokta (...) işaretini seçebilirsiniz.

1. **Depolama bağlantı dizesi oluştur** iletişim kutusunda, **kullanarak bağlan**seçeneğini belirleyin. Seçenek için yönergeleri izleyin:

    - **Microsoft Azure depolama öykünücüsü** -bu seçeneği belirlerseniz, iletişim kutusundaki geri kalan ayarlar yalnızca Azure 'a uygulandıklarında devre dışı bırakılır. **Tamam**’ı seçin.
    - **Aboneliğiniz** -bu seçeneği belirlerseniz, bir Microsoft hesabı seçip açmak ya da bir Microsoft hesabı eklemek için açılan listeyi kullanın. Bir Azure aboneliğini ve depolama hesabı seçin. **Tamam**’ı seçin.
    - **El ile girilen kimlik bilgileri** -depolama hesabı adını ve birincil ya da ikinci anahtarı girin. **Bağlantı** için bir seçenek belirleyin (çoğu senaryo için https önerilir.) **Tamam ' ı**seçin.

1. Bir bağlantı dizesini silmek için bağlantı dizesini seçin ve sonra **ayarı kaldır**' ı seçin.

1. Visual Studio araç çubuğundan **Kaydet**' i seçin.

## <a name="programmatically-access-a-connection-string"></a>Bir bağlantı dizesi programlamayla erişme

Aşağıdaki adımlarda, C# kullanarak bir bağlantı dizesi programlı olarak erişmek gösterilmektedir.

1. Aşağıdaki using yönergelerini nerede seçeceğiz ayarını kullanmak için bir C# dosyasına:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod, bir bağlantı dizesi erişmeye ilişkin bir örnek göstermektedir. &lt;ConnectionStringName > yer tutucusunu uygun değerle değiştirin.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Azure bulut hizmetinizde kullanmak için özel ayarlar Ekle
Hizmet yapılandırma dosyasında özel ayarlar bir ad ve bir özel hizmet yapılandırması için bir dize değeri eklemenize olanak sağlar. Bir ayarın değerini okumak ve kodunuzda mantığı denetlemek için bu değeri kullanarak bulut hizmetinizde bir özelliğini yapılandırmak için bu ayarı kullanmak seçebilirsiniz. Bu hizmet yapılandırma değerleri, hizmet paketi veya Bulut hizmetinizi çalışırken yeniden derlemeye gerek kalmadan değiştirebilirsiniz. Kodunuzu bildirimleri için bir ayar değiştiğinde kontrol edebilirsiniz. Bkz [. Roleenvironment. Changing olayı](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Ekleyin, kaldırın veya hizmet yapılandırmalarınız için özel ayarları değiştirin. Bu dizeler için farklı hizmet yapılandırması için farklı değerler isteyebilirsiniz.

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetiniz farklı dizeleri kullanın veya Bulut hizmetinizi Azure'da yayımlarken, kodunuzu değiştirmeniz gerekmez. Kodunuzda dize için aynı adı kullanabilirsiniz ve bulut hizmetinizi oluşturma sırasında veya uygulamayı yayımladığınızda seçtiğiniz hizmet yapılandırmasına göre farklı değerdir.

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin. **Roller** düğümü altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Ayarlar** sekmesini seçin.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. **Hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Özel bir ayar eklemek için **Ayar ekle**' yi seçin.

    ![Özel ayar Ekle](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Yeni ayar listesine eklendikten sonra listedeki satıra gerekli bilgilerle güncelleştirin.

    ![Yeni özel ayarı](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** -ayarın adını girin.
    - **Açılan listeden** **dize** ' yi seçin.
    - **Değer** -ayarın değerini girin. Değeri doğrudan **değer** hücresine girebilir veya **dizeyi Düzenle** iletişim kutusuna değeri girmek için üç nokta (...) işaretini seçebilirsiniz.

1. Özel bir ayarı silmek için ayarı seçin ve sonra **ayarı kaldır**' ı seçin.

1. Visual Studio araç çubuğundan **Kaydet**' i seçin.

## <a name="programmatically-access-a-custom-settings-value"></a>Özel bir ayarın değerini programlamayla erişme

Aşağıdaki adımlarda, C# kullanarak özel bir ayarı programlı olarak erişmek gösterilmektedir.

1. Aşağıdaki using yönergelerini nerede seçeceğiz ayarını kullanmak için bir C# dosyasına:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod bir özel ayarı erişmeye ilişkin bir örnek göstermektedir. &lt;SettingName > yer tutucusunu uygun değerle değiştirin.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Her rol örneği için yerel depolamayı yönetin
Her bir rol örneği için yerel dosya sistemi depolaması ekleyebilirsiniz. Depolama, erişilebilir değil. diğer verilerin depolandığı için rol örneklerini veya diğer rolleri tarafından depolanan veriler.

1. Oluşturun veya bir Azure bulut hizmeti projesini Visual Studio'da açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin. **Roller** düğümü altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Çözüm Gezgini Azure rolü bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Yerel depolama** sekmesini seçin.

    ![Yerel depolama sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. **Hizmet yapılandırma** listesinde, yerel depolama ayarları tüm hizmet yapılandırmalarına uygulandığından **Tüm yapılandırmaların** seçili olduğundan emin olun. Başka bir değer devre dışı bırakılmasını sayfasında tüm giriş alanlarını sonuçlanır.

    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Yerel depolama girişi eklemek için **yerel depolama Ekle**' yi seçin.

    ![Yerel depolama ekleyin](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Yerel depolama girişte listesine eklendikten sonra listedeki satıra gerekli bilgilerle güncelleştirin.

    ![Yerel depolama girişte](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Ad** -yeni yerel depolama için kullanmak istediğiniz adı girin.
    - **Boyut (MB)** -yeni yerel depolama için gereken boyutu MB olarak girin.
    - **Rol geri dönüşümü temizle** -rolün sanal makinesi geri dönüştürüldüğünde yeni yerel depolama alanındaki verileri kaldırmak için bu seçeneği belirleyin.

1. Yerel depolama girişini silmek için girişi seçin ve ardından **yerel depolamayı kaldır**' ı seçin.

1. Visual Studio araç çubuğundan **Kaydet**' i seçin.

## <a name="programmatically-accessing-local-storage"></a>Yerel depolama program aracılığıyla erişme

Bu bölümde, bir test metin dosyası `MyLocalStorageTest.txt`yazarak yerel C# depolamaya programlı olarak nasıl erişebileceğiniz gösterilmektedir.

### <a name="write-a-text-file-to-local-storage"></a>Yerel depolama alanına bir metin dosyasına yazma

Aşağıdaki kod, yerel depolama alanına bir metin dosyası yazmak nasıl bir örnek gösterir. &lt;LocalStorageName > yer tutucusunu uygun değerle değiştirin.

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

### <a name="find-a-file-written-to-local-storage"></a>Bir dosyayı yerel depolama alanına yazılan bulma

Önceki bölümde kod tarafından oluşturulan bir dosyayı görüntülemek için aşağıdaki adımları izleyin:

1. Windows bildirim alanında Azure simgesine sağ tıklayın ve bağlam menüsünde, **Işlem öykünücüsü Kullanıcı arabirimini göster**' i seçin.

    ![Azure işlem öykünücüsünü Göster](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Web rolü seçin.

    ![Azure işlem öykünücüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. **Microsoft Azure Işlem öykünücüsü** menüsünde **Araçlar** ' ı seçerek **yerel depoyu açın** > .

    ![Açık bir yerel depo menü öğesi](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Windows Gezgini penceresi açıldığında **arama** metin kutusuna ' MyLocalStorageTest. txt ' ' girin ve aramayı başlatmak için **ENTER** ' ı seçin.

## <a name="next-steps"></a>Sonraki adımlar
[Azure projesi yapılandırmayı](vs-azure-tools-configuring-an-azure-project.md)okuyarak, Visual Studio 'da Azure projeleri hakkında daha fazla bilgi edinin. [Şema başvurusunu](https://msdn.microsoft.com/library/azure/dd179398)okuyarak bulut hizmeti şeması hakkında daha fazla bilgi edinin.
