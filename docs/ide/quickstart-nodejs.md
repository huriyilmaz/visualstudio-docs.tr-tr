---
title: İlk Node.js uygulamanızı oluşturma
ms.custom: SEO-VS-2020
description: Bu hızlı başlangıçta, Visual Studio 'da bir Node.js uygulaması oluşturacaksınız
ms.date: 06/27/2018
ms.technology: vs-javascript
ms.topic: quickstart
ms.devlang: javascript
ms.assetid: b0e4ebed-1a01-41ef-aad1-4d8465ce5322
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: c342018a2331b27a411b5efc23af1438fa18518d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932624"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Hızlı başlangıç: ilk Node.js uygulamanızı oluşturmak için Visual Studio 'Yu kullanma

Bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (IDE) giriş yaptığınızda basit bir Node.js Web uygulaması oluşturacaksınız.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node.js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak zaten Visual Studio 'ya sahipseniz **Araçlar**  >  **ve Özellikler al.**.. ' a giderek Visual Studio yükleyicisi açılır. **Node.js geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.

    ![VS yükleyicisinde iş yükünü Node.js](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanının yüklü olması gerekir.

    Yüklü değilse, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yüklemenizi öneririz. Node.js, 32-bit ve 64-bit mimariler için oluşturulmuştur. Visual Studio 'daki Node.js araçları, Node.js iş yüküne dahil edilmiştir, her iki sürümü de destekler. Yalnızca bir tane gereklidir ve Node.js yükleyici yalnızca aynı anda yüklü olan birini destekler.
    
    Genel olarak, Visual Studio yüklü Node.js çalışma zamanını otomatik olarak algılar. Yüklü bir çalışma zamanı algılamazsa, projenizi Özellikler sayfasındaki yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz (bir proje oluşturduktan sonra proje düğümüne sağ tıklayın, **Özellikler**' i seçin ve **Node.exe yolunu** ayarlayın). Node.js genel bir yüklemesini kullanabilir veya Node.js projelerinizde her birinde yerel yorumlayıcı yolunu belirtebilirsiniz. 

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Node.js Web uygulaması projesi oluşturacaksınız.

1. Node.js çalışma zamanı zaten yüklü değilse, [Node.js](https://nodejs.org/en/download/) Web sitesinden LTS sürümünü yükleyebilirsiniz.

    Daha fazla bilgi için bkz. Önkoşullar.

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node.js** yazın ve sonra **Yeni boş Node.js Web uygulaması projesi** (JavaScript) öğesini seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan **Dosya**  >  **Yeni**  >  **Proje**' yi seçin. **Yeni proje** iletişim kutusunun sol bölmesinde **JavaScript**' i ve ardından **Node.js**' yi seçin. Orta bölmede, **Web uygulaması Node.js boş bırakın** ve **Tamam**' ı seçin.
    ::: moniker-end
    **Boş Node.js Web uygulaması** proje şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio, ve yeni çözüm oluşturur ve projeyi açar. *server.js* sol bölmedeki düzenleyicide açılır.

## <a name="explore-the-ide"></a>IDE 'yi keşfet

1. Sağ bölmedeki **Çözüm Gezgini** göz atın.

   ![Çözüm Gezgini](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Kalın olarak vurgulanmış, **Yeni proje** iletişim kutusunda verdiğiniz adı kullanarak projeniz. Disk üzerinde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir.

   - En üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - NPM düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilirsiniz.

1. Komut isteminden NPM paketleri veya Node.js komutları yüklemek isterseniz, proje düğümüne sağ tıklayın ve **komut Istemi 'Ni buradan aç**' ı seçin.

   ![Komut istemi Node.js](../ide/media/quickstart-nodejs-command-prompt.png)

1. Düzenleyicideki *server.js* dosyasında (sol bölme), `http.createServer` ardından **F12** tuşuna basın veya bağlam (sağ tıklama) menüsünde **Tanıma Git** ' i seçin. Bu komut sizi `createServer` *Dizin. d. TS* içindeki işlevin tanımına götürür.

   ![Tanım bağlam menüsüne git](../ide/media/quickstart-nodejs-gotodefinition.png)

1. *server.js* dönün, sonra imlecinizi bu kod satırındaki dizenin sonuna koyun `res.end('Hello World\n');` ve aşağıdaki gibi görünmesi için değiştirin:

    `res.end('Hello World\n' + res.connection.`

    Burada `connection.` , IntelliSense kod girişini otomatik olarak tamamlamaya yönelik seçenekler sağlar.

   ![IntelliSense otomatik tamamlamayı](../ide/media/quickstart-nodejs-intellisense.png)

1. **Localport** öğesini seçin ve ardından şunu yazarak ifadeyi şöyle olacak `);` şekilde doldurun:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1.  + Uygulamayı çalıştırmak için CTRL **F5** tuşuna basın (veya hata ayıklama **> başlatın**). Uygulama bir tarayıcıda açılır.

1. Tarayıcı penceresinde, "Merhaba Dünya" ve yerel bağlantı noktası numarasını görürsünüz.

1. Web tarayıcısını kapatın.

Tebrikler, Visual Studio IDE ve Node.js ile çalışmaya başladığınız bu hızlı başlangıcı tamamladım. Özelliklerini daha ayrıntılı olarak öğrenmek isterseniz, içindekiler tablosunun **öğreticiler** bölümünde öğreticiye devam edin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)

- [Node.js ve Express öğreticisi](../javascript/tutorial-nodejs.md)
- [Node.js ve tepki verme öğreticisi](../javascript/tutorial-nodejs-with-react-and-jsx.md)