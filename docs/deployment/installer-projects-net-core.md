---
description: Uygulamaları MSI olarak paketleme genellikle Visual Studio Yükleyicisi Projeleri Uzantısı kullanılarak kullanılmaktadır.
title: Visual Studio Yükleyicisi Projeler ve .NET Core 3.1
titleSuffix: ''
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
ms.openlocfilehash: 95e3b044c3f4f3ce72e15704874c2d8e03e3a2e3868ead006d1fab0635be9072
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121418440"
---
# <a name="visual-studio-installer-projects-extension-and-net-core-31"></a>Visual Studio Yükleyicisi Projeleri Uzantısı ve .NET Core 3.1

Uygulamaları MSI olarak paketleme genellikle Visual Studio Yükleyicisi Projeleri Uzantısı kullanılarak kullanılmaktadır.

Uzantıyı buradan indirebilirsiniz: [Visual Studio Yükleyicisi Projeleri](https://marketplace.visualstudio.com/items?itemName=VisualStudioClient.MicrosoftVisualStudio2017InstallerProjects)

## <a name="update-for-net-core"></a>.NET Core için güncelleştirme
.NET Core'un yayımlama için iki farklı modeli vardır.

- Çerçeveye bağımlı dağıtımlar

- Kendi içinde uygulamalar çalışma zamanı içerir.

Bu dağıtım stratejileri hakkında daha fazla bilgi edinmek için bkz. [.NET Core uygulama yayımlamaya genel bakış.](/dotnet/core/deploying/)

### <a name="workflow-changes-for-net-core-31"></a>.NET Core 3.1 için iş akışı değişiklikleri

1. .NET Core 3.1 **projeleri** için doğru çıkışı almak için Birincil Çıkış yerine Öğeleri Yayımla'yı seçin.   Bu iletişim kutusunu açmak için **projenin**  >  **Project...** öğesini seçin.

    ![Öğeleri Yayımla çıkış grubu, Project Grubu Ekle iletişim kutusunda](../deployment/media/installer-projects-net-core-publish-items-output.png "Öğeleri Yayımla'yı seçin")

2. Kendi içinde bir yükleyici oluşturmak için, doğru özellikler kümesine sahip bir yayımlama profilinin göreli yolunu kullanarak kurulum projesinde Öğeleri Yayımla düğümünde **PublishProfilePath** özelliğini ayarlayın. 

    ![Öğeleri Yayımla proje çıkış öğesinde yayımlama profilini ayarlama](../deployment/media/installer-projects-net-core-publish-profile.png "Yayımlama Profili Ayarlama")

### <a name="prerequisites-for-net-core-31"></a>.NET Core 3.1 önkoşulları

Yükleyicinizin, çerçeveye bağımlı bir .NET Core 3.1 uygulaması için gerekli çalışma zamanını yükleye biliyorsanız, önkoşulları kullanarak [bunu yapabiliriz.](../deployment/application-deployment-prerequisites.md)  Yükleyici projenizin özellikler iletişim kutusunda **Önkoşullar...** iletişim kutusunu açın; aşağıdaki girişleri görüntülenir:

![Önkoşullar iletişim kutusundaki .NET Core öğeleri](../deployment/media/installer-projects-net-core-prerequisites.png ".NET Core Önkoşulları")

Konsol **uygulamaları için .NET Core** Çalışma Zamanı... seçeneği seçilmelidir, WPF/WinForms uygulamaları için .NET Masaüstü Çalışma **Zamanı...** seçili olmalıdır.

>[!NOTE]
>Bu öğeler, Visual Studio 2019 Güncelleştirme 7 sürümüyle başlayarak mevcuttur.

## <a name="see-also"></a>Ayrıca bkz.

- [Önkoşullar İletişim Kutusu](../ide/reference/prerequisites-dialog-box.md)
- [Uygulama Dağıtımı Önkoşulları](../deployment/application-deployment-prerequisites.md)
