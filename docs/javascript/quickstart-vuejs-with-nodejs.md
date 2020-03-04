---
title: 'Hızlı Başlangıç: ilk Vue.js uygulamanızı oluşturma'
description: Bu hızlı başlangıçta, Visual Studio için Node.js araçları kullanarak Visual Studio'da bir Vue.js uygulaması oluşturma
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
ms.openlocfilehash: a1995353d00f9e48811f388e1d853c93850b85f4
ms.sourcegitcommit: 9eff8371b7a79a637ebb6850f775dd3eed343d8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78235112"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Hızlı Başlangıç: Kullanım ilk Vue.js uygulamanızı oluşturmak için Visual Studio

Bu 5-10 dakikalık bir giriş Visual Studio tümleşik geliştirme ortamı (IDE), oluşturun ve basit bir Vue.js web uygulaması çalıştırın.

> [!IMPORTANT]
> Bu makalede, Visual Studio 2017 sürüm 15,8'den itibaren kullanılabilmektedir Vue.js şablon gerektirir.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node. js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. **Node. js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![Node.js iş yükü VS yükleyicisi](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanı yüklü olması gerekir.

    Yüklü değilse, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node. js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz. Node. js, 32-bit ve 64-bit mimariler için oluşturulmuştur. Visual Studio 'daki Node. js Araçları, Node. js iş yüküne dahil edilmiştir, her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node. js yükleyicisi yalnızca aynı anda yüklü olan birini destekler.
    
    Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayın, **Özellikler**' i seçin ve **Node. exe yolunu**ayarlayın). Node. js ' nin genel bir yüklemesini kullanabilir veya Node. js projelerinizdeki her bir yerel yorumlayıcı yolunu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Vue.js web uygulaması projesi oluşturacaksınız.

1. Node. js çalışma zamanı zaten yüklü değilse, [Node. js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz.

    Daha fazla bilgi için bkz. Önkoşullar.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **temel Vue. js**yazın ve ardından **temel Vue. js web uygulaması** (JavaScript veya Typescript) öğesini seçin. Görüntülenen iletişim kutusunda, **Basic-vuejs**adını yazın ve ardından **Oluştur**' u seçin.

    ![VUE.js şablonu](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya** > **Yeni** > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **JavaScript** veya **TypeScript**' i genişletin ve **Node. js**' yi seçin. Orta bölmede, **temel Vue. js web uygulaması**' nı seçin, **Basic-vuejs**adını yazın ve ardından **Tamam**' ı seçin.

    ![VUE.js şablonu](../javascript/media/vuejs-template.png)
    ::: moniker-end
    **Temel Vue. js web uygulaması** proje şablonunu görmüyorsanız, **Node. js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni proje oluşturur. Yeni projeyi, Çözüm Gezgini'nde (sağ bölme) açar.

1. Uygulama için gerekli npm paketlerini yükleme ilerleme durumu için çıkış penceresine (alt bölme) denetleyin.

1. Çözüm Gezgini, **NPM** düğümünü açın ve listelenen tüm NPM paketlerinin yüklü olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **NPM** düğümüne sağ tıklayıp **eksik NPM paketlerini yüklemeyi**seçebilirsiniz.

## <a name="explore-the-ide"></a>IDE'yi keşfedin

1. Sağ bölmedeki **Çözüm Gezgini** göz atın.

     ![VUE.js çözümü](../javascript/media/vuejs-solution.png)

   - Kalın olarak vurgulanmış, **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projeniz. Diskte, bu proje bir ile temsil edilir. proje klasörünüzdeki *njsproj* dosyası.

   - En üst düzeyinde ve proje ile aynı ada sahip varsayılan bir çözümdür. İle temsil edilen bir çözüm. disk üzerindeki *sln* dosyası, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - **NPM** düğümü yüklü NPM paketlerini gösterir. İçin arama yapın ve iletişim kutusunu kullanarak npm paketlerini yüklemek için npm düğümünü sağ tıklayabilirsiniz.

2. Bir komut isteminden NPM paketleri yüklemek veya Node. js komutlarını çalıştırmak istiyorsanız, proje düğümüne sağ tıklayın ve **burada komut Istemi aç**' ı seçin.

## <a name="add-a-vue-file-to-the-project"></a>.Vue dosya projeye ekleyin.

1. Çözüm Gezgini, *src/Components* klasörü gibi bir klasöre sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.

1. **JavaScript Vue tek dosya bileşeni** ya da **TypeScript Vue tek dosya bileşeni**' ni seçin ve ardından **Ekle**' ye tıklayın.

    Visual Studio yeni dosyayı projeye ekler.

## <a name="build-the-project"></a>Projeyi derleme

1. (Yalnızca TypeScript Projesi) Visual Studio 'da **derleme** > **Temizleme çözümü**' ni seçin.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de bulunan TypeScript şablonunda, bu adımı atlayın.
    ::: moniker-end

1. Sonra, projeyi derlemek için **build** > **Build Solution** öğesini seçin. Derleme sonuçlarını görmek için **Çıkış** penceresini kontrol edin ve **çıktıyı göster** listesinden **Oluştur** ' u seçin.

    JavaScript Vue. js proje şablonu (ve TypeScript şablonunun eski sürümleri) derleme sonrası olayını yapılandırarak `build` NPM betiğini kullanır. Bu ayarı değiştirmek istiyorsanız, proje dosyasını ( *\<projectname\>. njsproj*) Windows Gezgini 'nden açın ve şu kod satırını bulun:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **Ctrl**+**F5** tuşuna basın (veya hata ayıklama **> Başlat**).

   Konsolunda, *geliştirme sunucusunu Başlatan*bir ileti görürsünüz.

   Ardından, uygulamayı bir tarayıcıda açılır.
   
   Çalışan uygulamayı görmüyorsanız, sayfayı yenileyin.

   ![Tarayıcıda çalışan Vue.js uygulama](../javascript/media/vuejs-running-app.png)

1. Web tarayıcısını kapatın.

Bu hızlı başlangıcı tamamladığınızda Tebrikler! Visual Studio IDE ile Vue.js kullanma hakkında biraz öğrenilen umuyoruz. Özelliklerini daha ayrıntılı olarak öğrenmek isterseniz, içindekiler tablosunun **öğreticiler** bölümünde öğreticiye devam edin.

## <a name="next-steps"></a>Sonraki adımlar

- [Node. js ve Express öğreticisine](tutorial-nodejs.md) gidin
- [Node. js öğreticisine gidin ve tepki](tutorial-nodejs-with-react-and-jsx.md) verin
- [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)