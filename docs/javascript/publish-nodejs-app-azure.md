---
title: Linux App Service’e bir Node.js uygulaması yayımlama
description: Visual Studio oluşturulan Node.js uygulamaları Azure 'da Linux App Service yayımlayabilirsiniz
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
ms.openlocfilehash: 2a3cad9500df712286c592c45c8c8ce03d96ea7f7d7eb4fca3cc1c0ecea7bb52
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121398753"
---
# <a name="publish-a-nodejs-application-to-azure-linux-app-service"></a>Azure 'da bir Node.js uygulaması yayımlama (Linux App Service)

Bu öğreticide, basit bir Node.js uygulaması oluşturma ve Azure 'da yayımlama görevi gösterilmektedir.

Azure 'da bir Node.js uygulaması yayımlarken birkaç seçenek vardır. Bunlar arasında Azure App Service, Kubernetes ile yönetim için Azure Container Service (AKS) bir VM çalıştıran bir VM, Docker kullanan bir kapsayıcı örneği ve daha fazlası bulunur. Bu seçeneklerin her biri hakkında daha fazla bilgi için bkz. [COMPUTE](https://azure.microsoft.com/product-categories/compute/).

Bu öğretici için, uygulamayı [Linux App Service](/azure/app-service/containers/app-service-linux-intro)'ye dağıtırsınız.
linux App Service, Node.js uygulamasını çalıştırmak için bir Linux docker kapsayıcısı dağıtır (Node.js ııs arkasındaki Windows uygulamaları çalıştıran Windows App Service aksine).

