---
title: Azure Cloud Services 'da rolleri yönetme
description: Visual Studio ile Azure bulut hizmetleri 'nde rol ekleme ve kaldırma hakkında bilgi edinin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 072fe84c0ca9c4fd4ef817457f912c0c43c81d69
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091740"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>Azure Cloud Services 'da Visual Studio ile rolleri yönetme
Azure bulut hizmetinizi oluşturduktan sonra bu hizmete yeni roller ekleyebilir veya mevcut rolleri kaldırabilirsiniz. Ayrıca, var olan bir projeyi içeri aktarabilir ve bir role dönüştürebilirsiniz. örneğin, bir ASP.NET web uygulamasını içeri aktarabilir ve bir web rolü olarak belirleyebilirsiniz.

## <a name="adding-a-role-to-an-azure-cloud-service"></a>Azure bulut hizmetine rol ekleme
Aşağıdaki adımlar, Visual Studio bir Azure bulut hizmeti projesine Web veya çalışan rolü ekleme konusunda size rehberlik sağlar.

1. Visual Studio bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin

1. Bağlam menüsünü göstermek için **Roller** düğümüne sağ tıklayın. Bağlam menüsünden **Ekle**' yi seçin, ardından geçerli çözümden mevcut bir Web rolü veya çalışan rolü seçin ya da bir Web ya da çalışan rolü projesi oluşturun. ayrıca, ASP.NET web uygulaması projesi gibi uygun bir proje seçebilir ve bunu bir rol projesiyle ilişkilendirebilirsiniz.

   ![Azure bulut hizmeti projesine rol eklemek için menü seçenekleri](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>Azure bulut hizmetinden rol kaldırma
Aşağıdaki adımlar, bir Web veya çalışan rolünü Visual Studio bir Azure bulut hizmeti projesinden kaldırmanıza yardımcı olmak için size kılavuzluk ediyor.

1. Visual Studio bir Azure bulut hizmeti projesi oluşturun veya açın.

1. **Çözüm Gezgini**, proje düğümünü genişletin

1. **Roller** düğümünü genişletin.

1. Kaldırmak istediğiniz düğüme sağ tıklayın ve bağlam menüsünden **Kaldır**' ı seçin.

   ![Azure bulut hizmetine rol eklemek için menü seçenekleri](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>Bir Azure bulut hizmeti projesine rol okuma
Bulut hizmeti projenizden bir rolü kaldırır ancak daha sonra rolü projeye geri eklemeye karar verirseniz, yalnızca rol bildirimi ve uç noktalar ve tanılama bilgileri gibi temel öznitelikler eklenir. Dosyaya veya dosyaya başka kaynak veya başvuru eklenmez `ServiceDefinition.csdef` `ServiceConfiguration.cscfg` . Bu bilgileri eklemek istiyorsanız, geri el ile bu dosyalara eklemeniz gerekir.

Örneğin, bir Web hizmeti rolünü kaldırabilir ve daha sonra bu rolü çözümünüze geri eklemeye karar verirsiniz. Bunu yaparsanız bir hata oluşur. Bu hatayı engellemek için `<LocalResources>` AŞAĞıDAKI XML içinde gösterilen öğeyi dosyasına geri eklemeniz gerekir `ServiceDefinition.csdef` . Öğe için ad özniteliğinin bir parçası olarak projeye geri eklediğiniz Web hizmeti rolünün adını kullanın **\<LocalStorage>** . Bu örnekte, Web hizmeti rolünün adı **WCFServiceWebRole1**' dir.

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
- [Azure bulut hizmeti rollerini Visual Studio ile yapılandırma](vs-azure-tools-configure-roles-for-cloud-service.md)
