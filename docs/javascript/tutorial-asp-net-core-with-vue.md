---
title: vue ile ASP.NET Core uygulaması oluşturma
description: bu öğreticide, ASP.NET Core ve vue kullanarak bir uygulama oluşturacaksınız
ms.date: 08/09/2021
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
ms.openlocfilehash: 50ee00867e6729c269753edeb0cdfa44f3215c3f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027918"
---
# <a name="tutorial-create-an-aspnet-core-app-with-vue-in-visual-studio"></a>öğretici: Visual Studio vue ile ASP.NET Core uygulama oluşturma

bu makalede, kullanıcı arabirimi olarak davranacak bir apı arka ucu ve bir vue projesi olarak hareket etmek için bir ASP.NET Core projesi oluşturmayı öğreneceksiniz.

şu anda Visual Studio, Angular, React ve vue 'yi destekleyen ASP.NET Core tek sayfalı uygulama (SPA) şablonları içerir. şablonlar, her bir çerçevenin temel dosya ve klasörlerini içeren ASP.NET Core projelerinizde yerleşik bir istemci uygulaması klasörü sağlar.

Visual Studio 2022 Preview 2 ' den başlayarak, bu makalede açıklanan yöntemi kullanarak aşağıdaki ASP.NET Core tek sayfalı uygulamalar oluşturabilirsiniz:

- istemci uygulamasını ASP.NET Core projeden farklı bir projeye yerleştirme
- Bilgisayarınızda yüklü olan Framework CLı 'yı temel alan istemci projesini oluşturun

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- **ASP.NET ve web geliştirme** iş yükü yüklü Visual Studio 2022 Preview 2 veya üzeri. ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
  iş yükünü yüklemeniz gerekiyorsa ve Visual Studio zaten varsa, **araçlar**  >  **ve özellikler al.**.. ' a giderek Visual Studio Yükleyicisi açan araçlar ' a gidin. **ASP.NET ve web geliştirme** iş yükünü seçin ve ardından **değiştir**' i seçin.
- NPM ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Vue CLı ( [https://cli.vuejs.org/](https://cli.vuejs.org/) )  

## <a name="create-the-frontend-app"></a>Ön uç uygulamasını oluşturma

1. yeni Project iletişim kutusunda **yeni proje oluştur**' u seçin. 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. Üstteki arama çubuğunda Vue araması yapın ve **tek başına JavaScript Vue şablonu** veya **tek başına TypeScript Vue şablonu**' nu seçin.

   :::image type="content" source="media/vs-2022/vue-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad verin. **ek bilgi** penceresine geldiğinizde, **boş ASP.NET Web apı 'si için tümleştirme ekle Project** seçeneğini denetlediğinizden emin olun. bu seçenek, daha sonra ASP.NET Core projesiyle kullanıma abilmesi için dosyaları vue şablonunuza ekler.

   :::image type="content" source="media/vs-2022/asp-net-core-vue-additional-info.png" alt-text="Ek bilgi":::

Proje oluşturulduktan sonra bazı yeni ve değiştirilmiş dosyalar görürsünüz:

- aspnetcore-https.js
- vue.config.json (değiştirilmiş)
- HelloWorld. Vue (değiştirilmiş)
- package.json (değiştirilmiş)

## <a name="create-the-backend-app"></a>Arka uç uygulamasını oluşturma

1. Çözüm Gezgini, çözüm adına sağ tıklayın, **Ekle**' nin üzerine gelin ve ardından **yeni Project**' yı seçin. 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Yeni Proje Ekle":::

1. ASP.NET Core Web apı projesinde arama yapın ve seçin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Web API şablonunu seçin":::

1. Projenize ve çözümünüze bir ad verin. **Ek bilgi** penceresine geldiğinizde, hedef çatısı olarak **.net 6,0** ' i seçin.

   Proje oluşturulduktan sonra Çözüm Gezgini şöyle görünmelidir:

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-solution-explorer.png" alt-text="Çözüm Gezgini göz atın":::

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Çözüm Gezgini, ASP.NET Core projesine sağ tıklayın ve **özellikler**' i seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-project-properties.png" alt-text="Proje özelliklerini aç"::: 
 
1. Hata Ayıkla menüsüne gidin ve **hata ayıklamayı başlatma profilleri kullanıcı arabirimi** seçeneğini belirleyin. **Tarayıcıyı Başlat** seçeneğini temizleyin.

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-deselect-launch-browser.png" alt-text="Hata ayıklama başlatma profilleri kullanıcı arabirimini açın"::: 

1. Ardından, Vue projesine sağ tıklayın ve **Özellikler** menüsünü seçin ve **hata ayıklama** bölümüne gidin. Hata ayıklayıcıyı başlatmak için **launch.js** seçeneğini değiştirin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (launch.js)":::

## <a name="set-the-startup-project"></a>Başlangıç projesini ayarla

1. Çözüme sağ tıklayın ve **başlangıç Project ayarla**' yı seçin. Başlangıç projesini tek başlangıç projesinden **Çoklu başlangıç projelerine** değiştirin. Her projenin eylemi için **Başlat** ' ı seçin.
  
1. Sonra, arka uç projesini seçin ve ilk kez başlaması için ön uca taşıyın.

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-set-first-project.png" alt-text="İlk başlangıç projesini seçin":::

## <a name="start-the-project"></a>Projeyi başlatma

**F5** tuşuna basın veya pencerenin üst kısmındaki **Başlat** düğmesini seçin. İki komut isteminin göründüğünü göreceksiniz:

- çalıştıran ASP.NET Core apı projesi
- Vue-CLI-Service hizmet komut komutunu çalıştıran Vue CLı

API aracılığıyla doldurulan bir Vue uygulamasının göründüğünü görmeniz gerekir.

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki hatayı görebilirsiniz:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Bu sorunu görürseniz, büyük olasılıkla ön uç arka uca başlamadan önce başlatılır. Arka uç komut istemi 'ni çalışır durumda olduktan sonra tarayıcıda Vue uygulamasını yenilemeniz yeterlidir.
