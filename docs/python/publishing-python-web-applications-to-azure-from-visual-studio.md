---
title: Azure App Service için bir Python uygulaması yayımlama
description: Bir Python uygulamasını Linux için git dağıtımı ve kapsayıcıları ve IIS 'e dağıtma dahil olmak üzere Azure App Service yayımlama seçenekleri.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b2848a54ddbce41b538bf58f82db42ede76026d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912410"
---
# <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

Mevcut olduğunda Python, Linux için Azure App Service desteklenir ve bu makalede açıklandığı gibi [Git dağıtımı](#publish-to-app-service-on-linux-using-git-deploy) ve [kapsayıcıları](#publish-to-app-service-on-linux-using-containers)kullanarak uygulama yayımlayabilirsiniz.

> [!Note]
> Windows için Azure App Service Python desteği resmi olarak kullanım dışıdır. Sonuç olarak, Visual Studio 'daki **Yayımla** komutu resmi olarak yalnızca bir [IIS hedefi](#publish-to-iis)için desteklenir ve Azure App Service üzerinde uzaktan hata ayıklama artık resmi olarak desteklenmez.
>
> Ancak Windows özelliklerinde [App Service yayımlama](publish-to-app-service-windows.md) , windows üzerinde App Service için Python uzantıları kullanılabilir olmaya devam ettiğinden, ancak hizmet verilmeyecektir veya güncelleştirilemediği için yine de çalışır.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Git dağıtımını kullanarak Linux üzerinde App Service yayımlama

Git Deploy, Linux üzerinde App Service bir git deposunun belirli bir dalına bağlar. Bu dala kod yürütme, otomatik olarak App Service dağıtır ve App Service *requirements.txt* listelenen tüm bağımlılıkları otomatik olarak yüklüyor. Bu durumda, Linux üzerinde App Service, kodunuzu Gunic, Web sunucusunu kullanan önceden yapılandırılmış bir kapsayıcı görüntüsünde çalıştırır. Bu hizmet, şu anda önizleme aşamasındadır ve üretim kullanımı için desteklenmez.

Daha fazla bilgi için Azure belgelerinde aşağıdaki makalelere bakın:

- [Hızlı başlangıç: App Service bir Python web uygulaması oluşturma](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) basit bir Flask uygulaması ve yerel bir git deposundan dağıtım kullanılarak git dağıtım işlemine kısa bir yol sağlar.
- [Python 'u yapılandırma](/azure/app-service/containers/how-to-configure-python) Linux kapsayıcısında App Service özelliklerini açıklar ve uygulamanız Için gunicgınstartup komutunu nasıl özelleştireceğinizi açıklar.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Kapsayıcıları kullanarak Linux üzerinde App Service yayımlama

Linux üzerinde App Service önceden oluşturulmuş kapsayıcıya güvenmek yerine kendi kapsayıcınızı sağlayabilirsiniz. Bu seçenek, kullandığınız Web sunucularını seçmenizi ve kapsayıcının davranışını özelleştirmenizi sağlar.

Kapsayıcıları derlemek, yönetmek ve göndermek için iki seçenek vardır:

- [Docker kapsayıcılarını kullanarak Python dağıtma](https://code.visualstudio.com/docs/python/tutorial-deploy-containers)bölümünde açıklandığı gibi Visual Studio Code ve Docker uzantısını kullanın. Visual Studio Code kullanmasanız bile, bu makalede, üretim-Ready uwsgi ve NGINX web sunucularını kullanarak Flask ve Docgo uygulamalarına yönelik kapsayıcı görüntüleri oluşturmaya yönelik faydalı Ayrıntılar sunulmaktadır. Azure CLı kullanarak aynı kapsayıcıyı dağıtabilirsiniz.

- Azure belgelerindeki [özel bir Docker görüntüsü kullanma](/azure/app-service/containers/tutorial-custom-docker-image) bölümünde açıklandığı gibi, komut satırını ve Azure CLI 'yi kullanın. Bu kılavuz genel, ancak ve Python 'a özgü değildir.

## <a name="publish-to-iis"></a>IIS 'de Yayımla

Visual Studio 'da **Yayımla** komutuyla bir Windows sanal makinesine veya diğer IIS özellikli bilgisayarlara yayımlayabilirsiniz. IIS kullanırken, uygulamada Python yorumlayıcısını bulma konusunda IIS 'ye bildiren bir *web.config* dosyası oluşturmayı veya değiştirmeyi unutmayın. Daha fazla bilgi için bkz. [IIS için Web uygulamalarını yapılandırma](configure-web-apps-for-iis-windows.md).
