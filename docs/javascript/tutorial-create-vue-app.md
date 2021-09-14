---
title: Vue.js uygulaması oluşturma
description: Bu öğreticide, Visual Studio Vue.js basit bir uygulama oluşturmayı öğrenin.
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
ms.openlocfilehash: 926051ad98d43715a15a20091eb6a17c20f96758
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635889"
---
# <a name="create-a-vuejs-app"></a>Vue.js uygulaması oluşturma

bu 5-10 dakikalık Visual Studio tümleşik geliştirme ortamına (ıde) giriş sırasında basit bir Vue.js ön uç web uygulaması oluşturup çalıştırırsınız.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio 2022 Preview 2 veya üzeri. ücretsiz olarak yüklemek için [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına gidin.
- NPM ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Vue.js ([yükleme | Vue.js (vuejs.org)](https://v3.vuejs.org/guide/installation.html#npm))
- Vue.js CLı ([(yükleme | Vue.js (vuejs.org)](https://v3.vuejs.org/guide/installation.html#cli))

## <a name="create-your-app"></a>Uygulamanızı oluşturun

1. yeni Project iletişim kutusunda **yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. Üstteki arama çubuğunda Vue araması yapın ve tercihinize göre **tek başına JavaScript Vue şablonu** veya **tek başına TypeScript Vue şablonu**' nu seçin.

   :::image type="content" source="media/vs-2022/vue-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad verin. 

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Çözüm Gezgini, Vue.js projesine sağ tıklayın, **Özellikler**' i seçin ve ardından **hata ayıklama** bölümüne gidin.

1. Hata ayıklayıcıyı Launch **. JSON** seçeneğine başlatılacak şekilde değiştirin.
 
   :::image type="content" source="media/vs-2022/vue-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (Launch. JSON)":::

## <a name="build-your-project"></a>Project oluşturun

  >  Projeyi derlemek için derleme **Yapı çözümünü** seçin.

## <a name="start-your-project"></a>Project başlatın

**F5** tuşuna basın veya pencerenin üst kısmındaki **Başlat** düğmesini seçin. Bir komut istemi görüntülenir:

- Vue-CLI-Service Start komutunu çalıştıran NPM

Sonra, temel Vue.js uygulamanın göründüğünü görmeniz gerekir!