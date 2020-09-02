---
title: Azure bulut hizmeti için rolleri yapılandırma
description: Visual Studio 'Yu kullanarak Azure bulut hizmetleri için rolleri ayarlamayı ve yapılandırmayı öğrenin.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "89315167"
---
# <a name="configure-azure-cloud-service-roles-with-visual-studio"></a>Visual Studio ile Azure bulut hizmeti rollerini yapılandırma
Bir Azure bulut hizmetinde bir veya daha fazla çalışan veya Web rolü olabilir. Her rol için, bu rolün nasıl ayarlandığını tanımlamanız ve ayrıca bu rolün nasıl çalıştığını tanımlamanız gerekir. Bulut hizmetlerindeki roller hakkında daha fazla bilgi edinmek için bkz. [Azure 'A giriş videosu Cloud Services](https://channel9.msdn.com/Series/Windows-Azure-Cloud-Services-Tutorials/Introduction-to-Windows-Azure-Cloud-Services).

Bulut hizmetinize ilişkin bilgiler aşağıdaki dosyalarda saklanır:

- **ServiceDefinition. csdef** -hizmet tanımı dosyası, gerekli rollerin, uç noktaların ve sanal makine boyutunun yanı sıra bulut hizmetiniz için çalışma zamanı ayarlarını tanımlar. Rolü çalışırken, içinde depolanan verilerin hiçbiri `ServiceDefinition.csdef` değiştirilemez.
- **ServiceConfiguration. cscfg** -hizmet yapılandırma dosyası, bir rolün kaç örneğinin çalıştırılacağını ve bir rol için tanımlanan ayarların değerlerini yapılandırır. Rolü çalışırken ' de depolanan veriler `ServiceConfiguration.cscfg` değiştirilebilir.

Rolün nasıl çalıştığını denetleyen ayarların farklı değerlerini depolamak için, birden çok hizmet yapılandırması tanımlayabilirsiniz. Her dağıtım ortamı için farklı bir hizmet yapılandırması kullanabilirsiniz. Örneğin, depolama hesabı Bağlantı dizenizi yerel bir hizmet yapılandırmasında yerel Azure depolama öykünücüsünü kullanacak şekilde ayarlayabilir ve Bulutta Azure Storage 'ı kullanmak için başka bir hizmet yapılandırması oluşturabilirsiniz.

Visual Studio 'da bir Azure bulut hizmeti oluşturduğunuzda, iki hizmet yapılandırması otomatik olarak oluşturulur ve Azure projenize eklenir:

- `ServiceConfiguration.Cloud.cscfg`
- `ServiceConfiguration.Local.cscfg`

## <a name="configure-an-azure-cloud-service"></a>Azure bulut hizmeti yapılandırma
Aşağıdaki adımlarda gösterildiği gibi, bir Azure bulut hizmetini Visual Studio 'da Çözüm Gezgini yapılandırabilirsiniz:

1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, projeye sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Çözüm Gezgini projesi bağlam menüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-project-context-menu.png)

1. Projenin Özellikler sayfasında **geliştirme** sekmesini seçin.

    ![Proje Özellikleri sayfası-geliştirme sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-development-tab.png)

1. **Hizmet yapılandırması** listesinde, düzenlemek istediğiniz hizmet yapılandırmasının adını seçin. (Bu rolün tüm hizmet yapılandırmalarında değişiklik yapmak istiyorsanız, **Tüm Konfigürasyonlar**' ı seçin.)

    > [!IMPORTANT]
    > Belirli bir hizmet yapılandırması seçerseniz bazı özellikler yalnızca tüm yapılandırmalar için ayarlanabileceğinden devre dışı bırakılır. Bu özellikleri düzenlemek için **Tüm Konfigürasyonlar**' ı seçmeniz gerekir.
    >
    >

    ![Azure bulut hizmeti için hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/cloud-service-service-configuration-property.png)

## <a name="change-the-number-of-role-instances"></a>Rol örneklerinin sayısını değiştirme
Bulut hizmetinizin performansını artırmak için, çalışan bir rolün örnek sayısını veya belirli bir rol için beklenen yükleme sayısını değiştirebilirsiniz. Bulut hizmeti Azure 'da çalıştığında, bir rolün her örneği için ayrı bir sanal makine oluşturulur. Bu, bu bulut hizmeti dağıtımına ilişkin faturalandırmayı etkiler. Faturalandırma hakkında daha fazla bilgi için bkz. [Microsoft Azure Faturanızı Anlama](/azure/billing/billing-understand-your-bill).

1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin. **Roller** düğümü altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Azure rolü bağlam menüsünü Çözüm Gezgini](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Yapılandırma** sekmesini seçin.

    ![Yapılandırma sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page.png)

1. **Hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-select-configuration.png)

