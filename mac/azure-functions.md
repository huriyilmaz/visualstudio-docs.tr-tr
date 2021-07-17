---
title: MacOs Azure İşlevleri da Azure İşlevleri
description: Mac için Visual Studio'Azure İşlevleri Mac için Visual Studio.
author: jmatthiesen
ms.author: jomatthi
ms.date: 04/02/2021
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: a91c40d0b6fe09aa88c0f3d72d21abde10621b5e
ms.sourcegitcommit: 879b11112c775a1c1dd9ebd4e59a3d0caec84220
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2021
ms.locfileid: "114397193"
---
# <a name="introduction-to-azure-functions"></a>Azure İşlevleri’ne Giriş

Azure İşlevleri, altyapıyı açıkça sağlamaya veya yönetmeye gerek kalmadan bulutta –– işlev –– kod parçacıkları oluşturmanın ve çalıştırmanın bir yoludur. Azure İşlevleri hakkında daha fazla bilgi için bkz. [Azure İşlevleri belgeleri](/azure/azure-functions/).

## <a name="requirements"></a>Gereksinimler

Azure İşlevi araçları Mac için Visual Studio **7.5 ve daha yeni sürümlerde** yer alır.

İşlevleri oluşturmak ve dağıtmak için bir Azure aboneliğine de ihtiyacınız vardır. Azure hesabınız yoksa ücretsiz olarak kaydolabilirsiniz ve 12 ay boyunca ücretsiz popüler hizmetler, 200 ABD doları ücretsiz kredi ve 25+her zaman ücretsiz hizmetler [https://azure.com/free](https://azure.com/free/dotnet) (>).

## <a name="creating-your-first-azure-functions-project"></a>İlk projenizi Azure İşlevleri oluşturma

1. Yeni Mac için Visual Studio **Dosya'>'ı seçin.**
2. Yeni Project iletişim kutusunda Cloud Azure İşlevleri Genel'in altında **>'a** **tıklayın:**

    ![Yeni Project seçeneğini gösteren yeni Azure İşlevleri iletişim kutusu](media/azure-functions-image1.png)

3. Kullanmak istediğiniz Azure İşlevleri şablonu seçin, işlev adını girin ve Sonraki'ye **tıklayın.**

    ![Şablon Project gösteren yeni Azure İşlevleri iletişim kutusu](media/azure-functions-image2.png)

    > [!TIP]
    > Paketlenmiş çalışma Azure İşlevleri ve şablonlar (CLI) mümkün olduğunca güncel tutulsa da kaçınılmaz olarak güncel değildir. Yeni bir İşlevler projesi oluştururken Mac için Visual Studio CLI güncelleştirmelerini kontrol eder ve aşağıdaki görüntüde gösterildiği gibi size bildirecek. Güncelleştirilmiş şablonları indirmek için düğmeye tıklamanız gerekir.
    > ![Güncelleştirmelerin kullanılabilir olduğunu Azure İşlevleri yeni proje iletişim kutusu](media/azure-functions-update.png)

    Seçtiğiniz işlev türüne bağlı olarak, sonraki sayfa aşağıdaki görüntüde gösterildiği gibi erişim hakları gibi ayrıntıları girmenizi istenir:

    ![Ek Project gösteren yeni uygulama iletişim kutusu](media/azure-functions-image3.png)

    Farklı türlerde şablon oluşturma ve Azure İşlevleri için gereken bağlama özellikleri hakkında daha fazla bilgi için Kullanılabilir işlev [şablonları bölümüne](#available-function-templates) bakın. Bu örnekte, erişim hakları anonim olarak ayarlanmış bir Http tetikleyicisi kullanıyoruz.

4. Parametreleri ayar verdiktan sonra projenin konumunu seçin ve Oluştur'a **tıklayın.**

Mac için Visual Studio varsayılan işlev .NET Standard bir proje oluşturur. Ayrıca, NuGet **AzureWebJobs** paketlerine başvurular ve paket üzerindeNewtonsoft.Js **içerir.**

![Mac için Visual Studio yepyeni bir Azure işlevini görüntüleyen bir düzenleyici](media/azure-functions-newproj.png)

Yeni proje aşağıdaki dosyaları içerir:

* **your-function-name.cs** – Bu sınıf, seçtiğiniz işlev için ortak kod içerir. İşlev adına sahip **bir FunctionName** özniteliğini ve işlevi neyin tetikleyeni belirten bir tetikleyici özniteliği içerir (örn. bir HTTP isteği). İşlev yöntemi hakkında daha fazla bilgi için Azure İşlevleri [C# geliştirici başvurusu makalesine](/azure/azure-functions/functions-dotnet-class-library) bakın.
* **host.js–** Bu dosya İşlevler ana bilgisayarı için genel yapılandırma seçeneklerini açıklar. Örnek bir dosya ve bu dosya için kullanılabilir ayarlar hakkında bilgi için,host.js[için başvuru Azure İşlevleri.](/azure/azure-functions/functions-host-json)
* **local.settings.js–** Bu dosya, işlevleri yerel olarak çalıştırmaya için tüm ayarları içerir. Bu ayarlar, Azure Functions Core Tools. Daha fazla bilgi için aşağıdaki [makalenin Yerel](/azure/azure-functions/functions-run-local#local-settings-file) ayarlar Azure Functions Core Tools bakın.

Mac için Visual Studio'de yeni bir Azure İşlevleri proje oluşturduğunuza göre, yerel makineden HTTP ile tetiklenen varsayılan işlevi test edin.

## <a name="testing-the-function-locally"></a>İşlevi yerel olarak test etme

Bu Azure İşlevleri destek Mac için Visual Studio yerel geliştirme bilgisayarınızda işlevinizi test ve hata ayıklama.

1. İşlevi yerel olarak test etmek için aşağıdaki **girişlerde** Çalıştır düğmesine Mac için Visual Studio:

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

    Azure İşlevi şablonlarının listesi Kullanılabilir işlev [şablonları bölümünde sağlanır.](#available-function-templates)

İşlev uygulaması projenize daha fazla işlev eklemek için yukarıdaki yordamı kullanabilirsiniz. Projede yer alan her işlevin farklı bir tetikleyicisi olabilir ancak bir işlevin tam olarak bir tetikleyicisi olması gerekir. Daha fazla bilgi için [bkz. Azure İşlevleri ve bağlama kavramları.](/azure/azure-functions/functions-triggers-bindings)

## <a name="publish-to-azure"></a>Azure’da Yayımlama

1. Proje adına sağ tıklayın ve Azure'da Yayımla' **>'** seçeneğini belirleyin: Azure'da Yayımla... >  ![ bağlam menüsü seçeneği vurgulanmış](media/azure-functions-image5.png)
2. Azure hesabınızla bağlantı Mac için Visual Studio kullanılabilir uygulama hizmetlerinin listesi görüntülenir. Henüz oturum açmadıysanız, oturum açmanız istenir.
3. **Azure App Service'da** yayımla iletişim kutusunda, var olan bir uygulama hizmetini seçerek veya Yeni'ye tıklayarak yeni bir uygulama **oluşturabilirsiniz.**
4. Yeni kaynak **grubu App Service** iletişim kutusunda ayarlarınızı girin: Yeni App Service iletişim kutusu; hizmet adı, abonelik, kaynak grubu ve  ![ hizmet planı ayarları alanlarını içerir.](media/azure-functions-image7.png)

    |Ayar  |Açıklama  |
    |---------|---------|
    |**App Service Adı**|Yeni işlev uygulamanızı tanımlayan genel olarak benzersiz bir ad.|
    |**Abonelik**|Kullanılacak Azure aboneliği.|
    |**[Kaynak Grubu](/azure/azure-resource-manager/resource-group-overview)**|İşlev uygulamanızın oluşturulacağı kaynak grubunun adı. Yeni **+** bir kaynak grubu oluşturmak için seçin.|
    |**[Hizmet Planı](/azure/azure-functions/functions-scale)**|Mevcut planı seçin veya özel bir plan oluşturun. Size yakın bir bölgede veya işlevlerinizin erişen diğer hizmetlere yakın bir konumda konum seçin.|

5. Depolama **hesabı** oluşturmak için Sonraki'ne tıklayın. İşlevler çalışma zamanı için bir Azure depolama hesabı gereklidir. Genel **amaçlı** depolama hesabı oluşturmak için Özel'e tıklayın veya var olan bir hesabı kullanın:

    ![Depolama App Service istemiyle yeni oturum açma iletişim kutusu.](media/azure-functions-image8.png)

6. **Oluştur**'a tıklayarak Azure'da bu ayarlarla bir işlev uygulaması ve ilgili kaynaklar oluşturun ve işlev proje kodunuzu dağıtın.

7. Yayımlama sırasında "Azure'da İşlev Sürümünü Güncelleştirme" konusunda sizi bilgilendiren bir iletişim kutusu istenebilirsiniz. **Evet'e tıklayın:**

    !["Azure uygulama ayarlarını yerel İşlevler sürümüyle eş olacak şekilde güncelleştirme" istemi Evet ve Hayır seçenekleriyle.](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>İşlev uygulaması ayarları

Uygulamanın açık olduğu local.settings.jstüm ayarların Azure'daki işlev uygulamasına da ekleniyor olması gerekir. Projeyi yayımlarken bu ayarlar otomatik olarak karşıya yüklenmez.

Uygulama ayarlarınıza erişmek için sayfasındaki Azure portal [https://ms.portal.azure.com/](https://ms.portal.azure.com/) gidin. İşlev **uygulamaları'nın** altında İşlev **Uygulamaları'ı** seçin ve işlev adını vurgulayın:

![azure işlevleri menüsü](media/azure-functions-image9.png)

Genel Bakış **sekmesinde Yapılandırılan** **özellikler'in** altında **Uygulama ayarları'ı seçin:**

![Azure işlevinin sekmesi üzerinde](media/azure-functions-image10.png)

Buradan, işlev uygulaması Ayarlar Uygulama Ayarları'nın ayarlarını oluşturabilir, burada yeni uygulama ayarları ekleyebilir veya mevcut ayarları değiştirebilirsiniz:

![uygulama ayarları alanı Azure portal](media/azure-functions-image11.png)

Ayarlamanız gereken önemli ayarlardan biri de `FUNCTIONS_EXTENSION_VERSION` ayarıdır. Bu değer Mac için Visual Studio, beta olarak ayar **gerekir.**

## <a name="available-function-templates"></a>Kullanılabilir işlev şablonları

- **GitHub:** Depolama depoları içinde oluşan olaylara GitHub yanıt verin. Daha fazla bilgi için Azure İşlevleri [makalesine GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - GitHub- Bu işlev, bir sorun veya çekme isteği GitHub bir web kancası aldığında ve bir açıklama ekleyene kadar çalıştır.
  - GitHub Web Kancası – Bu işlev bir web kancası aldığında GitHub olur.

- **HTTP:** Http isteği kullanarak kodunuzun yürütülmesini tetikler. Aşağıdaki HTTP tetikleyicileri için açık şablonlar vardır:
  - Http Tetikleyicisi
  - Http GET CRUD
  - Http POST CRUD
  - Parametrelerle Http Tetikleyicisi

- **Zamanlayıcı** : Temizlemeyi veya diğer toplu görevleri önceden tanımlanmış bir zaman çizelgesiyle yürütün. Bu şablon iki alan alır: Altı alanlı CRON ifadesi olan Ad ve zamanlama. Daha fazla bilgi için Time [Azure İşlevleri makalesine bakın](/azure/azure-functions/functions-create-scheduled-function)

- **Kuyruk Tetikleyicisi–** Bu işlev, Azure depolama kuyruğuna gelen iletilere yanıt Depolama işlevdir. İşlev adına ek olarak, bu şablon bir **Yol** (iletinin okunacak olduğu kuyruğun adı) ve depolama hesabı **Bağlantısı** (depolama hesabı bağlantı dizenizi içeren uygulama ayarının adı) alır. Daha fazla bilgi için Kuyruk Azure İşlevleri [makalesine Depolama.](/azure/azure-functions/functions-create-storage-queue-triggered-function)

- **Blob Tetikleyicisi** : Azure Depolama kapsayıcıya eklenen blobları işleme. Bu şablon, işlev adına ek olarak bir yol ve bağlantı özelliği de alır. path özelliği, tetikleyicinin izlemesi için depolama hesabı içindeki yoldur. Bağlantı hesabı, depolama hesabı bağlantı dizenizi içeren uygulama ayarının adıdır. Daha fazla bilgi için blob [Azure İşlevleri makalesine Depolama bakın.](/azure/azure-functions/functions-create-storage-blob-triggered-function)

- **Genel Web Kancası** – Bu, web kancalarını destekleyen herhangi bir hizmetten her istek aldığında çalıştıracak basit bir işlevdir. Daha fazla bilgi için genel [web kancaları Azure İşlevleri makalesine bakın.](/azure/azure-functions/functions-create-generic-webhook-triggered-function)

- **Dayanıklı işlevler düzenlemesi:** Dayanıklı İşlevler sunucusuz bir ortamda durum bilgisine sahip işlevler yazmanız için kullanılabilir. Uzantı sizin için durumu, denetim noktalarını ve yeniden başlatmaları yönetir. Daha fazla bilgi için Dayanıklı işlevler Azure İşlevleri [kılavuzlara bakın.](/azure/azure-functions/durable-functions-overview)

- **Resim Boyutlandırıcı:** Bu işlev kapsayıcıya her blob ekleniyorsa yeniden boyutlandırılır görüntüler oluşturur. Şablon tetikleyicinin yolunu ve bağlantı dizesini, küçük bir görüntü çıktısını ve orta ölçekli görüntü çıkışını alır.

- **SAS belirteci** – Bu işlev, kapsayıcı ve blob adı gibi azure Depolama sas belirteci üretir. Bu şablon, işlev adına ek olarak bir yol ve bağlantı özelliği de alır. path özelliği, tetikleyicinin izlemesi için depolama hesabı içindeki yoldur. Bağlantı hesabı, depolama hesabı bağlantı dizenizi içeren uygulama ayarının adıdır. Erişim **haklarının** da ayarlanmış olması gerekir. Yetkilendirme düzeyi, işlevin bir API anahtarı ve hangi anahtarın kullanılamayacaklarını kontrol eder; İşlev bir işlev anahtarı kullanır; Yönetici, hesap erişim anahtarınızı kullanır. Daha fazla bilgi için bkz. [SAS belirteçleri oluşturmak için C# Azure İşlevi](https://github.com/Azure-Samples/functions-dotnet-sas-token/) örneği.
