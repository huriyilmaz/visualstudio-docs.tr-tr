---
title: İlk Node.js uygulamanızı oluşturma
ms.custom:
- vs-acquisition
- SEO-VS-2020
description: Bu hızlı başlangıçta, Visual Studio Node.js bir uygulama oluşturacaksınız
ms.date: 03/25/2021
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
ms.openlocfilehash: 0c44bfcfe1e7f07f83ca2b7dbb8b0604f5efe5f1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635961"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Hızlı başlangıç: Visual Studio ile ilk Node.js uygulamanızı oluşturma

bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (ıde) giriş yaparken basit bir Node.js web uygulaması oluşturacaksınız.

## <a name="prerequisites"></a>Önkoşullar

başlamadan önce, Visual Studio yükleyip Node.js ortamınızı ayarlayın.

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range=">=vs-2019"
zaten 2019 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidin.
::: moniker-end
::: moniker range="vs-2017"
zaten 2017 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına gidin.
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Node.js ortamınızı ayarlama

Visual Studio, Node.js geliştirmeyle ortak araçlar yükleme dahil olmak üzere ortamınızı ayarlamanıza yardımcı olabilir.

1. Visual Studio ' **de araçlar**  >  **ve özellikler al**' a gidin.

1. Visual Studio Yükleyicisi, **Node.js geliştirme** iş yükünü seçin ve iş yükünü indirip yüklemek için **değiştir** ' i seçin.

    ![Visual Studio Yükleyicisi iş yükünü Node.js](../ide/media/quickstart-nodejs-workload.png)

1. [Node.js çalışma zamanının](https://nodejs.org/en/download/)LTS sürümünü yükler. LTS sürümünü, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için öneririz.

    Node.js, 32-bit ve 64-bit mimarilere yönelik olarak oluşturulmuştur, ancak Node.js yükleyicisi aynı anda yalnızca bir sürümü destekler.

1. Visual Studio yüklü çalışma zamanını algılamazsa (genel olarak), projenizi yüklü çalışma zamanına başvuracak şekilde yapılandırın:

   1. [Projenizi](#create-your-app-project)oluşturduktan sonra proje düğümüne sağ tıklayın.

   1. **Özellikler** ' i seçin ve **Node.exe yolunu** ayarlayın. Node.js genel bir yüklemesini kullanabilir veya Node.js projelerinizde her birinde yerel yorumlayıcı yolunu belirtebilirsiniz.

## <a name="create-your-app-project"></a>Uygulama projenizi oluşturma

1. Henüz yapmadıysanız, [Node.js çalışma zamanının](https://nodejs.org/en/download/)LTS sürümünü yükleyemezsiniz. Daha fazla bilgi için bkz. [Önkoşullar](#prerequisites).

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"

    1. Başlangıç penceresini kapatmak için **ESC** tuşuna basın.

    1. **CTRL + Q** tuşlarına basarak arama kutusunu açın ve **Node.js** yazın.

    1. **Boş Node.js Web uygulaması (JavaScript)** seçeneğini belirleyin. İletişim kutusunda **Oluştur**' u seçin.

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

    1. **yeni Project** iletişim kutusunun sol bölmesinde, **JavaScript** ' i genişletin ve **Node.js**' i seçin.

    1. Orta bölmede, **Web uygulaması Node.js boş** ve **Tamam**' ı seçin.

    ::: moniker-end
    
    **Boş Node.js Web uygulaması** proje şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Ayrıntılı yönergeler için bkz. [Önkoşullar](#prerequisites).

    Visual Studio projeyi oluşturur ve açar. Projenin *server.js* dosyası sol taraftaki düzenleyicide açılır.

## <a name="explore-the-ide"></a>IDE 'yi keşfet

1. Sağ bölmede **Çözüm Gezgini** bakın.

   ![Çözüm Gezgini](../ide/media/quickstart-nodejs-solution-explorer.png)

   - , Projeyi ayarlarken belirtilen adı kullanarak, kalın harfle vurgulanır. Disk üzerinde bu proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir.

   - En üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir çözümdür. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - **NPM** düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için NPM düğümüne sağ tıklayabilirsiniz.

1. Komut isteminden NPM paketleri veya Node.js komutları yüklemek isterseniz, proje düğümüne sağ tıklayın ve **komut Istemi 'Ni buradan aç**' ı seçin.

   ![Düğüm nokta j s komut istemi](../ide/media/quickstart-nodejs-command-prompt.png)

1. Kaynak koda gezinmeyi test etmek isterseniz, açık *server.js* dosyasından **http. CreateServer** ' ı seçin ve **F12** tuşuna basın veya bağlam (sağ tıklama) menüsünde **Tanıma Git** ' i seçin. Bu komut sizi `createServer` *http. d. TS* içindeki işlevin tanımına götürür.

   ![Tanım bağlam menüsüne git](../ide/media/quickstart-nodejs-gotodefinition.png)

1. *server.js* geri dönüp bu kod satırını bulun: `res.end('Hello World\n');` . Kodu şu şekilde değiştirin:

    `res.end('Hello World\n' + res.connection.`

    **Bağlantı** yazdığınızda, IntelliSense kod girişini otomatik olarak tamamlamaya yönelik seçenekler sağlar.

   ![IntelliSense otomatik tamamlamayı](../ide/media/quickstart-nodejs-intellisense.png)

1. **Localport** ve Type öğesini seçin **);** ifadeyi gerçekleştirmek için:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Uygulamayı çalıştırmak için **CTRL + F5** tuşuna basın **(veya hata ayıklama**  >  **olmadan Başlat**). 
 
   Uygulama bir tarayıcıda açılır.

1. Tarayıcıda bir "Merhaba Dünya" iletisi ve yerel bağlantı noktası numarasını görmediğinizi doğrulayın.

Tebrikler! Visual Studio olan basit bir Node.js uygulaması oluşturdunuz. Daha ayrıntılı bir şekilde, içerik tablosunun **öğreticiler** bölümünde devam edin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Node.js ve Express öğreticisi](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Node.js ve React öğreticisi](../javascript/tutorial-nodejs-with-react-and-jsx.md)
