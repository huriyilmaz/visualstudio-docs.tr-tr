---
title: Angular uygulaması oluşturma
description: bu öğreticide, Visual Studio Angular basit bir uygulama oluşturmayı öğrenin.
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
ms.openlocfilehash: 90c80b955b2e3e4ed19e68c11a720b199c97bf7a
ms.sourcegitcommit: 20f9529648e69707063dccb2b15089bf4e9bf639
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/31/2022
ms.locfileid: "137886754"
---
# <a name="create-an-angular-app"></a>Angular uygulaması oluşturma

bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (ıde) giriş sırasında basit bir Angular ön uç web uygulaması oluşturup çalıştırırsınız.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio 2022 Preview 2 veya üzeri. ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
- Node.js ile birlikte gelen NPM ( [https://www.npmjs.com/](https://www.npmjs.com/package/npm) )
- Angular clı ( [https://angular.io/cli](https://angular.io/cli) ) bu sizin tercih ettiğiniz sürümü olabilir

## <a name="create-your-app"></a>Uygulamanızı oluşturun

1. yeni Project iletişim kutusunda **yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. üstteki arama çubuğunda Angular araması yapın ve **tek başına TypeScript Angular şablonu**' nu seçin.

   :::image type="content" source="media/vs-2022/angular-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad verin.

   ek bilgi penceresine geldiğinizde, **boş ASP.NET Web apı 'si için tümleştirme ekle Project** seçeneğini denetlediğinizden emin olun. bu seçenek, bir ASP.NET Core projesi eklenirse ASP.NET Core projesiyle kullanıma abilmesi için Angular şablonunuza dosya ekler.

   :::image type="content" source="media/vs-2022/angular-additional-info.png" alt-text="Ek bilgi":::

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Çözüm Gezgini, Angular projesine sağ tıklayın, **özellikler**' i seçin ve ardından **hata ayıklama** bölümüne gidin.

1. Hata ayıklayıcıyı Launch **. JSON** seçeneğine başlatılacak şekilde değiştirin.
 
   :::image type="content" source="media/vs-2022/angular-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (Launch. JSON)":::

## <a name="build-your-project"></a>Project oluşturun

Projeyi derlemek için derleme **Yapı çözümünü** **seçin.**  > 

ilk derleme biraz zaman alabilir, bu Angular clı npm install komutunu çalıştırır.

## <a name="start-your-project"></a>Project başlatın

**F5** tuşuna basın veya pencerenin üst kısmındaki **Başlat** düğmesini seçin ve bir komut istemi görürsünüz:

- ng start komutunu çalıştıran Angular clı

   >[!NOTE]
   > Node.js sürümünüzü güncelleştirmenizi bir ileti gibi iletiler için konsol çıktısını denetleyin.

ardından, temel Angular uygulamaların göründüğünü görmeniz gerekir!