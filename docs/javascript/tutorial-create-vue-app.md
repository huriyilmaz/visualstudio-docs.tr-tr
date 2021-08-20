---
title: Vue.js oluşturma
description: Bu öğreticide, bu öğreticide basit bir Vue.js uygulaması Visual Studio.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085721"
---
# <a name="create-a-vuejs-app"></a>Vue.js oluşturma

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte, basit bir ön uç web uygulaması Vue.js ve çalıştırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio 2022 Preview 2 veya sonraki bir sürümü. Ücretsiz yüklemek [Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Vue.js ([Yükleme | Vue.js (vuejs.org) )](https://v3.vuejs.org/guide/installation.html#npm)
- Vue.js CLI ([(Yükleme | Vue.js (vuejs.org) )](https://v3.vuejs.org/guide/installation.html#cli)

## <a name="create-your-app"></a>Uygulama oluşturma

1. Yeni Proje Oluştur Project Yeni proje **oluştur'a seçin.**

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. Üsttaki arama çubuğunda Vue'yi aratın ve ardından tercihinizi temel alarak Tek Başına **JavaScript Vue Şablonu** veya Tek Başına **TypeScript Vue Şablonu** seçeneğini seçin.

   :::image type="content" source="media/vs-2022/vue-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad girin. 

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Bu Çözüm Gezgini, Vue.js projesine sağ tıklayın, **Özellikler'i seçin** ve hata ayıklama **bölümüne** gidin.

1. Hata Ayıklayıcısı'nın başlat seçeneğini **launch.js** olarak değiştirme.
 
   :::image type="content" source="media/vs-2022/vue-choose-debugger.png" alt-text="Hata ayıklayıcıyı seçin (launch.js)":::

## <a name="build-your-project"></a>Derleme Project

Projeyi   >  **derlemek için Derleme** Çözümü'ne seçin.

## <a name="start-your-project"></a>Çalışma Project

**F5 tuşuna** basın **veya** pencerenin üst kısmından Başlat düğmesini seçin. Bir komut istemi görüntülenir:

- npm running the vue-cli-service start command

Ardından, temel uygulamanın Vue.js görün!