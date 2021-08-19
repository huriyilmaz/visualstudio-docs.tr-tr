---
title: '&lt;customerrorreporting &gt; öğesi (ClickOnce dağıtımı) | Microsoft Docs'
description: CustomErrorReporting öğesi, özel durum yığınını gösteren bir hata iletişim kutusu yerine bir hata oluştuğunda gösterilecek URI 'yi belirtir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: b296e87accb896f25fe1d83d859e46b0e1d89755
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153764"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customerrorreporting &gt; öğesi (ClickOnce dağıtımı)
Bir hata oluştuğunda gösterilecek URI 'yi belirtir.

## <a name="syntax"></a>Syntax

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Açıklamalar
 Bu öğe isteğe bağlıdır. Bu olmadan, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] özel durum yığınını gösteren bir hata iletişim kutusu görüntüler. `customErrorReporting`Öğesi varsa, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bunun yerine parametresi tarafından belirtilen URI 'yi görüntüler `uri` . Hedef URI, dış özel durum sınıfını, iç özel durum sınıfını ve iç özel durum iletisini parametre olarak içerir.

 Uygulamanıza hata raporlama işlevi eklemek için bu öğeyi kullanın. Oluşturulan URI, hata türü hakkında bilgi içerdiğinden, Web siteniz bu bilgileri ayrıştırarak, örneğin uygun bir sorun giderme ekranı gibi görüntüleyebilir.

## <a name="example"></a>Örnek
 Aşağıdaki kod parçacığında, `customErrorReporting` ÜRETILEN URI 'nin üretebilecekleri bir ile birlikte öğesi gösterilmektedir.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce dağıtım bildirimi](../deployment/clickonce-deployment-manifest.md)