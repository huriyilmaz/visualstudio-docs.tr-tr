---
title: "Hızlı başlangıç: ilk Node. js uygulamanızı oluşturmak için Visual Studio 'Yu kullanma"
description: Bu hızlı başlangıçta, Visual Studio 'da bir Node. js uygulaması oluşturacaksınız
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
ms.openlocfilehash: 4995c6b95ba12eb776130b17dab1911c47988871
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180335"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-nodejs-app"></a>Hızlı başlangıç: ilk Node. js uygulamanızı oluşturmak için Visual Studio 'Yu kullanma

Bu 5-10 dakikalık bir Visual Studio tümleşik geliştirme ortamına (IDE) giriş yaparken basit bir Node. js web uygulaması oluşturacaksınız.

## <a name="prerequisites"></a>Önkoşullar

* Visual Studio yüklü ve Node. js geliştirme iş yüküne sahip olmanız gerekir.

    ::: moniker range=">=vs-2019"
    Visual Studio 2019 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Visual Studio 2017 ' ü henüz yüklemediyseniz [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleyebilirsiniz.
    ::: moniker-end

    İş yükünü yüklemeniz gerekir, ancak Visual Studio zaten varsa, Visual Studio Yükleyicisi açılan **Araçlar ve Özellikler al** > **Araçlar** ' a gidin. Seçin **Node.js geliştirme** iş yükü, ardından **Değiştir**.

    ![Node.js iş yükü VS yükleyicisi](../ide/media/quickstart-nodejs-workload.png)

* Node.js çalışma zamanı yüklü olması gerekir.

    LTS sürümünden yüklü yoksa, yükleme [Node.js](https://nodejs.org/en/download/) Web sitesi. Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılayan değil, projenizi yüklü çalışma zamanı özellikleri sayfasında başvurmak için yapılandırabilirsiniz (bir proje oluşturduğunuzda, proje düğümüne sağ tıklayın ve seçin **özellikleri**).

## <a name="create-a-project"></a>Proje oluşturma

Önce bir Node. js web uygulaması projesi oluşturacaksınız.

1. LTS sürümü zaten yüklü olan bir Node.js çalışma zamanı yoksa, yükleme [Node.js](https://nodejs.org/en/download/) Web sitesi.

    Genel olarak, Visual Studio yüklü Node.js çalışma zamanı otomatik olarak algılar. Yüklü bir çalışma zamanı algılayan değil, projenizi yüklü çalışma zamanı özellikleri sayfasında başvurmak için yapılandırabilirsiniz (bir proje oluşturduğunuzda, proje düğümüne sağ tıklayın ve seçin **özellikleri**).

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturun.

    ::: moniker range=">=vs-2019"
    Başlangıç penceresini kapatmak için **ESC** tuşuna basın. **CTRL + Q** yazarak arama kutusunu açın, **Node. js**yazın ve ardından **Yeni boş Node. js web uygulaması projesi** (JavaScript) öğesini seçin. Görüntülenen iletişim kutusunda **Oluştur**' u seçin.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Üstteki menü çubuğundan seçin **dosya** > **yeni** > **proje**. **Yeni proje** iletişim kutusunun sol bölmesinde, **JavaScript**' i genişletin ve **Node. js**' yi seçin. Orta bölmede **boş Node. js web uygulaması**' nı seçin ve ardından **Tamam**' ı seçin.
    ::: moniker-end
    **Boş Node. js web uygulaması** proje şablonunu görmüyorsanız **Node. js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio oluşturur ve yeni çözüm ve proje açılır. *Server. js* , sol bölmedeki düzenleyicide açılır.

## <a name="explore-the-ide"></a>IDE'yi keşfedin

1. Bir göz atın **Çözüm Gezgini** sağ bölmede.

   ![Çözüm Gezgini](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Kalın yazı tipinde vurgulanmış olduğu içinde verdiğiniz ad kullanarak projenize **yeni proje** iletişim kutusu. Disk üzerinde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir.

   - En üst düzeyinde ve proje ile aynı ada sahip varsayılan bir çözümdür. Tarafından temsil edilen bir çözüm, bir *.sln* dosya diskte, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - NPM düğümü yüklü NPM paketlerini gösterir. İçin arama yapın ve iletişim kutusunu kullanarak npm paketlerini yüklemek için npm düğümünü sağ tıklayabilirsiniz.

1. Bir komut isteminden NPM paketleri veya Node. js komutları yüklemek isterseniz, proje düğümüne sağ tıklayın ve **komut Istemi 'Ni buradan aç**' ı seçin.

   ![Node. js komut istemi](../ide/media/quickstart-nodejs-command-prompt.png)

1. Düzenleyicideki *Server. js* dosyasında (sol bölme) `http.createServer` ve ardından **F12** tuşuna basın veya bağlam (sağ tıklama) menüsünde **Tanıma Git** ' i seçin. Bu komut sizi *Index. d. TS*içindeki `createServer` işlevinin tanımına götürür.

   ![Tanım bağlam menüsüne git](../ide/media/quickstart-nodejs-gotodefinition.png)

1. *Server. js*' ye geri dönün, sonra imlecinizi bu kod satırındaki dizenin sonuna yerleştirin, `res.end('Hello World\n');`ve aşağıdaki gibi görünmesi için değiştirin:

    `res.end('Hello World\n' + res.connection.`

    `connection.`yazdığınızda, IntelliSense kod girişini otomatik olarak tamamlamaya yönelik seçenekler sağlar.

   ![IntelliSense otomatik tamamlamayı](../ide/media/quickstart-nodejs-intellisense.png)

1. **Localport**öğesini seçin ve ardından `);` yazarak ifadeyi şöyle olacak şekilde doldurun:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-application"></a>Uygulamayı çalıştırma

1. Tuşuna **Ctrl**+**F5** (veya **hata ayıklama > hata ayıklama olmadan Başlat**) uygulamayı çalıştırın. Uygulama bir tarayıcıda açılır.

1. Tarayıcı penceresinde, "Merhaba Dünya" ve yerel bağlantı noktası numarasını görürsünüz.

1. Web tarayıcısını kapatın.

Tebrikler, Visual Studio IDE ve Node. js ile çalışmaya başladığınız bu hızlı başlangıcı tamamlama. Özelliklerini daha ayrıntılı olarak öğrenmek isterseniz, içindekiler tablosunun **öğreticiler** bölümünde öğreticiye devam edin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service'e dağıtma](../javascript/publish-nodejs-app-azure.md)

- [Node. js ve Express öğreticisi](../javascript/tutorial-nodejs.md)
- [Node. js ve tepki verme öğreticisi](../javascript/tutorial-nodejs-with-react-and-jsx.md)