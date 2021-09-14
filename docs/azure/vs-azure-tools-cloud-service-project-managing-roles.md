---
title: Azure bulut hizmetlerinde rolleri yönetme
description: Azure bulut hizmetleriyle rol ekleme ve kaldırma hakkında bilgi Visual Studio.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 072fe84c0ca9c4fd4ef817457f912c0c43c81d69
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633222"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Azure bulut hizmetlerinde rollerini Visual Studio
Azure bulut hizmetinizi oluşturduktan sonra hizmetine yeni roller ekleyebilir veya var olan rolleri kaldırabilirsiniz. Ayrıca var olan bir projeyi içeri aktararak bir role dönüştüresiniz. Örneğin, bir web uygulamasını ASP.NET web rolü olarak kullanabilirsiniz.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Azure bulut hizmetine rol ekleme
Aşağıdaki adımlar, azure bulut hizmeti projesine web veya çalışan rolü ekleme konusunda size Visual Studio.

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini** proje düğümünü genişletin

1. Bağlam menüsünü görüntülemek **için Roller** düğümüne sağ tıklayın. Bağlam menüsünde Ekle'yi **seçin,** sonra geçerli çözümden mevcut bir web rolü veya çalışan rolü seçin ya da bir web veya çalışan rolü projesi oluşturun. Ayrıca web uygulaması projesi gibi uygun bir ASP.NET projesini de seçerek bir rol projesiyle ilişkilendirmeniz gerekir.

   ![Azure bulut hizmeti projesine rol eklemek için menü seçenekleri](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Azure bulut hizmetlerinden rol kaldırma
Aşağıdaki adımlar, bir Azure bulut hizmeti projesinde web veya çalışan rolünü kaldırma konusunda size Visual Studio.

1. Azure bulut hizmeti projesi oluşturma veya açma Visual Studio.

1. Bu **Çözüm Gezgini** proje düğümünü genişletin

1. Roller **düğümünü** genişletin.

1. Kaldırmak istediğiniz düğüme sağ tıklayın ve bağlam menüsünden Kaldır'ı **seçin.**

   ![Azure bulut hizmetine rol eklemek için menü seçenekleri](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Azure bulut hizmeti projesine rol okuma
Bulut hizmeti projenizin bir rolünü kaldırır ancak daha sonra rolü projeye geri eklemeye karar verirsiniz, yalnızca rol bildirimi ve uç noktalar ve tanılama bilgileri gibi temel öznitelikler eklenir. Dosyaya veya dosyaya ek kaynak veya `ServiceDefinition.csdef` başvuru `ServiceConfiguration.cscfg` eklenmez. Bu bilgileri eklemek için bu dosyalara el ile eklemeniz gerekir.

Örneğin, bir web hizmeti rolünü kaldırabilir ve daha sonra bu rolü çözümünüze yeniden eklemeye karar veebilirsiniz. Bunu yaparsanız bir hata oluşur. Bu hatayı önlemek için aşağıdaki XML dosyasında gösterilen öğesini `<LocalResources>` dosyaya geri eklemeniz `ServiceDefinition.csdef` gerekir. Öğenin name özniteliğinin bir parçası olarak projeye geri ekley istediğiniz web hizmeti rolünün adını **\<LocalStorage>** kullanın. Bu örnekte, web hizmeti rolünün adı **WCFServiceWebRole1'tir.**

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
- [Azure bulut hizmeti rollerini Visual Studio](vs-azure-tools-configure-roles-for-cloud-service.md)
