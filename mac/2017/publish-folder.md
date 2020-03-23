---
title: Klasörde yayımlama
ms.date: 01/22/2019
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.openlocfilehash: 02175180e5217a14a4464e46c75d519adab2a332
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "73714499"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>Mac için Visual Studio'u kullanarak bir klasöre Web uygulaması yayımlama

ASP.NET Core uygulamalarını bir klasörde yayımlamak için Yayımla aracını kullanabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017 Mac için](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) ASP.NET Core özellikli yüklü.
- Bir ASP.NET Core projesi. Zaten bir projeniz yoksa, yeni [bir](/visualstudio/mac/create-new-projects?view=vsmac-2017)proje oluşturabilirsiniz.

## <a name="publish-to-folder"></a>Klasöre Yayımlama

Mac için Visual Studio'yu kullanarak ASP.NET Core projelerinizi Yayımlama aracını kullanarak bir klasöre yayımlayabilirsiniz. Bir klasöre yayımladıktan sonra dosyaları farklı bir ortama almak için web sunucunuza aktarabilirsiniz. Bir klasörde yayımlamak için aşağıdaki adımları izleyin.

 1. Çözüm Defteri'nde projeyi sağ tıklatın ve **Yayımla'yı**seçin.

    ![Bağlam menüsünü yayımla](media/publish-context-menu.png)

 2. Bu projeyi daha önce yayımladıysanız, menüde yayımlama profilini görürsünüz. Yayımlama işlemini başlatmak için yayımlama profilini seçin.

 3. Bu projeyi ilk kez bir klasörde yayımlamak için **Klasöre Yayımla'yı** seçin

    ![Klasör bağlam menüsüne yayımlama](media/publish-to-folder-context-menu.png)

 4. **Klasöre Yayımla** iletişim kutusu görüntülenir. Bu iletişim kutusunda projenin yayımlanacağı klasörü özelleştirebilirsiniz. Bunu yapmak için **Gözat** düğmesini kullanabilir veya bir yola yapıştırabilirsiniz.

 5. Birkaç şey **olur yayımla'yı** tıklattıktan sonra. Önce bir yayımlama profili oluşturulur. Yayımlama profili, yayımlama işlemi sırasında projeye aktarılan bir MSBuild dosyasıdır. Yayımlama işlemi sırasında kullanılan özellikleri içerir. Bu dosyalar depolanır `Properties/PublishProfiles` ve uzantısı `.pubxml`var. Ardından, yayımlama işlemi başlatılır. Mac için Visual Studio'daki durum çubuğunu izleyerek ilerlemeyi izleyebilirsiniz.

    ![Yayımlama durumu olan IDE durum çubuğu](media/publish-to-folder-status-bar.png)

 6. Yayımlama başarıyla tamamlandıktan sonra bir Finder penceresi yayımlama klasörüne açılır. Artık bir yayımlama profili oluşturulduğuna göre, yayımlama bağlamında menüsünde görüntülenir.

    ![Klasör profili ile bağlam menüsünü yayımlama](media/publish-context-menu-with-folder-profile.png)

 7. Aynı ayarlarla projeyi yeniden yayınlamak için yayımlama bağlamı menüsündeki profile tıklayabilirsiniz.

## <a name="customize-publish-options"></a>Yayımlama Seçeneklerini Özelleştir

Yayımlama profilinin adını değiştirmek için (yayımlama bağlamında menüsünde görüntülenir), yayımlama profili dosyasını yeniden adlandırın. Dosyanın uzantısını değiştirmediğinden emin`.puxbml`olun ( ).

Yayımlama klasörü yolunu değiştirmek için yayımlama `publishUrl` profilini açın ve değeri edin.

Kullanılan yapı yapılandırmasını değiştirmek için `LastUsedBuildConfiguration` yayımlama profilindeki özelliği değiştirin.