---
title: Angular ASP.NET Core uygulama oluşturma
description: bu öğreticide, ASP.NET Core ve Angular kullanarak bir uygulama oluşturacaksınız
ms.date: 07/19/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
monikerRange: '>= vs-2022'
ms.openlocfilehash: 52e3e78fbfc6a407e684c2e9eeb237a603934764
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115093984"
---
# <a name="tutorial-create-an-aspnet-core-app-with-angular-in-visual-studio"></a>öğretici: Visual Studio Angular ile ASP.NET Core uygulama oluşturma

bu makalede, bir apı arka ucu görevi gören bir ASP.NET Core projesi ve kullanıcı arabirimi olarak görev yapacak bir Angular projesi oluşturmayı öğreneceksiniz.

şu anda Visual Studio, Angular ve React destekleyen ASP.NET Core tek sayfalı uygulama (SPA) şablonlarını içerir. şablonlar, her bir çerçevenin temel dosya ve klasörlerini içeren ASP.NET Core projelerinizde yerleşik bir istemci uygulaması klasörü sağlar.

Visual Studio 2022 Preview 2 ' den başlayarak, bu makalede açıklanan yöntemi kullanarak aşağıdaki ASP.NET Core tek sayfalı uygulamalar oluşturabilirsiniz:

- istemci uygulamasını ASP.NET Core projeden farklı bir projeye yerleştirme
- Bilgisayarınızda yüklü olan Framework CLı 'yı temel alan istemci projesini oluşturun

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- NPM ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Angular CLı ( [https://angular.io/cli](https://angular.io/cli) ) Bu, tercih ettiğiniz sürümü olabilir

## <a name="create-the-frontend-app"></a>Ön uç uygulamasını oluşturma

1. yeni Project iletişim kutusunda **yeni proje oluştur**' u seçin. 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. üstteki arama çubuğunda Angular araması yapın ve **tek başına Angular şablonu**' nu seçin.

   :::image type="content" source="media/vs-2022/angular-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad verin. **ek bilgi** penceresine geldiğinizde, **boş ASP.NET Web apı 'si için tümleştirme ekle Project** seçeneğini denetlediğinizden emin olun. bu seçenek, daha sonra ASP.NET Core projesiyle kullanıma abilmesi için Angular şablonunuza dosya ekler.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-additional-info.png" alt-text="Ek bilgi":::

   Proje oluşturulduktan sonra bazı yeni ve değiştirilmiş dosyalar görürsünüz:

   - aspnetcore-https.js
   - proxy.js
   - package.json (değiştirilmiş)
   - angular.json (değiştirilmiş)
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

1. sonra, Angular projesine sağ tıklayın ve **özellikler** menüsünü seçin ve **hata ayıklama** bölümüne gidin. Hata ayıklayıcıyı başlatmak için **launch.js** seçeneğini değiştirin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (launch.js)":::

## <a name="set-the-startup-project"></a>Başlangıç projesini ayarla

1. Çözüme sağ tıklayın ve **başlangıç Project ayarla**' yı seçin. Başlangıç projesini tek başlangıç projesinden **Çoklu başlangıç projelerine** değiştirin. Her projenin eylemi için **Başlat** ' ı seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-multiple-startup-projects.png" alt-text="Çoklu başlangıç projeleri ayarlama":::
  
1. Sonra, arka uç projesini seçin ve ilk kez başlaması için ön uca taşıyın.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-set-first-project.png" alt-text="İlk başlangıç projesini seçin":::

## <a name="start-the-project"></a>Projeyi başlatma

**F5** tuşuna basın veya pencerenin üst kısmındaki **Başlat** düğmesini seçin. İki komut isteminin göründüğünü göreceksiniz:

- çalıştıran ASP.NET Core apı projesi
- ng start komutunu çalıştıran Angular clı

apı aracılığıyla doldurulan bir Angular uygulamasının göründüğünü görmeniz gerekir.

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki hatayı görebilirsiniz:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Bu sorunu görürseniz, büyük olasılıkla ön uç arka uca başlamadan önce başlatılır. arka uç komut istemi 'ni çalışır durumda olduktan sonra tarayıcıda Angular uygulamayı yenilemeniz yeterlidir.
