---
title: Azure bulut hizmetlerinde rolleri yönetme
description: Visual Studio ile Azure bulut hizmetlerinde nasıl rol ekleyeceğinizi ve kaldırabileceğinizi öğrenin.
author: ghogen
manager: jillfra
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: f03ac134a54f3a32108175fa858d22b5c4aec8af
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489694"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Visual Studio ile Azure bulut hizmetlerinde rolleri yönetme
Azure bulut hizmetinizi oluşturduktan sonra, bu hizmete yeni roller ekleyebilir veya varolan rolleri ondan kaldırabilirsiniz. Ayrıca varolan bir projeyi içe aktarAbilir ve bir role dönüştürebilirsiniz. Örneğin, bir ASP.NET web uygulaması içe aktarabilir ve bir web rolü olarak belirleyebilirsiniz.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Azure bulut hizmetine rol ekleme
Aşağıdaki adımlar, Visual Studio'daki bir Azure bulut hizmeti projesine web veya çalışan rolü eklemede size yol gösterin.

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde,** proje düğümlerini genişletin

1. Bağlam menüsünü görüntülemek için **Roller** düğümünün sağ düğmesini tıklatın. Bağlam menüsünden **Ekle'yi**seçin, ardından geçerli çözümden varolan bir web rolü veya çalışan rolü seçin veya bir web veya çalışan rol projesi oluşturun. Ayrıca, ASP.NET bir web uygulama projesi gibi uygun bir proje seçebilir ve bir rol projesiyle ilişkilendirebilirsiniz.

   ![Azure bulut hizmeti projesine rol eklemek için menü seçenekleri](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Azure bulut hizmetinden bir rolü kaldırma
Aşağıdaki adımlar, Visual Studio'daki bir Azure bulut hizmeti projesinden bir web veya çalışan rolünü kaldırmada size yol gösterin.

1. Visual Studio'da bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini'nde,** proje düğümlerini genişletin

1. **Roller** düğümlerini genişletin.

1. Kaldırmak istediğiniz düğümü sağ tıklatın ve bağlam menüsünden **Kaldır'ı**seçin.

   ![Azure bulut hizmetine rol eklemek için menü seçenekleri](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Azure bulut hizmeti projesine rol yeniden ekleme
Bir rolü bulut hizmeti projenizden kaldırır, ancak daha sonra rolü projeye geri eklemeye karar verirseniz, yalnızca son noktalar ve tanılama bilgileri gibi temel öznitelikler eklenir. `ServiceDefinition.csdef` Dosyaya veya `ServiceConfiguration.cscfg` dosyaya ek kaynak veya başvuru eklenmez. Bu bilgileri eklemek istiyorsanız, bu dosyalara el ile geri eklemeniz gerekir.

Örneğin, bir web hizmeti rolünü kaldırabilir ve daha sonra bu rolü çözüme geri eklemeye karar verebilirsiniz. Bunu yaparsanız, bir hata oluşur. Bu hatayı önlemek için, aşağıdaki `<LocalResources>` XML'de gösterilen öğeyi `ServiceDefinition.csdef` dosyaya geri eklemeniz gerekir. ** \<Yerel Depolama>** öğesiiçin ad özniteliğinin bir parçası olarak projeye geri eklediğiniz web hizmeti rolünün adını kullanın. Bu örnekte, web hizmeti rolünün adı **WCFServiceWebRole1'dir.**

```xml
<WebRole name="WCFServiceWebRole1">
    <Sites>
      <Site name="Web">
        <Bindings>
          <Binding name="Endpoint1" endpointName="Endpoint1" />
        </Bindings>
      </Site>
    </Sites>
    <Endpoints>
      <InputEndpoint name="Endpoint1" protocol="http" port="80" />
    </Endpoints>
    <Imports>
      <Import moduleName="Diagnostics" />
    </Imports>
    <LocalResources>
      <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
    </LocalResources>
</WebRole>
```

## <a name="next-steps"></a>Sonraki adımlar
- [Visual Studio ile Azure bulut hizmetinin Rollerini yapılandırma](vs-azure-tools-configure-roles-for-cloud-service.md)
