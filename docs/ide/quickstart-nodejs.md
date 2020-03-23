---
title: "Quickstart: İlk Node.js uygulamanızı oluşturmak için Visual Studio'yı kullanın"
description: Bu hızlı başlangıçta, Visual Studio'da bir Düğüm.js uygulaması oluşturursunuz
ms.date: 06/27/2018
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: f716421da3b9f888dbb7656c55db6814de88332b
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "78235060"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Quickstart: İlk Node.js uygulamanızı oluşturmak için Visual Studio'yı kullanın

Visual Studio entegre geliştirme ortamı (IDE) için bu 5-10 dakikalık giriş, basit bir Node.js web uygulaması oluşturacaksınız.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node.js geliştirme iş yükünü yüklü olmalıdır.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019'u henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017'yi henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.
    ::: moniker-end

    İş yükünü yüklemeniz gerekiyorsa ancak visual studio'ya zaten sahipseniz, **Visual** > Studio Installer'ı açan**Araçlar Ve Özellikler...'** a gidin. **Düğüm.js geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.

    ![VS Yükleyici'de Düğüm.js iş yükü](../ide/media/quickstart-nodejs-workload.png)

* Düğüm.js çalışma saatini yüklemelisiniz.

    Yüklü değilse, dış çerçeveler ve kitaplıklarla en iyi uyumluluk için LTS sürümünü [Node.js](https://nodejs.org/en/download/) web sitesinden yüklemenizi öneririz. Node.js 32-bit ve 64-bit mimariler için inşa edilmiştir. Visual Studio'daki Düğüm.js iş yüküne dahil olan Düğüm.js araçları her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyicisi aynı anda yalnızca bir tanenin yüklenmesini destekler.
    
    Genel olarak, Visual Studio yüklenen Node.js çalışma süresini otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi özellikler sayfasındayüklü çalışma süresine başvuru yapacak şekilde yapılandırabilirsiniz (proje oluşturduktan sonra, proje düğümüne sağ tıklayın, **Özellikler'i**seçin ve **Düğüm.exe yolunu**ayarlayın). Node.js'nin genel yüklemesini kullanabilir veya Node.js projelerinizin her birinde yerel bir yorumlayıcıya giden yolu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Düğüm.js web uygulama projesi oluşturursunuz.

1. Node.js çalışma zamanı zaten yüklü değilse, [Node.js](https://nodejs.org/en/download/) web sitesinden LTS sürümünü yükleyin.

    Daha fazla bilgi için ön koşullara bakın.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **Esc** tuşuna basın. Arama kutusunu açmak için **Ctrl + Q** yazın, **Düğüm.js**yazın, ardından **yeni Boş Düğüm Oluştur Web uygulama projesi** (JavaScript) seçeneğini belirleyin. Görünen iletişim kutusunda **Oluştur'u**seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin. **Yeni Proje** iletişim kutusunun sol bölmesinde, **JavaScript**genişletmek, sonra **Node.js**seçin. Orta bölmede, **Boş Düğüm.js Web uygulamasını**seçin, ardından **Tamam'ı**seçin.
    ::: moniker-end
    **Boş Düğüm.js Web uygulaması** proje şablonu görmüyorsanız, Düğüm **geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı talimatlar için [Önkoşullar'a](#prerequisites)bakın.

    Visual Studio ve yeni bir çözüm oluşturur ve proje açılır. *server.js* sol bölmedeki düzenleyicide açılır.

## <a name="explore-the-ide"></a>IDE'yi keşfedin

1. Sağ bölmedeki **Çözüm Gezgini'ne** bir göz atın.

   ![Çözüm Gezgini](../ide/media/quickstart-nodejs-solution-explorer.png)

   - **Yeni Proje** iletişim kutusunda vermiş olduğunuz adı kullanarak projeniz kalın olarak vurgulanır. Diskte, bu proje proje klasörünüzde bir *.njsproj* dosyası yla temsil edilir.

   - En üst düzeyde varsayılan olarak projenizle aynı ada sahip bir çözüm vardır. Diskteki *bir .sln* dosyasıyla temsil edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - npm düğümü yüklü npm paketlerini gösterir. Bir iletişim kutusunu kullanarak npm paketlerini aramak ve yüklemek için npm düğümüne sağ tıklayabilirsiniz.

1. Bir komut isteminden npm paketleri veya Node.js komutları yüklemek istiyorsanız, proje düğümüne sağ tıklayın ve **Burada Komut İstemini Aç'ı**seçin.

   ![Düğüm.js komut istemi](../ide/media/quickstart-nodejs-command-prompt.png)

1. Düzenleyicideki *server.js* dosyasında (sol bölme) `http.createServer` **F12'yi** seçin ve ardından F12 tuşuna basın veya bağlam (sağ tıklatma) menüsünden **Tanıma Git'i** seçin. Bu komut sizi `createServer` *index.d.ts'deki*işlevin tanımına götürür.

   ![Tanım bağlamına git menüsü](../ide/media/quickstart-nodejs-gotodefinition.png)

1. *Server.js'ye*geri döndü, sonra imlecinizi bu kod `res.end('Hello World\n');`satırındaki dizenin sonuna koyun ve şuna benzeyecek şekilde değiştirin:

    `res.end('Hello World\n' + res.connection.`

    Yazdığınız `connection.`yerde, IntelliSense kod girişini otomatik olarak tamamlamak için seçenekler sağlar.

   ![IntelliSense otomatik tamamlama](../ide/media/quickstart-nodejs-intellisense.png)

1. **LocalPort'u**seçin `);` ve ardından deyimi şu na benzer şekilde tamamlamak için yazın:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **Ctrl**+**F5** (veya **Hata Ayıklama > Hata Ayıklama Olmadan Başlat)** tuşuna basın. Uygulama bir tarayıcıda açılır.

1. Tarayıcı penceresinde "Hello World" ve yerel bağlantı noktası numarasını görürsünüz.

1. Web tarayıcısını kapatın.

Visual Studio IDE ve Node.js ile başladığınız bu Quickstart'ı tamamladığınız için tebrikler. Yeteneklerini daha derinlemesine araştırmak istiyorsanız, içindekiler tablosunun **Öğreticiler** bölümünde bir öğretici ile devam edin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux Uygulama Hizmetine dağıtın](../javascript/publish-nodejs-app-azure.md)

- [Node.js ve Express için Öğretici](../javascript/tutorial-nodejs.md)
- [Node.js ve React için Öğretici](../javascript/tutorial-nodejs-with-react-and-jsx.md)