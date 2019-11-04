---
title: 'Hızlı başlangıç: ilk Vue. js uygulamanızı oluşturma'
description: Bu hızlı başlangıçta, Visual Studio için Node.js Araçları kullanarak Visual Studio 'da bir Vue. js uygulaması oluşturacaksınız
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
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Hızlı başlangıç: ilk Vue. js uygulamanızı oluşturmak için Visual Studio 'Yu kullanma

Visual Studio tümleşik geliştirme ortamına (IDE) bu 5-10 dakikalık bir giriş ile basit bir Vue. js web uygulaması oluşturacaksınız ve çalıştıracaksınız.

> [!IMPORTANT]
> Bu makale, Visual Studio 2017 sürüm 15,8 ' den itibaren kullanılabilen Vue. js şablonunu gerektirir.

## <a name="prerequisites"></a>Prerequisites

* Visual Studio yüklü ve Node. js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/)  page gidin ve ücretsiz olarak yüklemek için bu dosyayı açın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/)  page gidin ve ücretsiz olarak yüklemek için bu dosyayı açın.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan**Araçlar ve Özellikler al** >  **Araçlar** ' a gidin. **Node. js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![VS yükleyicisinde Node. js iş yükü](../ide/media/quickstart-nodejs-workload.png)

* Node. js çalışma zamanının yüklü olması gerekir.

    Yüklü değilse, [Node. js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz. Genel olarak, Visual Studio yüklü Node. js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayıp **Özellikler**' i seçin).

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Vue. js web uygulaması projesi oluşturacaksınız.

1. Node. js çalışma zamanı zaten yüklü değilse, [Node. js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz.

    Genel olarak, Visual Studio yüklü Node. js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayıp **Özellikler**' i seçin).

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **temel Vue. js**yazın ve ardından **temel Vue. js web uygulaması** (JavaScript veya Typescript) öğesini seçin. Görüntülenen iletişim kutusunda, **Basic-vuejs**adını yazın ve ardından **Oluştur**' u seçin.

    ![Vue. js şablonu](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **dosya**  > **Yeni**  > **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde, **JavaScript** veya **TypeScript**' i genişletin ve **Node. js**' yi seçin. Orta bölmede, **temel Vue. js web uygulaması**' nı seçin, **Basic-vuejs**adını yazın ve ardından **Tamam**' ı seçin.

    ![Vue. js şablonu](../javascript/media/vuejs-template.png)
    ::: moniker-end
    **Temel Vue. js web uygulaması** proje şablonunu görmüyorsanız, **Node. js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio yeni projeyi oluşturur. Yeni proje Çözüm Gezgini açılır (sağ bölme).

1. Uygulama için gereken NPM paketlerinin yüklenmesiyle ilgili ilerleme durumu için çıkış penceresini (alt bölme) denetleyin.

1. Çözüm Gezgini, **NPM** düğümünü açın ve listelenen tüm NPM paketlerinin yüklü olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **NPM** düğümüne sağ tıklayıp **eksik NPM paketlerini yüklemeyi**seçebilirsiniz.

## <a name="explore-the-ide"></a>IDE 'yi keşfet

1. Sağ bölmedeki **Çözüm Gezgini** göz atın.

     ![Vue. js çözümü](../javascript/media/vuejs-solution.png)

   - Kalın olarak vurgulanmış, **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projeniz. Diskte, bu proje bir ile temsil edilir. proje klasörünüzdeki *njsproj* dosyası.

   - En üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. İle temsil edilen bir çözüm. disk üzerindeki *sln* dosyası, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - **NPM** düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilirsiniz.

2. Bir komut isteminden NPM paketleri yüklemek veya Node. js komutlarını çalıştırmak istiyorsanız, proje düğümüne sağ tıklayın ve **burada komut Istemi aç**' ı seçin.

## <a name="add-a-vue-file-to-the-project"></a>Projeye bir. vue dosyası ekleyin

1. Çözüm Gezgini, *src/Components* klasörü gibi bir klasöre sağ tıklayın ve ardından > **Yeni öğe** **Ekle** ' yi seçin.

1. **JavaScript Vue tek dosya bileşeni** ya da **TypeScript Vue tek dosya bileşeni**' ni seçin ve ardından **Ekle**' ye tıklayın.

    Visual Studio, yeni dosyayı projeye ekler.

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

   Ardından, uygulama bir tarayıcıda açılır.
   
   Çalışan uygulamayı görmüyorsanız, sayfayı yenileyin.

   ![Tarayıcıda çalışan Vue. js uygulaması](../javascript/media/vuejs-running-app.png)

1. Web tarayıcısını kapatın.

Tebrikler, bu hızlı başlangıcı Tamamlanıyor! Vue. js ile Visual Studio IDE 'yi kullanmayla ilgili biraz bilgi edindiniz. Özelliklerini daha ayrıntılı olarak öğrenmek isterseniz, içindekiler tablosunun **öğreticiler** bölümünde öğreticiye devam edin.

## <a name="next-steps"></a>Sonraki adımlar

- [Node. js ve Express öğreticisine](tutorial-nodejs.md) gidin
- [Node. js öğreticisine gidin ve tepki](tutorial-nodejs-with-react-and-jsx.md) verin
- [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)