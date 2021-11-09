---
title: ASP.NET Core ile bir ASP.NET Core uygulaması Angular
description: Bu öğreticide, ASP.NET Core ve Angular
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
ms.openlocfilehash: 50bd68ea9835c94dd20737162e414a37241a9d17
ms.sourcegitcommit: ac681e983f3b217c3fd9d2a31e3a3ddcc4dd3546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2021
ms.locfileid: "132041965"
---
# <a name="tutorial-create-an-aspnet-core-app-with-angular-in-visual-studio"></a>Öğretici: ASP.NET Core'da Angular uygulama Visual Studio

Bu makalede API arka ucu olarak davranacak bir ASP.NET Core projesi ve kullanıcı arabirimi olarak davranacak bir Angular projesi oluşturma hakkında bilgi edinebilirsiniz.

Şu anda, Visual Studio ve ASP.NET Core destekleyen tek sayfalı uygulama (SPA) şablonları Angular React. Şablonlar, her çerçevenin temel dosyalarını ve klasörlerini içeren ASP.NET Core projelerinde yerleşik bir İstemci Uygulaması klasörü sağlar.

2022 Visual Studio 2022 Preview 2'den başlayarak, şu tek sayfalı uygulamaları oluşturmak ASP.NET Core bu makalede açıklanan yöntemi kullanabilirsiniz:

- İstemci uygulamasını, istemci projesinin dışında ayrı bir ASP.NET Core koyma
- Bilgisayarınızda yüklü olan çerçeve CLI'sini temel alarak istemci projesini oluşturma

>[!NOTE]
> Şu anda ön uç projesinin el ile yayımlanır (şu anda Yayımla aracıyla desteklenmiyor). Daha fazla bilgi için [https://github.com/MicrosoftDocs/visualstudio-docs/issues/7135](https://github.com/MicrosoftDocs/visualstudio-docs/issues/7135) bkz. .

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio ve web geliştirme iş yükünün yüklü olduğu 2022 **Preview 2 ASP.NET** sürümü. Ücretsiz yüklemek [Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
  İş yükünü yüklemeniz ve önceden yüklemeniz gerekirse Visual Studio Araçları ve Özellikleri Al... 'a gidin  >  **ve** Visual Studio Yükleyicisi. Web geliştirme **ASP.NET iş yükünü ve ardından** Değiştir'i **seçin.**
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Angular CLI ( [https://angular.io/cli](https://angular.io/cli) ) Bu, tercihe bağlı bir sürüm olabilir

## <a name="create-the-frontend-app"></a>Ön uç uygulamasını oluşturma

1. Yeni Proje Oluştur Project Yeni proje **oluştur'a seçin.** 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. Üst Angular arama çubuğundan Tek Başına uygulama şablonu'Angular **seçin.**

   :::image type="content" source="media/vs-2022/angular-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad girin. Ek bilgiler penceresine **bakarak** Boş web **API'si** ASP.NET tümleştirmesi ekle seçeneğini Project olun. Bu seçenek, daha sonra Angular projeyle bağlanacak şekilde dosya şablonunuz ASP.NET Core ekler.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-additional-info.png" alt-text="Ek bilgi":::

   Proje oluşturulduktan sonra bazı yeni ve değiştirilmiş dosyalar görüyorsunuz:

   - aspnetcore-https.js
   - proxy.js
   - package.json(modified)
   - angular.json(modified)
   - app.components.ts
   - app.module.ts

## <a name="create-the-backend-app"></a>Arka uç uygulamasını oluşturma

1. Çözüm gezgininde çözüm adına sağ tıklayın, Ekle'nin üzerine **gelin ve** Ardından Yeni **girişler'i Project.** 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Yeni proje ekleme":::

1. Web API projesini ASP.NET Core ve seçin.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Web API şablonunu seçme":::

1. Projenize ve çözümünüze bir ad girin. Ek bilgiler penceresine **ulaşarak hedef** çerçeveniz **olarak .NET 6.0'ı** seçin.

   Proje oluşturulduktan sonra Çözüm Gezgini aşağıdaki gibi olması gerekir:

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-solution-explorer.png" alt-text="Çözüm Gezgini":::

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. ASP.NET Core projesine sağ tıklayın ve Özellikler'i **seçin.**

   :::image type="content" source="media/vs-2022/asp-net-core-project-properties.png" alt-text="Proje özelliklerini açma"::: 
 
1. Hata ayıkla menüsüne gidin ve Hata ayıklama **başlatma profilleri kullanıcı arabirimini aç seçeneğini** belirleyin. Tarayıcıyı Başlat **seçeneğinin işaretini** kaldırın.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-deselect-launch-browser.png" alt-text="Hata ayıklama başlatma profilleri kullanıcı arabirimini açma"::: 

1. Ardından, Angular projesine sağ tıklayın, **Özellikler menüsünü seçin** ve Hata Ayıklama **bölümüne** gidin. Debugger'ı **launch.json seçeneğiyle değiştirebilirsiniz.**
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-choose-debugger.png" alt-text="Hata ayıklayıcısını (launch.json) seçin":::

## <a name="set-the-startup-project"></a>Başlangıç projesini ayarlama

1. Çözüme sağ tıklayın ve Başlangıç ayarlarını **ayarla'yı Project.** Tek başlangıç projesi olan başlangıç projesini Birden çok başlangıç **projesi olarak değiştirme.** Her **projenin** eylemi için Başlat'ı seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-multiple-startup-projects.png" alt-text="Çoklu başlangıç projeleri ayarlama":::
  
1. Ardından, arka uç projesini seçin ve ön ucun üzerine taşıarak ilk olarak başlamayı seçin.

   :::image type="content" source="media/vs-2022/asp-net-core-with-angular-set-first-project.png" alt-text="İlk başlangıç projesini seçin":::

## <a name="start-the-project"></a>Projeyi başlatma

Projeyi başlatmadan önce bağlantı noktası numaralarının eş olduğundan emin olun. ASP.NET Core *projenizin launchSettings.json* dosyasına gidin *(Özellikler klasöründe).* özelliğinden bağlantı noktası numarasını `applicationUrl` almak. (Şuna benzer şekilde `https://localhost:7049` görünüyor: .)

Ardından, Angular *projenizin* proxy.conf.jsdosyasına gidin *(src klasörüne* bakın). hedef özelliğini `applicationUrl` *launchSettings.json'daki özelliğiyle eşecek şekilde güncelleştirin.*

Projeyi başlatmak için **F5 tuşuna** basın veya **pencerenin** üst kısmından Başlat düğmesini seçin. İki komut istemi görüntülenir:

- Çalışan ASP.NET Core API projesi
- ng start Angular çalıştıran Angular CLI

API aracılığıyla Angular bir uygulamanın görüntü olduğunu görüyorsanız.

## <a name="troubleshooting"></a>Sorun giderme

Aşağıdaki hatayı alabilirsiniz:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Bu sorunu görüyorsanız, büyük olasılıkla ön uç arka uç öncesinde başlamıştır. Arka uç komut isteminin çalışır olduğunu gördüğünüzde, tarayıcıda Angular App'i yenilemeniz gerekir.