1. **Örnek sayısı** metin kutusunda, bu rol için başlamasını istediğiniz örneklerin sayısını girin. Bulut hizmetini Azure 'da yayımladığınızda her örnek ayrı bir sanal makinede çalışır.

    ![Örnek sayısı güncelleştiriliyor](./media/vs-azure-tools-configure-roles-for-cloud-service/role-configuration-properties-page-instance-count.png)

1. Visual Studio araç çubuğundan **Kaydet**' i seçin.

## <a name="manage-connection-strings-for-storage-accounts"></a>Depolama hesapları için bağlantı dizelerini yönetme
Hizmet yapılandırmanız için bağlantı dizelerini ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Örneğin, bir değeri olan yerel bir hizmet yapılandırması için yerel bir bağlantı dizesi isteyebilirsiniz `UseDevelopmentStorage=true` . Azure 'da bir depolama hesabı kullanan bir bulut hizmeti yapılandırması da yapılandırmak isteyebilirsiniz.

> [!WARNING]
> Bir depolama hesabı bağlantı dizesi için Azure depolama hesabı anahtar bilgilerini girdiğinizde, bu bilgiler yerel olarak hizmet yapılandırma dosyasında depolanır. Ancak, bu bilgiler şu anda şifrelenmiş metin olarak depolanmaz.
>
>

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetinizde farklı bağlantı dizeleri kullanmanız veya bulut hizmetinizi Azure 'da yayımladığınızda kodunuzda değişiklik yapmanız gerekmez. Kodunuzda bağlantı dizesi için aynı adı kullanabilirsiniz ve değer, bulut hizmetinizi oluştururken veya yayımladığınızda seçtiğiniz hizmet yapılandırmasına göre farklılık gösteren bir addır.

