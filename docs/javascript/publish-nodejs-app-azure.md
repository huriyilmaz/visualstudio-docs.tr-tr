---
title: Linux App Service’e bir Node.js uygulaması yayımlama
description: Visual Studio'da oluşturulan Node.js uygulamalarını Azure'da Linux Uygulama Hizmeti'ne yayınlayabilirsiniz
ms.date: 11/22/2019
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c304aca5171e1addab9a941105f11fb534eaa5ff
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74474021"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Bir Düğüm.js uygulamasını Azure'da yayımla (Linux Uygulama Hizmeti)

Bu öğretici, basit bir Düğüm.js uygulaması oluşturma ve Azure'da yayımlama görevi nde size yol sunar.

Bir Düğüm.js uygulamasını Azure'a yayınlarken birkaç seçenek vardır. Bunlar arasında seçtiğiniz bir işletim sistemi çalıştıran bir VM olan Azure Uygulama Hizmeti, Kubernetes ile yönetim için Azure Konteyner Hizmeti (AKS), Docker kullanan bir Konteyner Örneği ve daha fazlası yer almaktadır. Bu seçeneklerin her biri hakkında daha fazla bilgi için [Bilgi İşlem'e](https://azure.microsoft.com/product-categories/compute/)bakın.

Bu öğretici için uygulamayı [Linux Uygulama Hizmeti'ne](/azure/app-service/containers/app-service-linux-intro)dağıtabilirsiniz.
Linux App Service, Node.js uygulamasını çalıştırmak için bir Linux Docker kapsayıcısı dağıtır (Windows'da IIS'in arkasındaki Node.js uygulamalarını çalıştıran Windows Uygulama Hizmeti'nin aksine).

Bu öğretici, Visual Studio için Node.js Tools ile yüklü bir şablondan başlayarak bir Düğüm.js uygulamasının nasıl oluşturulabileceğini, kodu GitHub'daki bir depoya nasıl itebileceğinizi ve azure web portalı üzerinden azure uygulama hizmeti sağlamanın nasıl GitHub deposu. Azure Uygulama Hizmeti'ni sağlamak ve kodu yerel bir Git deposundan itmek için komut satırını kullanmak için [bkz.](/azure/app-service/containers/quickstart-nodejs)

Bu öğreticide şunların nasıl yapıldığını öğrenirsiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * Kod için Bir GitHub deposu oluşturma
> * Azure'da Linux Uygulama Hizmeti Oluşturma
> * Linux'a dağıtın

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node.js geliştirme iş yükünü yüklü olmalıdır.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'u henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'yi henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekiyorsa ancak visual studio'ya zaten sahipseniz, **Visual** > Studio Installer'ı açan**Araçlar Ve Özellikler...'** a gidin. **Düğüm.js geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

    ![VS Yükleyici'de Düğüm.js iş yükü](../ide/media/quickstart-nodejs-workload.png)

* Düğüm.js çalışma saatini yüklemelisiniz.

    Yüklü değilseniz, [Node.js](https://nodejs.org/en/download/) web sitesinden LTS sürümünü yükleyin. Genel olarak, Visual Studio yüklenen Node.js çalışma süresini otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi özellikler sayfasındaki yüklü çalışma süresine başvurmak üzere yapılandırabilirsiniz (proje oluşturduktan sonra, proje düğümüne sağ tıklayın ve **Özellikler'i**seçin).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Azure'da çalışacak bir Düğüm.js projesi oluşturma

1. Visual Studio'yu açın.

1. Yeni bir TypeScript Express uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **Düğüm.js**yazın, ardından **yeni Temel Azure Düğümleri Express 4 uygulaması (TypeScript) oluştur'u** seçin. Görünen iletişim kutusunda **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni Proje** iletişim kutusunun sol bölmesinde, **TypeScript'i**genişletin, ardından **Düğüm.js'yi**seçin. Orta bölmede, **Temel Azure Düğümü.js Express 4 uygulamasını**seçin, ardından **Tamam'ı**seçin.

    ![Yeni bir TypeScript Express uygulaması oluşturma](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    **Temel Azure Düğümü.js Express 4 uygulama** projesi şablonunu görmüyorsanız, Düğüm **geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı talimatlar için [Önkoşullar'a](#prerequisites)bakın.

    Visual Studio projeyi oluşturur ve Solution Explorer'da (sağ bölme) açar.

1. Uygulamayı oluşturmak ve çalıştırmak ve her şeyin beklendiği gibi çalışmasını sağlamak için **F5** tuşuna basın.

1. Proje için yerel bir Git deposu oluşturmak için**kaynak denetimine** **Dosya** > Ekle'yi seçin.

    Bu noktada, Express çerçevesini kullanan ve TypeScript'te yazılı olan bir Düğüm.js uygulaması çalışıyor ve yerel kaynak denetimine giriş iyor.

1. Sonraki adımlara geçmeden önce projeyi istediğiniz gibi edin.

## <a name="push-code-from-visual-studio-to-github"></a>Visual Studio'dan GitHub'a itme kodu

Visual Studio için GitHub'ı kurmak için:

1. [Visual Studio için GitHub Uzantısı'nın](https://visualstudio.github.com/) menü öğesi **Araçlar** > Uzantıları ve**Güncellemeleri**kullanılarak yüklü ve etkin olduğundan emin olun.

2. Menüden**Diğer Windows** > **GitHub'ı** **Görüntüle'yi** > seçin.

    GitHub penceresi açılır.

3. GitHub penceresinde Başlat **düğmesini** görmüyorsanız, **Kaynak** > **Denetimine Dosya Ekle'yi** tıklatın ve Kullanıcı Arasını'nın güncelmesini bekleyin.

    ![GitHub penceresini açma](../javascript/media/azure-github-get-started.png)

4. **Başlayın**'a tıklayın.

    Zaten GitHub'a bağlıysanız, araç kutusu aşağıdaki çizime benzer görünür.

    ![GitHub repo ayarları](../javascript/media/azure-github-publish.png)

5. Yayımlanacak yeni deponun alanlarını tamamlayın ve sonra **Yayımla'yı**tıklatın.

    Birkaç dakika sonra, "Repository başarıyla oluşturuldu" belirten bir afiş görüntülenir.

    Bir sonraki bölümde, bu depodan Linux'taki bir Azure Uygulama Hizmetine nasıl yayınlayacağınızı öğreneceksiniz.

## <a name="create-a-linux-app-service-in-azure"></a>Azure'da Linux Uygulama Hizmeti Oluşturma

1. [Azure portalında](https://portal.azure.com)oturum açın.

2. Soldaki hizmetler listesinden **Uygulama Hizmetleri'ni** seçin ve sonra **Ekle'yi**tıklatın.

3. Gerekirse, yeni uygulamayı barındırmak için yeni bir Kaynak Grubu ve Uygulama Hizmeti planı oluşturun.

4. **İşletim sistemi'ni** **Linux'a**ayarladıktan ve **Runtime Stack'i** resimde gösterildiği gibi gerekli Node.js sürümüne ayarladıktan emin olun.

    ![Linux Uygulama Hizmeti Oluşturma](../javascript/media/azure-create-appservice-annotated.png)

5. Uygulama Hizmetini oluşturmak için **Oluştur'u** tıklatın.

    Dağıtmak birkaç dakika sürebilir.

6. Dağıtıldıktan **sonra, Uygulama ayarları** bölümüne gidin ve bir ad `SCM_SCRIPT_GENERATOR_ARGS` ve `--node`değeri olan bir ayar ekleyin.

    ![Uygulama ayarları](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > Uygulama Hizmeti dağıtım işlemi, hangi uygulama türünü deneyeceğini ve çalıştıracağını belirlemek için bir dizi buluşsal uygulama kullanır. Eğer bir . *sln* dosyası dağıtılan içerikte algılanır, msbuild tabanlı bir projenin dağıtıldığını varsayar. Yukarıda eklenen ayar bu mantığı geçersiz kılar ve bunun bir Düğüm.js uygulaması olduğunu açıkça belirtir. Bu ayar olmadan, Düğüm.js uygulaması . *sln* dosyası, App Service'e dağıtılan deponun bir parçasıdır.

7. **Uygulama ayarları**altında, bir ad `WEBSITE_NODE_DEFAULT_VERSION` ve değeri `8.9.0`ile başka bir ayar ekleyin.

8. Dağıtıldıktan sonra Uygulama Hizmeti'ni açın ve **Dağıtım seçeneklerini**seçin.

    ![Dağıtım seçenekleri](../javascript/media/azure-deployment-options.png)

9. **Kaynak Seç'i**tıklatın ve ardından **GitHub'ı**seçin ve ardından gerekli izinleri yapılandırın.

    ![GitHub izinleri](../javascript/media/azure-choose-source.png)

10. Yayımlanmak üzere depo yu ve dalını seçin ve ardından **Tamam'ı**seçin.

    ![Linux App Service’e yayımlama](../javascript/media/azure-repo-and-branch.png)

    **Eşitleme** sırasında dağıtım seçenekleri sayfası görüntülenir.

    ![GitHub ile dağıtma ve eşitleme](../javascript/media/azure-deployment-options-sync.png)

    Eşitleme tamamlandıktan sonra bir onay işareti görüntülenir.

    Site artık GitHub deposundan Node.js uygulamasını çalıştırıyor ve Azure Uygulama Hizmeti için oluşturulan URL'den erişilebilir (varsayılan olarak Azure Uygulama Hizmeti'ne verilen ad ve ardından ".azurewebsites.net").

## <a name="modify-your-app-and-push-changes"></a>Uygulamanızı değiştirin ve değişiklikleri itin

1. Satırdan `app.use('/users', users);`sonra *app.ts'de* gösterilen kodu buraya ekleyin. Bu URL */ api*bir REST API ekler.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Kodu oluşturun ve yerel olarak test edin, sonra iade edin ve GitHub'a itin.

    Azure portalında, GitHub reposundaki değişiklikleri algılamak birkaç dakika sürer ve ardından dağıtımın yeni bir eşitlemi başlar. Bu aşağıdaki çizime benzer.

    ![Değiştirme ve eşitleme](../javascript/media/azure-changes-detected.png)

3. Dağıtım tamamlandıktan sonra genel siteye gidin ve URL'ye */api* ekleyin. JSON yanıtı geri döner.

## <a name="troubleshooting"></a>Sorun giderme

* Düğüm.exe işlemi ölürse (diğer bir şekilde işlenmemiş bir özel durum oluşursa), kapsayıcı yeniden başlatılır.
* Konteyner başlatıldığında, Node.js işlemini nasıl başlatacağını bulmak için çeşitli buluşsal çalışmalardan geçer. Uygulamanın ayrıntıları [generateStartupCommand.js](https://github.com/Azure-App-Service/node/blob/master/8.9.4/startup/generateStartupCommand.js)adresinde görülebilir.
* İncelemeler için SSH üzerinden çalışan konteynere bağlanabilirsiniz. Bu, Azure portalı kullanılarak kolayca yapılır. Uygulama Hizmeti'ni seçin ve **Geliştirme Araçları** bölümündesi altında **SSH'ye** ulaşana kadar araç listesini aşağı kaydırın.
* Sorun gidermeye yardımcı olmak için, Uygulama Hizmeti için **Tanılama günlükleri** ayarlarına gidin ve **Docker Konteyner günlüğe kaydetme** ayarını **Kapalı'dan** **Dosya Sistemi'ne**değiştirin. Günlükler */home/LogFiles/*_docker.log* altındaki kapta oluşturulur ve Kutudan SSH veya FTP(S) kullanılarak erişilebilir.
* Varsayılan olarak atanan *.azurewebsites.net URL yerine siteye özel bir etki alanı adı atanabilir. Daha fazla bilgi için, konu [Haritası Özel Etki Alanı](/azure/app-service/app-service-web-tutorial-custom-domain)bakın.
* Üretime geçmeden önce daha fazla test için bir evreleme alanına dağıtmak en iyi yöntemdir. Bunu nasıl yapılandırılabiliyorum, [evreleme ortamlarını oluştur](/azure/app-service/web-sites-staged-publishing)konusuna bakın.
* Daha sık sorulan sorular için [Linux SSS'deki Uygulama Hizmeti'ne](/azure/app-service/containers/app-service-linux-faq) bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, bir Linux Uygulama Hizmeti oluşturmayı ve bir Düğüm.js uygulamasını hizmete nasıl dağıttığını öğrendiniz. Linux Uygulama Hizmeti hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Linux Uygulama Hizmeti](/azure/app-service/containers/app-service-linux-intro)
