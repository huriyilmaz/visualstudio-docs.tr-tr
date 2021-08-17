---
title: Python uygulamasını Azure App Service
description: Linux için Git dağıtımı ve kapsayıcıları Azure App Service IIS'ye dağıtma dahil olmak üzere python uygulamasını yayımlama seçenekleri.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f8338ea3810c45758029694fd3725e0ecf924b01
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027311"
---
# <a name="publish-to-azure-app-service"></a>Azure App Service’e yayımlama

Şu anda Python, Linux için Azure App Service desteklemektedir ve bu makalede açıklandığı [](#publish-to-app-service-on-linux-using-containers)gibi [Git](#publish-to-app-service-on-linux-using-git-deploy) dağıtımı ve kapsayıcıları kullanarak uygulama yayımabilirsiniz.

> [!Note]
> Windows için Azure App Service Python desteği resmi olarak kullanım dışıdır. Sonuç olarak,  Visual Studio'daki Yayımla komutu yalnızca [bir IIS](#publish-to-iis)hedefi için resmi olarak de desteklene ve Azure App Service uzaktan hata ayıklama artık resmi olarak desteklenmeyecektir.
>
> Ancak [App Service](publish-to-app-service-windows.md) Windows'da App Service Için Python uzantıları kullanılabilir olmaya devam Windows hizmet ve güncelleştirmeden önce kullanılabilir olmaya devam ediyor.

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>Git dağıtımı Linux üzerinde App Service yayımlama

Git dağıtımı, Linux üzerinde App Service Git deposunun belirli bir dalına bağlar. Bu dala kod işlenirse otomatik olarak App Service ve App Service içinde listelenen bağımlılıkları otomatik olarak *requirements.txt.* Bu durumda, Linux üzerinde App Service Gunicorn web sunucusunu kullanan önceden yapılandırılmış bir kapsayıcı görüntüsünde çalıştırır. Şu anda bu hizmet Önizlemededir ve üretimde kullanım için desteklenmiyor.

Daha fazla bilgi için Azure belgelerinde aşağıdaki makalelere bakın:

- [Hızlı Başlangıç:](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json) App Service'de Python web uygulaması oluşturma, basit bir Flask uygulaması kullanarak Git dağıtma işleminin kısa bir adım adım kılavuz ve yerel Git deposundan dağıtım sağlar.
- [Python'ın yapılandırılması,](/azure/app-service/containers/how-to-configure-python) Linux üzerinde App Service kapsayıcının özelliklerini ve gunicorn başlangıç komutunun nasıl özelleştirebileceğinizi açıklar.

## <a name="publish-to-app-service-on-linux-using-containers"></a>Kapsayıcıları kullanarak Linux üzerinde App Service yayımlama

Önceden Linux üzerinde App Service kapsayıcıya güvenmek yerine kendi kapsayıcınızı sabilirsiniz. Bu seçenek, hangi web sunucularını kullanabileceğinizi ve kapsayıcının davranışını özelleştirmenizi sağlar.

Kapsayıcıları oluşturmak, yönetmek ve itmek için iki seçenek vardır:

- Docker kapsayıcılarını Visual Studio Code Python'ı dağıtma konusunda açıklandığı gibi Visual Studio Code [ve Docker uzantısını kullanın.](https://code.visualstudio.com/docs/python/tutorial-deploy-containers) Visual Studio Code kullanmasanız bile makale, üretime hazır uwsgi ve nginx web sunucularını kullanarak Flask ve Django uygulamaları için kapsayıcı görüntüleri yapmaya ilişkin yararlı ayrıntılar sağlar. Daha sonra azure CLI kullanarak aynı kapsayıcıyı dağıtabilirsiniz.

- Azure belgelerinde Özel [Docker](/azure/app-service/containers/tutorial-custom-docker-image) görüntüsü kullanma konusunda açıklandığı gibi komut satırı ve Azure CLI kullanın. Ancak bu kılavuz geneldir ve Python'a özgü değildir.

## <a name="publish-to-iis"></a>IIS'de yayımlama

Bu Visual Studio, Yayımla komutuyla Windows bir sanal makineye veya IIS  özellikli başka bir bilgisayara yayımlarsınız. IIS kullanırken, uygulamada IIS'ye Python *yorumlayıcının neredeweb.config* söyleyen bir dosya oluşturun veya dosyayı değiştirmeyin. Daha fazla bilgi için [bkz. IIS için web uygulamalarını yapılandırma.](configure-web-apps-for-iis-windows.md)
