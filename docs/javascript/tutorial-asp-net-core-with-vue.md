---
title: Vue ile ASP.NET Core uygulama oluşturma
description: Bu öğreticide, ASP.NET Core ve Vue kullanarak bir uygulama oluşturabilirsiniz
ms.date: 09/28/2021
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
ms.openlocfilehash: 64db27eb96d3ea3536377a68ab322e6df2e09d1d
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131126486"
---
# <a name="tutorial-create-an-aspnet-core-app-with-vue-in-visual-studio"></a>Öğretici: ASP.NET Core Vue ile bir Visual Studio

Bu makalede API arka ucu gibi davranacak bir ASP.NET Core projesi ve kullanıcı arabirimi olarak hareket etmek için vue projesi derlemeyi öğrenirsiniz.

Şu anda Visual Studio, ASP.NET Core, uygulama ve Vue'Angular tek sayfalı uygulama (SPA) React şablonlarını içerir. Şablonlar, her çerçevenin temel dosyalarını ve klasörlerini içeren ASP.NET Core projelerinde yerleşik bir İstemci Uygulaması klasörü sağlar.

2022 Visual Studio 2022 Preview 2'den başlayarak, şu tek sayfalı uygulamaları oluşturmak ASP.NET Core bu makalede açıklanan yöntemi kullanabilirsiniz:

- İstemci uygulamasını, istemci projesinin dışında, ayrı bir ASP.NET Core koyma
- Bilgisayarınızda yüklü olan çerçeve CLI'sini temel alarak istemci projesini oluşturma

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio ve web geliştirme iş yükünün yüklü olduğu 2022 **Preview 2 ASP.NET** sürümü. Ücretsiz yüklemek [Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
  İş yükünü yüklemeniz ve önceden yüklemeniz gerekirse Visual Studio Araçları ve Özellikleri Al... 'a  >  **gidin.** Bu işlem Visual Studio Yükleyicisi. Web geliştirme **ASP.NET iş yükünü ve ardından** Değiştir'i **seçin.**
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Vue CLI ( [https://cli.vuejs.org/](https://cli.vuejs.org/) )  

## <a name="create-the-frontend-app"></a>Ön uç uygulamasını oluşturma

1. Yeni Proje Oluştur Project Yeni proje **oluştur'a seçin.** 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. Üst çubuktaki arama çubuğunda Vue'yi aratın ve Ardından Tek Başına **JavaScript Vue Şablonu** veya **Tek Başına TypeScript Vue** Şablonu seçeneğini seçin.

   :::image type="content" source="media/vs-2022/vue-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad girin. Ek bilgiler penceresine **bakarak** Boş web API'si ASP.NET **tümleştirmesi** ekle seçeneğini Project olun. Bu seçenek Vue şablonunuza dosyaları ekler, böylece daha sonra ASP.NET Core bağlanabilirsiniz.

   :::image type="content" source="media/vs-2022/asp-net-core-vue-additional-info.png" alt-text="Ek bilgi":::

Proje oluşturulduktan sonra bazı yeni ve değiştirilmiş dosyalar görüyorsunuz:

- aspnetcore-https.js
- vue.config.json (değiştirilmiş)
- HelloWorld.vue (değiştirilmiş)
- package.json (değiştirilmiş)

## <a name="create-the-backend-app"></a>Arka uç uygulamasını oluşturma

1. Bu Çözüm Gezgini, çözüm adına sağ tıklayın, Ekle'nin üzerine **gelin** ve yeni **girişler'i Project.** 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Yeni proje ekleme":::

1. ASP.NET Core Web API'si projesini arama ve seçme.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Web API şablonunu seçme":::

1. Projenize ve çözümünüze bir ad girin. Ek bilgiler penceresine **ulaşarak hedef** çerçeveniz **olarak .NET 6.0'ı** seçin.

   Proje oluşturulduktan sonra Çözüm Gezgini şu şekilde olması gerekir:

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-solution-explorer.png" alt-text="Çözüm Gezgini":::

1. Özellikler klasöründen açın ve arka uç uygulamasının profiller bölümünde varsayılan bağlantı noktalarını `launchSettings.json` 5001 ve  5003 olarak değiştirin.

   ```json
   "profiles": {
     "yourbackendapp": {
       "commandName": "Project",
       "launchUrl": "swagger",
       "environmentVariables": {
         "ASPNETCORE_ENVIRONMENT": "Development"
       },
       "applicationUrl": "https://localhost:5001;http://localhost:5003",
       "dotnetRunMessages": true
     },
   ```

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Bu Çözüm Gezgini projesini sağ tıklatın ASP.NET Core özellikler'i **seçin.**

   :::image type="content" source="media/vs-2022/asp-net-core-project-properties.png" alt-text="Proje özelliklerini açma"::: 
 
1. Hata ayıkla menüsüne gidin ve Hata ayıklama **başlatma profilleri kullanıcı arabirimini aç seçeneğini** belirleyin. Tarayıcıyı **başlat seçeneğinin temizleyin.**

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-deselect-launch-browser.png" alt-text="Hata ayıklama başlatma profilleri kullanıcı arabirimini açma"::: 

1. Ardından Vue projesine sağ tıklayın, Özellikler menüsünü **seçin** ve Hata Ayıklama **bölümüne** gidin. Debugger'ı **launch.json seçeneğiyle değiştirebilirsiniz.**
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-choose-debugger.png" alt-text="Hata ayıklayıcısını (launch.json) seçin":::

## <a name="set-the-startup-project"></a>Başlangıç projesini ayarlama

1. Çözüme sağ tıklayın ve Başlangıç ayarlarını **ayarla'yı Project.** Tek başlangıç projesi olan başlangıç projesini Birden çok başlangıç **projesi olarak değiştirme.** Her **projenin** eylemi için Başlat'ı seçin.
  
1. Ardından, arka uç projesini seçin ve ön ucun üzerine taşıarak ilk olarak başlamayı seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-set-first-project.png" alt-text="İlk başlangıç projesini seçin":::

## <a name="start-the-project"></a>Projeyi başlatma

Projeyi başlatmadan önce bağlantı noktası numaralarının eş olduğundan emin olun. ASP.NET Core *projenizin launchSettings.json* dosyasına gidin *(Özellikler klasöründe).* özelliğinden bağlantı noktası numarasını `applicationUrl` almak. (Şuna benzer şekilde `https://localhost:7049` görünüyor: .)

Ardından Vue *projenizinvue.config.js* dosyasına gidin. hedef özelliğini `applicationUrl` *launchSettings.json'daki özelliğiyle eşecek şekilde güncelleştirin.*

Projeyi başlatmak için **F5 tuşuna** basın veya **pencerenin** üst kısmından Başlat düğmesini seçin. İki komut istemi görüntülenir:

- Çalışan ASP.NET Core API projesi
- vue-cli-service service komutunu çalıştıran Vue CLI

API aracılığıyla doldurulan bir Vue uygulamasının görüntü olduğunu görüyorsanız.

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki hatayı alabilirsiniz:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Bu sorunu görüyorsanız, büyük olasılıkla ön uç arka uç öncesinde başlamıştır. Arka uç komut isteminin çalışır olduğunu gördüğünüzde, tarayıcıda Vue uygulamasını yenilemeniz gerekir.
