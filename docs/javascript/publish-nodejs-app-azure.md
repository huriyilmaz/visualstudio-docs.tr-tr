---
title: Linux App Service’e bir Node.js uygulaması yayımlama
description: Azure'da Node.js linux Visual Studio uygulamaları App Service yayımabilirsiniz
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 397374c1df912707d308acdf5df9fcdbc9d5221b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625791"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Azure'Node.js uygulama yayımlama (Linux App Service)

Bu öğretici, basit bir uygulama oluşturma ve Azure'Node.js yayımlama görevi boyunca size yol gösterir.

Azure'Node.js uygulama yayımlarken çeşitli seçenekler vardır. Bunlar arasında Azure App Service işletim sistemi çalıştıran bir VM, Kubernetes ile yönetim için Azure Container Service (AKS), Docker kullanan bir Container Instance ve daha fazlası yer almaktadır. Bu seçeneklerin her biri hakkında daha fazla bilgi için bkz. [İşlem.](https://azure.microsoft.com/product-categories/compute/)

Bu öğreticide, uygulamayı Linux'a [dağıtın App Service.](/azure/app-service/containers/app-service-linux-intro)
Linux App Service, Node.js uygulamasını çalıştırmak için bir Linux Docker kapsayıcısı dağıtır (Windows App Service'da IIS'nin arkasındaki Node.js uygulamaları Windows).

Bu öğreticide, Visual Studio için Node.js Araçları'nın yüklü olduğu bir şablondan başlayarak bir Node.js uygulaması oluşturma, kodu GitHub Azure App Service'de bir depoya itme ve GitHub deposundan dağıtabilirsiniz. Komut satırı kullanarak yerel git deposundan Azure App Service ve kodu itmek için bkz. [Node.js Uygulaması oluşturma.](/azure/app-service/containers/quickstart-nodejs)

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kod GitHub depo oluşturma
> * Azure'da Linux App Service oluşturma
> * Linux'a dağıtma

## <a name="prerequisites"></a>Önkoşullar

