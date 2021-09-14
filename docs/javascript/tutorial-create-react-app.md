---
title: React oluşturma
description: Bu öğreticide, bu öğreticide basit bir React uygulaması Visual Studio.
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
ms.openlocfilehash: fbf4b68c1f5f82af8af47cda7e21389b14c21bb2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635894"
---
# <a name="create-a-react-app"></a>React oluşturma

Visual Studio tümleşik geliştirme ortamına (IDE) 5-10 dakikalık bir girişte, basit bir ön uç web uygulaması React ve çalıştırabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

Aşağıdakilerin yüklü olduğundan emin olun:

- Visual Studio 2022 Preview 2 veya sonraki bir sürümü. Ücretsiz yüklemek [Visual Studio](https://visualstudio.microsoft.com/downloads/) indirmeler sayfasına gidin.
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- npx ( [https://www.npmjs.com/package/npx](https://www.npmjs.com/package/npx) )

## <a name="create-your-app"></a>Uygulama oluşturma

1. Yeni Proje Oluştur Project Yeni proje **oluştur'a seçin.**

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Yeni proje oluşturma":::

1. Üst React arama çubuğunda tek başına **JavaScript** React Şablonu veya Tek başına **TypeScript React Şablonu'React** seçin.

   :::image type="content" source="media/vs-2022/react-choose-template.png" alt-text="Şablon seçme":::

1. Projenize ve çözümünüze bir ad girin. 

   Daha önce Tek Başına JavaScript React Şablonu'React seçtiyseniz, Ek bilgiler penceresine bakarak Boş Web API'si ASP.NET tümleştirmesi ekle seçeneğini **denetlemeyi Project** olun. Bu seçenek, React bir proje eklenirse ASP.NET Core projeyle bağlanacak şekilde ASP.NET Core ekler.

   :::image type="content" source="media/vs-2022/react-additional-info.png" alt-text="Ek bilgi":::

   Şu anda çalışan create-react-app React npm install komutunu da çalıştıracak olduğundan, React projesinin oluşturulmasının biraz zaman alır

## <a name="set-the-project-properties"></a>Proje özelliklerini ayarlama

1. Bu Çözüm Gezgini, React projesine sağ tıklayın, Özellikler'i **seçin** ve hata ayıklama **bölümüne** gidin.

1. Debugger'ı **launch.json seçeneğiyle değiştirebilirsiniz.**
 
   :::image type="content" source="media/vs-2022/react-choose-debugger.png" alt-text="Hata ayıklayıcısını (launch.json) seçin":::

## <a name="build-your-project"></a>Derleme Project

Projeyi   >  **derlemek için Derleme** Çözümü'ne seçin.

## <a name="start-your-project"></a>Çalışma Project

**F5 tuşuna** basın **veya** pencerenin üst kısmından Başlat düğmesini seçin. Bir komut istemi görüntülenir:

- react-scripts start komutunu çalıştıran npm

Ardından, temel uygulamanın React görün!