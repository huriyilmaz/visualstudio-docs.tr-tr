---
title: Angular oluşturma
description: Bu öğreticide, bu öğreticide basit bir Angular uygulaması Visual Studio.
ms.date: 07/30/2021
ms.custom: vs-acquisition
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
ms.openlocfilehash: 1b40a03c63665be09ecea5c28fb8e82dcc69c7a7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635897"
---
# <a name="create-an-angular-app"></a>Angular oluşturma

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte, basit bir ön uç web uygulaması Angular ve çalıştırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio 2022 Preview 2 veya sonraki bir sürümü. Ücretsiz yüklemek [Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Angular CLI ( [https://angular.io/cli](https://angular.io/cli) ) Bu, tercihe bağlı bir sürüm olabilir

## <a name="create-your-app"></a>Uygulama oluşturma

1. Yeni Proje Oluştur Project Yeni proje **oluştur'a seçin.**

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. Üst Angular arama çubuğundan Tek Başına uygulama şablonu'Angular **seçin.**

   :::image type="content" source="media/vs-2022/angular-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad girin. 

   Ek bilgiler penceresine inerseniz Boş web **API'si** ASP.NET tümleştirmesi ekle seçeneğini Project emin olun. Bu seçenek, Angular bir proje eklenirse ASP.NET Core projeyle bağlanacak şekilde ASP.NET Core ekler.

   :::image type="content" source="media/vs-2022/angular-additional-info.png" alt-text="Ek bilgi":::

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Bu Çözüm Gezgini, Angular projesine sağ tıklayın, Özellikler'i **seçin** ve hata ayıklama **bölümüne** gidin.

1. Debugger'ı **launch.json seçeneğiyle değiştirebilirsiniz.**
 
   :::image type="content" source="media/vs-2022/angular-choose-debugger.png" alt-text="Hata ayıklayıcısını (launch.json) seçin":::

## <a name="build-your-project"></a>Derleme Project

Projeyi   >  **derlemek için Derleme** Çözümü'ne seçin.

Angular CLI npm install komutunu çalıştıracak olduğu için ilk derlemenin biraz uzun zaman alyabilirsiniz.

## <a name="start-your-project"></a>Çalışma Project

**F5 tuşuna** basın **veya** pencerenin üst kısmından Başlat düğmesini seçin. Bir komut istemi görüntülenir:

- ng start Angular çalıştıran Angular CLI

Ardından, temel uygulamanın Angular görün!