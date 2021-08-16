---
title: Klasöre yayımlama
description: Bir klasöre uygulama yayımlamak için ASP.NET Core aracını kullanabilirsiniz.
ms.date: 01/22/2019
helpviewer_keywords:
- deployment, website
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: sayedihashimi
ms.author: sayedha
manager: unniravindranathan
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: 89adbc2c3b6ddef502fa615d9b01146016451c672d6dab9e3f8deeaa84a9a21f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121382634"
---
# <a name="publish-a-web-app-to-a-folder-using-visual-studio-for-mac"></a>Web uygulamasını bir klasöre yayımlamak için Mac için Visual Studio

Bir klasöre uygulama yayımlamak için ASP.NET Core aracını kullanabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- [Visual Studio 2017'nin yüklü](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2017) olduğu mac için ASP.NET Core.
- Bir ASP.NET Core projesi. Henüz bir projeniz yoksa yeni bir [tane oluşturabilirsiniz.](./create-new-projects.md?view=vsmac-2017&preserve-view=true)

## <a name="publish-to-folder"></a>Klasöre Yayımlama

Bu Mac için Visual Studio yayımla aracını kullanarak ASP.NET Core projelerinizi bir klasöre yayımlayın. Bir klasöre yayımlandıktan sonra dosyaları web sunucunuza aktararak farklı bir ortama aktarabilirsiniz. Bir klasöre yayımlamak için aşağıdaki adımları izleyin.

 1. Giriş Çözüm Bölmesi projeye sağ tıklayın ve Yayımla'yı **seçin.**

    ![Yayımla bağlam menüsü](media/publish-context-menu.png)

 2. Bu projeyi daha önce yayımladıysanız, yayımlama profilini menüde bulabilirsiniz. Yayımlama işlemini başlatmak için bu yayımlama profilini seçin.

 3. Bu projeyi bir klasöre ilk kez yayımlamak için Klasöre **Yayımla'yı seçin**

    ![Klasöre yayımla bağlam menüsü](media/publish-to-folder-context-menu.png)

 4. Klasöre **Yayımla iletişim** kutusu görüntülenir. Bu iletişim kutusunda projenin yayımlanacak klasörünü özelleştirebilirsiniz. Bunu yapmak için **Gözat** düğmesini kullanabilir veya bir yola yapıştırabilirsiniz.

 5. **Yayımla'ya** tıklayan birkaç şey olur. İlk olarak bir yayımlama profili oluşturulur. Yayımlama profili, MSBuild sırasında projeye aktarılan bir dosyadır. Yayımlama işlemi sırasında kullanılan özellikleri içerir. Bu dosyalar içinde depolanır `Properties/PublishProfiles` ve uzantısına sahip `.pubxml` olur. Ardından yayımlama işlemi başlatıldı. İlerleme durumunu izlemek için, çalışma çubuğundaki durum çubuğunu Mac için Visual Studio.

    ![Yayımla durumuna sahip IDE durum çubuğu](media/publish-to-folder-status-bar.png)

 6. Yayımlama başarıyla tamamlandıktan sonra yayımla klasörüne bir Bulıcı penceresi açılır. Yayımlama profili oluşturulduktan sonra Yayımla bağlam menüsünde görüntülenir.

    ![Klasör profili ile bağlam menüsünü yayımlama](media/publish-context-menu-with-folder-profile.png)

 7. Projeyi aynı ayarlarla yeniden yayımlamak için yayımlama bağlam menüsünde profile tıkabilirsiniz.

## <a name="customize-publish-options"></a>Yayımlama Seçeneklerini Özelleştirme

Yayımlama profilinin adını değiştirmek için (yayımlama bağlam menüsünde görüntülenir), yayımlama profili dosyasını yeniden adlandırır. Dosyanın uzantısını ( ) `.puxbml` değiştirmeyebilirsiniz.

Yayımlama klasörü yolunu değiştirmek için yayımlama profilini açın ve değeri `publishUrl` düzenleyin.

Kullanılan derleme yapılandırmasını değiştirmek için yayımlama `LastUsedBuildConfiguration` profilinde özelliğini değiştirme.