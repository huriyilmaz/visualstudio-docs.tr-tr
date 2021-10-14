---
title: İlk Node.js uygulamanızı oluşturma
ms.custom:
- vs-acquisition
description: Bu hızlı başlangıçta, Visual Studio Node.js bir uygulama oluşturacaksınız
ms.date: 09/14/2021
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
ms.openlocfilehash: c95e8aa7daa93fee7c2cc4e27ed21c377d62afbf
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971614"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Hızlı başlangıç: Visual Studio ile ilk Node.js uygulamanızı oluşturma

bu 5-10 dakika içinde Visual Studio tümleşik geliştirme ortamına (ıde) giriş yaparken basit bir Node.js web uygulaması oluşturursunuz.

## <a name="prerequisites"></a>Önkoşullar

başlamadan önce, Visual Studio yükleyip Node.js ortamınızı ayarlayın.

::: moniker range=">=vs-2022"
### <a name="install-visual-studio-and-the-nodejs-workload"></a>Visual Studio ve Node.js iş yükünü yükleyip

Henüz Visual Studio yüklemediyseniz:

1. Visual Studio 2022 ' ü ücretsiz yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidin.

1. Visual Studio Yükleyicisi, **Node.js geliştirme** iş yükünü seçin ve ardından **yükler**' i seçin.

   ![Visual Studio Yükleyicisi seçili düğüm j iş yükünü gösteren ekran görüntüsü.](../ide/media/quickstart-nodejs-workload.png)

zaten yüklüyse Visual Studio.

1. Visual Studio ' **de araçlar** > **ve özellikler al**' a gidin.

1. Visual Studio Yükleyicisi, **Node.js geliştirme** iş yükünü seçin ve iş yükünü indirmek ve yüklemek için **değiştir** ' i seçin.

### <a name="set-up-your-nodejs-environment"></a>Node.js ortamınızı ayarlama

