---
title: MacOs 'ta Azure Işlevleri
description: Mac için Visual Studio 'de Azure işlevleri 'ni kullanmaya başlama.
author: jmatthiesen
ms.author: jomatthi
ms.date: 04/02/2021
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.topic: how-to
ms.openlocfilehash: a91c40d0b6fe09aa88c0f3d72d21abde10621b5e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725995"
---
# <a name="introduction-to-azure-functions"></a>Azure İşlevleri’ne Giriş

Azure Işlevleri, altyapıyı açıkça sağlamak veya yönetmek zorunda kalmadan, kod – – işlevleri – –, bulutta olay odaklı kod parçacıkları oluşturup çalıştırmanın bir yoludur. Azure İşlevleri hakkında daha fazla bilgi için bkz. [Azure İşlevleri belgeleri](/azure/azure-functions/).

## <a name="requirements"></a>Gereksinimler

Azure işlev araçları, **Mac için Visual Studio 7,5** ve daha yeni bir sürüme dahildir.

İşlev oluşturup dağıtmak için bir Azure aboneliğine de ihtiyacınız vardır. Azure hesabınız yoksa bugün ücretsiz olarak kaydolabilir ve 12 aylık ücretsiz hizmetler, $200 ücretsiz kredi ve 25 + her zaman ücretsiz hizmetler > alabilirsiniz [https://azure.com/free](https://azure.com/free/dotnet) .

## <a name="creating-your-first-azure-functions-project"></a>İlk Azure Işlevleri projenizi oluşturma

1. Mac için Visual Studio **dosya > yeni çözüm**' ı seçin.
2. yeni Project iletişim kutusunda **Cloud > genel** ' in altındaki Azure işlevleri şablonunu seçin ve **ileri**' ye tıklayın:

    ![Azure işlevleri seçeneğini gösteren yeni Project iletişim kutusu](media/azure-functions-image1.png)

3. Kullanmak istediğiniz ilk Azure Işlevleri şablonunu seçin, işlevinizin adını girin ve **İleri**' ye tıklayın.

    ![Azure işlevleri şablonlarını gösteren yeni Project iletişim kutusu](media/azure-functions-image2.png)

    > [!TIP]
    > Paketlenmiş Azure Işlevleri çalışma zamanı ve şablonları (CLı) mümkün olduğunca güncel tutulurken, kaçınılmaz olarak güncelliğini yitirmiş. yeni bir işlevler projesi oluştururken, Mac için Visual Studio clı güncelleştirmelerini denetler ve aşağıdaki görüntüde gösterildiği gibi size bildirir. Güncelleştirilmiş şablonları indirmek için düğmeye tıklamanız yeterlidir.
    > ![Azure Işlevleri güncelleştirmelerini gösteren yeni proje iletişim kutusu kullanılabilir](media/azure-functions-update.png)

    Seçtiğiniz işlevin türüne bağlı olarak, sonraki sayfada aşağıdaki görüntüde gösterildiği gibi erişim hakları gibi ayrıntılar girmeniz istenir:

    ![ek seçeneği gösteren yeni Project iletişim kutusu](media/azure-functions-image3.png)

    Farklı türlerde Azure Işlevleri şablonları ve her bir şablonu yapılandırmak için gereken bağlama özellikleri hakkında daha fazla bilgi için, [kullanılabilir işlev şablonları](#available-function-templates) bölümüne bakın. Bu örnekte, erişim hakları anonim olarak ayarlanmış bir http tetikleyicisi kullanıyoruz.

4. Parametreleri ayarladıktan sonra, projenin konumunu seçin ve **Oluştur**' a tıklayın.

Mac için Visual Studio, varsayılan bir işlevle dahil .NET Standard bir proje oluşturur. ayrıca, çeşitli **AzureWebJobs** paketlerine ek olarak, **newtonsoft. Json** paketini de NuGet başvuruları içerir.

![şablondan yeni bir azure işlevi görüntüleyen Mac için Visual Studio düzenleyicisi](media/azure-functions-newproj.png)

Yeni proje aşağıdaki dosyaları içerir:

* **işleviniz-Name. cs** – Bu sınıf seçtiğiniz işlevin ortak kodunu içerir. İşlev adına sahip bir **fonksiyonadı** özniteliği ve işlevi neyin tetikleyeceğini belirten bir tetikleyici özniteliği içerir (örn. bir HTTP isteği). İşlev yöntemi hakkında daha fazla bilgi için bkz. [Azure Işlevleri C# Geliştirici başvurusu](/azure/azure-functions/functions-dotnet-class-library) makalesi.
* **Host. JSON** – bu dosya, işlevler ana bilgisayarı için genel yapılandırma seçeneklerini açıklar. Örnek bir dosya ve bu dosya için kullanılabilir ayarlar hakkında bilgi için bkz. [Azure işlevleri için Host. JSON başvurusu](/azure/azure-functions/functions-host-json).
* **Local. Settings. JSON** – bu dosya, işlevleri yerel olarak çalıştırmaya yönelik tüm ayarları içerir. Bu ayarlar Azure Functions Core Tools tarafından kullanılır. Daha fazla bilgi için Azure Functions Core Tools makalesindeki [yerel ayarlar dosyası](/azure/azure-functions/functions-run-local#local-settings-file) ' na bakın.

artık Mac için Visual Studio yeni bir Azure işlevleri projesi oluşturduğunuza göre, yerel makinenizden varsayılan HTTP ile tetiklenen işlevi test edebilirsiniz.

## <a name="testing-the-function-locally"></a>İşlevi yerel olarak test etme

Mac için Visual Studio Azure işlevleri desteğiyle, işlevinizi yerel geliştirme bilgisayarınızda test edebilir ve hatalarını ayıklayabilirsiniz.

1. işlevinizi yerel olarak test etmek için Mac için Visual Studio içindeki **çalıştır** düğmesine basın:

    ![Mac için Visual Studio 'da hata ayıklamayı Başlat düğmesi](media/azure-functions-run.png)

1. Projeyi çalıştırmak, Azure Işlevinde yerel hata ayıklamayı başlatır ve aşağıdaki görüntüde gösterildiği gibi yeni bir Terminal penceresi açar:

    ![işlev çıkışını gösteren Terminal penceresi](media/azure-functions-terminal.png)

    Çıktıdan URL 'YI kopyalayın.

3. HTTP isteğinin URL’sini tarayıcınızın adres çubuğuna yapıştırın. Sorgu dizesini `?name=<yourname>` URL 'nin sonuna ekleyin ve isteği yürütün. Aşağıdaki görüntüde, bu işlevin döndürdüğü yerel GET isteğine tarayıcıda yapılan yanıt gösterilmektedir:

    ![tarayıcıda http isteği](media/azure-functions-httpreq.png)

## <a name="adding-another-function-to-your-project"></a>Projenize başka bir işlev ekleme

İşlev Şablonları, en sık kullanılan tetikleyicileri ve şablonları kullanarak yeni işlevleri hızlıca oluşturmanızı sağlar. Başka bir işlev türü oluşturmak için aşağıdakileri yapın:

1. Yeni bir işlev eklemek için proje adına sağ tıklayın ve **> Ekle Işlev Ekle..**. öğesini seçin:

    ![Yeni işlev ekleme için bağlam eylemi](media/azure-functions-addnew.png)

2. **Yeni Azure işlevi** iletişim kutusunda, ihtiyacınız olan işlevi seçin:

    ![yeni Azure işlevi iletişim kutusu](media/azure-functions-image4.png)

    [Kullanılabilir işlev şablonları](#available-function-templates) bölümünde Azure işlev şablonlarının bir listesi verilmiştir.

İşlev uygulaması projenize daha fazla işlev eklemek için yukarıdaki yordamı kullanabilirsiniz. Projedeki her bir işlev farklı bir tetikleyicisine sahip olabilir, ancak bir işlevin tam olarak bir tetikleyicisi olmalıdır. Daha fazla bilgi için bkz. [Azure işlevleri Tetikleyicileri ve bağlamaları kavramları](/azure/azure-functions/functions-triggers-bindings).

## <a name="publish-to-azure"></a>Azure’da Yayımlama

1. Proje adına sağ tıklayın ve **yayımla > Azure 'Da Yayımla**' yı seçin:  ![ > Yayımla Ile bağlam menüsü Azure 'da Yayımla... seçenek vurgulandı](media/azure-functions-image5.png)
2. Azure hesabınızı Mac için Visual Studio için zaten bağladıysanız, kullanılabilir uygulama hizmetlerinin bir listesi görüntülenir. Oturum açmadıysanız bunu yapmanız istenir.
3. **Azure App Service Yayımla** iletişim kutusunda, var olan bir uygulama hizmetini seçebilir veya **Yeni**' ye tıklayarak yeni bir tane oluşturabilirsiniz.
4. **Yeni App Service oluştur** iletişim kutusunda, ![ hizmet adı, abonelik, kaynak grubu ve hizmet planı ayarları alanlarıyla birlikte ayarlar: yeni App Service iletişim kutusunu girin.](media/azure-functions-image7.png)

    |Ayar  |Açıklama  |
    |---------|---------|
    |**App Service Adı**|Yeni işlev uygulamanızı tanımlayan genel olarak benzersiz bir ad.|
    |**Abonelik**|Kullanılacak Azure aboneliği.|
    |**[Kaynak grubu](/azure/azure-resource-manager/resource-group-overview)**|İşlev uygulamanızın oluşturulacağı kaynak grubunun adı. **+** Yeni bir kaynak grubu oluşturmayı seçin.|
    |**[Hizmet planı](/azure/azure-functions/functions-scale)**|Mevcut bir planı seçin veya özel bir plan oluşturun. Size yakın bir bölgede veya işlevlerinizin erişebileceği diğer hizmetlere yakın bir konum seçin.|

5. Bir depolama hesabı oluşturmak için **İleri** ' ye tıklayın. İşlevler çalışma zamanı için bir Azure depolama hesabı gereklidir. Genel amaçlı bir depolama hesabı oluşturmak için **özel** ' e tıklayın veya var olan birini kullanın:

    ![Depolama hesabı adı istemiyle yeni App Service iletişim kutusu.](media/azure-functions-image8.png)

6. **Oluştur**'a tıklayarak Azure'da bu ayarlarla bir işlev uygulaması ve ilgili kaynaklar oluşturun ve işlev proje kodunuzu dağıtın.

7. Yayımlama sırasında bir iletişim kutusu istenebilir, "Azure 'da Işlevleri güncelleştirme" konusunda sizi bilgilendiren bir iletişim kutusu görüntülenebilir. **Evet**' e tıklayın:

    !["Azure uygulama ayarlarını yerel Işlevlerin sürümüyle eşleşecek şekilde güncelleştirin mi?" uyarısını yazın. Evet ve seçenek yoktur.](media/azure-functions-image12.png)

## <a name="function-app-settings"></a>İşlev uygulaması ayarları

Yerel. Settings. JSON içine eklediğiniz tüm ayarlar ayrıca Azure 'daki işlev uygulamasına eklenmelidir. Projeyi yayımladığınızda bu ayarlar otomatik olarak karşıya yüklenemez.

Uygulama ayarlarınıza erişmek için Azure portal gidin [https://ms.portal.azure.com/](https://ms.portal.azure.com/) . **Işlevler uygulamalar**' ın altında **işlev uygulamaları** ' nı seçin ve işlevinizin adını vurgulayın:

![Azure işlevleri menüsü](media/azure-functions-image9.png)

**Genel bakış** sekmesinden **yapılandırılmış özellikler** altında **uygulama ayarları** ' nı seçin:

![Azure işlevinin Over sekmesi](media/azure-functions-image10.png)

buradan, yeni uygulama ayarları ekleyebileceğiniz veya var olanları değiştirebileceğiniz işlev uygulaması için uygulama Ayarlar ayarlayabilirsiniz:

![Azure portal uygulama ayarları alanı](media/azure-functions-image11.png)

Ayarlamanız gerekebilmeniz gereken önemli bir ayardır `FUNCTIONS_EXTENSION_VERSION` . Mac için Visual Studio yayımlarken, bu değer **beta** olarak ayarlanmalıdır.

## <a name="available-function-templates"></a>Kullanılabilir işlev şablonları

- **GitHub Tetikleyicisi:** Depolama depolarınız içinde GitHub yanıt verin. Daha fazla bilgi için Azure İşlevleri [makalesine GitHub](/azure/azure-functions/functions-create-github-webhook-triggered-function)
  - GitHub- Bu işlev, bir sorun veya çekme isteği için GitHub bir web kancası aldığında ve bir açıklama ekleyene kadar çalıştır.
  - GitHub Web Kancası – Bu işlev bir web kancası aldığında GitHub olur.

- **HTTP:** Http isteği kullanarak kodunuzun yürütülmesini tetikler. Aşağıdaki HTTP tetikleyicileri için açık şablonlar vardır:
  - Http Tetikleyicisi
  - Http GET CRUD
  - Http POST CRUD
  - Parametrelerle Http Tetikleyicisi

- **Zamanlayıcı** : Temizlemeyi veya diğer toplu görevleri önceden tanımlanmış bir zaman çizelgesiyle yürütün. Bu şablon iki alan alır: Altı alanlı CRON ifadesi olan Ad ve zamanlama. Daha fazla bilgi için Time [Azure İşlevleri makalesine bakın](/azure/azure-functions/functions-create-scheduled-function)

- **Kuyruk Tetikleyicisi:** Bu işlev, Azure depolama kuyruğuna gelen iletilere yanıt Depolama olur. İşlev adına ek olarak, bu şablon bir **Yol** (iletinin okunacak olduğu kuyruğun adı) ve depolama hesabı **Bağlantısı** (depolama hesabı bağlantı dizenizi içeren uygulama ayarının adı) alır. Daha fazla bilgi için Kuyruk Azure İşlevleri [makalesine Depolama.](/azure/azure-functions/functions-create-storage-queue-triggered-function)

- **Blob Tetikleyicisi** : Azure Depolama blobları kapsayıcıya eklendiğinde işler. Bu şablon, işlev adına ek olarak bir yol ve bağlantı özelliği de alır. path özelliği, tetikleyicinin izlemesi için depolama hesabı içindeki yoldur. Bağlantı hesabı, depolama hesabı bağlantı dizenizi içeren uygulama ayarının adıdır. Daha fazla bilgi için blob [Azure İşlevleri makalesine Depolama bakın.](/azure/azure-functions/functions-create-storage-blob-triggered-function)

- **Genel Web Kancası** – Bu, web kancalarını destekleyen herhangi bir hizmetten her istek aldığında çalıştıracak basit bir işlevdir. Daha fazla bilgi için genel web kancaları Azure İşlevleri [makalesine bakın.](/azure/azure-functions/functions-create-generic-webhook-triggered-function)

- **Dayanıklı işlevler düzenlemesi:** Dayanıklı İşlevler sunucusuz bir ortamda durum bilgisine sahip işlevler yazmanız için kullanılır. Uzantı sizin için durumu, denetim noktalarını ve yeniden başlatmaları yönetir. Daha fazla bilgi için Dayanıklı Azure İşlevleri [kılavuzlara bakın.](/azure/azure-functions/durable-functions-overview)

- **Resim Boyutlandırıcı:** Bu işlev, kapsayıcıya her blob ekleniyorsa yeniden boyutlandırılır görüntüler oluşturur. Şablon tetikleyicinin yolunu ve bağlantı dizesini, küçük bir görüntü çıktısını ve orta ölçekli görüntü çıkışını alır.

- **SAS belirteci** – Bu işlev, kapsayıcı ve blob adı gibi azure Depolama sas belirteci üretir. Bu şablon, işlev adına ek olarak bir yol ve bağlantı özelliği de alır. path özelliği, tetikleyicinin izlemesi için depolama hesabı içindeki yoldur. Bağlantı hesabı, depolama hesabı bağlantı dizenizi içeren uygulama ayarının adıdır. Erişim **haklarının** da ayarlanmış olması gerekir. Yetkilendirme düzeyi, işlevin bir API anahtarı ve hangi anahtarın kullanılamayacaklarını kontrol eder; İşlev bir işlev anahtarı kullanır; Yönetici, hesap erişim anahtarınızı kullanır. Daha fazla bilgi için bkz. [SAS belirteçleri oluşturmak için C# Azure İşlevi](https://github.com/Azure-Samples/functions-dotnet-sas-token/) örneği.
