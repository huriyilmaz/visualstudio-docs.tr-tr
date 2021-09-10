---
title: Azure İşlevleri’ne Giriş
description: Azure işlevlerini Mac için Visual Studio.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: 63793548bd3ea1098cc1113724cd9a3b513adbf5
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962093"
---
# <a name="introduction-to-azure-functions"></a>Azure İşlevleri’ne Giriş

Azure işlevleri, altyapıyı açıkça sağlama veya yönetmeye gerek kalmadan bulutta olay odaklı kod parçacıkları oluşturmanın ve çalıştırmanın bir yoludur. Azure İşlevleri hakkında daha fazla bilgi için bkz. [Azure İşlevleri belgeleri](/azure/azure-functions/).

## <a name="requirements"></a>Gereksinimler

Azure İşlevi araçları Mac için Visual Studio **7.5'e dahildir.**

İşlevleri oluşturmak ve dağıtmak için, 'den ücretsiz olarak kullanılabilen bir Azure aboneliğine de ihtiyacınız [https://azure.com/free](https://azure.com/free) vardır.

## <a name="creating-your-first-azure-functions-project"></a>İlk projenizi Azure İşlevleri oluşturma

1. Yeni Mac için Visual Studio **Dosya'>'ı seçin.**
2. Yeni Project iletişim kutusunda, Cloud Azure İşlevleri Genel altında > **şablonu seçin ve** Ardından'ya **tıklayın:**

    ![Azure Project seçeneğini gösteren yeni uygulama iletişim kutusu](media/azure-functions-image1.png)

