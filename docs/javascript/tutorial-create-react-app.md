---
title: React uygulaması oluşturma
description: bu öğreticide, Visual Studio React basit bir uygulama oluşturmayı öğrenin.
ms.date: 07/30/2021
ms.custom: vs-acquisition
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
ms.openlocfilehash: 2dd56faf17c7982f7b18d0d83469b8e2c56feea6
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115095088"
---
# <a name="create-a-react-app"></a>React uygulaması oluşturma

bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (ıde) giriş sırasında basit bir React ön uç web uygulaması oluşturup çalıştırırsınız.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- NPM ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- NPX ( [https://www.npmjs.com/package/npx](https://www.npmjs.com/package/npx) )

## <a name="create-your-app"></a>Uygulamanızı oluşturun

1. yeni Project iletişim kutusunda **yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. en üstteki arama çubuğunda React arayın ve tercihinize göre **tek başına JavaScript React şablonu** veya **tek başına TypeScript React şablonunu** seçin.

   :::image type="content" source="media/vs-2022/react-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad verin. 

   daha önce tek başına JavaScript React şablonu seçtiyseniz, ek bilgi penceresine geldiğinizde, **boş ASP.NET Web apı 'si için tümleştirme ekle Project** seçeneğini denetlediğinizden emin olun. bu seçenek, bir ASP.NET Core projesi eklenirse ASP.NET Core projesiyle kullanıma abilmesi için React şablonunuza dosya ekler.

   :::image type="content" source="media/vs-2022/react-additional-info.png" alt-text="Ek bilgi":::

   bu sırada çalışan create-tepki-app komutu, npm install komutunu da çalıştırdığından React projesinin oluşturulması bir süre sonra zaman aldığına lütfen emin olun.

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Çözüm Gezgini, React projesine sağ tıklayın, **özellikler**' i seçin ve ardından **hata ayıklama** bölümüne gidin.

1. Hata ayıklayıcıyı başlatmak için **launch.js** seçeneğini değiştirin.
 
   :::image type="content" source="media/vs-2022/react-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (launch.js)":::

## <a name="build-your-project"></a>Project oluşturun

  >  Projeyi derlemek için derleme **Yapı çözümünü** seçin.

## <a name="start-your-project"></a>Project başlatın

**F5** tuşuna basın veya pencerenin üst kısmındaki **Başlat** düğmesini seçin. Bir komut istemi görüntülenir:

- Yanıt verme betikleri başlangıç komutunu çalıştıran NPM

sonra, temel React uygulamanın göründüğünü görmeniz gerekir!