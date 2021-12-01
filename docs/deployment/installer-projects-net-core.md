---
description: uygulamaları msı olarak paketleme, genellikle Visual Studio Yükleyicisi projeleri uzantısı kullanılarak gerçekleştirilir.
title: Visual Studio Yükleyicisi projeleri ve .net 6,0
titleSuffix: ''
ms.date: 11/29/2021
ms.topic: conceptual
helpviewer_keywords:
- installer projects
- installer projects, .NETCore
author: MSLukeWest
ms.author: lukewest
manager: MSLukeWest
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 23c927de1cc6a40988679c9991cbb5cbafae90f3
ms.sourcegitcommit: 263703af9c4840e0e0876aa99df6dd7455c43519
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2021
ms.locfileid: "133387194"
---
# <a name="visual-studio-installer-projects-extension-and-net-60"></a>Visual Studio Yükleyicisi projeleri uzantısı ve .net 6,0

uygulamaları msı olarak paketleme, genellikle Visual Studio Yükleyicisi projeleri uzantısı kullanılarak gerçekleştirilir.

Bu makale, .NET Core 3,1, .NET 5 ve .NET 6 ' yı hedefleyen uygulamalar için geçerlidir.

Uzantıyı buradan indirebilirsiniz:

::: moniker range=">= vs-2022"
[Visual Studio Yükleyicisi projeleri](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2022InstallerProjects)
::: moniker-end
::: moniker range="vs-2019"
[Visual Studio Yükleyicisi projeleri](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)
::: moniker-end

## <a name="update-for-net-core"></a>.NET Core için güncelleştirme

.NET Core yayımlamanın iki farklı modeline sahiptir.

- Çerçeveye bağımlı dağıtımlar

- Kendi içinde bulunan uygulamalar çalışma zamanını içerir.

Bu dağıtım stratejileri hakkında daha fazla bilgi edinmek için bkz. [.NET Core uygulama yayımlamaya genel bakış](/dotnet/core/deploying/).

### <a name="workflow-changes-for-net-core-31-and-later-versions"></a>.NET Core 3,1 ve üzeri sürümler için iş akışı değişiklikleri

1. .NET Core 3,1, .NET 5,0 veya .NET 6,0 projeleri için doğru çıktıyı almak üzere **birincil çıkış** yerine **öğeleri yayımla** ' yı seçin.  bu iletişim kutusunu açmak için   >  projenin bağlam menüsünden **Project Output...** ekle öğesini seçin.

    ![Project çıkış grubu ekle iletişim kutusunda öğeleri yayımla çıkış grubu](../deployment/media/installer-projects-net-core-publish-items-output.png "Yayımlama öğelerini seçin")

2. Kendi kendine içerilen bir yükleyici oluşturmak için, doğru Özellikler ayarlanmış bir yayımlama profilinin göreli yolunu kullanarak, kurulum projesindeki **öğeleri yayımla** düğümünde **publishprofilepath** özelliğini ayarlayın.

    ![Öğeleri yayımla proje çıkış öğesinde yayımlama profilini ayarlama](../deployment/media/installer-projects-net-core-publish-profile.png "Yayımlama profilini ayarla")

>[!NOTE]
>bu iş akışı ASP.NET Core uygulamalar için desteklenmez, yalnızca masaüstü uygulamaları Windows.

### <a name="prerequisites"></a>Önkoşullar

Yükleyicinizin, çerçeveye bağımlı bir .NET Core 3,1, .NET 5,0 veya .NET 6,0 uygulaması için gerekli çalışma zamanını yükleyebilmesini isterseniz, bunu [önkoşulları](../deployment/application-deployment-prerequisites.md)kullanarak yapabilirsiniz.  Yükleyici projenizin Özellikler iletişim kutusunda **Önkoşullar...** iletişim kutusunu açın ve aşağıdaki girdileri görürsünüz:

![Önkoşullar iletişim kutusunda .NET Core öğeleri](../deployment/media/installer-projects-net-core-prerequisites.png ".NET Core önkoşulları")

**.NET Core Runtime...** seçeneği konsol uygulamaları için seçilmelidir, **.net Masaüstü çalışma zamanı...** WPF/WinForms uygulamaları için seçilmelidir.

>[!NOTE]
>bu öğeler Visual Studio 2019 güncelleştirme 7 sürümünden başlayarak mevcuttur.

## <a name="see-also"></a>Ayrıca bkz.

- [Önkoşullar İletişim Kutusu](../ide/reference/prerequisites-dialog-box.md)
- [Uygulama dağıtımı önkoşulları](../deployment/application-deployment-prerequisites.md)
