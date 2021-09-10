---
title: Klasöre yayımlama
description: yayımla aracını bir klasöre ASP.NET Core uygulamalar yayımlamak için kullanabilirsiniz.
ms.date: 01/22/2019
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: e2d1b0bb67c30daf13503196546f3280ceb7a635
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123962302"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak bir Web uygulamasını bir klasöre yayımlama

yayımla aracını bir klasöre ASP.NET Core uygulamalar yayımlamak için kullanabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- ASP.NET Core etkin olarak yüklenen [Mac için Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) .
- bir ASP.NET Core projesi. Zaten bir projeniz yoksa [Yeni bir tane oluşturabilirsiniz](./create-new-projects.md?view=vsmac-2017&preserve-view=true).

## <a name="publish-to-folder"></a>Klasöre Yayımlama

Mac için Visual Studio kullanarak ASP.NET Core projelerinizi yayımla aracını kullanarak bir klasöre yayımlayabilirsiniz. Bir klasöre yayımladıktan sonra, farklı bir ortama ulaşmak için dosyaları Web sunucunuza aktarabilirsiniz. Bir klasöre yayımlamak için aşağıdaki adımları izleyin.

 1. Çözüm Bölmesi projeye sağ tıklayın ve **Yayımla**' yı seçin.

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

Yayımlama profilinin adını değiştirmek için (Yayımla bağlam menüsünde görüntülenir), yayımlama profili dosyasını yeniden adlandırın. Dosyanın () uzantısını değiştirmediğinden emin olun `.puxbml` .

Yayımlama klasörü yolunu değiştirmek için yayımlama profilini açın ve `publishUrl` değeri düzenleyin.

Kullanılan yapı yapılandırmasını değiştirmek için `LastUsedBuildConfiguration` Yayımlama profilindeki özelliği değiştirin.