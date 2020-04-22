---
title: 'Quickstart: İlk Vue.js uygulamanızı oluşturun'
description: Bu hızlı başlangıçta, Visual Studio için Node.js Tools'u kullanarak Visual Studio'da bir Vue.js uygulaması oluşturursunuz.
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
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744980"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Quickstart: İlk Vue.js uygulamanızı oluşturmak için Visual Studio'yı kullanın

Visual Studio entegre geliştirme ortamı (IDE) için bu 5-10 dakikalık giriş, oluşturmak ve basit bir Vue.js web uygulaması çalıştırın.

> [!IMPORTANT]
> Bu makale, Visual Studio 2017 sürüm 15.8'den başlayarak kullanılabilen Vue.js şablonu gerektirir.

## <a name="prerequisites"></a>Ön koşullar

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

    Yüklü değilse, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için LTS sürümünü [Node.js](https://nodejs.org/en/download/) web sitesinden yüklemenizi öneririz. Node.js 32-bit ve 64-bit mimariler için inşa edilmiştir. Visual Studio'daki Düğüm.js iş yüküne dahil olan Düğüm.js araçları her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca bir tanenin yüklenmesini destekler.
    
    Genel olarak, Visual Studio yüklenen Node.js çalışma süresini otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi özellikler sayfasındayüklü çalışma süresine başvuru yapacak şekilde yapılandırabilirsiniz (proje oluşturduktan sonra, proje düğümüne sağ tıklayın, **Özellikler'i**seçin ve **Düğüm.exe yolunu**ayarlayın). Node.js'nin genel yüklemesini kullanabilir veya Node.js projelerinizin her birinde yerel bir yorumlayıcıya giden yolu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Vue.js web uygulama projesi oluşturursunuz.

1. Node.js çalışma zamanı zaten yüklü değilse, [Node.js](https://nodejs.org/en/download/) web sitesinden LTS sürümünü yükleyin.

    Daha fazla bilgi için ön koşullara bakın.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **Temel Vue.js**yazın, ardından **Temel Vue.js Web uygulamasını** (JavaScript veya TypeScript) seçin. Görünen iletişim kutusunda, **temel-vuejs**adını yazın ve sonra **Oluştur'u**seçin.

    ![Vue.js şablonu](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni Proje** iletişim kutusunun sol bölmesinde, **JavaScript** veya **TypeScript'i**genişletin, ardından **Düğüm.js'yi**seçin. Orta bölmede, **Temel Vue.js Web uygulamasını**seçin , adını **temel-vuejs**yazın , ve sonra **Tamam**seçin .

    ![Vue.js şablonu](../javascript/media/vuejs-template.png)
    ::: moniker-end
    **Temel Vue.js Web uygulaması** proje şablonu görmüyorsanız, Düğüm **geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı talimatlar için [Önkoşullar'a](#prerequisites)bakın.

    Visual Studio yeni projeyi oluşturur. Yeni proje Solution Explorer'da (sağ bölme) açılır.

1. Uygulama için gerekli npm paketlerini yükleme konusunda ilerleme kaydetmek için Çıktı penceresinde (alt bölme) denetleyin.

1. Çözüm Gezgini'nde **npm** düğümlerini açın ve listelenen tüm npm paketlerinin yüklü olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **npm** düğümüne sağ tıklayıp **Eksik npm Paketlerini Yükle'yi**seçebilirsiniz.

## <a name="explore-the-ide"></a>IDE'yi keşfedin

1. Sağ bölmedeki **Çözüm Gezgini'ne** bir göz atın.

     ![Vue.js çözümü](../javascript/media/vuejs-solution.png)

   - **Yeni Proje** iletişim kutusunda vermiş olduğunuz adı kullanarak projeniz kalın olarak vurgulanır. Diskte, bu proje bir . proje klasörünüzde *njsproj* dosyası.

   - En üst düzeyde varsayılan olarak projenizle aynı ada sahip bir çözüm vardır. Bir çözüm, bir . diskteki *sln* dosyası, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - **npm** düğümü yüklü npm paketlerini gösterir. Bir iletişim kutusunu kullanarak npm paketlerini aramak ve yüklemek için npm düğümüne sağ tıklayabilirsiniz.

2. NPM paketleri yüklemek veya Bir komut isteminden Düğüm.js komutlarını çalıştırmak istiyorsanız, proje düğümüne sağ tıklayın ve **Burada Komut İstemin'i Aç'ı**seçin.

## <a name="add-a-vue-file-to-the-project"></a>Projeye bir .vue dosyası ekleme

1. Çözüm Gezgini'nde, *src/components* klasörü gibi herhangi bir klasöre sağ tıklayın ve ardından**Yeni Öğe** **Ekle'yi** > seçin.

1. **JavaScript Vue Tek Dosya Bileşeni** veya **TypeScript Vue Tek Dosya Bileşeni'ni**seçin ve sonra **Ekle'yi**tıklatın.

    Visual Studio yeni dosyayı projeye ekler.

## <a name="build-the-project"></a>Projeyi derleme

::: moniker range=">=vs-2019"
1. Ardından, projeyi oluşturmak için **Yapı** > **Çözüm'üne** çözüm oluşturmayı seçin.

1. Yapı sonuçlarını görmek için **Çıktı** penceresini denetleyin ve **listeden çıktıyı göster'i** **seçin.**
::: moniker-end
::: moniker range="vs-2017"
1. (Yalnızca TypeScript projesi) Visual Studio'dan **Build** > **Clean Solution'ı**seçin.

1. Ardından, projeyi oluşturmak için **Yapı** > **Çözüm'üne** çözüm oluşturmayı seçin.

1. Yapı sonuçlarını görmek için **Çıktı** penceresini denetleyin ve **listeden çıktıyı göster'i** **seçin.**
::: moniker-end

JavaScript Vue.js proje şablonu (ve TypeScript şablonunun `build` eski sürümleri) bir post build olayı yapılandırarak npm komut dosyasını kullanır. Bu ayarı değiştirmek istiyorsanız, Windows Gezgini'nden proje dosyasını*\<(projeadı\>.njsproj)* açın ve bu kod satırını bulun:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **Ctrl**+**F5** (veya **Hata Ayıklama > Hata Ayıklama Olmadan Başlat)** tuşuna basın.

   Konsolda, *Geliştirme Sunucusu'nu Başlatan*bir ileti görürsünüz.

   Ardından, uygulama bir tarayıcıda açılır.
   
   Çalışan uygulamayı görmüyorsanız, sayfayı yenileyin.

   ![Vue.js uygulaması tarayıcıda çalışıyor](../javascript/media/vuejs-running-app.png)

1. Web tarayıcısını kapatın.

Bu Quickstart'ı tamamladığınız için tebrikler! Umarız Vue.js ile Visual Studio IDE'yi kullanmayı öğrenmişsinizdir. Yeteneklerini daha derinlemesine araştırmak istiyorsanız, içindekiler tablosunun **Öğreticiler** bölümünde bir öğretici ile devam edin.

## <a name="next-steps"></a>Sonraki adımlar

- [Vue.js](create-application-with-vuejs.md) için makale üzerinden gidin
- [Node.js ve Express için Öğretici](tutorial-nodejs.md) ile gidin
- [Uygulamayı Linux Uygulama Hizmetine dağıtın](../javascript/publish-nodejs-app-azure.md)