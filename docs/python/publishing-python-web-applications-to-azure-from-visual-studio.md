---
title: Python uygulamasını Azure Uygulama Hizmetinde yayımlama
description: Git dağıtımı ve Linux için kapsayıcılar ve IIS'de dağıtım dahil olmak üzere Bir Python uygulamasını Azure Uygulama Hizmetine yayımlama seçenekleri.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: c3c8d6c16f2f7e432b6b5e988bf63521f3dfc8c0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62784121"
---
# <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

Şu anda Python, Linux için Azure Uygulama Hizmeti'nde desteklenir ve bu makalede açıklandığı gibi [Git dağıtımı](#publish-to-app-service-on-linux-using-git-deploy) ve [kapsayıcıları](#publish-to-app-service-on-linux-using-containers)kullanarak uygulamaları yayımlayabilirsiniz.

> [!Note]
> Windows için Azure Uygulama Hizmeti'ndeki Python desteği resmi olarak küçümsür. Sonuç olarak, Visual Studio'daki **Yayımla** komutu yalnızca bir [IIS hedefi](#publish-to-iis)için resmi olarak desteklenir ve Azure Uygulama Hizmeti'nde uzaktan hata ayıklama artık resmi olarak desteklenmez.
>
> Ancak, Windows'daki Uygulama Hizmeti için Python uzantıları kullanılabilir durumda kaldığından, ancak servis edilmeyeceğini veya güncelleştirilmediği için, [Windows'da Uygulama Hizmeti'ne Yayımlama](publish-to-app-service-windows.md) özellikleri şimdilik hala çalışır.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Git dağıtımı kullanarak Linux'ta Uygulama Hizmetine yayımlama

Git deploy, Linux'taki bir Uygulama Hizmetini git deposunun belirli bir şubesine bağlar. Bu şubeye kod işlemek Otomatik Olarak App Hizmetine dağıtır ve Uygulama *Hizmeti, requirements.txt'de*listelenen bağımlılıkları otomatik olarak yükler. Bu durumda, Linux'taki App Service kodunuzu Gunicorn web sunucusunu kullanan önceden yapılandırılmış bir kapsayıcı görüntüsünde çalıştırın. Şu anda, bu hizmet Önizleme'dedir ve üretim kullanımı için desteklenmez.

Daha fazla bilgi için Azure belgelerinde aşağıdaki makalelere bakın:

- [Hızlı başlangıç: Uygulama Hizmeti'nde bir Python web uygulaması oluşturun,](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) basit bir Flask uygulamasını ve yerel bir Git deposundan dağıtım kullanarak Git dağıtma işleminin kısa bir geçiş sürecini sağlar.
- [Python nasıl yapılandırılabilen](/azure/app-service/containers/how-to-configure-python) Linux kapsayıcısındaki Uygulama Hizmetinin özelliklerini ve uygulamanız için Gunicorn başlangıç komutunu nasıl özelleştireceğimiz açıklanır.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Kapsayıcıları kullanarak Linux'ta Uygulama Hizmetine yayımlama

Linux'ta App Service ile önceden oluşturulmuş konteynere güvenmek yerine, kendi konteynırınızı sağlayabilirsiniz. Bu seçenek, hangi web sunucularını kullandığınızı seçmenize ve kapsayıcının davranışını özelleştirmenize olanak tanır.

Kapsayıcıoluşturmak, yönetmek ve itmek için iki seçenek vardır:

- Visual Studio Code ve Docker uzantısını kullanın, [Docker Konteynerlerini kullanarak Python'u Dağıt'ta](https://code.visualstudio.com/docs/python/tutorial-deploy-containers)açıklandığı gibi. Visual Studio Code'u kullanmasanız bile, makale, üretime hazır uwsgi ve nginx web sunucularını kullanarak Flask ve Django uygulamaları için konteyner görüntüleri oluşturma konusunda yararlı ayrıntılar sağlar. Daha sonra aynı kapsayıcıyı Azure CLI'yi kullanarak dağıtabilirsiniz.

- Azure belgelerinde [özel bir Docker görüntüsünü kullanma'da](/azure/app-service/containers/tutorial-custom-docker-image) açıklandığı gibi komut satırını ve Azure CLI'yi kullanın. Ancak bu kılavuz geneldir ve Python'a özgü değildir.

## <a name="publish-to-iis"></a>IIS'de yayımlayın

Visual Studio'dan, **Yayımla** komutuyla Windows sanal makinesine veya IIS özellikli başka bir bilgisayara yayımlayabilirsiniz. IIS'yi kullanırken, uygulamada Python yorumlayıcısını nerede bulacağını gösteren bir *web.config* dosyası oluşturduğunuzdan veya değiştirdiğinden emin olun. Daha fazla bilgi [için IIS için web uygulamalarını yapılandır'a](configure-web-apps-for-iis-windows.md)bakın.
