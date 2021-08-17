---
title: Dağıtım API'sini ClickOnce otomatik uygulama güncelleştirmeleri
description: Kullanıcı isteği gibi bir ClickOnce güncelleştirmeleri kontrol etmek için ApplicationDeployment sınıfını kullanan bir uygulamada kod yazmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: e8440b6d5b3d83138183c368525486d0cad3778be9aee47b4c519b0ac563f461
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121435536"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Nasıl kullanılır: ClickOnce dağıtım API'sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme
ClickOnce dağıtıldıktan sonra uygulamayı güncelleştirmek için iki yol sağlar. İlk yöntemde, belirli aralıklarla güncelleştirmeleri ClickOnce için dağıtım dağıtımını yapılandırabilirsiniz. İkinci yöntemde, kullanıcı isteği gibi bir olayı temel alan güncelleştirmeleri kontrol etmek için <xref:System.Deployment.Application.ApplicationDeployment> sınıfını kullanan kod yazabilirsiniz.

 Aşağıdaki yordamlar, programlı güncelleştirme gerçekleştirmek için bazı kodlar gösterir ve ayrıca programlı güncelleştirme denetimlerini etkinleştirmek için ClickOnce dağıtım yapılandırmayı açıklar.

 Bir uygulamayı program ClickOnce güncelleştirmek için güncelleştirmeler için bir konum belirtmeniz gerekir. Bu bazen dağıtım sağlayıcısı olarak adlandırılır. Bu özelliği ayarlama hakkında daha fazla bilgi için [bkz. Güncelleştirme ClickOnce seçin.](../deployment/choosing-a-clickonce-update-strategy.md)

> [!NOTE]
> Uygulamanızı bir konumdan dağıtmak ancak başka bir konumdan güncelleştirmek için aşağıda açıklanan tekniği de kullanabilirsiniz. Daha fazla bilgi için, [bkz. How to: Specify a alternate location for deployment updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Güncelleştirmeleri program aracılığıyla denetleme

1. Tercih ettiğiniz komut Windows görsel araçlarını kullanarak yeni bir FormLar uygulaması oluşturun.

2. Kullanıcılarının güncelleştirmeleri kontrol etmek için seçmelerini istediğiniz düğme, menü öğesi veya başka bir kullanıcı arabirimi öğesi oluşturun. Güncelleştirmeleri kontrol etmek ve yüklemek için bu öğenin olay işleyicisinde aşağıdaki yöntemi arayın.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs" id="Snippet6":::
    :::code language="cpp" source="../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp" id="Snippet6":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb" id="Snippet6":::

3. Uygulama derle.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Güncelleştirmeleri Mage.exe bir uygulamayı dağıtmak için Mage.exe'yi kullanma

- Uygulamalarınızı uygulama kullanarak dağıtma yönergelerini Mage.exe: El ile bir uygulama dağıtma konusunda ClickOnce [izleyin.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) Dağıtım Mage.exe için komut satırı anahtarını ve güncelleştirmeleri denetlemesi gereken `providerUrl` URL'yi belirttiğinizden emin ClickOnce olun. Örneğin, uygulamanız `http://www.adatum.com/MyApp` uygulamasından güncelleştirilecekse, dağıtım bildirimini oluşturma çağrınız aşağıdaki gibi olabilir:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Güncelleştirmeleri MageUI.exe bir uygulamayı dağıtmak için MageUI.exe'yi kullanma

- Uygulamalarınızı uygulama kullanarak dağıtma yönergelerini Mage.exe: El ile bir uygulama dağıtma konusunda ClickOnce [izleyin.](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) Dağıtım **Seçenekleri sekmesinde,** Başlangıç Konumu **alanını güncelleştirmeleri** denetlemesi gereken uygulama ClickOnce bildirim olarak ayarlayın. Güncelleştirme Seçenekleri **sekmesinde Bu** uygulama güncelleştirmeleri **denetlemeli onay kutusunun** işaretini kaldırın.

## <a name="net-framework-security"></a>.NET Framework Güvenliği
 Programlı güncelleştirmeyi kullanmak için uygulamanıza tam güven izinleri gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıllı: Dağıtım güncelleştirmeleri için alternatif bir konum belirtme](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)