bu öğreticide, Visual Studio için Node.js araçlarla yüklenmiş bir şablondan başlayan Node.js bir uygulama oluşturma, kodu GitHub bir depoya gönderme ve sonra Azure App Service deposundan dağıtabilmeniz için Azure web portalı aracılığıyla bir GitHub sağlama işlemlerinin nasıl yapılacağı gösterilmektedir. Azure App Service sağlamak ve kodu yerel bir git deposundan göndermek için komut satırını kullanmak üzere, bkz. [Create Node.js App](/azure/app-service/containers/quickstart-nodejs).

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:
> [!div class="checklist"]
> * Node.js projesi oluşturma
> * kod için GitHub deposu oluşturma
> * Azure 'da Linux App Service oluşturma
> * Linux 'a dağıtma

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node.js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    zaten 2019 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    zaten 2017 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
    ::: moniker-end

    iş yükünü yüklemeniz gerekir, ancak zaten Visual Studio sahipseniz **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **Node.js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![VS yükleyicisinde iş yükünü Node.js](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanının yüklü olması gerekir.

    Yüklü değilse, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz. genellikle Visual Studio, yüklü Node.js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayıp **Özellikler**' i seçin).

## <a name="create-a-nodejs-project-to-run-in-azure"></a>Azure 'da çalıştırmak için bir Node.js projesi oluşturma

1. Visual Studio'yu açın.

1. Yeni bir TypeScript Express uygulaması oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node.js** yazın ve ardından **Yeni temel Azure Node.js Express 4 uygulaması** (TypeScript) öğesini seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    üstteki menü çubuğundan **dosya**  >  **yeni**  >  **Project** öğesini seçin. **yeni Project** iletişim kutusunun sol bölmesinde **TypeScript**' i genişletin ve **Node.js**' ı seçin. Orta bölmede **temel Azure Node.js Express 4 uygulaması**' nı seçin ve ardından **Tamam**' ı seçin.

    ![Yeni bir TypeScript Express uygulaması oluşturun](../javascript/media/azure-ts-express-app.png)
    ::: moniker-end
    **Temel Azure Node.js Express 4 uygulama** projesi şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio projeyi oluşturur ve Çözüm Gezgini (sağ bölme) içinde açar.

1. Uygulamayı derlemek ve çalıştırmak için **F5** tuşuna basın ve her şeyin beklendiği gibi çalıştığından emin olun.

1.   >  Proje için yerel bir git deposu oluşturmak üzere dosya **kaynak denetimine Ekle** ' yi seçin.

    Bu noktada, Express çerçevesini kullanan ve TypeScript 'te yazılan Node.js bir uygulama çalışır ve yerel kaynak denetimine iade edilir.

1. Sonraki adımlara geçmeden önce projeyi istediğiniz gibi düzenleyin.

## <a name="push-code-from-visual-studio-to-github"></a>Visual Studio 'den GitHub 'a gönderme kodu

Visual Studio için GitHub ayarlamak için:

1. [Visual Studio için GitHub uzantısının](https://visualstudio.github.com/) , menü öğesi **araçları**  >  **uzantıları ve güncelleştirmeleri** kullanılarak yüklendiğinden ve etkinleştirildiğinden emin olun.

2. menüden   >  **diğer Windows** görüntüle  >  **GitHub**' yi seçin.

    GitHub penceresi açılır.

3. GitHub penceresinde **Başlarken** düğmesini görmüyorsanız, **dosya**  >  **kaynak denetimine ekle** ' ye tıklayın ve kullanıcı arabiriminin güncelleştirilmesini bekleyin.

    ![GitHub penceresini açın](../javascript/media/azure-github-get-started.png)

4. **Başlarken**' e tıklayın.

    zaten GitHub bağlıysanız, araç kutusu aşağıdaki çizime benzer şekilde görünür.

    ![depo ayarlarını GitHub](../javascript/media/azure-github-publish.png)

5. Yayımlanacak yeni deponun alanlarını tamamlayıp **Yayımla**' ya tıklayın.

    Birkaç dakika sonra, "depo başarıyla oluşturuldu" belirten bir başlık görüntülenir.

    Sonraki bölümde, bu depodan Linux üzerinde bir Azure App Service nasıl yayımlayacağınızı öğreneceksiniz.

## <a name="create-a-linux-app-service-in-azure"></a>Azure 'da Linux App Service oluşturma

1. [Azure Portal](https://portal.azure.com)’ında oturum açın.

2. Sol taraftaki hizmetler listesinden **uygulama hizmetleri** ' ni seçin ve ardından **Ekle**' ye tıklayın.

3. Gerekirse, yeni bir kaynak grubu oluşturun ve yeni uygulamayı barındırmak için plan App Service.

4. **Işletim sistemini** **Linux**'a ayarladığınızdan emin olun ve **çalışma zamanı yığınını** çizimde gösterildiği gibi gerekli Node.js sürümüne ayarlayın.

    ![Linux App Service oluşturma](../javascript/media/azure-create-appservice-annotated.png)

5. App Service oluşturmak için **Oluştur** ' a tıklayın.

    Dağıtım birkaç dakika sürebilir.

6. Dağıtıldıktan sonra, **uygulama ayarları** bölümüne gidin ve adı ve değeri olan bir ayar ekleyin `SCM_SCRIPT_GENERATOR_ARGS` `--node` .

    ![Uygulama ayarları](../javascript/media/azure-script-generator-args.png)

    > [!WARNING]
    > App Service dağıtım işlemi, deneyebileceğiniz ve çalıştırılacak uygulama türünü belirleyen bir buluşsal yöntem kümesi kullanır. Bir. dağıtılan içerikte *bir dosya dosyası* algılanırsa, MSBuild tabanlı bir projenin dağıtılmakta olduğunu varsayacaktır. Yukarıda eklenen ayar bu mantığı geçersiz kılar ve açıkça bunun Node.js bir uygulama olduğunu belirtir. Bu ayar olmadan, Node.js uygulaması. *sln* dosyası, App Service dağıtılan deponun bir parçasıdır.

7. **Uygulama ayarları**' nın altında, adı ve değeri olan başka bir ayar ekleyin `WEBSITE_NODE_DEFAULT_VERSION` `8.9.0` .

8. Dağıtıldıktan sonra, App Service açın ve **dağıtım seçenekleri**' ni seçin.

    ![Dağıtım seçenekleri](../javascript/media/azure-deployment-options.png)

9. **kaynak seç**' e ve ardından **GitHub**' yi seçin ve ardından gerekli izinleri yapılandırın.

    ![GitHub izinleri](../javascript/media/azure-choose-source.png)

10. Yayımlanacak depoyu ve dalı seçin ve ardından **Tamam**' ı seçin.

    ![Linux App Service’e yayımlama](../javascript/media/azure-repo-and-branch.png)

    **Dağıtım seçenekleri** sayfası eşitleme sırasında görüntülenir.

    ![GitHub dağıtma ve eşitleme](../javascript/media/azure-deployment-options-sync.png)

    Eşitleme tamamlandıktan sonra bir onay işareti görünür.

    site artık GitHub deposundan Node.js uygulamayı çalıştırıyor ve Azure App Service için oluşturulan URL 'den (varsayılan olarak, ". azurewebsites.net" tarafından izlenen Azure App Service verilen ad) erişilebilir.

## <a name="modify-your-app-and-push-changes"></a>Uygulamanızı değiştirin ve değişiklikleri gönderin

1. Burada gösterilen kodu, satırdan sonra *app. TS* ' de ekleyin `app.use('/users', users);` . Bu, */API* URL 'sinde bir REST API ekler.

    ```typescript
    app.use('/api', (req, res, next) => {
        res.json({"result": "success"});
    });
    ```

2. Kodu derleyin ve yerel olarak test edin, ardından iade edin ve GitHub gönderin.

    Azure portal, GitHub depodaki değişikliklerin algılanması birkaç dakika sürer ve ardından dağıtımın yeni bir eşitlemesi başlar. Bu, aşağıdaki resme benzer şekilde görünür.

    ![Değiştir ve Eşitle](../javascript/media/azure-changes-detected.png)

3. Dağıtım tamamlandıktan sonra ortak siteye gidin ve URL 'ye */API* ekleyin. JSON yanıtı döndürülür.

## <a name="troubleshooting"></a>Sorun giderme

* node.exe işlem olursa (diğer bir deyişle, işlenmeyen bir özel durum oluşursa), kapsayıcı yeniden başlatılır.
* Kapsayıcı başladığında, Node.js işlemini nasıl başlatacağınızı anlamak için çeşitli buluşsal yöntemler aracılığıyla çalışır. Uygulamanın ayrıntıları, [generateStartupCommand.js](https://github.com/Azure/app-service-builtin-images/blob/master/node/8.9.4/startup/generateStartupCommand.js)' de görülebilir.
* Araştırmalar için SSH aracılığıyla çalışan kapsayıcıya bağlanabilirsiniz. Bu, Azure portal kullanılarak kolayca yapılır. App Service seçin ve **geliştirme araçları** bölümü altında **SSH** 'ye ulaşıncaya kadar araç listesini aşağı kaydırın.
* Sorun gidermeye yardımcı olmak için, App Service için **tanılama günlükleri** ayarlarına gidin ve **Docker kapsayıcı günlüğü** ayarını **dosya sistemine** çevirin.  Günlükler */Home/LogFiles/* _docker. log * altındaki kapsayıcıda oluşturulur ve SSH veya FTP kullanılarak kutudan erişilebilir.
* Varsayılan olarak atanmış *. azurewebsites.net URL 'SI yerine siteye özel bir etki alanı adı atanabilir. Daha ayrıntılı bilgi için bkz. [özel etki alanı eşleme](/azure/app-service/app-service-web-tutorial-custom-domain)konusu.
* Üretime geçmeden önce daha fazla test için bir hazırlama sitesine dağıtım en iyi uygulamadır. Bunun nasıl yapılandırılacağı hakkında ayrıntılı bilgi için, [hazırlama ortamları oluşturma](/azure/app-service/web-sites-staged-publishing)konusuna bakın.
* Daha sık sorulan sorular için [Linux 'ta App Service](/azure/app-service/containers/app-service-linux-faq) bakın.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bir Linux App Service oluşturma ve hizmete bir Node.js uygulaması dağıtma hakkında daha fazla öğrendiniz. Linux App Service hakkında daha fazla bilgi edinmek isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Linux App Service](/azure/app-service/containers/app-service-linux-intro)