[Node.js çalışma zamanının LTS sürümünü yükler](https://nodejs.org/en/download/). LTS sürümü, diğer çerçeveler ve kitaplıklarla en iyi uyumluluğu içerir.

Node.js, 32-bit ve 64-bit mimarilere yönelik olarak oluşturulmuştur, ancak Node.js yükleyici aynı anda yalnızca bir sürümü destekler.

Visual Studio genellikle yüklü çalışma zamanını algılar, ancak yoksa, projenizi yüklü çalışma zamanına başvuracak şekilde yapılandırabilirsiniz:

   1. [Projenizi](#create-your-app-project)oluşturduktan sonra proje düğümüne sağ tıklayın.

   1. **Özellikler**' i seçin ve **Node.exe yolunu** ayarlayın. Genel bir Node.js yüklemesi kullanabilir veya herhangi bir Node.js projesi için yerel yorumlayıcı yolunu belirtebilirsiniz.

:::moniker-end
::: moniker range="vs-2019"
### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

zaten 2019 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına gidin.
::: moniker-end
::: moniker range="vs-2017"
### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

zaten 2017 Visual Studio yüklemediyseniz, ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına gidin.
::: moniker-end

::: moniker range="<=vs-2019"
### <a name="set-up-your-nodejs-environment"></a>Node.js ortamınızı ayarlama

Visual Studio, Node.js geliştirmeyle ortak araçlar yükleme dahil olmak üzere ortamınızı ayarlamanıza yardımcı olabilir.

1. Visual Studio ' **de araçlar** > **ve özellikler al**' a gidin.

1. Visual Studio Yükleyicisi, **Node.js geliştirme** iş yükünü seçin ve iş yükünü indirip yüklemek için **değiştir** ' i seçin.

    ![Visual Studio Yükleyicisi seçili düğüm J iş yükünü gösteren ekran görüntüsü.](../ide/media/quickstart-nodejs-workload.png)

1. [Node.js çalışma zamanının](https://nodejs.org/en/download/)LTS sürümünü yükler. LTS sürümünü, dış çerçeveler ve kitaplıklar ile en iyi uyumluluk için öneririz.

    Node.js, 32-bit ve 64-bit mimarilere yönelik olarak oluşturulmuştur, ancak Node.js yükleyicisi aynı anda yalnızca bir sürümü destekler.

1. Visual Studio yüklü çalışma zamanını algılamazsa (genel olarak), projenizi yüklü çalışma zamanına başvuracak şekilde yapılandırın:

   1. [Projenizi](#create-your-app-project)oluşturduktan sonra proje düğümüne sağ tıklayın.

   1. **Özellikler** ' i seçin ve **Node.exe yolunu** ayarlayın. Node.js genel bir yüklemesini kullanabilir veya Node.js projelerinizde her birinde yerel yorumlayıcı yolunu belirtebilirsiniz.

::: moniker-end
## <a name="create-your-app-project"></a>Uygulama projenizi oluşturma

Visual Studio, yeni bir Node.js projesi oluşturun.

::: moniker range=">=vs-2022"

1. Visual Studio başlatın ve sonra başlangıç penceresini kapatmak için **Esc** tuşuna basın.

1. **CTRL** + **Q** tuşlarına basın ve arama kutusuna *node.js* yazın.

1. **Boş Node.js Web uygulaması**' nı seçin.

1. İletişim kutusunda **Oluştur**' u seçin.

::: moniker-end

::: moniker range="vs-2019"

1. Başlangıç penceresini kapatmak için **ESC** tuşuna basın.

1. **CTRL + Q** tuşlarına basarak arama kutusunu açın ve **Node.js** yazın.

1. **Boş Node.js Web uygulaması (JavaScript)** seçeneğini belirleyin. İletişim kutusunda **Oluştur**' u seçin.

::: moniker-end

::: moniker range="vs-2017"
1. üstteki menü çubuğundan **dosya** > **yeni** > **Project** öğesini seçin.

1. **yeni Project** iletişim kutusunun sol bölmesinde, **JavaScript** ' i genişletin ve **Node.js**' i seçin.

1. Orta bölmede, **Web uygulaması Node.js boş** ve **Tamam**' ı seçin.

::: moniker-end
Visual Studio projeyi oluşturur ve açar. Projenin *server.js* dosyası düzenleyicide açılır.

**Boş Node.js Web uygulaması** proje şablonunu görmüyorsanız, **Node.js geliştirme** iş yükünü eklemeniz gerekir. Yönergeler için bkz. [Önkoşullar](#prerequisites).

## <a name="explore-the-ide"></a>IDE 'yi keşfet

::: moniker range=">=vs-2022"
Visual Studio, Node.js geliştirmeyle ortak araçlar yükleme dahil olmak üzere ortamınızı ayarlamanıza yardımcı olabilir.

1. Sağ bölmede **Çözüm Gezgini** bakın.
   
   - En üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir *çözümdür*. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.
   - Projeniz, ayarladığınızda kullandığınız ada sahip kalın olarak vurgulanır. Disk üzerinde proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir.
   - **NPM** düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için **NPM** düğümüne sağ tıklayabilirsiniz.

   ![Çözüm Gezgini bölmesini gösteren ekran görüntüsü.](../ide/media/vs-2022/quickstart-nodejs-solution-explorer.png)

1. Komut isteminden NPM paketleri veya Node.js komutları yüklemek için, proje düğümüne sağ tıklayın ve **komut Istemi 'Ni buradan aç**' ı seçin.

   ![Proje bağlam menüsünde Aç komut Istemi ' ni gösteren ekran görüntüsü.](../ide/media/vs-2022/quickstart-nodejs-command-prompt.png)

1. Kaynak koda gezinmeyi test etmek için, açma *server.js* dosyasında, `createServer` **F12** tuşuna basın veya sağ tıklayın `createServer` ve bağlam menüsünden **Tanıma Git** ' i seçin. Bu komut sizi `createServer` *http. d. TS* içindeki işlevin tanımına götürür.

   ![CreateServer bağlam menüsünde tanıma git gösteren ekran görüntüsü.](../ide/media/vs-2022/quickstart-nodejs-go-to-definition.png)

1. *server.js*, bu kod satırını bulun `res.end('Hello World\n');` ve şu şekilde değiştirin:

   `res.end('Hello World\n' + res.connection.`

   Yazdığınızda `connection.` , IntelliSense kod girişini otomatik tamamlamayı sağlayan seçenekler sağlar.

   ![IntelliSense otomatik tamamlanma seçeneklerini gösteren ekran görüntüsü.](../ide/media/vs-2022/quickstart-nodejs-intellisense.png)

1. `localPort`İfadeyi seçin ve yazın `);` :

    `res.end('Hello World\n' + res.connection.localPort);`

::: moniker-end

::: moniker range="<=vs-2019"
1. Sağ bölmede **Çözüm Gezgini** bakın.
   
   - En üst düzeyde, varsayılan olarak projenizle aynı ada sahip olan bir *çözümdür*. Disk üzerinde *. sln* dosyası tarafından temsil edilen bir çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.
   - Projeniz, ayarladığınızda kullandığınız ada sahip kalın olarak vurgulanır. Disk üzerinde proje, proje klasörünüzdeki bir *. njsproj* dosyası tarafından temsil edilir.
   - **NPM** düğümü yüklü NPM paketlerini gösterir. Bir iletişim kutusu kullanarak NPM paketlerini aramak ve yüklemek için **NPM** düğümüne sağ tıklayabilirsiniz.

   ![Çözüm Gezgini bölmesini gösteren ekran görüntüsü.](../ide/media/quickstart-nodejs-solution-explorer.png)

1. Komut isteminden NPM paketleri veya Node.js komutları yüklemek için, proje düğümüne sağ tıklayın ve bağlam menüsünden **komut istemi 'Ni aç** ' ı seçin.

   ![Proje bağlam menüsünde Aç komut Istemi ' ni gösteren ekran görüntüsü.](../ide/media/quickstart-nodejs-command-prompt.png)

1. Kaynak koda gezinmeyi test etmek için, açık *server.js* dosyasında **http. CreateServer** ' ı seçin ve **F12** tuşuna basın veya sağ tıklama bağlam menüsünden **Tanıma Git** ' i seçin. Bu komut sizi `createServer` *http. d. TS* içindeki işlevin tanımına götürür.

   ![CreateServer bağlam menüsünde tanıma git gösteren ekran görüntüsü.](../ide/media/quickstart-nodejs-gotodefinition.png)

1. *server.js*, bu kod satırını bulun `res.end('Hello World\n');` ve şu şekilde değiştirin:

   `res.end('Hello World\n' + res.connection.`

   **Bağlantı** yazdığınızda, IntelliSense kod girişini otomatik tamamlamayı sağlayan seçenekler sağlar.

   ![IntelliSense otomatik tamamlanma seçeneklerini gösteren ekran görüntüsü.](../ide/media/quickstart-nodejs-intellisense.png)

1. **Localport**' ı seçin ve ardından `);` ifadesini yazın:

    `res.end('Hello World\n' + res.connection.localPort);`
:::moniker-end

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1.  + Uygulamayı çalıştırmak için CTRL **F5** tuşuna basın veya **hata ayıklama**  >  **olmadan Başlat** ' ı seçin.
 
   Uygulama bir tarayıcıda açılır.

1. Tarayıcıda **Merhaba Dünya** bir ileti ve yerel bağlantı noktası numarasını görmediğinizi doğrulayın.

Tebrikler! Visual Studio olan basit bir Node.js uygulaması oluşturdunuz. Daha ayrıntılı bir şekilde, içerik tablosunun **öğreticiler** bölümüne geçin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux 'a dağıtma App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Node.js ve Express öğreticisi](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Node.js ve React öğreticisi](../javascript/tutorial-nodejs-with-react-and-jsx.md)

