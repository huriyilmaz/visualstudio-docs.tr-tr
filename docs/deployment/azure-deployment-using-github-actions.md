---
title: GitHub Actions kullanarak Azure'a dağıtma
description: Visual Studio tarafından oluşturulan GitHub Actions iş akışlarını kullanarak uygulamanızı Azure'a Visual Studio
ms.date: 12/06/2021
ms.topic: how-to
helpviewer_keywords:
- deployment, GitHub Actions
- GitHub Actions, publish
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 21e6ed4123735ac2aa9dcead8451a6f4998b49a5
ms.sourcegitcommit: 64d6c5cf93984bbb22812577af17128cd2239f79
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2021
ms.locfileid: "134366923"
---
# <a name="deploy-your-application-to-azure-using-github-actions-workflows-created-by-visual-studio"></a>Uygulama tarafından oluşturulan GitHub Actions iş akışlarını kullanarak uygulamanızı Azure'a Visual Studio

Visual Studio 2019 sürüm 16.11'den başlayarak, GitHub.com'da barındırılan .NET projeleri için yeni GitHub Eylemi iş akışları oluşturabilirsiniz.

## <a name="how-does-it-work"></a>Nasıl çalışır?

Bu Çözüm Gezgini, GitHub.com'da barındırılan projenize sağ tıklayın ve Yayımla'yı **seçin.**

![Yayımla'ya > tıklayın](./media/solution-explorer-publish.png)

Sonraki ekranda Azure'ı ve **ardından Sonraki'yi** **seçin.**

![Azure'ı seçme](./media/wizard-azure.png)

Projenizin [türüne bağlı olarak,](#which-project-types-are-supported)seçim yapmak için farklı bir Azure hizmeti listesi alırsiniz. İhtiyaçlarınızı karşılamak [için desteklenen Azure](#which-azure-services-are-supported) hizmetlerinden birini seçme.

![projeniz için uygun Azure hizmetini seçme](./media/wizard-pick-azure-service.png)

Sihirbazın son adımını, GitHub Actions iş akışlarını **kullanarak CI/CD'yi seçin (yml** dosyası üretir) ve ardından Son'a **tıklayın.**

![GitHub Actions iş akışlarını kullanan CI/CD (yml dosyası üretir)](./media/wizard-final-step.png)

Visual Studio Actions iş akışı GitHub ve işlemeyi ve GitHub.com'a GitHub.

![işleme ve itme](./media/summary-commit-and-push.png)

Bu adımı yerleşik [Git](../version-control/git-with-visual-studio.md?view=vs-2019&preserve-view=true#git-changes-window-in-visual-studio-2019)aracını kullanarak tamamlarsanız, Visual Studio iş akışının yürütülmesini algılar.

![iş akışı çalışıyor](./media/summary-workflow-running.png)

## <a name="setting-the-github-secrets"></a>Gizli dizileri GitHub ayarlama

Oluşturulan iş akışının Azure'a başarıyla dağıtılana kadar bir yayımlama profiline [erişimi olabilir.](/azure/app-service/deploy-github-actions?tabs=applevel#configure-the-github-secret)

![bir github gizli dizisi](./media/summary-one-github-secret.png)

Başarılı bir dağıtım için hizmet sorumlusuna erişim [de gerekli olabilir.](/azure/app-service/deploy-github-actions?tabs=userlevel#configure-the-github-secret)

![iki github gizli dizisi](./media/summary-two-github-secrets.png)

Her durumda, Visual Studio doğru değerle GitHub gizli diziyi ayarlamaya çalışır. Başarısız olursa bunu size haber verecek ve yeniden deneme fırsatı verecek.

![github gizli dizisi eksik](./media/summary-one-github-secret-missing.png)

Gizli diziyi yeniden ayarlayamazsa Visual Studio gizli diziye el ile erişim elde etme fırsatı verir. Böylece, gizli dizinin sayfasındaki repo github.com.

![eksik github gizli dizilerini ayarlama](./media/summary-set-github-secret.png)

## <a name="which-project-types-are-supported"></a>Hangi proje türleri destekleni?

* ASP.NET Core
* ASP.NET 5 ve üzeri
* Azure İşlevleri

## <a name="which-azure-services-are-supported"></a>Hangi Azure hizmetleri desteklemektedir?

* Azure Web Apps
* Azure İşlevleri
* Azure API Management
