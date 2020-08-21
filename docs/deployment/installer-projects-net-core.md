---
title: Visual Studio Yükleyicisi projeleri ve .NET Core 3,1
ms.date: 08/18/2020
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
ms.openlocfilehash: c35e6a12262083d09575b51f6c9f918ba30a27b1
ms.sourcegitcommit: de98ed7edc81383e47b87ae6e61143fbbbe7bc56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2020
ms.locfileid: "88714452"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Visual Studio Yükleyicisi projeleri uzantısı ve .NET Core 3,1

Uygulamaları MSI olarak paketleme, genellikle Visual Studio Yükleyicisi projeleri uzantısı kullanılarak gerçekleştirilir.

Uzantıyı buradan indirebilirsiniz: [Visual Studio yükleyicisi projeler](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>.NET Core için güncelleştirme
.NET Core yayımlamanın iki farklı modeline sahiptir.

- Çerçeveye bağımlı dağıtımlar

- Kendi içinde bulunan uygulamalar çalışma zamanını içerir.

Bu dağıtım stratejileri hakkında daha fazla bilgi edinmek için bkz. [.NET Core uygulama yayımlamaya genel bakış](https://docs.microsoft.com/dotnet/core/deploying/).

### <a name="workflow-changes-for-net-core-31"></a>.NET Core 3,1 için iş akışı değişiklikleri

1. .NET Core 3,1 projeleri için doğru çıktıyı almak üzere **birincil çıkış** yerine **öğeleri yayımla** ' yı seçin.  Bu iletişim kutusunu açmak için **Add**  >  projenin bağlam menüsünden**Proje çıktısı Ekle...** seçeneğini belirleyin.

    ![Proje çıkış grubu Ekle iletişim kutusunda öğeleri yayımla çıkış grubu](../deployment/media/installer-projects-net-core-publish-items-output.png "Yayımlama öğelerini seçin")

2. Kendi kendine içerilen bir yükleyici oluşturmak için, doğru Özellikler ayarlanmış bir yayımlama profilinin göreli yolunu kullanarak, kurulum projesindeki **öğeleri yayımla** düğümünde **publishprofilepath** özelliğini ayarlayın.

    ![Öğeleri yayımla proje çıkış öğesinde yayımlama profilini ayarlama](../deployment/media/installer-projects-net-core-publish-profile.png "Yayımlama profilini ayarla")

### <a name="prerequisites-for-net-core-31"></a>.NET Core 3,1 önkoşulları

Yükleyicinizin, çerçeveye bağımlı bir .NET Core 3,1 uygulaması için gerekli çalışma zamanını yükleyebilmesini isterseniz, bunu [önkoşulları](../deployment/application-deployment-prerequisites.md)kullanarak yapabilirsiniz.  Yükleyici projenizin Özellikler iletişim kutusunda **Önkoşullar...** iletişim kutusunu açın ve aşağıdaki girdileri görürsünüz:

![Önkoşullar iletişim kutusunda .NET Core öğeleri](../deployment/media/installer-projects-net-core-prerequisites.png ".NET Core önkoşulları")

**.NET Core Runtime...** seçeneği konsol uygulamaları için seçilmelidir, **.net Masaüstü çalışma zamanı...** WPF/WinForms uygulamaları için seçilmelidir.

>[!NOTE]
>Bu öğeler, Visual Studio 2019 güncelleştirme 7 sürümünden itibaren bulunur.

## <a name="see-also"></a>Ayrıca bkz.

- [Önkoşullar İletişim Kutusu](../ide/reference/prerequisites-dialog-box.md)
- [Uygulama dağıtımı önkoşulları](../deployment/application-deployment-prerequisites.md)
