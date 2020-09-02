---
title: 'Hızlı başlangıç: ilk Vue.js uygulamanızı oluşturma'
description: Bu hızlı başlangıçta, Visual Studio 'da Visual Studio Node.js araçlarını kullanarak bir Vue.js uygulaması oluşturacaksınız
ms.custom: ''
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 882c3a148164ab88412a817abd72d0608fadf9b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81744980"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Hızlı başlangıç: ilk Vue.js uygulamanızı oluşturmak için Visual Studio 'Yu kullanma

Visual Studio tümleşik geliştirme ortamına (IDE) bu 5-10 dakikalık bir giriş ile basit bir Vue.js Web uygulaması oluşturup çalıştıracaksınız.

> [!IMPORTANT]
> Bu makale, Visual Studio 2017 sürüm 15,8 ' den itibaren kullanılabilen Vue.js şablonunu gerektirir.

## <a name="prerequisites"></a>Ön koşullar

* Visual Studio yüklü ve Node.js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/)   sayfasına giderek ücretsiz olarak yükleme yapın.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak zaten Visual Studio 'ya sahipseniz **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açılır. **Node.js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![VS yükleyicisinde iş yükünü Node.js](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanının yüklü olması gerekir.

    Yüklü değilse, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz. Node.js, 32-bit ve 64-bit mimariler için oluşturulmuştur. Visual Studio 'daki Node.js araçları, Node.js iş yüküne dahil edilmiştir, her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyici yalnızca aynı anda yüklü olan birini destekler.
    
    Genel olarak, Visual Studio yüklü Node.js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayın, **Özellikler**' i seçin ve **Node.exe yolunu**ayarlayın). Node.js genel bir yüklemesini kullanabilir veya Node.js projelerinizde her birinde yerel yorumlayıcı yolunu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Vue.js Web uygulaması projesi oluşturacaksınız.

1. Node.js çalışma zamanı zaten yüklü değilse, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz.

    Daha fazla bilgi için bkz. Önkoşullar.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **temel Vue.js**yazın ve **temel Vue.js Web uygulaması** (JavaScript veya Typescript) öğesini seçin. Görüntülenen iletişim kutusunda, **Basic-vuejs**adını yazın ve ardından **Oluştur**' u seçin.

    ![Vue.js şablonu](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **JavaScript** veya **TypeScript**' i genişletin ve ardından **Node.js**' yi seçin. Orta bölmede **temel Vue.js Web uygulaması**' nı seçin, **Basic-vuejs**adını yazın ve ardından **Tamam**' ı seçin.

    ![Vue.js şablonu](../javascript/media/vuejs-template.png)
    ::: moniker-end
    **Temel Vue.js Web uygulaması** proje şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni projeyi oluşturur. Yeni proje Çözüm Gezgini açılır (sağ bölme).

1. Uygulama için gereken NPM paketlerinin yüklenmesiyle ilgili ilerleme durumu için çıkış penceresini (alt bölme) denetleyin.

1. Çözüm Gezgini, **NPM** düğümünü açın ve listelenen tüm NPM paketlerinin yüklü olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **NPM** düğümüne sağ tıklayıp **eksik NPM paketlerini yüklemeyi**seçebilirsiniz.

## <a name="explore-the-ide"></a>IDE 'yi keşfet

1. Sağ bölmedeki **Çözüm Gezgini** göz atın.

     ![Vue.js çözümü](../javascript/media/vuejs-solution.png)

   - Kalın olarak vurgulanmış, **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projeniz. Diskte, bu proje bir ile temsil edilir. proje klasörünüzdeki *njsproj* dosyası.

   - En üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. İle temsil edilen bir çözüm. disk üzerindeki *sln* dosyası, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - **NPM** düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilirsiniz.

2. Bir komut isteminden NPM paketleri yüklemek veya Node.js komutları çalıştırmak istiyorsanız, proje düğümüne sağ tıklayın ve **komut Istemi 'Ni buradan aç**' ı seçin.

## <a name="add-a-vue-file-to-the-project"></a>Projeye bir. vue dosyası ekleyin

1. Çözüm Gezgini, *src/Components* klasörü gibi bir klasöre sağ tıklayın ve ardından **Add**  >  **Yeni öğe**Ekle ' yi seçin.

1. **JavaScript Vue tek dosya bileşeni** ya da **TypeScript Vue tek dosya bileşeni**' ni seçin ve ardından **Ekle**' ye tıklayın.

    Visual Studio, yeni dosyayı projeye ekler.

## <a name="build-the-project"></a>Projeyi derleme

::: moniker range=">=vs-2019"
1. Sonra, **Build** > Projeyi derlemek için derleme **Build Solution** öğesini seçin.

1. Derleme sonuçlarını görmek için **Çıkış** penceresini kontrol edin ve **çıktıyı göster** listesinden **Oluştur** ' u seçin.
::: moniker-end
::: moniker range="vs-2017"
1. (Yalnızca TypeScript Projesi) Visual Studio 'da, **Build** > **temiz çözüm**oluştur ' u seçin.

1. Sonra, **Build** > Projeyi derlemek için derleme **Build Solution** öğesini seçin.

1. Derleme sonuçlarını görmek için **Çıkış** penceresini kontrol edin ve **çıktıyı göster** listesinden **Oluştur** ' u seçin.
::: moniker-end

JavaScript Vue.js proje şablonu (ve TypeScript şablonunun eski sürümleri) `build` Derleme sonrası olayını yapılandırarak NPM betiğini kullanır. Bu ayarı değiştirmek istiyorsanız, Windows Gezgini 'nden proje dosyasını (* \<projectname\> . njsproj*) açın ve şu kod satırını bulun:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. **Ctrl** + Uygulamayı çalıştırmak için CTRL**F5** tuşuna basın (veya hata ayıklama **> başlatın**).

   Konsolunda, *geliştirme sunucusunu Başlatan*bir ileti görürsünüz.

   Ardından, uygulama bir tarayıcıda açılır.
   
   Çalışan uygulamayı görmüyorsanız, sayfayı yenileyin.

   ![Tarayıcıda çalışan Vue.js uygulama](../javascript/media/vuejs-running-app.png)

1. Web tarayıcısını kapatın.

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! Vue.js ile Visual Studio IDE 'yi kullanma hakkında biraz bilgi edindiniz. Özelliklerini daha ayrıntılı olarak öğrenmek isterseniz, içindekiler tablosunun **öğreticiler** bölümünde öğreticiye devam edin.

## <a name="next-steps"></a>Sonraki adımlar

- [Vue.js](create-application-with-vuejs.md) makalesine gidin
- [Node.js ve Express öğreticisine](tutorial-nodejs.md) bakın
- [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)