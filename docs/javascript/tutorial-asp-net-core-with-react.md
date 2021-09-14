---
title: React ASP.NET Core uygulama oluşturma
description: bu öğreticide, ASP.NET Core ve React kullanarak bir uygulama oluşturacaksınız
ms.date: 07/19/2021
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
ms.openlocfilehash: 4d6fefdda40e550a62616a82734a84037c0c10b0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725716"
---
# <a name="tutorial-create-an-aspnet-core-app-with-react-in-visual-studio"></a>öğretici: Visual Studio React ile ASP.NET Core uygulama oluşturma

bu makalede, bir apı arka ucu görevi gören bir ASP.NET Core projesi ve kullanıcı arabirimi olarak görev yapacak bir React projesi oluşturmayı öğreneceksiniz.

şu anda Visual Studio, Angular ve React destekleyen ASP.NET Core tek sayfalı uygulama (SPA) şablonlarını içerir. şablonlar, her bir çerçevenin temel dosya ve klasörlerini içeren ASP.NET Core projelerinizde yerleşik bir istemci uygulaması klasörü sağlar.

Visual Studio 2022 Preview 2 ' den başlayarak, bu makalede açıklanan yöntemi kullanarak aşağıdaki ASP.NET Core tek sayfalı uygulamalar oluşturabilirsiniz:

- istemci uygulamasını ASP.NET Core projeden farklı bir projeye yerleştirme
- Bilgisayarınızda yüklü olan Framework CLı 'yı temel alan istemci projesini oluşturun

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- **ASP.NET ve web geliştirme** iş yükü yüklü Visual Studio 2022 Preview 2 veya üzeri. ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
  iş yükünü yüklemeniz gerekiyorsa ve Visual Studio zaten varsa, **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.
- NPM ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- NPX ( [https://www.npmjs.com/package/npx](https://www.npmjs.com/package/npx) )

## <a name="create-the-frontend-app"></a>Ön uç uygulamasını oluşturma

1. yeni Project iletişim kutusunda **yeni proje oluştur**' u seçin. 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. üstteki arama çubuğunda React arayın ve sonra **tek başına JavaScript React şablonu**' nu seçin. (tek başına TypeScript React şablonu bu öğreticide şu anda desteklenmiyor.)

   :::image type="content" source="media/vs-2022/react-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad verin. **ek bilgi** penceresine geldiğinizde, **boş ASP.NET Web apı 'si için tümleştirme ekle Project** seçeneğini denetlediğinizden emin olun. bu seçenek, daha sonra ASP.NET Core projesiyle kullanıma abilmesi için React şablonunuza dosya ekler.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-additional-info.png" alt-text="Ek bilgi":::

   Proje oluşturulduktan sonra bazı yeni ve değiştirilmiş dosyalar görürsünüz:

   - aspnetcore-https.js
   - aspnetcore-react.js
   - setupProxy.js
   - App.js (değiştirilmiş)
   - App.test.js (değiştirilmiş)

## <a name="create-the-backend-app"></a>Arka uç uygulamasını oluşturma

1. Çözüm Gezgini ' nde çözüm adına sağ tıklayın, **Ekle**' nin üzerine gelin ve sonra **yeni Project**' yi seçin. 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Yeni Proje Ekle":::

1. ASP.NET Core Web apı projesinde arama yapın ve seçin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Web API şablonunu seçin":::

1. Projenize ve çözümünüze bir ad verin. **Ek bilgi** penceresine geldiğinizde, hedef çatısı olarak **.net 6,0** ' i seçin.

   Proje oluşturulduktan sonra Çözüm Gezgini şöyle görünmelidir:

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-solution-explorer.png" alt-text="Çözüm Gezgini göz atın":::

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. ASP.NET Core projesine sağ tıklayın ve **özellikler**' i seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-project-properties.png" alt-text="Proje özelliklerini aç"::: 
 
1. Hata Ayıkla menüsüne gidin ve **hata ayıklamayı başlatma profilleri kullanıcı arabirimi** seçeneğini belirleyin. **Tarayıcıyı Başlat** seçeneğinin işaretini kaldırın.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-deselect-launch-browser.png" alt-text="Hata ayıklama başlatma profilleri kullanıcı arabirimini açın"::: 

1. sonra, React projesine sağ tıklayın ve **özellikler** menüsünü seçin ve **hata ayıklama** bölümüne gidin. Hata ayıklayıcıyı Launch **. JSON** seçeneğine başlatılacak şekilde değiştirin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-react-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (Launch. JSON)":::

## <a name="set-the-startup-project"></a>Başlangıç projesini ayarla

1. Çözüme sağ tıklayın ve **başlangıç Project ayarla**' yı seçin. Başlangıç projesini tek başlangıç projesinden **Çoklu başlangıç projelerine** değiştirin. Her projenin eylemi için **Başlat** ' ı seçin.
  
1. Sonra, arka uç projesini seçin ve ilk kez başlaması için ön uca taşıyın.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-startup-project.png" alt-text="Başlangıç projesini seçin":::

## <a name="start-the-project"></a>Projeyi başlatma

**F5** tuşuna basın veya pencerenin üst kısmındaki **Başlat** düğmesini seçin. İki komut isteminin göründüğünü göreceksiniz:

- çalıştıran ASP.NET Core apı projesi
- Yanıt verme betikleri başlangıç komutunu çalıştıran NPM

apı aracılığıyla doldurulan bir React uygulamasının göründüğünü görmeniz gerekir.

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki hatayı görebilirsiniz:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Bu sorunu görürseniz, büyük olasılıkla ön uç arka uca başlamadan önce başlatılır. arka uç komut istemi 'ni çalışır durumda olduktan sonra tarayıcıda React uygulamayı yenilemeniz yeterlidir.
