---
title: Azure İşlevleri’ne Giriş
description: Mac için Visual Studio'da Azure işlevlerini kullanma.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 85e66711c8bfe65319bf6af90ce0452478c4b7f8
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983472"
---
# <a name="introduction-to-azure-functions"></a>Azure İşlevleri’ne Giriş

Azure işlevleri, altyapıyı açıkça sağlamak veya yönetmek zorunda kalmadan bulutta olay odaklı kod parçacıkları (– işlevleri- oluşturmanın) bir yoludur. Azure İşlevleri hakkında daha fazla bilgi için [Azure İşlevleri belgelerine](/azure/azure-functions/)bakın.

## <a name="requirements"></a>Gereksinimler

Azure İşlevi araçları **Mac 7.5 için Visual Studio'ya**dahildir.

İşlevler oluşturmak ve dağıtmak için, [https://azure.com/free](https://azure.com/free)'den ücretsiz olarak kullanılabilen bir Azure aboneliğine de ihtiyacınız vardır.

## <a name="creating-your-first-azure-functions-project"></a>İlk Azure İşlevleri projenizi oluşturma

1. Mac için Visual Studio'da **Dosya > Yeni Çözüm'u**seçin.
2. Yeni Proje iletişim kutusundan Bulut > **Genel** altında Azure İşlevler şablonuna tıklayın ve **İleri'yi**tıklatın:

    ![Azure işlevleri seçeneğini gösteren Yeni Proje iletişim kutusu](media/azure-functions-image1.png)

3. Kullanmak istediğiniz ilk Azure İşlevler şablonunu seçin, işlev adınızı girin ve **İleri'yi**tıklatın.

    ![Azure işlevleri şablonlarını gösteren yeni Proje iletişim kutusu](media/azure-functions-image2.png)

    Seçtiğiniz işlevin türüne bağlı olarak, bir sonraki sayfa aşağıdaki resimde gösterildiği gibi erişim hakları gibi ayrıntıları girmenizi ister:

    ![Ek seçeneği gösteren Yeni Proje iletişim kutusu](media/azure-functions-image3.png)

    Farklı Azure İşlevleri şablonları türleri ve her şablonu yapılandırmak için gereken bağlama özellikleri hakkında daha fazla bilgi için [Kullanılabilir işlev şablonları](#available-function-templates) bölümüne bakın. Bu örnekte, erişim hakları anonim olarak ayarlanmış bir Http tetikleyicisi kullanıyoruz.

4. Parametreleri ayarladıktan sonra projenin konumunu seçin ve **Oluştur'u**tıklatın.

Mac için Visual Studio, varsayılan işlevi içeren bir .NET Standard projesi oluşturur. Ayrıca, Çeşitli **AzureWebJobs** paketlerine ve **Newtonsoft.Json** paketine yapılan NuGet referanslarını da içerir.

![Şablondan yepyeni bir azure işlevi görüntüleyen Mac düzenleyicisi için Visual Studio](media/azure-functions-newproj.png)

Yeni proje aşağıdaki dosyaları içerir:

* **your-function-name.cs** – Bu sınıf seçtiğiniz işlev için ortak kod içerir. İşlev adı ile bir **FunctionName** özniteliği ve işlevi neyin tetiklediğini belirten bir tetikleyici özniteliği içerir (örneğin. bir HTTP isteği). İşlev yöntemi hakkında daha fazla bilgi için [Azure İşlevleri C# geliştirici başvuru](/azure/azure-functions/functions-dotnet-class-library) makalesine bakın.
* **host.json** – Bu dosya, İşlevler ana bilgisayar için genel yapılandırma seçeneklerini açıklar. Örnek bir dosya ve bu dosyanın kullanılabilir ayarlarıyla ilgili bilgiler için [Azure İşlevleri için ana bilgisayar.json başvurusuna](/azure/azure-functions/functions-host-json)bakın.
* **local.settings.json** – Bu dosya, yerel olarak çalışan işlevlerin tüm ayarlarını içerir. Bu ayarlar Azure İşlevler Temel Araçları tarafından kullanılır. Daha fazla bilgi için Azure İşlevler Temel Araçları makalesinde [Yerel ayarlar dosyasına](/azure/azure-functions/functions-run-local#local-settings-file) bakın.

Mac için Visual Studio'da yeni bir Azure İşlevleri projesi oluşturduğunuza göre, yerel makinenizden varsayılan HTTP tetiklenen işlevi test edebilirsiniz.

## <a name="testing-the-function-locally"></a>İşlevin yerel olarak test edilmesi

Mac için Visual Studio'daki Azure İşlevler desteği ile yerel geliştirme bilgisayarınızda işlevinizi sınayabilir ve hata ayıklayabilirsiniz.

1. İşlevinizi yerel olarak test etmek için, Mac için Visual Studio'da **Çalıştır** düğmesine basın:

    ![mac için visual studio'da hata ayıklama düğmesini başlatın](media/azure-functions-run.png)

1. Projeyi çalıştırmak Azure İşlevi'nde yerel hata ayıklamaya başlar ve aşağıdaki resimde gösterildiği gibi yeni bir Terminal penceresi açar:

    ![fonksiyon çıktısını gösteren terminal penceresi](media/azure-functions-terminal.png)

    Çıkıştan URL'yi kopyalayın.

3. HTTP isteğinin URL’sini tarayıcınızın adres çubuğuna yapıştırın. Sorgu dizesini `?name=<yourname>` URL'nin sonuna ekleyin ve isteği çalıştırın. Aşağıdaki resim, tarayıcıdaki işlevi tarafından döndürülen yerel GET isteğine verilen yanıtı gösterir:

    ![tarayıcıda http istek](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Projenize başka bir işlev ekleme

İşlev Şablonları, en sık kullanılan tetikleyicileri ve şablonları kullanarak yeni işlevleri hızlıca oluşturmanızı sağlar. Başka bir işlev türü oluşturmak için aşağıdakileri yapın:

1. Yeni bir işlev eklemek için proje adına sağ tıklayın ve **İşlev Ekle >'yi seçin...**:

    ![yeni işlev eklemek için bağlam eylemi](media/azure-functions-addnew.png)

2. Yeni **Azure İşlevi** iletişim kutusundan, gereksinim duyduğunuz işlevi seçin:

    ![yeni azure işlev iletişim kutusu](media/azure-functions-image4.png)

    [Kullanılabilir işlev şablonları](#available-function-templates) bölümünde Azure İşlevi şablonlarının listesi sağlanır.

İşlev uygulaması projenize daha fazla işlev eklemek için yukarıdaki yordamı kullanabilirsiniz. Projedeki her işlevin farklı bir tetikleyicisi olabilir, ancak bir işlevin tam olarak bir tetikleyicisi olmalıdır. Daha fazla bilgi için Azure [İşlevleri tetikleyicileri ve bağlama kavramlarını](/azure/azure-functions/functions-triggers-bindings)görün.

## <a name="publish-to-azure"></a>Azure’da Yayımlama

1. Proje adına sağ tıklayın ve **Azure'> Yayımla**seçeneğini seçin : ![Azure menüsüne yayımla seçeneği](media/azure-functions-image5.png)
2. Azure hesabınızı Mac için Visual Studio'ya zaten bağladıysanız, kullanılabilir uygulama hizmetlerinin listesi görüntülenir. Oturum açmadıysanız, bunu yapmanız istenir.
3. Yayımla'dan Azure Uygulama Hizmeti iletişim **kutusuna,** varolan bir uygulama hizmetini seçebilir veya **Yeni'yi**tıklatarak yeni bir uygulama oluşturabilirsiniz.
4. Yeni **Uygulama Hizmeti Oluştur** iletişim kutusunda ayarlarınızı girin: ![Azure menüsüne yayımla seçeneği](media/azure-functions-image7.png)

    |Ayar  |Açıklama  |
    |---------|---------|
    |**Uygulama Hizmet Adı**|Yeni işlev uygulamanızı tanımlayan, genel olarak benzersiz bir ad.|
    |**Abonelik**|Kullanılacak Azure aboneliği.|
    |**[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)**|İşlev uygulamanızın oluşturulacağı kaynak grubunun adı. Yeni **+** bir kaynak grubu oluşturmayı seçin.|
    |**[Hizmet Planı](/azure/azure-functions/functions-scale)**|Varolan bir plan seçin veya özel bir plan oluşturun. Yakınınızdaki bir bölgede veya işlevlerinizin erişebileceği diğer hizmetlere yakın bir konumda bir Konum seçin.|

    > [!CAUTION]
    > Visual Studio for Mac'in 7.6 sürümünde, **Tüketim**için **belirlenen Fiyatlandırma** ile özel bir hizmet planı oluşturmaya çalışırsanız, yayımlamanın bir sağlama hatasıyla başarısız olmasına neden olacak bir hata vardır. Bu, bir sonraki hizmet sürümünde düzeltilir.

5. Depolama hesabı oluşturmak için **İleri'yi** tıklatın. İşlevler çalışma zamanı için bir Azure depolama hesabı gereklidir. Genel amaçlı bir depolama hesabı oluşturmak veya varolan bir depoyu kullanmak için **Özel'i** tıklatın:

    ![Azure menüsüne yayımlama seçeneği](media/azure-functions-image8.png)

6. **Oluştur**'a tıklayarak Azure'da bu ayarlarla bir işlev uygulaması ve ilgili kaynaklar oluşturun ve işlev proje kodunuzu dağıtın.

7. Yayımlama sırasında "Azure'da İşlevler Sürümünü Güncelleştir" konusunda sizi bilgilendiren bir iletişim kutusu istenebilir. **Evet'i**tıklatın :

    ![Azure menüsüne yayımlama seçeneği](media/azure-functions-image12.png)

> [!CAUTION]
> Visual Studio for Mac'in `FUNCTIONS_EXTENSION_VERSION` 7.6 sürümünde, işlevinizin çalışmayabileceği anlamına gelen "beta" olarak doğru şekilde ayarlanmayan bir hata vardır. Bunu düzeltmek için [Fonksiyon uygulama ayarlarınıza](#function-app-settings) gidin ve "-1"den "beta"ya ayarlayın. `FUNCTIONS_EXTENSION_VERSION`

## <a name="function-app-settings"></a>İşlev uygulaması ayarları

local.settings.json'a eklediğiniz tüm ayarlar Azure'daki işlev uygulamasına da eklenmelidir. Projeyi yayımladığınızda bu ayarlar otomatik olarak yüklenmez.

Uygulama ayarlarınıza erişmek için [https://ms.portal.azure.com/](https://ms.portal.azure.com/)azure portalına gidin. **Fonksiyon uygulamaları** **altında, İşlev Uygulamaları'nı** seçin ve işlev adınızı vurgulayın:

![azure fonksiyonlar menüsü](media/azure-functions-image9.png)

Genel **Bakış** sekmesinden **Yapılandırılan özellikler**altında **Uygulama ayarlarını** seçin:

![Azure işlevinin sekmesi üzerinde](media/azure-functions-image10.png)

Buradan, yeni uygulama ayarları ekleyebileceğiniz veya varolanları değiştirebileceğiniz işlev uygulaması için Uygulama Ayarları ayarlayabilirsiniz:

![azure portalUygulama ayarları alanı](media/azure-functions-image11.png)

Ayarlamanız gereken önemli bir `FUNCTIONS_EXTENSION_VERSION`ayar. Mac için Visual Studio'dan yayımlarken, bu değer **beta**olarak ayarlanmalıdır.

## <a name="available-function-templates"></a>Kullanılabilir işlev şablonları

- **GitHub Tetikleyici** – GitHub depolarınızda meydana gelen olaylara yanıt verin. Daha fazla bilgi için [GitHub'daki Azure İşlevler makalesine](/azure/azure-functions/functions-create-github-webhook-triggered-function) bakın
  - GitHub yorumcusu – Bu işlev, bir sorun veya çekme isteği için Bir GitHub webhook aldığında ve bir yorum eklendiğinde çalıştırılacaktır.
  - GitHub WebHook – Bu işlev, Bir GitHub webhook aldığında çalıştırılacaktır.

- **HTTP** – Bir HTTP isteği kullanarak kodunuzu yürütmeyi tetikler. Aşağıdaki HTTP tetikleyicileri için açık şablonlar vardır:
  - Http Tetik
  - Http GET CRUD
  - Http POST CRUD
  - Parametreleri ile Http Tetik

- **Zamanlayıcı** – Önceden tanımlanmış bir zamanlamada temizleme veya diğer toplu iş görevlerini yürütün. Bu şablon iki alan alır: bir Ad ve altı alan CRON ifadesi olan bir zamanlama. Daha fazla bilgi [için, Zaman hakkındaki Azure işlevleri makalesine](/azure/azure-functions/functions-create-scheduled-function) bakın

- **Sıra Tetikleyicisi** – Bu, iletilerin Azure Depolama kuyruğuna geldiklerinde yanıt verecek bir işlevdir. Bu şablon, işlev adına ek olarak bir **Yol** (iletinin okunacağı sıranın adı) ve depolama hesabı **Bağlantısı** (depolama hesabı bağlantı dizenizi içeren uygulama ayarı adı) alır. Daha fazla bilgi için [Sıra Depolama'daki Azure işlevleri makalesine](/azure/azure-functions/functions-create-storage-queue-triggered-function)bakın.

- **Blob Trigger** – Bir kapsayıcıya eklendiğinde Azure Depolama lekelerini işleme. İşlev adına ek olarak, bu şablon da bir yol ve bağlantı özelliği alır. Yol özelliği, depolama hesabınızdaki tetikleyicinin izleyeceği yoldur. Bağlantı hesabı, depolama hesabı bağlantı dizenizi içeren uygulama ayarının adıdır. Daha fazla bilgi için [Azure işlevleri Blob Depolama makalesine](/azure/azure-functions/functions-create-storage-blob-triggered-function)bakın.

- **Genel WebHook** - Bu webhooks destekleyen herhangi bir hizmetten bir istek aldığında çalışacak basit bir işlevdir. Daha fazla bilgi [için, genel webhooks'taki Azure işlevleri makalesine](/azure/azure-functions/functions-create-generic-webhook-triggered-function)bakın.

- **Dayanıklı işlevler düzenleme** – Dayanıklı Fonksiyonlar, sunucusuz bir ortamda durumlu işlevleri yazmanızı sağlar. Uzantı sizin için durumu, denetim noktalarını ve yeniden başlatmaları yönetir. Daha fazla bilgi [için, Dayanıklı işlevler](/azure/azure-functions/durable-functions-overview)hakkındaki Azure işlevleri kılavuzlarına bakın.

- **Görüntü Resizer** – Bu işlev, bir kapsayıcıya bir leke eklendiğinde yeniden boyutlandırılmış görüntüler oluşturur. Şablon, tetikleyici, küçük bir görüntü çıkışı ve orta görüntü çıkışı için yol ve bağlantı dizesini alır.

- **SAS belirteci** – Bu işlev, belirli bir Azure Depolama kapsayıcısı ve blob adı için bir SAS belirteci oluşturur. İşlev adına ek olarak, bu şablon da bir yol ve bağlantı özelliği alır. Yol özelliği, depolama hesabınızdaki tetikleyicinin izleyeceği yoldur. Bağlantı hesabı, depolama hesabı bağlantı dizenizi içeren uygulama ayarının adıdır. **Erişim haklarının** da ayarlanabilmesi gerekir. Yetkilendirme düzeyi, işlevin bir API anahtarı gerektireyip gerektirmediğini ve hangi anahtarın kullanılacağını denetler; İşlev bir işlev anahtarı kullanır; Yönetici ana anahtarınızı kullanır. Daha fazla bilgi [için, SAS belirteçleri örneği oluşturmak için C# Azure İşlevi'ne](https://github.com/Azure-Samples/functions-dotnet-sas-token/) bakın.
