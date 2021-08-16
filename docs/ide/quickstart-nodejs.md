---
title: İlk Node.js oluşturma
ms.custom:
- vs-acquisition
- SEO-VS-2020
description: Bu hızlı başlangıçta, Visual Studio'de Node.js uygulama Visual Studio
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
ms.openlocfilehash: 0b9203d9e6f785bd652ccbb60fcecd45c030fdbdd84b05c835cc601d85c92fe2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412575"
---
# <a name="quickstart-create-your-first-nodejs-app-with-visual-studio"></a>Hızlı Başlangıç: Node.js ile ilk Visual Studio

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte basit bir Node.js oluşturabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Başlamadan önce, Visual Studio ortamınızı yükleyin ve Node.js ayarlayın.

### <a name="install-visual-studio"></a>Visual Studio'yu yükleme

::: moniker range=">=vs-2019"
Visual Studio 2019'Visual Studio yüklemediyebilirsiniz. [](https://visualstudio.microsoft.com/downloads)
::: moniker-end
::: moniker range="vs-2017"
Visual Studio 2017'de henüz yüklememişsinizdir, ücretsiz Visual Studio [](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) indirmeler sayfasına gidin.
::: moniker-end

### <a name="set-up-your-nodejs-environment"></a>Node.js ortamınızı ayarlama

Visual Studio, geliştirme aşamasında yaygın olarak kullanılan araçları yükleme dahil olmak üzere ortamınızı Node.js yardımcı olabilir.

1. Bu Visual Studio Araçlar Araçları ve **Özellikleri**  >  **Al'a gidin.**

1. Aşağıdaki Visual Studio Yükleyicisi iş yükünü seçin **Node.js iş** yükünü indirip yüklemek için Değiştir'i seçin. 

    ![Node.js iş yükü Visual Studio Yükleyicisi](../ide/media/quickstart-nodejs-workload.png)

1. Node.js çalışma zamanının LTS [sürümünü yükleyin.](https://nodejs.org/en/download/) Dış çerçeveler ve kitaplıklarla en iyi uyumluluk için LTS sürümünü öneririz.

    Node.js 32 bit ve 64 bit mimariler için tasarlanmıştır ancak Node.js yükleyicisi aynı anda yalnızca bir sürümün yüklü olduğunu destekler.

1. Bu Visual Studio çalışma zamanlarınızı algılamazsanız (genellikle algılar), projenizi yüklü çalışma zamanının başvurusu olacak şekilde yapılandırın:

   1. Projenizi [oluşturduk sonra](#create-your-app-project)proje düğümüne sağ tıklayın.

   1. **Özellikler'i** seçin ve **Node.exe ayarlayın.** Bir yerel yorumlayıcının Node.js yüklemesini kullanabilir veya her bir yerel yorumlayıcının yolunu Node.js belirtebilirsiniz.

## <a name="create-your-app-project"></a>Uygulama projenizi oluşturma

1. Henüz yüklememişsanız,Node.js çalışma zamanının LTS [sürümünü yükleyin.](https://nodejs.org/en/download/) Daha fazla bilgi için [önkoşullara bakın.](#prerequisites)

1. Visual Studio'yu açın.

1. Yeni bir proje oluşturma.

    ::: moniker range=">=vs-2019"

    1. Başlangıç penceresini kapatmak için **Esc** tuşuna basın.

    1. **Arama kutusunu açmak için Ctrl + Q** tuşlarına basın ve ardındanNode.js. ****

    1. **Boş Web Node.js (JavaScript) 'i seçin.** İletişim kutusunda Oluştur'a **seçin.**

    ::: moniker-end

    ::: moniker range="vs-2017"
    1. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

    1. Yeni Uygulama iletişim kutusunun sol **bölmesinde JavaScript Project** genişletin ve yeni **bir** Node.js. 

    1. Orta bölmede Boş Web **uygulaması'Node.js ve Tamam'ı** **seçin.**

    ::: moniker-end
    
    Blank **Node.js Web uygulaması** proje şablonunu görmüyorsanız, uygulama geliştirme iş yükünüNode.js **gerekir.** Ayrıntılı yönergeler için önkoşullara [bakın.](#prerequisites)

    Visual Studio projeyi oluşturur ve açar. Projeninserver.js *dosyası,* sol tarafta düzenleyicide açılır.

## <a name="explore-the-ide"></a>IDE'ye keşfetme

1. Sağ bölmede, **Çözüm Gezgini.**

   ![Çözüm Gezgini](../ide/media/quickstart-nodejs-solution-explorer.png)

   - Kalın yazıyla vurgulanan projeniz, projeyi ayarlayan ad kullanılarak sağlanır. Diskte, bu proje proje klasörünüzdeki *bir .njsproj* dosyasıyla temsil edildi.

   - En üst düzeyde, varsayılan olarak projeniz ile aynı adı alan bir çözümdür. Diskte bir *.sln dosyasıyla temsil* edilen çözüm, bir veya daha fazla ilgili proje için bir kapsayıcıdır.

   - **npm düğümü** yüklü npm paketlerini gösterir. npm düğümünü sağ tıklar ve bir iletişim kutusu kullanarak npm paketlerini arayabilir ve yükleyebilirsiniz.

1. Npm paketlerini yüklemek veya komut Node.js komutlarını yüklemek için proje düğümüne sağ tıklayın ve Komut İstemi'ne **Buradan Aç'ı seçin.**

   ![Node dot j s komut istemi](../ide/media/quickstart-nodejs-command-prompt.png)

1. Kaynak kodunda gezinmeyi test etmek için açık *server.js* **dosyasından http.createServer** öğesini seçin ve  **F12** tuşuna basın veya bağlam (sağ tıklama) menüsünden Tanıma Git'i seçin. Bu komut sizi `createServer` *http.d.ts'de işlevinin tanımına alır.*

   ![Tanıma Git bağlam menüsü](../ide/media/quickstart-nodejs-gotodefinition.png)

1. Geri dön *server.js* şu kod satırı bulun: `res.end('Hello World\n');` . Kodu şu şekilde değiştirme:

    `res.end('Hello World\n' + res.connection.`

    connection. **yazarak** IntelliSense, kod girişini otomatik olarak tamamlama seçenekleri sunar.

   ![IntelliSense otomatik tamamlama](../ide/media/quickstart-nodejs-intellisense.png)

1. **localPort'ı seçin** ve **yazın);** deyimini tamamlamak için:

    `res.end('Hello World\n' + res.connection.localPort);`

## <a name="run-the-app"></a>Uygulamayı çalıştırma

1. Uygulamayı **çalıştırmak için Ctrl+F5** **(veya** Hata Ayıklama Olmadan  >  Başlat) tuşlarına basın. 
 
   Uygulama bir tarayıcıda açılır.

1. Tarayıcıda bir "Merhaba Dünya" iletisi ve yerel bağlantı noktası numarası gördüğünüzden emin olun.

Tebrikler! Visual Studio ile Node.js basit bir Visual Studio. Daha fazla bilgi için **içindekiler'in** Öğreticiler bölümünde devam edin.

## <a name="next-steps"></a>Sonraki adımlar

> [!div class="nextstepaction"]
> [Uygulamayı Linux App Service](../javascript/publish-nodejs-app-azure.md)

> [!div class="nextstepaction"]
> [Node.js express öğreticisi](../javascript/tutorial-nodejs.md)

> [!div class="nextstepaction"]
> [Öğretici: Node.js ve React](../javascript/tutorial-nodejs-with-react-and-jsx.md)
