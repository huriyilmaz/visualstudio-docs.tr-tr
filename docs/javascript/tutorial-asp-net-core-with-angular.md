---
title: Angular ASP.NET Core uygulama oluşturma
description: bu öğreticide, ASP.NET Core ve Angular kullanarak bir uygulama oluşturacaksınız
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
ms.openlocfilehash: 55245b11de769371349da0a8d560b56effccca39
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886780"
---
# <a name="tutorial-create-an-aspnet-core-app-with-angular-in-visual-studio"></a>öğretici: Visual Studio Angular ile ASP.NET Core uygulama oluşturma

bu makalede, bir apı arka ucu görevi gören bir ASP.NET Core projesi ve kullanıcı arabirimi olarak görev yapacak bir Angular projesi oluşturmayı öğreneceksiniz.

şu anda Visual Studio, Angular ve React destekleyen ASP.NET Core tek sayfalı uygulama (SPA) şablonlarını içerir. şablonlar, her bir çerçevenin temel dosya ve klasörlerini içeren ASP.NET Core projelerinizde yerleşik bir istemci uygulaması klasörü sağlar.

Visual Studio 2022 Preview 2 ' den başlayarak, bu makalede açıklanan yöntemi kullanarak aşağıdaki ASP.NET Core tek sayfalı uygulamalar oluşturabilirsiniz:

- istemci uygulamasını ASP.NET Core projeden farklı bir projeye yerleştirme
- Bilgisayarınızda yüklü olan Framework CLı 'yı temel alan istemci projesini oluşturun

>[!NOTE]
> Şu anda ön uç projesinin el ile yayımlanması gerekir (yayımlama aracı ile henüz desteklenmemektedir). Daha fazla bilgi için bkz [https://github.com/MicrosoftDocs/visualstudio-docs/issues/7135](https://github.com/MicrosoftDocs/visualstudio-docs/issues/7135) ..

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- **ASP.NET ve web geliştirme** iş yükü yüklü Visual Studio 2022 Preview 2 veya üzeri. ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
  iş yükünü yüklemeniz gerekiyorsa ve Visual Studio zaten varsa, araçlar **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan **araçlar**  >  ' a gidin. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.
- Node.js ile birlikte gelen NPM ( [https://www.npmjs.com/](https://www.npmjs.com/package/npm) )
- Angular clı ( [https://angular.io/cli](https://angular.io/cli) ) bu sizin tercih ettiğiniz sürümü olabilir

## <a name="create-the-frontend-app"></a>Ön uç uygulamasını oluşturma

1. yeni Project iletişim kutusunda **yeni proje oluştur**' u seçin. 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. üstteki arama çubuğunda Angular araması yapın ve **tek başına TypeScript Angular şablonu**' nu seçin.

   :::image type="content" source="media/vs-2022/angular-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad verin. **ek bilgi** penceresine geldiğinizde, **boş ASP.NET Web apı 'si için tümleştirme ekle Project** seçeneğini denetlediğinizden emin olun. bu seçenek, daha sonra ASP.NET Core projesiyle kullanıma abilmesi için Angular şablonunuza dosya ekler.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-additional-info.png" alt-text="Ek bilgi":::

   Proje oluşturulduktan sonra bazı yeni ve değiştirilmiş dosyalar görürsünüz:

   - aspnetcore-https.js
   - proxy.js
   - Package. JSON (değiştirilmiş)
   - Angular. JSON (değiştirilmiş)
   - App. components. TS
   - App. Module. TS

## <a name="create-the-backend-app"></a>Arka uç uygulamasını oluşturma

1. Çözüm Gezgini ' nde çözüm adına sağ tıklayın, **Ekle**' nin üzerine gelin ve sonra **yeni Project**' yi seçin. 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Yeni Proje Ekle":::

1. ASP.NET Core Web apı projesinde arama yapın ve seçin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Web API şablonunu seçin":::

1. Projenize ve çözümünüze bir ad verin. **Ek bilgi** penceresine geldiğinizde, hedef çatısı olarak **.net 6,0** ' i seçin.

   Proje oluşturulduktan sonra Çözüm Gezgini şöyle görünmelidir:

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-solution-explorer.png" alt-text="Çözüm Gezgini göz atın":::

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. ASP.NET Core projesine sağ tıklayın ve **özellikler**' i seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-project-properties.png" alt-text="Proje özelliklerini aç"::: 
 
1. Hata Ayıkla menüsüne gidin ve **hata ayıklamayı başlatma profilleri kullanıcı arabirimi** seçeneğini belirleyin. **Tarayıcıyı Başlat** seçeneğinin işaretini kaldırın.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-deselect-launch-browser.png" alt-text="Hata ayıklama başlatma profilleri kullanıcı arabirimini açın"::: 

1. sonra, Angular projesine sağ tıklayın ve **özellikler** menüsünü seçin ve **hata ayıklama** bölümüne gidin. Hata ayıklayıcıyı Launch **. JSON** seçeneğine başlatılacak şekilde değiştirin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (Launch. JSON)":::

## <a name="set-the-startup-project"></a>Başlangıç projesini ayarla

1. Çözüme sağ tıklayın ve **başlangıç Project ayarla**' yı seçin. Başlangıç projesini tek başlangıç projesinden **Çoklu başlangıç projelerine** değiştirin. Her projenin eylemi için **Başlat** ' ı seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-multiple-startup-projects.png" alt-text="Çoklu başlangıç projeleri ayarlama":::
  
1. Sonra, arka uç projesini seçin ve ilk kez başlaması için ön uca taşıyın.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-set-first-project.png" alt-text="İlk başlangıç projesini seçin":::

## <a name="start-the-project"></a>Projeyi başlatma

Projeye başlamadan önce, bağlantı noktası numaralarının eşleştiğinden emin olun.

1. ASP.NET Core projenizdeki *launchsettings. json* dosyasına gidin ( *özellikler* klasöründe). Özellikten bağlantı noktası numarasını `applicationUrl` alın.

   Birden çok `applicationUrl` özellik varsa, uç nokta kullanarak `https` bir tane bulun. Şuna benzer `https://localhost:7049` görünmelidir.

1. sonra, Angular projeniz için *proxy.conf.js* dosyasına gidin ( *src* klasörüne bakın). *Launchsettings. JSON* içindeki özellik ile eşleşecek `applicationUrl` şekilde Target özelliğini güncelleştirin. Bunu güncelleştirdiğinizde bu değer şuna benzer görünmelidir:

   ```js
   target: 'https://localhost:7049',
   ```

1. Projeyi başlatmak için **F5** tuşuna basın veya pencerenin üst kısmındaki **Başlat** düğmesini seçin. İki komut isteminin göründüğünü göreceksiniz:

   - çalıştıran ASP.NET Core apı projesi
   - ng start komutunu çalıştıran Angular clı

   >[!NOTE]
   > Node.js sürümünüzü güncelleştirmenizi bir ileti gibi iletiler için konsol çıktısını denetleyin.

apı aracılığıyla doldurulan bir Angular uygulamasının göründüğünü görmeniz gerekir.

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki hatayı görebilirsiniz:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Bu sorunu görürseniz, büyük olasılıkla ön uç arka uca başlamadan önce başlatılır. arka uç komut istemi 'ni çalışır durumda olduktan sonra tarayıcıda Angular uygulamayı yenilemeniz yeterlidir.
