---
title: Klasöre yayımlama
description: Web uygulamasını bir klasöre yayımlamak için Mac için Visual Studio.
ms.date: 11/09/2020
helpviewer_keywords:
- deployment, website, console, publish
ms.assetid: e963fb4b-6d32-4d45-86bb-ef7e4d3028b0
author: jmatthiesen
ms.author: jomatthi
manager: dominicn
ms.prod: visual-studio-mac
ms.topic: how-to
ms.openlocfilehash: c8da51de58abeb070e327aab7c4b7612891c1075
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135803667"
---
# <a name="publish-to-a-folder-using-visual-studio-for-mac"></a>Mac için Visual Studio kullanarak bir klasöre yayımlama

.NET Core Konsolunu yayımlamak veya uygulamaları bir ASP.NET Core yayımlamak için Yayımla aracını kullanabilirsiniz.

## <a name="prerequisites"></a>Önkoşullar

- Visual Studio .NET Core etkin olarak yüklenmiş Mac için [2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs4mac2019) sürümü.
- Bir .NET Core konsolu veya ASP.NET Core projesi. Henüz bir projeniz yoksa yeni bir [tane oluşturabilirsiniz.](./create-new-projects.md)

## <a name="publish-to-folder"></a>Klasöre Yayımlama

Bu Mac için Visual Studio.NET Core projelerinizi Yayımla aracını kullanarak bir klasöre yayımlayın. Bir klasöre yayımlandıktan sonra dosyaları farklı bir ortama aktarabilirsiniz. Bir klasöre yayımlamak için aşağıdaki adımları izleyin.

 1. Çözüm Penceresinde projeye sağ tıklayın ve Yayımla'yı **seçin.**

    ![Yayımla bağlam menüsü](media/publish-context-menu.png)

 2. Bu projeyi daha önce yayımladıysanız, yayımlama profilini menüde bulabilirsiniz. Yayımlama işlemini başlatmak için bu yayımlama profilini seçin.

 3. Bu projeyi bir klasöre ilk kez yayımlamak için Klasöre **Yayımla'yı seçin**

    ![Klasöre yayımla bağlam menüsü](media/publish-to-folder-context-menu.png)

 4. Klasöre **Yayımla iletişim** kutusu görüntülenir. Bu iletişim kutusunda projenin yayımlanacak klasörünü özelleştirebilirsiniz. Bunu yapmak için **Gözat** düğmesini kullanabilir veya bir yola yapıştırabilirsiniz.

 5. **Yayımla'ya** tıklayan birkaç şey olur. İlk olarak bir yayımlama profili oluşturulur. Yayımlama profili, MSBuild projeye aktarılan bir dosyadır. Yayımlama işlemi sırasında kullanılan özellikleri içerir. Bu dosyalar içinde depolanır `Properties/PublishProfiles` ve uzantısına sahip `.pubxml` olur. Ardından yayımlama işlemi başlatıldı. İlerleme durumunu izlemek için, çalışma çubuğundaki durum çubuğunu Mac için Visual Studio.

    ![Yayımla durumuna sahip IDE durum çubuğu](media/publish-to-folder-status-bar.png)

 6. Yayımlama başarıyla tamamlandıktan sonra yayımla klasörüne bir Bulıcı penceresi açılır. Yayımlama profili oluşturulduktan sonra Yayımla bağlam menüsünde görüntülenir.

    ![Klasör profili ile bağlam menüsünü yayımlama](media/publish-context-menu-with-folder-profile.png)

 7. Projeyi aynı ayarlarla yeniden yayımlamak için yayımlama bağlam menüsünde profile tıkabilirsiniz.

## <a name="customize-publish-options"></a>Yayımlama Seçeneklerini Özelleştirme

Yayımlama profilinin adını değiştirmek için (yayımlama bağlam menüsünde görüntülenir), yayımlama profili dosyasını yeniden adlandırır. Dosyanın uzantısını ( ) `.pubxml` değiştirmeyebilirsiniz.

Yayımlama klasörü yolunu değiştirmek için yayımlama profilini açın ve değeri `publishUrl` düzenleyin.

Kullanılan derleme yapılandırmasını değiştirmek için yayımlama `LastUsedBuildConfiguration` profilinde özelliğini değiştirme.

## <a name="see-also"></a>Ayrıca bkz.
 - [dotnet publish](/dotnet/core/tools/dotnet-publish)
 - [Web uygulamasını kullanarak web sitesinde yayımlama Visual Studio](/visualstudio/deployment/quickstart-deploy-to-a-web-site?view=vs-2019&preserve-view=true)
 - [IIS'ASP.NET Core uygulama yayımlama](/aspnet/core/tutorials/publish-to-iis?view=aspnetcore-5.0&tabs=visual-studio&preserve-view=true)
