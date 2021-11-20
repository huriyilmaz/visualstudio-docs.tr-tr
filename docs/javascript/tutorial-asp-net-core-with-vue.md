---
title: Vue ile ASP.NET Core uygulama oluşturma
description: Bu öğreticide, ASP.NET Core vue kullanarak bir uygulama oluşturabilirsiniz
ms.date: 11/08/2021
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
ms.openlocfilehash: 05c47320efe74f186786954bc608b445255f150a
ms.sourcegitcommit: 8b44ba7864f67afa476708d5092729345e689f93
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132861516"
---
# <a name="tutorial-create-an-aspnet-core-app-with-vue-in-visual-studio"></a>Öğretici: Visual Studio'ASP.NET Core Vue ile bir Visual Studio

Bu makalede API arka ucu olarak davranacak bir ASP.NET Core projesi ve kullanıcı arabirimi olarak hareket etmek için vue projesi derlemeyi öğrenirsiniz.

Şu anda Visual Studio, ASP.NET Core ve Vue'Angular destekleyen tek sayfalı uygulama (SPA) React şablonlarını içerir. Şablonlar, her çerçevenin temel dosyalarını ve klasörlerini içeren ASP.NET Core projelerinde yerleşik bir İstemci Uygulaması klasörü sağlar.

2022 Visual Studio 2022 Preview 2'den başlayarak, tek sayfalı uygulamalar oluşturmak için bu ASP.NET Core açıklanan yöntemi kullanabilirsiniz:

- İstemci uygulamasını ASP.NET Core projesinin dışında ayrı bir projeye koyma
- Bilgisayarınızda yüklü olan çerçeve CLI'sini temel alarak istemci projesini oluşturma

> [!NOTE]
> Şu anda ön uç projesinin el ile yayımlanır (şu anda Yayımla aracıyla desteklenmiyor). Daha fazla bilgi için [https://github.com/MicrosoftDocs/visualstudio-docs/issues/7135](https://github.com/MicrosoftDocs/visualstudio-docs/issues/7135) bkz. .

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio ve web geliştirme iş yükünün yüklü olduğu 2022 **Preview 2 ASP.NET veya** sonraki bir sürümü yükleyin. Ücretsiz yüklemek [Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
  İş yükünü yüklemeniz ve önceden yüklemeniz gerekirse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Web geliştirme **ASP.NET iş yükünü ve ardından** Değiştir'i **seçin.**
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

1. Bu Çözüm Gezgini, çözüm adına sağ tıklayın, Ekle'nin üzerine **gelin ve** yeni **girişler'i Project.** 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Yeni proje ekleme":::

1. Web API projesini ASP.NET Core ve seçin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Web API şablonunu seçme":::

1. Projenize ve çözümünüze bir ad girin. Ek bilgiler penceresine **ulaşarak hedef** çerçeveniz **olarak .NET 6.0'ı** seçin.

   Proje oluşturulduktan sonra Çözüm Gezgini aşağıdaki gibi olması gerekir:

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
 
1. Hata ayıkla menüsüne gidin ve Hata ayıklama **başlatma profilleri kullanıcı arabirimini aç seçeneğini** belirleyin. Tarayıcıyı **başlat seçeneğinin temizleme.**

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-deselect-launch-browser.png" alt-text="Hata ayıklama başlatma profilleri kullanıcı arabirimini açma"::: 

1. Ardından Vue projesine sağ tıklayın, Özellikler menüsünü **seçin** ve Hata Ayıklama **bölümüne** gidin. Debugger'ı **launch.json seçeneğiyle değiştirebilirsiniz.**
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-choose-debugger.png" alt-text="Hata ayıklayıcısını (launch.json) seçin":::

## <a name="set-the-startup-project"></a>Başlangıç projesini ayarlama

1. Çözüme sağ tıklayın ve Başlangıç Ayarlarını **Ayarla'yı Project.** Tek başlangıç projesi olan başlangıç projesini Birden çok başlangıç **projesi olarak değiştirme.** Her **projenin** eylemi için Başlat'ı seçin.
  
1. Ardından, arka uç projesini seçin ve ön ucun üzerine taşıarak ilk olarak başlamayı seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-set-first-project.png" alt-text="İlk başlangıç projesini seçin":::

## <a name="start-the-project"></a>Projeyi başlatma

1. Projeyi başlatmadan önce bağlantı noktası numaralarının eş olduğundan emin olun. ASP.NET Core *projenizin launchSettings.json* dosyasına gidin *(Özellikler klasöründe).* özelliğinden bağlantı noktası numarasını `applicationUrl` almak.

   Birden çok özellik `applicationUrl` varsa, uç nokta kullanarak bir tane `https` olup bakabilirsiniz. şuna benzer şekilde görünüyor `https://localhost:7049` olabilir: .

1. Ardından Vue *projenizinvue.config.js* dosyanıza gidin. `applicationUrl` *launchSettings.json'daki özelliğiyle eşleşmesi için hedef özelliği güncelleştirin.*

1. Projeyi başlatmak için **F5 tuşuna** basın veya **pencerenin** üst kısmından Başlat düğmesini seçin. İki komut istemi görüntülenir:

   - Çalışan ASP.NET Core API projesi
   - vue-cli-service service komutunu çalıştıran Vue CLI

API aracılığıyla doldurulan Vue uygulamasının görüntü olduğunu görüyorsanız.

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki hatayı alabilirsiniz:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Bu sorunu görüyorsanız, büyük olasılıkla ön uç arka uç öncesinde başlamıştır. Arka uç komut isteminin çalışır olduğunu gördüğünüzde, tarayıcıda Vue uygulamasını yenilemeniz gerekir.