1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin. **Roller** düğümü altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Azure rolü bağlam menüsünü Çözüm Gezgini](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Ayarlar** sekmesini seçin.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. **Hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet yapılandırması](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Bir bağlantı dizesi eklemek için, **Ayar ekle**' yi seçin.

    ![Bağlantı dizesi Ekle](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Listeye yeni ayar eklendikten sonra, listedeki satırı gerekli bilgilerle güncelleştirin.

    ![Yeni bağlantı dizesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** -bağlantı dizesi için kullanmak istediğiniz adı girin.
    - **Yazın** -açılan listeden **bağlantı dizesini** seçin.
    - **Değer** -bağlantı dizesini doğrudan **değer** hücresine girebilir veya **depolama bağlantı dizesi oluştur** iletişim kutusunda çalışmak için üç nokta (...) işaretini seçebilirsiniz.

1. **Depolama bağlantı dizesi oluştur** iletişim kutusunda, **kullanarak bağlan**seçeneğini belirleyin. Ardından, seçtiğiniz seçeneğe ilişkin yönergeleri izleyin:

    - **Microsoft Azure depolama öykünücüsü** -bu seçeneği belirlerseniz, iletişim kutusundaki geri kalan ayarlar yalnızca Azure 'a uygulandıklarında devre dışı bırakılır. **Tamam**’ı seçin.
    - **Aboneliğiniz** -bu seçeneği belirlerseniz, bir Microsoft hesabı seçip açmak ya da bir Microsoft hesabı eklemek için açılan listeyi kullanın. Bir Azure aboneliği ve depolama hesabı seçin. **Tamam**’ı seçin.
    - **El ile girilen kimlik bilgileri** -depolama hesabı adını ve birincil ya da ikinci anahtarı girin. **Bağlantı** için bir seçenek belirleyin (çoğu senaryo için https önerilir.) **Tamam ' ı**seçin.

1. Bir bağlantı dizesini silmek için bağlantı dizesini seçin ve sonra **ayarı kaldır**' ı seçin.

1. Visual Studio araç çubuğundan **Kaydet**' i seçin.

## <a name="programmatically-access-a-connection-string"></a>Bir bağlantı dizesine program aracılığıyla erişin

Aşağıdaki adımlarda, C# kullanarak bir bağlantı dizesine programlı olarak nasıl erişebileceğiniz gösterilmektedir.

1. Aşağıdaki using yönergelerini, ayarı kullanacağınız bir C# dosyasına ekleyin:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod, bir bağlantı dizesine nasıl erişeceinin bir örneğini göstermektedir. &lt;ConnectionStringName> yer tutucusunu uygun değerle değiştirin.

    ```csharp
    // Setup the connection to Azure Storage
    var storageAccount = CloudStorageAccount.Parse(RoleEnvironment.GetConfigurationSettingValue("<ConnectionStringName>"));
    ```

## <a name="add-custom-settings-to-use-in-your-azure-cloud-service"></a>Azure bulut hizmetinizde kullanmak üzere özel ayarlar ekleme
Hizmet yapılandırma dosyasındaki özel ayarlar, belirli bir hizmet yapılandırması için bir dize adı ve değeri eklemenize olanak tanır. Bu ayarı, ayarın değerini okuyarak ve kodunuzda mantığı denetlemek için bu değeri kullanarak bulut hizmetinizdeki bir özelliği yapılandırmak için kullanmayı tercih edebilirsiniz. Hizmet paketinizi yeniden derlemek zorunda kalmadan veya bulut hizmetiniz çalışırken bu hizmet yapılandırma değerlerini değiştirebilirsiniz. Kodunuz, bir ayarın ne zaman değiştiği hakkında bildirimleri denetleyebilir. Bkz [. Roleenvironment. Changing olayı](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleenvironment.changing.aspx).

Hizmet yapılandırmalara yönelik özel ayarları ekleyebilir, kaldırabilir veya değiştirebilirsiniz. Farklı hizmet yapılandırmalarında bu dizeler için farklı değerler isteyebilirsiniz.

Her hizmet yapılandırması için farklı bir değer kullanarak, bulut hizmetinizde farklı dizeler kullanmanıza veya bulut hizmetinizi Azure 'da yayımladığınızda kodunuzu değiştirmenize izin vermeyin. Kodunuzda dize için aynı adı kullanabilirsiniz ve değer, bulut hizmetinizi oluştururken veya yayımladığınızda seçtiğiniz hizmet yapılandırmasına göre farklılık gösteren bir addır.

1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin. **Roller** düğümü altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Azure rolü bağlam menüsünü Çözüm Gezgini](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Ayarlar** sekmesini seçin.

    ![Ayarlar sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab.png)

1. **Hizmet yapılandırması** listesinde, güncelleştirmek istediğiniz hizmet yapılandırmasını seçin.

    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-select-configuration.png)

1. Özel bir ayar eklemek için **Ayar ekle**' yi seçin.

    ![Özel ayar Ekle](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting.png)

1. Listeye yeni ayar eklendikten sonra, listedeki satırı gerekli bilgilerle güncelleştirin.

    ![Yeni özel ayar](./media/vs-azure-tools-configure-roles-for-cloud-service/project-properties-settings-tab-add-setting-new-setting.png)

    - **Ad** -ayarın adını girin.
    - **Açılan listeden** **dize** ' yi seçin.
    - **Değer** -ayarın değerini girin. Değeri doğrudan **değer** hücresine girebilir veya **dizeyi Düzenle** iletişim kutusuna değeri girmek için üç nokta (...) işaretini seçebilirsiniz.

1. Özel bir ayarı silmek için ayarı seçin ve sonra **ayarı kaldır**' ı seçin.

1. Visual Studio araç çubuğundan **Kaydet**' i seçin.

## <a name="programmatically-access-a-custom-settings-value"></a>Programlı olarak özel bir ayarın değerine erişme

Aşağıdaki adımlarda, C# kullanarak programlı olarak özel bir ayara nasıl erişebileceğiniz gösterilmektedir.

1. Aşağıdaki using yönergelerini, ayarı kullanacağınız bir C# dosyasına ekleyin:

    ```csharp
    using Microsoft.WindowsAzure;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.ServiceRuntime;
    ```

1. Aşağıdaki kod, özel bir ayara erişme hakkında bir örnek gösterir. &lt;SettingName> yer tutucusunu uygun değerle değiştirin.

    ```csharp
    var settingValue = RoleEnvironment.GetConfigurationSettingValue("<SettingName>");
    ```

## <a name="manage-local-storage-for-each-role-instance"></a>Her rol örneği için yerel depolamayı yönetme
Bir rolün her örneği için yerel dosya sistemi depolaması ekleyebilirsiniz. Bu depolamada depolanan verilere, verilerin depolandığı diğer rolün diğer örnekleri veya diğer roller tarafından erişilemez.

1. Visual Studio 'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin. **Roller** düğümü altında, güncelleştirmek istediğiniz role sağ tıklayın ve bağlam menüsünden **Özellikler**' i seçin.

    ![Azure rolü bağlam menüsünü Çözüm Gezgini](./media/vs-azure-tools-configure-roles-for-cloud-service/solution-explorer-azure-role-context-menu.png)

1. **Yerel depolama** sekmesini seçin.

    ![Yerel depolama sekmesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab.png)

1. **Hizmet yapılandırma** listesinde, yerel depolama ayarları tüm hizmet yapılandırmalarına uygulandığından **Tüm yapılandırmaların** seçili olduğundan emin olun. Diğer herhangi bir değer, sayfadaki tüm giriş alanlarının devre dışı bırakılmakta olduğunu sonuçlanır.

    ![Hizmet yapılandırma listesi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-service-configuration.png)

1. Yerel depolama girişi eklemek için **yerel depolama Ekle**' yi seçin.

    ![Yerel depolama Ekle](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-add-local-storage.png)

1. Yeni yerel depolama girdisi listeye eklendikten sonra listedeki satırı gerekli bilgilerle güncelleştirin.

    ![Yeni yerel depolama girişi](./media/vs-azure-tools-configure-roles-for-cloud-service/role-local-storage-tab-new-local-storage.png)

    - **Ad** -yeni yerel depolama için kullanmak istediğiniz adı girin.
    - **Boyut (MB)** -yeni yerel depolama için gereken boyutu MB olarak girin.
    - **Rol geri dönüşümü temizle** -rolün sanal makinesi geri dönüştürüldüğünde yeni yerel depolama alanındaki verileri kaldırmak için bu seçeneği belirleyin.

1. Yerel depolama girişini silmek için girişi seçin ve ardından **yerel depolamayı kaldır**' ı seçin.

1. Visual Studio araç çubuğundan **Kaydet**' i seçin.

## <a name="programmatically-accessing-local-storage"></a>Yerel depolamaya programlı bir şekilde erişme

Bu bölümde, bir test metin dosyası yazarak C# kullanarak yerel depolamaya programlı bir şekilde nasıl erişebileceğiniz gösterilmektedir `MyLocalStorageTest.txt` .

### <a name="write-a-text-file-to-local-storage"></a>Yerel depolamaya bir metin dosyası yaz

Aşağıdaki kod, yerel depolamaya bir metin dosyasının nasıl yazılacağını gösteren bir örnek gösterir. &lt;Localstoragename> yer tutucusunu uygun değerle değiştirin.

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

### <a name="find-a-file-written-to-local-storage"></a>Yerel depolamaya yazılan bir dosya bulun

Önceki bölümde kodla oluşturulan dosyayı görüntülemek için aşağıdaki adımları izleyin:

1. Windows bildirim alanında Azure simgesine sağ tıklayın ve bağlam menüsünde, **Işlem öykünücüsü Kullanıcı arabirimini göster**' i seçin.

    ![Azure işlem öykünücüsünü göster](./media/vs-azure-tools-configure-roles-for-cloud-service/show-compute-emulator.png)

1. Web rolünü seçin.

    ![Azure işlem öykünücüsü](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator.png)

1. **Microsoft Azure işlem öykünücüsü** menüsünde **Araçlar**  >  **yerel depo aç**' ı seçin.

    ![Yerel mağaza menü öğesini aç](./media/vs-azure-tools-configure-roles-for-cloud-service/compute-emulator-open-local-store-menu.png)

1. Windows Gezgini penceresi açıldığında **arama** metin kutusuna 'MyLocalStorageTest.txt' ' girin ve aramayı başlatmak için **ENTER** ' u seçin.

## <a name="next-steps"></a>Sonraki adımlar
[Azure projesi yapılandırmayı](vs-azure-tools-configuring-an-azure-project.md)okuyarak, Visual Studio 'da Azure projeleri hakkında daha fazla bilgi edinin. [Şema başvurusunu](https://msdn.microsoft.com/library/azure/dd179398)okuyarak bulut hizmeti şeması hakkında daha fazla bilgi edinin.
