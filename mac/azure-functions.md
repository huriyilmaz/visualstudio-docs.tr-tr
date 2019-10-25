---
title: Azure İşlevleri’ne Giriş
description: Mac için Visual Studio 'de Azure işlevleri 'ni kullanma.
author: sayedihashimi
ms.author: sayedha
ms.date: 04/02/2019
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 493e03ecd2a10d7cd9e81467d5886f863cd7229b
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888589"
---
# <a name="introduction-to-azure-functions"></a>Azure İşlevleri’ne Giriş

Azure işlevleri, altyapıyı açıkça sağlamak veya yönetmek zorunda kalmadan, kod – – işlevleri – –, bulutta olay odaklı kod parçacıkları oluşturup çalıştırmanın bir yoludur. Azure Işlevleri hakkında daha fazla bilgi için bkz. [Azure işlevleri belgeleri](/azure/azure-functions/).

## <a name="requirements"></a>Gereksinimler

Azure Işlev araçları, **Mac için Visual Studio 7,5** ve daha yeni bir sürüme dahildir.

İşlevleri oluşturup dağıtmak için, [https://azure.com/free](https://azure.com/free)ücretsiz olarak kullanılabilen bir Azure aboneliğine de ihtiyacınız vardır.

## <a name="creating-your-first-azure-functions-project"></a>İlk Azure Işlevleri projenizi oluşturma

1. Mac için Visual Studio **dosya > yeni çözüm**' ı seçin.
2. Yeni proje iletişim kutusunda **Cloud > genel** ' ın altındaki Azure işlevleri şablonunu seçin ve **İleri**' ye tıklayın:

    ![Azure işlevleri seçeneğini gösteren yeni proje iletişim kutusu](media/azure-functions-image1.png)

3. Kullanmak istediğiniz ilk Azure Işlevleri şablonunu seçin, işlevinizin adını girin ve **İleri**' ye tıklayın.

    ![Azure işlevleri şablonlarını gösteren yeni proje iletişim kutusu](media/azure-functions-image2.png)

    > [!TIP]
    > Paketlenmiş Azure Işlevleri çalışma zamanı ve şablonları (CLı) mümkün olduğunca güncel tutulurken, kaçınılmaz olarak güncelliğini yitirmiş. Yeni bir Işlevler projesi oluştururken, Mac için Visual Studio CLı güncelleştirmelerini denetler ve aşağıdaki görüntüde gösterildiği gibi size bildirir. Güncelleştirilmiş şablonları indirmek için düğmeye tıklamanız yeterlidir.
    > ![Azure işlevlerini gösteren yeni proje iletişim kutusu güncelleştirmeleri kullanılabilir](media/azure-functions-update.png)

    Seçtiğiniz işlevin türüne bağlı olarak, sonraki sayfada aşağıdaki görüntüde gösterildiği gibi erişim hakları gibi ayrıntılar girmeniz istenir:

    ![Ek seçeneği gösteren yeni proje iletişim kutusu](media/azure-functions-image3.png)

    Farklı türlerde Azure Işlevleri şablonları ve her bir şablonu yapılandırmak için gereken bağlama özellikleri hakkında daha fazla bilgi için, [kullanılabilir işlev şablonları](#available-function-templates) bölümüne bakın. Bu örnekte, erişim hakları anonim olarak ayarlanmış bir http tetikleyicisi kullanıyoruz.

4. Parametreleri ayarladıktan sonra, projenin konumunu seçin ve **Oluştur**' a tıklayın.

Mac için Visual Studio, varsayılan bir işlevle dahil .NET Standard bir proje oluşturur. Ayrıca, çeşitli **AzureWebJobs** paketlerine ek olarak, **Newtonsoft. JSON** paketini de NuGet başvuruları içerir.

![Şablondan yeni bir Azure işlevi görüntüleyen Mac için Visual Studio Düzenleyicisi](media/azure-functions-newproj.png)

Yeni proje aşağıdaki dosyaları içerir:

* **Your-Function-Name.cs** – Bu sınıf seçtiğiniz işlevin ortak kodunu içerir. İşlev adına sahip bir **fonksiyonadı** özniteliği ve işlevi neyin tetikleyeceğini belirten bir tetikleyici özniteliği içerir (örn. bir HTTP isteği). İşlev yöntemi hakkında daha fazla bilgi için [Azure işlevleri C# geliştirici başvurusu](/azure/azure-functions/functions-dotnet-class-library) makalesine bakın.
* **Host. JSON** – bu dosya, işlevler ana bilgisayarı için genel yapılandırma seçeneklerini açıklar. Örnek bir dosya ve bu dosya için kullanılabilir ayarlar hakkında bilgi için bkz. [Azure işlevleri için Host. JSON başvurusu](/azure/azure-functions/functions-host-json).
* **Local. Settings. JSON** – bu dosya, işlevleri yerel olarak çalıştırmaya yönelik tüm ayarları içerir. Bu ayarlar Azure Functions Core Tools tarafından kullanılır. Daha fazla bilgi için Azure Functions Core Tools makalesindeki [yerel ayarlar dosyası](/azure/azure-functions/functions-run-local#local-settings-file) ' na bakın.

Artık Mac için Visual Studio yeni bir Azure Işlevleri projesi oluşturduğunuza göre, yerel makinenizden varsayılan HTTP ile tetiklenen işlevi test edebilirsiniz.

## <a name="testing-the-function-locally"></a>İşlevi yerel olarak test etme

Mac için Visual Studio Azure Işlevleri desteğiyle, işlevinizi yerel geliştirme bilgisayarınızda test edebilir ve hatalarını ayıklayabilirsiniz.

1. İşlevinizi yerel olarak test etmek için Mac için Visual Studio içindeki **Çalıştır** düğmesine basın:

    ![Mac için Visual Studio 'da hata ayıklamayı Başlat düğmesi](media/azure-functions-run.png)

1. Projeyi çalıştırmak, Azure Işlevinde yerel hata ayıklamayı başlatır ve aşağıdaki görüntüde gösterildiği gibi yeni bir Terminal penceresi açar:

    ![işlev çıkışını gösteren Terminal penceresi](media/azure-functions-terminal.png)

    Çıktıdan URL 'YI kopyalayın.

3. HTTP isteğinin URL 'sini tarayıcınızın adres çubuğuna yapıştırın. `?name=<yourname>` sorgu dizesini URL 'nin sonuna ekleyin ve isteği yürütün. Aşağıdaki görüntüde, bu işlevin döndürdüğü yerel GET isteğine tarayıcıda yapılan yanıt gösterilmektedir:

    ![tarayıcıda http isteği](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Projenize başka bir işlev ekleme

İşlev Şablonları, en sık kullanılan tetikleyicileri ve şablonları kullanarak yeni işlevleri hızlıca oluşturmanızı sağlar. Başka bir işlev türü oluşturmak için aşağıdakileri yapın:

1. Yeni bir işlev eklemek için proje adına sağ tıklayın ve **> Ekle Işlev Ekle..** . öğesini seçin:

    ![Yeni işlev ekleme için bağlam eylemi](media/azure-functions-addnew.png)

2. **Yeni Azure işlevi** iletişim kutusunda, ihtiyacınız olan işlevi seçin:

    ![yeni Azure işlevi iletişim kutusu](media/azure-functions-image4.png)

    [Kullanılabilir işlev şablonları](#available-function-templates) bölümünde Azure işlev şablonlarının bir listesi verilmiştir.

İşlev uygulaması projenize daha fazla işlev eklemek için yukarıdaki yordamı kullanabilirsiniz. Projedeki her bir işlev farklı bir tetikleyicisine sahip olabilir, ancak bir işlevin tam olarak bir tetikleyicisi olmalıdır. Daha fazla bilgi için bkz. [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Azure'a Yayımlama

1. Proje adına sağ tıklayın ve **yayımla > Azure**'da Yayımla ' yı seçin: Azure 'da Yayımla menü seçeneğini ![](media/azure-functions-image5.png)
2. Azure hesabınızı Mac için Visual Studio için zaten bağladıysanız, kullanılabilir uygulama hizmetlerinin bir listesi görüntülenir. Oturum açmadıysanız bunu yapmanız istenir.
3. **Azure App Service Yayımla** iletişim kutusunda, var olan bir uygulama hizmetini seçebilir veya **Yeni**' ye tıklayarak yeni bir tane oluşturabilirsiniz.
4. **Yeni App Service oluştur** iletişim kutusunda ayarlarınızı girin: ![Azure 'a Yayımla menü seçeneği](media/azure-functions-image7.png)

    |Ayar  |Açıklama  |
    |---------|---------|
    |**App Service adı**|Yeni işlev uygulamanızı tanımlayan genel olarak benzersiz bir ad.|
    |**Aboneliğiniz**|Kullanılacak Azure aboneliği.|
    |**[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)**|İşlev uygulamanızın oluşturulacağı kaynak grubunun adı. Yeni bir kaynak grubu oluşturmak için **+** seçin.|
    |**[Hizmet planı](/azure/azure-functions/functions-scale)**|Mevcut bir planı seçin veya özel bir plan oluşturun. Size yakın bir bölgede veya işlevlerinizin erişebileceği diğer hizmetlere yakın bir konum seçin.|

5. Bir depolama hesabı oluşturmak için **İleri** ' ye tıklayın. Işlevler çalışma zamanı için bir Azure depolama hesabı gereklidir. Genel amaçlı bir depolama hesabı oluşturmak için **özel** ' e tıklayın veya var olan birini kullanın:

    ![Azure 'da Yayımla menü seçeneği](media/azure-functions-image8.png)

6. Azure 'da bu ayarlarla bir işlev uygulaması ve ilgili kaynaklar oluşturmak ve işlev proje kodunuzu dağıtmak için **Oluştur** ' a tıklayın.

7. Yayımlama sırasında bir iletişim kutusu istenebilir, "Azure 'da Işlevleri güncelleştirme" konusunda sizi bilgilendiren bir iletişim kutusu görüntülenebilir. **Evet**' e tıklayın:

    ![Azure 'da Yayımla menü seçeneği](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>İşlev uygulaması ayarları

Yerel. Settings. JSON içine eklediğiniz tüm ayarlar ayrıca Azure 'daki işlev uygulamasına eklenmelidir. Projeyi yayımladığınızda bu ayarlar otomatik olarak karşıya yüklenemez.

Uygulama ayarlarınıza erişmek için [https://ms.portal.azure.com/](https://ms.portal.azure.com/)Azure Portal gidin. **Işlevler uygulamalar**' ın altında **işlev uygulamaları** ' nı seçin ve işlevinizin adını vurgulayın:

![Azure işlevleri menüsü](media/azure-functions-image9.png)

**Genel bakış** sekmesinden **yapılandırılmış özellikler**altında **uygulama ayarları** ' nı seçin:

![Azure işlevinin Over sekmesi](media/azure-functions-image10.png)

Buradan, yeni uygulama ayarları ekleyebileceğiniz veya var olanları değiştirebileceğiniz işlev uygulaması için uygulama ayarlarını belirleyebilirsiniz:

![Azure portal uygulama ayarları alanı](media/azure-functions-image11.png)

Ayarlamanız gerekebilecek önemli bir ayar `FUNCTIONS_EXTENSION_VERSION`. Mac için Visual Studio yayımlarken, bu değer **Beta**olarak ayarlanmalıdır.

## <a name="available-function-templates"></a>Kullanılabilir işlev şablonları

- **GitHub tetikleyicisi** – GitHub depolarınızda oluşan olaylara yanıt verir. Daha fazla bilgi için [GitHub 'Daki Azure işlevleri makalesine](/azure/azure-functions/functions-create-github-webhook-triggered-function) bakın
  - GitHub yorumlayıcısı – bu işlev, bir sorun veya çekme isteği için GitHub Web kancası aldığında çalıştırılır ve bir açıklama ekler.
  - GitHub Web kancası – bu işlev, GitHub Web kancası aldığında çalıştırılır.

- **Http** – bir http isteği kullanarak kodunuzun yürütülmesini tetikler. Aşağıdaki HTTP Tetikleyicileri için açık şablonlar vardır:
  - Http tetikleyicisi
  - HTTP GET CRUD
  - HTTP POST CRUD
  - Parametrelerle http tetikleyicisi

- **Zamanlayıcı** – önceden tanımlanmış bir zamanlamaya göre Temizleme veya diğer toplu işleri yürütün. Bu şablon iki alan alır: bir ad ve bir zamanlama, altı bir alan CRON ifadesi. Daha fazla bilgi için bkz. [Azure işlevleri makalesi saat](/azure/azure-functions/functions-create-scheduled-function)

- **Kuyruk tetikleyicisi** – bu, Azure depolama kuyruğuna ulaşan iletilere yanıt verecek bir işlevdir. İşlev adına ek olarak, bu şablon bir **yol** (iletinin okunacağı kuyruğun adı) ve depolama hesabı **bağlantısı** (depolama hesabı Bağlantı dizenizi içeren uygulama ayarının adı) alır. Daha fazla bilgi için [kuyruk depolama hakkında Azure işlevleri makalesine](/azure/azure-functions/functions-create-storage-queue-triggered-function)bakın.

- **BLOB tetikleyicisi** – Azure Storage bloblarını bir kapsayıcıya eklendiğinde işleyin. Bu şablon, işlev adının yanı sıra bir yol ve bağlantı özelliği de alır. Path özelliği, depolama hesabınızda tetikleyicinin izleyecektir. Bağlantı hesabı, depolama hesabı Bağlantı dizenizi içeren uygulama ayarının adıdır. Daha fazla bilgi için bkz. [Azure Işlevleri BLOB depolama makalesi](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Genel Web kancası** – bu, Web kancalarını destekleyen herhangi bir hizmetten her istek aldığında çalıştırılacak basit bir işlevdir. Daha fazla bilgi için bkz. [Genel Web kancaları hakkında Azure işlevleri makalesi](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Dayanıklı işlevler düzenleme** – dayanıklı işlevler sunucusuz bir ortamda durum bilgisi olan işlevler yazmanızı sağlar. Uzantı durum, denetim noktaları ve yeniden başlatma işlemlerini sizin için yönetir. Daha fazla bilgi için bkz. [dayanıklı Işlevlerde](/azure/azure-functions/durable-functions-overview)Azure işlevleri Kılavuzu.

- **Görüntü Resizer** – bu işlev, bir kapsayıcıya bir blob eklendiğinde yeniden boyutlandırılmış görüntüler oluşturur. Şablon, tetikleyici için yol ve bağlantı dizesi, küçük bir görüntü çıkışı ve orta görüntü çıkışı alır.

- **SAS belirteci** – bu işlev, belirli bir Azure depolama kapsayıcısı ve BLOB adı IÇIN bir SAS belirteci oluşturur. Bu şablon, işlev adının yanı sıra bir yol ve bağlantı özelliği de alır. Path özelliği, depolama hesabınızda tetikleyicinin izleyecektir. Bağlantı hesabı, depolama hesabı Bağlantı dizenizi içeren uygulama ayarının adıdır. **Erişim haklarının** de ayarlanması gerekir. Yetkilendirme düzeyi, işlevin bir API anahtarı gerektirip gerektirmediğini ve hangi anahtarın kullanılacağını denetler; İşlev bir işlev anahtarı kullanır; Yönetici ana anahtarınızı kullanır. Daha fazla bilgi için bkz. [ C# SAS belirteçleri oluşturma örneği için Azure işlevi](https://github.com/Azure-Samples/functions-dotnet-sas-token/) .
