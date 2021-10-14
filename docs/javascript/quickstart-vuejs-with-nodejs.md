---
title: 'Hızlı Başlangıç: İlk Vue.js oluşturma'
description: Bu hızlı başlangıçta, Visual Studio tools for Vue.js kullanarak Node.js bir Visual Studio
ms.date: 10/31/2019
ms.topic: quickstart
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
monikerRange: <= vs-2019
ms.openlocfilehash: 54752b44463b14ee0619300277bfc388abfd4203
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129970860"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-vuejs-app"></a>Hızlı Başlangıç: Visual Studio uygulama oluşturmak için Vue.js kullanma

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte basit bir web uygulaması Vue.js çalıştırabilirsiniz.

> [!IMPORTANT]
> Bu makale, Vue.js 2017 sürüm 15.8'Visual Studio başlayarak kullanılabilen Visual Studio şablonunu gerektirir.

## <a name="prerequisites"></a>Önkoşullar

* Uygulama ve Visual Studio iş yükünün yüklü Node.js gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'Visual Studio yüklemediyebilirsiniz. [](https://visualstudio.microsoft.com/downloads/)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'de henüz yüklememişsinizdir, ücretsiz Visual Studio [indirmeler](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekse ama zaten Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Geliştirme iş **Node.js seçin** ve ardından Değiştir'i **seçin.**

    ![Node.js Yükleyicisi'ne iş yükü yükleme](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma Node.js gerekir.

    Yüklü yoksa, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için [ LTS ](https://nodejs.org/en/download/) sürümünüNode.jsweb sitesinden yüklemenizi öneririz. Node.js 32 bit ve 64 bit mimariler için tasarlanmıştır. Node.js iş yüküne dahil Visual Studio tüm Node.js iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca birinin yüklü olduğunu destekler.
    
    Genel olarak, Visual Studio çalışma zamanı otomatik olarak Node.js algılar. Yüklü bir çalışma zamanı algılanmazsa, projenizi özellikler sayfasında yüklü çalışma zamanının başvurusu için yapılandırabilirsiniz (bir proje oluşturduk sonra proje düğümüne sağ tıklayın, Özellikler'i seçin veNode.exe **yolunu ayarlayın).** Bir uygulamanın genel yüklemesini Node.js veya her bir yerel yorumlayıcının yolunu belirterek Node.js belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir web uygulaması Vue.js oluşturabilirsiniz.

1. Node.js çalışma zamanı yüklü değilse,Node.jsweb [ sitesinden ](https://nodejs.org/en/download/) LTS sürümünü yükleyin.

    Daha fazla bilgi için önkoşullara bakın.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama **kutusunu açmak için Ctrl + Q** tuşlarına basın, Temel **Vue.js** yazın ve temel web uygulaması (JavaScript Vue.js TypeScript) seçin.  Görüntülenen iletişim kutusuna **basic-vuejs** adını yazın ve Oluştur'u **seçin.**

    ![Vue.js şablonu](../javascript/media/vs-2019/vuejs-template.png)
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan Dosya Yeni **Dosya'Project.**  >    >   Yeni Giriş iletişim kutusunun sol **bölmesinde JavaScript**  Project **TypeScript'i** genişletin ve ardından Yeni'yi **Node.js.** Orta bölmede Temel web **uygulaması'Vue.js seçin,** **basic-vuejs** adını yazın ve tamam'ı **seçin.**

    ![Vue.js şablonu](../javascript/media/vuejs-template.png)
    ::: moniker-end
    Temel Web uygulaması Vue.js **proje şablonunu** görmüyorsanız, uygulama geliştirme iş yükünüNode.js **eklemeniz** gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar.](#prerequisites)

    Visual Studio yeni projeyi oluşturur. Yeni proje bir Çözüm Gezgini (sağ bölme) açılır.

1. Uygulama için gereken npm paketlerinin yükleme ilerleme durumu için Çıkış penceresini (alt bölme) kontrol edin.

1. Bu Çözüm Gezgini **npm düğümünü** açın ve listelenen tüm npm paketlerinin yüklü olduğundan emin olun.

    Herhangi bir paket eksikse (ünlem işareti simgesi), **npm** düğümüne sağ tıklar ve Eksik npm Paketlerini **Yükle'yi seçebilirsiniz.**

## <a name="explore-the-ide"></a>IDE'ye keşfetme

1. Sağ bölmede **Çözüm Gezgini** göz atabilirsiniz.

     ![Vue.js çözümü](../javascript/media/vuejs-solution.png)

   - Yeni Çalışma Alanı iletişim kutusunda verdiği ad kullanılarak projeniz **kalın Project** vurgulanır. Diskte, bu proje bir ile temsil edildi. *proje klasörünüzdeki njsproj* dosyası.

   - En üst düzeyde, varsayılan olarak projenizin adıyla aynı adı alan bir çözümdür. bir ile temsil edilen bir çözüm. *diskte sln* dosyası, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - npm **düğümü** yüklü npm paketlerini gösterir. npm düğümünü sağ tıklar ve bir iletişim kutusu kullanarak npm paketlerini arayabilir ve yükleyebilirsiniz.

2. npm paketlerini yüklemek veya komut Node.js komutlarını çalıştırmak için proje düğümüne sağ tıklayın ve Komut İstemi'ne **Buradan Aç'ı seçin.**

## <a name="add-a-vue-file-to-the-project"></a>Projeye bir .vue dosyası ekleme

1. Bu *Çözüm Gezgini, src/components* klasörü gibi herhangi bir klasöre sağ tıklayın ve ardından Yeni Öğe **Ekle'yi**  >  **seçin.**

1. **JavaScript Vue Tek Dosya Bileşeni'ne veya** **TypeScript Vue Tek Dosya Bileşeni'ne ve** ardından Ekle'ye **tıklayın.**

    Visual Studio yeni dosyayı projeye ekler.

## <a name="build-the-project"></a>Projeyi derleme

::: moniker range=">=vs-2019"
1. Ardından,  projeyi > **derlemek için Derleme Çözümü'ne** seçin.

1. Derleme sonuçlarını **görmek** için Çıkış penceresini kontrol edin ve **Çıktıyı** göster **listesinden Derleme'yi** seçin.
::: moniker-end
::: moniker range="vs-2017"
1. (Yalnızca TypeScript projesi) Bu Visual Studio Temiz Çözüm  > **Derleme'yi seçin.**

1. Ardından,  projeyi > **derlemek için Derleme Çözümü'ne** seçin.

1. Derleme sonuçlarını **görmek** için Çıkış penceresini kontrol edin ve **Çıktıyı** göster **listesinden Derleme'yi** seçin.
::: moniker-end

JavaScript Vue.js proje şablonu (ve TypeScript şablonunun eski sürümleri) derleme sonrası olayı yapılandırarak `build` npm betiği kullanır. Bu ayarı değiştirmek istediğiniz proje dosyasını (*\<projectname\> .njsproj*) Windows Explorer'dan açın ve şu kod satırı bulun:

```xml
<PostBuildEvent>npm run build</PostBuildEvent>
```

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı **çalıştırmak için Ctrl** + **F5** **(veya > Hata** Ayıklama Olmadan Başlat) tuşlarına basın.

   konsolunda, Geliştirme Sunucusunu Başlatan *bir ileti görüyorsunuz.*

   Ardından uygulama bir tarayıcıda açılır.
   
   Çalışan uygulamayı görmüyorsanız sayfayı yenileyin.

   ![Vue.js çalışan bir uygulama](../javascript/media/vuejs-running-app.png)

1. Web tarayıcısını kapatın.

Tebrikler, bu Hızlı Başlangıç'a devam ediyoruz! Visual Studio IDE'nin Vue.js. Özelliklerini daha derinlemesine öğrenmek için içindekiler tablosundaki Öğreticiler **bölümünde** yer alan öğreticiye devam edin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Vue.js oluşturma](create-application-with-vuejs.md)

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service'a dağıtma](../javascript/publish-nodejs-app-azure.md)