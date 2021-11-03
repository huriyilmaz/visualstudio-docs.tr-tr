---
title: Genel bakış yayımlama
description: Visual Studio'de Yayımla penceresi hakkında bilgi Visual Studio
ms.date: 10/14/2021
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish tool
- .NET applications, publishing
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2019'
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 4eefc0c2d4122d3e9b6b96f026fb9f823bb52dbd
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131130496"
---
# <a name="overview-of-publish"></a>Yayımlamaya Genel Bakış

Daha ASP.NET, .NET Core ve Python uygulamaları için Yayımla aracını kullanarak uygulamalarınızı dağıtabilirsiniz.

## <a name="what-is-publish"></a>Yayımla nedir?

Yayımla aracı uygulamanızı çeşitli hedeflere dağıtmanıza yardımcı olur. Kullanmaya başlayın projenize sağ tıklar ve Çözüm Gezgini menüsünde **Yayımla'yı** seçerek bu seçeneği belirleyin.

## <a name="how-does-it-work"></a>Nasıl çalışır?

Yayımlama, *tek bir proje* için birden çok proje yapılandırmasına ve birden çok yayımlama hedefine izin vermek için profilleri (.pubxml dosyaları) kullanır.

![profil yayımlama](./media/publish-profiles.png)

Profilin içeriği XML'tir ve MSBuild.

![profil örneği içeriklerini yayımlama](./media/publish-profile-example-contents.png)

Yayımla profili, kimlik bilgilerini iade almayan ayrı ve varsayılan olarak gizli bir dosyada tutar.

![gizli kullanıcı dosyaları](./media/separate-user-files.png)

Yayımlama profillerini IIS ve [Azure App Service'den](../deployment/tutorial-import-publish-settings-iis.md#create-the-publish-settings-file-in-iis-on-windows-server) her zaman [içeri Azure App Service](../deployment/tutorial-import-publish-settings-azure.md#create-the-publish-settings-file-in-azure-app-service)

![profili içeri aktarma](./media/import-profile.png)

## <a name="visual-studio-can-help-you-manage-dependencies-to-azure-services"></a>Visual Studio Azure hizmetleri bağımlılıklarını yönetmenize yardımcı olabilir

Uygulamanızı Azure'a dağıtmak için Yayımla aracını kullanarak Azure hizmetleri bağımlılıklarını yapılandırma fırsatınız olur.

![yayımlama sırasında bağımlılıklar](./media/publish-dependencies.png)

Burada fikir, farklı bir SQL veritabanına veya farklı bir Depolama hesabına ya da test, KALITE KONTROL, ön Key Vault gibi farklı ortamlar için farklı bir Key Vault hesabına bağlanmak istemeyebilirsiniz.