* Uygulama ve Visual Studio geliştirme iş Node.js gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'Visual Studio yüklemediyebilirsiniz. [](https://visualstudio.microsoft.com/downloads/)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de henüz yüklememişsinizdir, ücretsiz Visual Studio [](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekse ama zaten yüklüyse Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Geliştirme iş **Node.js seçin** ve ardından Değiştir'i **seçin.**

    ![VS YükleyicisiNode.js de iş yükü yükleme](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma Node.js gerekir.

    Yüklü yoksa,Node.jsweb sitesinden LTS [ sürümünü ](https://nodejs.org/en/download/) yükleyin. Genel olarak, Visual Studio çalışma zamanı otomatik olarak Node.js algılar. Yüklü bir çalışma zamanı algılanmazsa, projenizi özellikler sayfasında yüklü çalışma zamanının başvurusu için yapılandırabilirsiniz (bir proje oluşturduk sonra proje düğümüne sağ tıklayın ve Özellikler'i **seçin).**

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Azure'Node.js bir proje oluşturma

1. Visual Studio'yu açın.

1. Yeni bir TypeScript Express uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın, **Node.js** yazın, ardından Yeni Temel Azure Node.js Express 4 uygulaması (TypeScript) oluştur'a tıklayın.  Görüntülenen iletişim kutusunda Oluştur'a **tıklayın.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni Giriş iletişim kutusunun sol **bölmesinde TypeScript Project** genişletin ve ardından yeni bir **Node.js.**  Orta bölmede Temel Azure Node.js **Express 4 uygulamasını ve ardından Tamam'ı** **seçin.**

    ![Yeni bir TypeScript Express uygulaması oluşturma](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    Temel Azure Node.js **Express 4 uygulama** projesi şablonunu görmüyorsanız, uygulama geliştirme iş yükünüNode.js **eklemeniz** gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio projeyi oluşturur ve Çözüm Gezgini (sağ bölme) içinde açar.

1. Uygulamayı **derlemek ve** çalıştırmak için F5 tuşuna basın ve her şeyin beklendiği gibi çalışıyor olduğundan emin olun.

1. Proje **için** yerel bir Git  >  **deposu oluşturmak** üzere Kaynak denetimine Dosya Ekle'yi seçin.

    Bu noktada Express çerçevesini Node.js TypeScript ile yazılmış bir uygulama çalışır ve yerel kaynak denetimine iade edilir.

1. Sonraki adımlara devam etmeden önce projeyi istediğiniz gibi düzenleyin.

## <a name="push-code-from-visual-studio-to-github"></a>Kodu Visual Studio'a GitHub

Şunları ayarlamak Visual Studio için GitHub:

1. Araçlar için [GitHub Uzantısı'nın Visual Studio](https://visualstudio.github.com/) ve Araç Uzantıları ve Güncelleştirmeleri menü öğesi kullanılarak   >  **etkinleştirildiğinden emin olun.**

2. Menüden Diğer Öğeleri   >  **Görüntüle'yi Windows**  >  **GitHub.**

    GitHub penceresi açılır.

3. Başlarken penceresinde GitHub düğmesi  görmüyorsanız, Kaynak Denetimine Dosya Ekle'ye tıklayın ve kullanıcı arabiriminin   >   güncelleştirmesi için bekleyin.

    ![GitHub açın](../javascript/media/azure-github-get-started.png)

4. Öğesini Kullanmaya başlayın.

    GitHub'a zaten bağlıysanız, araç kutusu aşağıdaki çizime benzer şekilde görünür.

    ![GitHub ayarları](../javascript/media/azure-github-publish.png)

5. Yayımlanacak yeni depo alanlarını doldurun ve ardından Yayımla'ya **tıklayın.**

    Birkaç dakika sonra "Depo başarıyla oluşturuldu" yazılı bir başlık görüntülenir.

    Sonraki bölümde, bu depodan bir depoya yayımlamayı Linux üzerinde Azure App Service.

## <a name="create-a-linux-app-service-in-azure"></a>Azure'da Linux App Service oluşturma

1. [Azure Portal](https://portal.azure.com)’ında oturum açın.

2. Sol **tarafta hizmet** listesinden Uygulama Hizmetleri'ne tıklayın ve ekle'ye **tıklayın.**

3. Gerekirse yeni bir Kaynak Grubu oluşturun ve App Service barındırmayı planlayın.

4. Çizimde gösterildiği gibi **işletim sistemini** **Linux** olarak ayarla ve Çalışma Zamanı Yığını'Node.js gerekli sürüme ayarla. 

    ![Create a Linux App Service](../javascript/media/azure-create-appservice-annotated.png)

5. **Oluştur'a** tıklar ve App Service.

    Dağıtımı birkaç dakika sürebilir.

6. Dağıtıldıktan sonra Uygulama ayarları **bölümüne gidin** ve adına ve değerine sahip `SCM_SCRIPT_GENERATOR_ARGS` bir ayar `--node` ekleyin.

    ![Uygulama ayarları](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Dağıtım App Service, hangi tür uygulamanın çalıştırılamayacaklarını belirlemek için bir dizi heuristics kullanır. Bir ise. *Dağıtılan içerikte sln* dosyası algılandığında, MSBuild tabanlı bir projenin dağıtılacağı varsayılacaktır. Yukarıda eklenen ayar bu mantığı geçersiz kılar ve bunun bir uygulama Node.js belirtir. Bu ayar olmadan, Node.js uygulaması , dağıtımı başarısız olur. *sln* dosyası, depoya dağıtılan deponun bir App Service.

7. Uygulama **ayarları'nın** altına, adına ve değerine sahip `WEBSITE_NODE_DEFAULT_VERSION` başka bir ayar `8.9.0` ekleyin.

8. Dağıtıldıktan sonra, yapılandırmayı açın App Service **seçenekleri'ne tıklayın.**

    ![Dağıtım seçenekleri](../javascript/media/azure-deployment-options.png)

9. Kaynak **seçin'e** tıklayın, ardından **GitHub'ı** seçin ve gerekli izinleri yapılandırabilirsiniz.

    ![GitHub izinleri](../javascript/media/azure-choose-source.png)

10. Yayımlayacak depoyu ve dalı ve ardından Tamam'ı **seçin.**

    ![Linux App Service’e yayımlama](../javascript/media/azure-repo-and-branch.png)

    Eşitleme **sırasında** dağıtım seçenekleri sayfası görüntülenir.

    ![Dağıtım ve eşitleme GitHub](../javascript/media/azure-deployment-options-sync.png)

    Eşitleme tamamlandığında bir onay işareti görünür.

    Site artık Node.js uygulamasını GitHub deposundan çalıştırmıştır ve Azure App Service için oluşturulan URL'den erişilebilir (varsayılan olarak Azure App Service'ye verilen ad ve ardından ".azurewebsites.net") .

## <a name="modify-your-app-and-push-changes"></a>Uygulama ve anında değişikliklerinizi değiştirme

1. Burada gösterilen kodu *app.ts satırına* `app.use('/users', users);` ekleyin. Bu, /api REST API bir dosya *ekler.*

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Kodu derleme ve yerel olarak test edin, sonra kodu iade edin ve GitHub.

    Bu Azure portal, GitHub'daki değişiklikleri algılamak birkaç dakika sürer ve ardından dağıtımın yeni bir eşitlemesi başlatılır. Bu, aşağıdaki çizime benzer.

    ![Değiştirme ve eşitleme](../javascript/media/azure-changes-detected.png)

3. Dağıtım tamamlandıktan sonra genel siteye gidin ve *URL'ye /api* ekleyin. JSON yanıtı döndürülür.

## <a name="troubleshooting"></a>Sorun giderme

* İşlem node.exe (başka bir ifadeyle, işlanmamış bir özel durum oluşursa) kapsayıcı yeniden başlatılır.
* Kapsayıcı başlatıldığında, kapsayıcının çalışma sürecini nasıl başlatacaklarını anlamaları için çeşitli Node.js çalışır. Uygulamanın ayrıntıları [generateStartupCommand.js. ](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js)
* Araştırma için SSH aracılığıyla çalışan kapsayıcıya bağlanabilirsiniz. Bu, Azure portal. Uygulama App Service seçin ve Geliştirme Araçları bölümünde **SSH'ye** ulaşana kadar araç **listesini aşağı** kaydırın.
* Sorun gidermeye yardımcı olmak  için uygulamanın Tanılama günlükleri ayarlarına App Service **Docker Kapsayıcısı** günlük kaydı ayarını **Kapalı** olarak Dosya Sistemi **olarak değiştirin.** *Günlükler/home/LogFiles/* _docker.log* altında kapsayıcıda oluşturulur ve SSH veya FTP(S) kullanılarak kutudan erişilebilir.
* Varsayılan olarak atanmış *. azurewebsites.net URL 'SI yerine siteye özel bir etki alanı adı atanabilir. Daha ayrıntılı bilgi için bkz. [özel etki alanı eşleme](/azure/app-service/app-service-web-tutorial-custom-domain)konusu.
* Üretime geçmeden önce daha fazla test için bir hazırlama sitesine dağıtım en iyi uygulamadır. Bunun nasıl yapılandırılacağı hakkında ayrıntılı bilgi için, [hazırlama ortamları oluşturma](/azure/app-service/web-sites-staged-publishing)konusuna bakın.
* Daha sık sorulan sorular için [Linux 'ta App Service](/azure/app-service/containers/app-service-linux-faq) bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir Linux App Service oluşturma ve hizmete bir Node.js uygulaması dağıtma hakkında daha fazla öğrendiniz. Linux App Service hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
