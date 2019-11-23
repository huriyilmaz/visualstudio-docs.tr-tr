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
ms.openlocfilehash: 5f7b877d825a573b935a9bf0f2c907ec2ce6f808
ms.sourcegitcommit: 2f64b3b231900018fceafb72b5a1c65140213a18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73428766"
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

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. Seçin **Node.js geliştirme** iş yükü, ardından **Değiştir**.

    ![Node.js iş yükü VS yükleyicisi](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanı yüklü olması gerekir.

    LTS sürümünden yüklü yoksa, yükleme [Node.js](https://nodejs.org/en/download/) Web sitesi. Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılayan değil, projenizi yüklü çalışma zamanı özellikleri sayfasında başvurmak için yapılandırabilirsiniz (bir proje oluşturduğunuzda, proje düğümüne sağ tıklayın ve seçin **özellikleri**).

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Vue.js web uygulaması projesi oluşturacaksınız.

1. LTS sürümü zaten yüklü olan bir Node.js çalışma zamanı yoksa, yükleme [Node.js](https://nodejs.org/en/download/) Web sitesi.

    Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayıp **Özellikler**' i seçin).

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **temel Vue. js**yazın ve ardından **temel Vue. js web uygulaması** (JavaScript veya Typescript) öğesini seçin. Görüntülenen iletişim kutusunda, **Basic-vuejs**adını yazın ve ardından **Oluştur**' u seçin.

    ![VUE.js şablonu](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**. **Yeni proje** iletişim kutusunun sol bölmesinde, **JavaScript** veya **TypeScript**' i genişletin ve **Node. js**' yi seçin. Orta bölmede, **temel Vue. js web uygulaması**' nı seçin, **Basic-vuejs**adını yazın ve ardından **Tamam**' ı seçin.

    ![VUE.js şablonu](../javascript/media/vuejs-template.png)
    ::: moniker-end
    **Temel Vue. js web uygulaması** proje şablonunu görmüyorsanız, **Node. js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni proje oluşturur. Yeni projeyi, Çözüm Gezgini'nde (sağ bölme) açar.

1. Uygulama için gerekli npm paketlerini yükleme ilerleme durumu için çıkış penceresine (alt bölme) denetleyin.

1. Çözüm Gezgini'nde açın **npm** düğümü ve tüm listelenen npm paketleri yüklü olduğundan emin olun.

    Tüm paketler (ünlem simgesi) eksikse, sağ tıklayabilirsiniz **npm** düğümünü seçip **eksik npm paketlerini yükle**.

## <a name="explore-the-ide"></a>IDE'yi keşfedin

1. Bir göz atın **Çözüm Gezgini** sağ bölmede.

     ![VUE.js çözümü](../javascript/media/vuejs-solution.png)

   - Kalın yazı tipinde vurgulanmış olduğu içinde verdiğiniz ad kullanarak projenize **yeni proje** iletişim kutusu. Disk üzerinde bu proje tarafından temsil edilen bir. *njsproj* proje klasörünüzdeki dosya.

   - En üst düzeyinde ve proje ile aynı ada sahip varsayılan bir çözümdür. Bir çözüm tarafından temsil edilen bir. *sln* dosya diskte, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - **Npm** düğüm tüm yüklü npm paketlerini gösterir. İçin arama yapın ve iletişim kutusunu kullanarak npm paketlerini yüklemek için npm düğümünü sağ tıklayabilirsiniz.

2. Npm paketlerini yükle veya bir komut istemi'nden Node.js komutları çalıştırmak, proje düğümüne sağ tıklayın ve seçin, isterseniz **burada açık komut istemi**.

## <a name="add-a-vue-file-to-the-project"></a>.Vue dosya projeye ekleyin.

1. Çözüm Gezgini, *src/Components* klasörü gibi bir klasöre sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.

1. Şunlardan birini seçin **JavaScript Vue tek dosya bileşen** veya **TypeScript Vue tek dosya bileşen**ve ardından **Ekle**.

    Visual Studio yeni dosyayı projeye ekler.

## <a name="build-the-project"></a>Proje derleme

1. (Yalnızca TypeScript Proje) Visual Studio'dan seçin **derleme** > **çözümü Temizle**.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' de bulunan TypeScript şablonunda, bu adımı atlayın.
    ::: moniker-end

1. Ardından, **derleme** > **Çözümü Derle** Projeyi derlemek için. Derleme sonuçlarını görmek için **Çıkış** penceresini kontrol edin ve **çıktıyı göster** listesinden **Oluştur** ' u seçin.

    JavaScript Vue. js proje şablonu (ve TypeScript şablonunun eski sürümleri) derleme sonrası olayını yapılandırarak `build` NPM betiğini kullanır. Bu ayarı değiştirmek istiyorsanız, proje dosyasını açın ( *\<projectname\>.njsproj*) Windows Gezgini'nden ve bu kod satırı bulun:

    ```xml
    <PostBuildEvent>npm run build</PostBuildEvent>
    ```

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Tuşuna **Ctrl**+**F5** (veya **hata ayıklama > hata ayıklama olmadan Başlat**) uygulamayı çalıştırın.

   Bir ileti görürsünüz konsolda *geliştirme sunucusu başlatma*.

   Ardından, uygulamayı bir tarayıcıda açılır.
   
   Çalışan uygulamayı görmüyorsanız, sayfayı yenileyin.

   ![Tarayıcıda çalışan Vue.js uygulama](../javascript/media/vuejs-running-app.png)

1. Web tarayıcısını kapatın.

Bu hızlı başlangıcı tamamladığınızda Tebrikler! Visual Studio IDE ile Vue.js kullanma hakkında biraz öğrenilen umuyoruz. Özelliklerini daha ayrıntılı olarak öğrenmek isterseniz, içindekiler tablosunun **öğreticiler** bölümünde öğreticiye devam edin.

## <a name="next-steps"></a>Sonraki adımlar

- Git aracılığıyla [Node.js ve Express Öğreticisi](tutorial-nodejs.md)
- Git aracılığıyla [Node.js ve React öğretici](tutorial-nodejs-with-react-and-jsx.md)
- [Uygulamayı Linux App Service'e dağıtma](../javascript/publish-nodejs-app-azure.md)