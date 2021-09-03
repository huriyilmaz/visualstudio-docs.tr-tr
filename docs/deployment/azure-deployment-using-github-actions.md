---
title: GitHub Actions kullanarak Azure'a dağıtma
description: Visual Studio tarafından oluşturulan GitHub Actions iş akışlarını kullanarak uygulamanızı Azure'a dağıtmayı Visual Studio
ms.date: 08/31/2021
ms.topic: tutorial
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
ms.openlocfilehash: fa9a9a8d052a4003dc15b454df21b90cf956d069
ms.sourcegitcommit: 9a340611faaaa143946b3ede66ee84ec19108b09
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2021
ms.locfileid: "123423084"
---
# <a name="deploy-your-application-to-azure-using-github-actions-workflows-created-by-visual-studio"></a>Visual Studio tarafından oluşturulan GitHub Actions iş akışlarını kullanarak uygulamanızı Azure'a Visual Studio
2019 Visual Studio 16.11 sürümünden başlayarak, GitHub.com'da barındırılan .NET projeleri için yeni GitHub Eylemi iş akışları oluşturabilirsiniz.

## <a name="how-does-it-work"></a>Nasıl çalışır?
Bu Çözüm Gezgini, GitHub.com'da barındırılan projenize sağ tıklayın ve Yayımla'yı **seçin**

![Yayımla'ya > tıklayın](./media/solution-explorer-publish.png)

Sonraki ekranda Azure ve **Sonraki'yi** **seçin**

![Azure'ı seçme](./media/wizard-azure.png)

Proje [türünüze bağlı olarak,](#which-project-types-are-supported) seçerek farklı bir Azure hizmeti listesi alırsiniz. İhtiyaçlarınızı karşılamak [için desteklenen Azure](#which-azure-services-are-supported) hizmetlerinden birini seçme.

![projeniz için uygun Azure hizmetini seçme](./media/wizard-pick-azure-service.png)

Sihirbazın son adımını, GitHub Actions iş akışlarını **kullanarak CI/CD'yi seçin (yml** dosyası üretir) ve ardından Son'a **tıklayın.**

![GitHub Actions iş akışlarını kullanan CI/CD (yml dosyası üretir)](./media/wizard-final-step.png)

Visual Studio actions iş GitHub yeni bir iş akışı oluşturulur ve bunu işlemeyi ve GitHub.com'a gönderin.

![işleme ve itme](./media/summary-commit-and-push.png)

Yerleşik Git araç aracını kullanarak bu adımı tamamlarsanız Visual Studio iş akışının yürütülmesini algılar. [](../version-control/git-with-visual-studio.md#git-changes-window)

![iş akışı çalışıyor](./media/summary-workflow-running.png)

## <a name="setting-the-github-secrets"></a>Gizli dizileri GitHub ayarlama
Oluşturulan iş akışının Azure'a başarıyla dağıtımı için bir yayımlama profiline [erişim gerekli olabilir](/azure/app-service/deploy-github-actions?tabs=applevel#configure-the-github-secret) 

![bir github gizli dizisi](./media/summary-one-github-secret.png)

Başarılı bir dağıtım için hizmet sorumlusuna erişim [de gerekli olabilir](/azure/app-service/deploy-github-actions?tabs=userlevel#configure-the-github-secret)

![iki github gizli dizisi](./media/summary-two-github-secrets.png)

Her durumda Visual Studio doğru değerle GitHub gizli diziyi ayarlamaya çalışır. Başarısız olursa, bunu size haber ve sonra tekrar deneme fırsatı sağlar.

![github gizli dizisi eksik](./media/summary-one-github-secret-missing.png)

Gizli diziyi yeniden ayarlayamazsa Visual Studio gizli diziye el ile erişim elde etme fırsatı sunar. Bu nedenle, gizli dizide yer alan repo sayfasından işlemi github.com.

![eksik github gizli dizilerini ayarlama](./media/summary-set-github-secret.png)

## <a name="which-project-types-are-supported"></a>Hangi proje türleri destekleni?
 * ASP.NET Core
 * ASP.NET 5 ve üzeri
 * Azure İşlevleri

## <a name="which-azure-services-are-supported"></a>Hangi Azure hizmetleri desteklemektedir?
* Azure Web Apps
* Azure İşlevleri
* Azure API Management
