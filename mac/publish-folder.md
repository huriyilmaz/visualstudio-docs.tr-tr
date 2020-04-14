---
title: Klasörde yayımlama
ms.date: 04/02/2019
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.openlocfilehash: 0ea70fb1a5898e2415b7f74e93233ca03ea52c45
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224504"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Mac için Visual Studio'u kullanarak bir klasörde yayımlama

.NET Core Console veya ASP.NET Core uygulamalarını bir klasörde yayımlamak için Yayımla aracını kullanabilirsiniz.

## <a name="prerequisites"></a>Ön koşullar

- .NET Core ile yüklenen [Mac için Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) etkinleştirildi.
- .NET Core konsolu veya ASP.NET Core projesi. Zaten bir projeniz yoksa, yeni [bir](/visualstudio/mac/create-new-projects?view=vsmac-2019)proje oluşturabilirsiniz.

## <a name="publish-to-folder"></a>Klasöre Yayımlama

Mac için Visual Studio'yu kullanarak .NET Core projelerinizi Yayımlama aracını kullanarak bir klasörde yayımlayabilirsiniz. Bir klasöre yayımladıktan sonra dosyaları farklı bir ortama aktarabilirsiniz. Bir klasörde yayımlamak için aşağıdaki adımları izleyin.

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

Yayımlama profilinin adını değiştirmek için (yayımlama bağlamında menüsünde görüntülenir), yayımlama profili dosyasını yeniden adlandırın. Dosyanın uzantısını değiştirmediğinden emin`.pubxml`olun ( ).

Yayımlama klasörü yolunu değiştirmek için yayımlama `publishUrl` profilini açın ve değeri edin.

Kullanılan yapı yapılandırmasını değiştirmek için `LastUsedBuildConfiguration` yayımlama profilindeki özelliği değiştirin.
