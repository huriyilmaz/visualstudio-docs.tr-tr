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
dev_langs:
- JavaScript
ms.workload:
- nodejs
monikerRange: '>= vs-2022'
ms.openlocfilehash: 1f9078360987a531be544eb15460d4eb760a1677
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2021
ms.locfileid: "115095080"
---
# <a name="create-an-angular-app"></a>Angular uygulaması oluşturma

bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (ıde) giriş sırasında basit bir Angular ön uç web uygulaması oluşturup çalıştırırsınız.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- NPM ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Angular CLı ( [https://angular.io/cli](https://angular.io/cli) ) Bu, tercih ettiğiniz sürümü olabilir

## <a name="create-your-app"></a>Uygulamanızı oluşturun

1. yeni Project iletişim kutusunda **yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. üstteki arama çubuğunda Angular araması yapın ve **tek başına Angular şablonu**' nu seçin.

   :::image type="content" source="media/vs-2022/angular-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad verin. 

   ek bilgi penceresine geldiğinizde, **boş ASP.NET Web apı 'si için tümleştirme ekle Project** seçeneğini denetlediğinizden emin olun. bu seçenek, bir ASP.NET Core projesi eklenirse ASP.NET Core projesiyle kullanıma abilmesi için Angular şablonunuza dosya ekler.

   :::image type="content" source="media/vs-2022/angular-additional-info.png" alt-text="Ek bilgi":::

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Çözüm Gezgini, Angular projesine sağ tıklayın, **özellikler**' i seçin ve ardından **hata ayıklama** bölümüne gidin.

1. Hata ayıklayıcıyı başlatmak için **launch.js** seçeneğini değiştirin.
 
   :::image type="content" source="media/vs-2022/angular-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (launch.js)":::

## <a name="build-your-project"></a>Project oluşturun

  >  Projeyi derlemek için derleme **Yapı çözümünü** seçin.

ilk derleme biraz zaman alabilir, bu Angular clı npm install komutunu çalıştırır.

## <a name="start-your-project"></a>Project başlatın

**F5** tuşuna basın veya pencerenin üst kısmındaki **Başlat** düğmesini seçin. Bir komut istemi görüntülenir:

- ng start komutunu çalıştıran Angular clı

sonra, temel Angular uygulamanın göründüğünü görmeniz gerekir!