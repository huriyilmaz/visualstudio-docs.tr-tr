---
title: React ile ASP.NET Core uygulama oluşturma
description: Bu öğreticide, ASP.NET Core ve React
ms.date: 01/28/2022
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
monikerRange: '>= vs-2022'
ms.openlocfilehash: 683ea6e92afe2f0720c3feb21e391f6c83fd39db
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886779"
---
# <a name="tutorial-create-an-aspnet-core-app-with-react-in-visual-studio"></a>Öğretici: ASP.NET Core'de React uygulama Visual Studio

Bu makalede, API arka ucu gibi davranacak bir ASP.NET Core projesi ve kullanıcı arabirimi olarak React bir React projesi derlemeyi öğrenirsiniz.

Şu anda, Visual Studio ve ASP.NET Core destekleyen Tek Sayfalı Uygulama (SPA) Angular (SPA) React. Şablonlar, her çerçevenin temel dosyalarını ve klasörlerini içeren ASP.NET Core projelerinde yerleşik bir İstemci Uygulaması klasörü sağlar.

2022 Visual Studio 2022 Preview 2'den başlayarak, şu tek sayfalı uygulamaları oluşturmak ASP.NET Core bu makalede açıklanan yöntemi kullanabilirsiniz:

- İstemci uygulamasını, istemci projesinin dışında ayrı bir ASP.NET Core koyma
- Bilgisayarınızda yüklü olan çerçeve CLI'sini temel alarak istemci projesini oluşturma

