---
title: Klasöre yayımlama
description: Mac için Visual Studio kullanarak bir web uygulamasını bir klasöre yayımlama.
ms.date: 11/09/2020
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 2944fa88297cbf7b0d3fe7149b4b690f5a7f1012cebdcd25daeb9c85e68461fc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381711"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak bir klasöre yayımlama

.net Core konsolunu veya ASP.NET Core uygulamalarını bir klasöre yayımlamak için yayımla aracını kullanabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- .net Core ile yüklenen [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) .
- bir .net Core konsolu veya ASP.NET Core projesi. Zaten bir projeniz yoksa [Yeni bir tane oluşturabilirsiniz](./create-new-projects.md).

## <a name="publish-to-folder"></a>Klasöre Yayımlama

Mac için Visual Studio kullanarak .net Core projelerinizi yayımla aracını kullanarak bir klasöre yayımlayabilirsiniz. Bir klasöre yayımladıktan sonra, dosyaları farklı bir ortama aktarabilirsiniz. Bir klasöre yayımlamak için aşağıdaki adımları izleyin.

 1. Çözüm penceresinde projeye sağ tıklayın ve **Yayımla**' yı seçin.

    ![Yayımla bağlam menüsü](media/publish-context-menu.png)

 2. Bu projeyi daha önce yayımladıysanız, menüde Yayımla profilini görürsünüz. Yayımlama işlemini başlatmak için bu profili Yayımla ' yı seçin.

 3. Bu projeyi ilk kez bir klasöre yayımlamak için, **klasöre Yayımla** ' yı seçin.

    ![Klasöre Yayımla bağlam menüsü](media/publish-to-folder-context-menu.png)

 4. **Klasöre Yayımla** iletişim kutusu görüntülenir. Bu iletişim kutusunda projenin yayımlanacağı klasörü özelleştirebilirsiniz. Bunu yapmak için, **Araştır** düğmesini veya bir yolu yapıştırmak için kullanabilirsiniz.

 5. **Yayımla** ' ya tıkladıktan sonra birkaç şey meydana gelir. İlk olarak bir yayımlama profili oluşturulur. yayımlama profili, yayımlama işlemi sırasında projeye içeri aktarılan bir MSBuild dosyasıdır. Yayımlama işlemi sırasında kullanılan özellikleri içerir. Bu dosyalar içinde depolanır `Properties/PublishProfiles` ve uzantısına sahiptir `.pubxml` . Sonra yayımlama işlemi başlatılır. Mac için Visual Studio ' de durum çubuğunu izleyerek ilerlemeyi izleyebilirsiniz.

    ![Yayımlama durumuyla IDE durum çubuğu](media/publish-to-folder-status-bar.png)

 6. Yayımlama başarıyla tamamlandığında, bir bulucu penceresi Yayımla klasörüne açılır. Şimdi bir yayımlama profili oluşturuldığına göre, Yayımla bağlam menüsünde görüntülenecektir.

    ![Bağlam menüsünü klasör profiliyle Yayımla](media/publish-context-menu-with-folder-profile.png)

 7. Projeyi aynı ayarlarla yeniden yayımlamak için Yayımla bağlam menüsünde profile tıklayabilirsiniz.

## <a name="customize-publish-options"></a>Yayımlama seçeneklerini özelleştirin

Yayımlama profilinin adını değiştirmek için (Yayımla bağlam menüsünde görüntülenir), yayımlama profili dosyasını yeniden adlandırın. Dosyanın () uzantısını değiştirmediğinden emin olun `.pubxml` .

Yayımlama klasörü yolunu değiştirmek için yayımlama profilini açın ve `publishUrl` değeri düzenleyin.

Kullanılan yapı yapılandırmasını değiştirmek için `LastUsedBuildConfiguration` Yayımlama profilindeki özelliği değiştirin.

## <a name="see-also"></a>Ayrıca bkz.
 - [dotnet publish](https://docs.microsoft.com/dotnet/core/tools/dotnet-publish)
 - [Bir Web uygulamasını Visual Studio kullanarak Web sitesinde yayımlama](https://docs.microsoft.com/visualstudio/deployment/quickstart-deploy-to-a-web-site?view=vs-2019)