3. Kullanmak istediğiniz Azure İşlevleri şablon seçin, işlev adını girin ve Sonraki 'ye **tıklayın.**

    ![Azure Project şablonlarını gösteren yeni uygulama iletişim kutusu](media/azure-functions-image2.png)

    Seçtiğiniz işlev türüne bağlı olarak, sonraki sayfa aşağıdaki görüntüde gösterildiği gibi erişim hakları gibi ayrıntıları girmenizi istenir:

    ![Ek Project gösteren yeni uygulama iletişim kutusu](media/azure-functions-image3.png)

    Farklı türlerde şablon oluşturma ve Azure İşlevleri için gereken bağlama özellikleri hakkında daha fazla bilgi için Kullanılabilir işlev şablonları [bölümüne](#available-function-templates) bakın. Bu örnekte, erişim hakları anonim olarak ayarlanmış bir Http tetikleyicisi kullanıyoruz.

4. Parametreleri ayar verdiktan sonra projenin konumunu seçin ve Oluştur'a **tıklayın.**

Mac için Visual Studio, varsayılan işlev .NET Standard bir proje oluşturur. Ayrıca, NuGet **AzureWebJobs** paketlerine başvurular ve paket üzerindeNewtonsoft.Js **içerir.**

![Mac için Visual Studio yepyeni bir Azure işlevini görüntüleyen bir düzenleyici](media/azure-functions-newproj.png)

Yeni proje aşağıdaki dosyaları içerir:

* **your-function-name.cs** – Bu sınıf, seçtiğiniz işlev için ortak kod içerir. İşlev adına sahip **bir FunctionName** özniteliğini ve işlevi tetikleyen tetikleyici özniteliğini içerir (örn. bir HTTP isteği). İşlev yöntemi hakkında daha fazla bilgi için [C# Azure İşlevleri makalesine](/azure/azure-functions/functions-dotnet-class-library) bakın.
* **host.js–** Bu dosya İşlevler ana bilgisayarı için genel yapılandırma seçeneklerini açıklar. Örnek bir dosya ve bu dosya için kullanılabilir ayarlar hakkında bilgi için,host.js[için başvuru Azure İşlevleri.](/azure/azure-functions/functions-host-json)
* **local.settings.js–** Bu dosya, işlevleri yerel olarak çalıştırmaya için tüm ayarları içerir. Bu ayarlar, Azure Functions Core Tools. Daha fazla bilgi için [Azure Functions Core Tools](/azure/azure-functions/functions-run-local#local-settings-file) makalesinde yerel ayarlar dosyası.

Mac için Visual Studio'da yeni bir Azure İşlevleri proje oluşturduğunuza göre, yerel makineden HTTP ile tetiklenen varsayılan işlevi test edin.

## <a name="testing-the-function-locally"></a>İşlevi yerel olarak test etme

Bu Azure İşlevleri destek Mac için Visual Studio yerel geliştirme bilgisayarınızda işlevinizi test ve hata ayıklama.

1. İşlevini yerel olarak test etmek için aşağıdaki **girişlerde** Çalıştır düğmesine Mac için Visual Studio:

    ![Mac için Visual Studio'da hata ayıklamayı başlat düğmesi](media/azure-functions-run.png)

1. Proje çalıştırıldıktan sonra Azure İşlevinde yerel hata ayıklama başlatılır ve aşağıdaki görüntüde gösterildiği gibi yeni bir Terminal penceresi açılır:

    ![işlev çıktısını gösteren terminal penceresi](media/azure-functions-terminal.png)

    Çıkıştan URL'yi kopyalayın.

3. HTTP isteğinin URL’sini tarayıcınızın adres çubuğuna yapıştırın. URL'nin `?name=<yourname>` sonuna sorgu dizesini ekleyin ve isteği yürütün. Aşağıdaki görüntüde, tarayıcıda işlev tarafından döndürülen yerel GET isteğine verilen yanıt görüntülenir:

    ![tarayıcıda http isteği](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Projenize başka bir işlev ekleme

İşlev Şablonları, en sık kullanılan tetikleyicileri ve şablonları kullanarak yeni işlevleri hızlıca oluşturmanızı sağlar. Başka bir işlev türü oluşturmak için şunları yapın:

1. Yeni bir işlev eklemek için proje adına sağ tıklayın ve İşlev Ekle... > **Ekle'yi seçin:**

    ![yeni işlev eklemek için bağlam eylemi](media/azure-functions-addnew.png)

2. Yeni **Azure İşlevi iletişim** kutusunda, istediğiniz işlevi seçin:

    ![yeni azure işlevi iletişim kutusu](media/azure-functions-image4.png)

    Azure İşlevi şablonlarının listesi Kullanılabilir işlev [şablonları bölümünde](#available-function-templates) sağlanır.

İşlev uygulaması projenize daha fazla işlev eklemek için yukarıdaki yordamı kullanabilirsiniz. Projede yer alan her işlevin farklı bir tetikleyicisi olabilir, ancak bir işlevin tam olarak bir tetikleyicisi olması gerekir. Daha fazla bilgi için [bkz. Azure İşlevleri ve bağlama kavramları.](/azure/azure-functions/functions-triggers-bindings)

## <a name="publish-to-azure"></a>Azure’da Yayımlama

1. Proje adına sağ tıklayın ve Azure'da yayımla **>'ı** seçin: AF-httptrigger projesini seçerek Azure İşlevleri'den ekran görüntüsü ve bağlam menüsünde Azure'da Yayımla ve Yayımla komutları  ![ vurgulanmış.](media/azure-functions-image5.png)
2. Azure hesabınıza zaten bağlandıysanız Mac için Visual Studio uygulama hizmetlerinin listesi görüntülenir. Henüz oturum açmadıysanız, oturum açmanız istenir.
3. **Azure App Service'da** yayımla iletişim kutusunda, var olan bir uygulama hizmetini seçerek veya Yeni'ye tıklayarak yeni bir uygulama **oluşturabilirsiniz.**
4. Yeni **App Service** oluştur iletişim kutusuna ayarlarınızı girin: Azure'da yeni bir App Service oluşturmaya Azure İşlevleri gösteren Yeni App Service  ![ penceresinin ekran görüntüsü.](media/azure-functions-image7.png)

    |Ayar  |Açıklama  |
    |---------|---------|
    |**App Service Adı**|Yeni işlev uygulamanızı tanımlayan genel olarak benzersiz bir ad.|
    |**Abonelik**|Kullanılacak Azure aboneliği.|
    |**[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)**|İşlev uygulamanızın oluşturulacağı kaynak grubunun adı. Yeni **+** bir kaynak grubu oluşturmak için seçin.|
    |**[Hizmet Planı](/azure/azure-functions/functions-scale)**|Mevcut planı seçin veya özel bir plan oluşturun. Size yakın bir bölgede veya işlevlerinizin erişen diğer hizmetlere yakın bir konumda konum seçin.|

    > [!CAUTION]
    > Mac için Visual Studio'nin 7.6 sürümünde, Fiyatlandırma olarak Tüketim olarak ayarlanmış bir özel hizmet planı oluşturma girişiminde bulundurarak yayımlamanın sağlama hatasıyla başarısız olmasına neden olan **bir** **hata var.** Bu, bir sonraki hizmet yayında düzeltilecek.

5. Depolama **hesabı** oluşturmak için Sonraki'ne tıklayın. İşlevler çalışma zamanı için bir Azure depolama hesabı gereklidir. Genel **amaçlı** depolama hesabı oluşturmak için Özel'e tıklayın veya var olan bir hesabı kullanın:

    ![Depolama hesabı yapılandırma ekran Azure İşlevleri. Hesap için Depolama seçilir ve Hesap Adı ve Hesap türü doldurulur.](media/azure-functions-image8.png)

6. **Oluştur**'a tıklayarak Azure'da bu ayarlarla bir işlev uygulaması ve ilgili kaynaklar oluşturun ve işlev proje kodunuzu dağıtın.

7. Yayımlama sırasında "Azure'da İşlev Sürümünü Güncelleştirme" konusunda sizi bilgilendiren bir iletişim kutusu istenebilirsiniz. **Evet'e tıklayın:**

    !["Azure uygulama ayarlarını yerel İşlev sürümleriyle eş olacak şekilde güncelleştirme" isteminin Azure'da İşlev Sürümünü Güncelleştir iletişim kutusunun ekran görüntüsü.](media/azure-functions-image12.png)

> [!CAUTION]
> Mac için Visual Studio'nin 7.6 sürümünde " beta" olarak doğru ayarlanmazsa, işlevinizin çalışmay olduğu `FUNCTIONS_EXTENSION_VERSION` bir hata vardır. Bunu düzeltmek için İşlev uygulaması [ayarlarınıza gidin ve](#function-app-settings) `FUNCTIONS_EXTENSION_VERSION` "-1" yerine "beta" olarak ayarlayın.

## <a name="function-app-settings"></a>İşlev uygulaması ayarları

Uygulamanın üzerinde local.settings.jstüm ayarların Azure'daki işlev uygulamasına da ekleniyor olması gerekir. Projeyi yayımlarken bu ayarlar otomatik olarak karşıya yüklenmez.

Uygulama ayarlarınıza erişmek için sayfasındaki Azure portalına [https://ms.portal.azure.com/](https://ms.portal.azure.com/) gidin. İşlev **uygulamaları'nın** altında İşlev **Uygulamaları'ı** seçin ve işlev adını vurgulayın:

![azure işlevleri menüsü](media/azure-functions-image9.png)

Genel Bakış **sekmesinde Yapılandırılan** **özellikler'in** altında **Uygulama ayarları'ı seçin:**

![Azure işlevinin sekmesi üzerinde](media/azure-functions-image10.png)

Buradan işlev uygulaması için Uygulama Ayarlar'sini, burada yeni uygulama ayarları ekleyebilir veya mevcut ayarları değiştirebilirsiniz:

![Azure portalının uygulama ayarları alanı](media/azure-functions-image11.png)

Ayarlamanız gereken önemli ayarlardan biri de `FUNCTIONS_EXTENSION_VERSION` ayarıdır. Bu değer Mac için Visual Studio, beta olarak ayar **gerekir.**

## <a name="available-function-templates"></a>Kullanılabilir işlev şablonları

- **GitHub:** Depolama depoları içinde oluşan olaylara GitHub yanıt verin. Daha fazla bilgi için [GitHub Azure işlevleri makalesine](/azure/azure-functions/functions-create-github-webhook-triggered-function) bakın
  - GitHub yorumu – bu işlev, bir sorun veya çekme isteği için GitHub web kancasını aldığında çalıştırılır ve bir açıklama ekler.
  - GitHub web kancası – bu işlev, GitHub web kancası aldığında çalıştırılır.

- **Http** – bir http isteği kullanarak kodunuzun yürütülmesini tetikler. Aşağıdaki HTTP Tetikleyicileri için açık şablonlar vardır:
  - Http tetikleyicisi
  - HTTP GET CRUD
  - HTTP POST CRUD
  - Parametrelerle http tetikleyicisi

- **Zamanlayıcı** – önceden tanımlanmış bir zamanlamaya göre Temizleme veya diğer toplu işleri yürütün. Bu şablon iki alan alır: bir ad ve bir zamanlama, altı bir alan CRON ifadesi. Daha fazla bilgi için bkz. [Azure işlevleri makalesi saat](/azure/azure-functions/functions-create-scheduled-function)

- **kuyruk tetikleyicisi** – bu, Azure Depolama kuyruğuna geldikçe iletilere yanıt verecek bir işlevdir. İşlev adına ek olarak, bu şablon bir **yol** (iletinin okunacağı kuyruğun adı) ve depolama hesabı **bağlantısı** (depolama hesabı Bağlantı dizenizi içeren uygulama ayarının adı) alır. daha fazla bilgi için [sırasıyla Depolama Azure işlevleri makalesine](/azure/azure-functions/functions-create-storage-queue-triggered-function)bakın.

- **Blob tetikleyicisi** : bir kapsayıcıya eklendiğinde Azure Depolama bloblarını işleyin. Bu şablon, işlev adının yanı sıra bir yol ve bağlantı özelliği de alır. Path özelliği, depolama hesabınızda tetikleyicinin izleyecektir. Bağlantı hesabı, depolama hesabı Bağlantı dizenizi içeren uygulama ayarının adıdır. daha fazla bilgi için bkz. [Azure işlevleri blobu Depolama makalesi](/azure/azure-functions/functions-create-storage-blob-triggered-function).

- **Genel Web kancası** – bu, Web kancalarını destekleyen herhangi bir hizmetten her istek aldığında çalıştırılacak basit bir işlevdir. Daha fazla bilgi için bkz. [Genel Web kancaları hakkında Azure işlevleri makalesi](/azure/azure-functions/functions-create-generic-webhook-triggered-function).

- **Dayanıklı işlevler düzenleme** – dayanıklı işlevler sunucusuz bir ortamda durum bilgisi olan işlevler yazmanızı sağlar. Uzantı sizin için durumu, denetim noktalarını ve yeniden başlatmaları yönetir. Daha fazla bilgi için bkz. [dayanıklı Işlevlerde](/azure/azure-functions/durable-functions-overview)Azure işlevleri Kılavuzu.

- **Görüntü Resizer** – bu işlev, bir kapsayıcıya bir blob eklendiğinde yeniden boyutlandırılmış görüntüler oluşturur. Şablon, tetikleyici için yol ve bağlantı dizesi, küçük bir görüntü çıkışı ve orta görüntü çıkışı alır.

- **sas belirteci** – bu işlev, belirli bir Azure Depolama kapsayıcısı ve blob adı için bir SAS belirteci oluşturur. Bu şablon, işlev adının yanı sıra bir yol ve bağlantı özelliği de alır. Path özelliği, depolama hesabınızda tetikleyicinin izleyecektir. Bağlantı hesabı, depolama hesabı Bağlantı dizenizi içeren uygulama ayarının adıdır. **Erişim haklarının** de ayarlanması gerekir. Yetkilendirme düzeyi, işlevin bir API anahtarı gerektirip gerektirmediğini ve hangi anahtarın kullanılacağını denetler; İşlev bir işlev anahtarı kullanır; Yönetici, hesap erişim anahtarınızı kullanır. Daha fazla bilgi için bkz. [SAS belirteçleri oluşturma örneği Için C# Azure işlevi](https://github.com/Azure-Samples/functions-dotnet-sas-token/) .