> [!NOTE]
> Şu anda ön uç projesinin el ile yayımlanır (şu anda Yayımla aracıyla desteklenmiyor). Daha fazla bilgi için bkz. [https://github.com/MicrosoftDocs/visualstudio-docs/issues/7135](https://github.com/MicrosoftDocs/visualstudio-docs/issues/7135).

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio ve web geliştirme iş yükünün yüklü olduğu **ASP.NET** 2022 veya sonraki bir sürümü yükleyin. Ücretsiz yüklemek [Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
  İş yükünü yüklemeniz ve önceden yüklemeniz gerekirse Visual Studio Araçları ve  >  Özellikleri... edin...'e gidin ve Visual Studio Yükleyicisi. Web geliştirme **ASP.NET iş yükünü ve ardından** Değiştir'i **seçin**.
- npm ()[https://www.npmjs.com/](https://www.npmjs.com/package/npm)), bu, Node.js
- npx ([https://www.npmjs.com/package/npx](https://www.npmjs.com/package/npx))

## <a name="create-the-frontend-app"></a>Ön uç uygulamasını oluşturma

1. Yeni Proje Oluştur Project Yeni proje **oluştur'a seçin**. 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. Üst React arama çubuğundan Tek Başına **JavaScript** Komut Şablonu'React seçin. (Tek başına TypeScript React Şablonu şu anda bu öğreticide desteklenmiyor.)

   :::image type="content" source="media/vs-2022/react-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad girin. Ek bilgiler penceresine **bakarak** Boş web **API'si** ASP.NET tümleştirmesi ekle seçeneğini Project olun. Bu seçenek, daha sonra React projeyle bağlanacak şekilde dosya şablonunuz ASP.NET Core ekler.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-additional-info.png" alt-text="Ek bilgi":::

   Proje oluşturulduktan sonra bazı yeni ve değiştirilmiş dosyalar görüyorsunuz:

   - aspnetcore-https.js
   - aspnetcore-react.js
   - setupProxy.js
   - App.js (değiştirilmiş)
   - App.test.js (değiştirilmiş)

1. Hata Ayıklama araç çubuğunda Chrome veya Microsoft Edge gibi yüklü bir tarayıcı seçin.

   İstediğiniz tarayıcı henüz yüklenmemişse önce tarayıcıyı yükleyin ve seçin.

## <a name="create-the-backend-app"></a>Arka uç uygulamasını oluşturma

1. Çözüm gezgininde, çözüm adına sağ tıklayın, Ekle'nin üzerine **gelin ve** yeni **çözüm Project.** 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Yeni proje ekleme":::

1. ASP.NET Core Web API'si projesini arama ve seçme.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Web API şablonunu seçme":::

1. Projenize ve çözümünüze bir ad girin. Ek bilgiler penceresine **ulaşarak hedef** çerçeveniz **olarak .NET 6.0'ı** seçin.

   Proje oluşturulduktan sonra Çözüm Gezgini şu şekilde olması gerekir:

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-solution-explorer.png" alt-text="Çözüm Gezgini":::

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. ASP.NET Core projesine sağ tıklayın ve Özellikler'i **seçin**.

   :::image type="content" source="media/vs-2022/asp-net-core-project-properties.png" alt-text="Proje özelliklerini açma"::: 

1. Hata ayıkla menüsüne gidin ve Hata ayıklama **başlatma profilleri kullanıcı arabirimini aç seçeneğini** belirleyin. Tarayıcıyı Başlat **seçeneğinin işaretini** kaldırın.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-deselect-launch-browser.png" alt-text="Hata ayıklama başlatma profilleri kullanıcı arabirimini açma"::: 

1. Ardından, React projesine sağ tıklayın, **Özellikler menüsünü seçin** ve Hata Ayıklama **bölümüne** gidin. Debugger'ı **launch.json seçeneğiyle değiştirebilirsiniz** .

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-choose-debugger.png" alt-text="Hata ayıklayıcısını (launch.json) seçin":::

## <a name="set-the-startup-project"></a>Başlangıç projesini ayarlama

1. Çözüme sağ tıklayın ve Başlangıç Ayarlarını **Ayarla'yı Project**. Tek başlangıç projesi olan başlangıç projesini Birden çok başlangıç **projesi olarak değiştirme**. Her **projenin** eylemi için Başlat'ı seçin.
  
1. Ardından, arka uç projesini seçin ve ön ucun üzerine taşıarak ilk olarak başlamayı seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-startup-project.png" alt-text="Başlangıç projesini seçin":::

## <a name="start-the-project"></a>Projeyi başlatma

1. Projeyi başlatmadan önce bağlantı noktası numaralarının eş olduğundan emin olun. ASP.NET Core *projenizin launchSettings.json* dosyasına gidin (*Özellikler klasöründe*). özelliğinden bağlantı noktası numarasını `applicationUrl` almak.

   Birden çok özellik varsa `applicationUrl` , uç nokta kullanarak bir tane olup bakabilirsiniz `https` . şuna benzer şekilde görünüyor olabilir `https://localhost:7049`: .

1. Ardından, *setupProxy.jsprojenizin* React (*src klasörüne* bakın) gidin. *launchSettings.json'daki özelliğiyle eşleşmesi için hedef özelliği güncelleştirin*.`applicationUrl` Güncelleştirin, bu değerin şuna benzer olması gerekir:

   ```js
   target: 'https://localhost:7049',
   ```

1. Projeyi başlatmak için **F5 tuşuna** basın veya **pencerenin** üst kısmından Başlat düğmesini seçin. İki komut istemi görüntülenir:

   - Çalışan ASP.NET Core API projesi
   - react-scripts start komutunu çalıştıran npm

   >[!NOTE]
   > Konsol çıkışında iletileri kontrol edin; örneğin, bir ileti, sürüm sürümünü güncelleştirmenizi Node.js.

API aracılığıyla React bir uygulamanın görüntü olduğunu görüyorsanız.

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki hatayı alabilirsiniz:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Bu sorunu görüyorsanız, büyük olasılıkla ön uç arka uç öncesinde başlamıştır. Arka uç komut isteminin çalışır olduğunu gördüğünüzde, tarayıcıda React App'i yenilemeniz gerekir.
