---
title: ClickOnce dağıtım API 'sini kullanarak otomatik uygulama güncelleştirmeleri
description: Kullanıcı isteği gibi bir olaya göre güncelleştirmeleri denetlemek için ApplicationDeployment sınıfını kullanan ClickOnce 'da kod yazmayı öğrenin.
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
ms.workload:
- multiple
ms.openlocfilehash: 6e7168b78303f93ccf89fad324992dd580481ac2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888452"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Nasıl yapılır: ClickOnce dağıtım API 'sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme
ClickOnce, bir uygulamayı dağıtıldıktan sonra güncelleştirmek için iki yol sağlar. İlk yöntemde, belirli aralıklarda güncelleştirmeleri otomatik olarak denetlemek için ClickOnce dağıtımını yapılandırabilirsiniz. İkinci yöntemde, <xref:System.Deployment.Application.ApplicationDeployment> bir Kullanıcı isteği gibi bir olaya göre güncelleştirmeleri denetlemek için sınıfını kullanan kodu yazabilirsiniz.

 Aşağıdaki yordamlarda, programlı güncelleştirme gerçekleştirmeye yönelik bazı kodlar gösterilmektedir ve ayrıca, programlı güncelleştirme denetimlerini etkinleştirmek için ClickOnce dağıtımınızın nasıl yapılandırılacağı açıklanır.

 Bir ClickOnce uygulamasını programlı bir şekilde güncelleştirmek için, güncelleştirmeler için bir konum belirtmeniz gerekir. Bu, bazen bir dağıtım sağlayıcısı olarak adlandırılır. Bu özelliği ayarlama hakkında daha fazla bilgi için bkz. [bir ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Uygulamanızı tek bir konumdan dağıtmak, ancak başka bir konumdan güncelleştirmek için aşağıda açıklanan tekniği de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Güncelleştirmeleri program aracılığıyla denetlemek için

1. Tercih ettiğiniz komut satırı veya görsel araçları kullanarak yeni bir Windows Forms uygulaması oluşturun.

2. Kullanıcılarınızın güncelleştirmeleri denetlemek için seçmesini istediğiniz düğme, menü öğesi veya diğer kullanıcı arabirimi öğelerini oluşturun. Bu öğenin olay işleyicisinden, güncelleştirmeleri denetlemek ve yüklemek için aşağıdaki yöntemi çağırın.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Uygulamanızı derleyin.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Güncelleştirmeleri program aracılığıyla denetleyen bir uygulamayı dağıtmak için Mage.exe kullanın

- [Izlenecek yol: bir ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi Mage.exe kullanarak uygulamanızı dağıtmaya yönelik yönergeleri izleyin. Dağıtım bildirimini oluşturmak için Mage.exe çağırırken, komut satırı anahtarını kullandığınızdan `providerUrl` ve ClickOnce 'ın güncelleştirmeleri denetlemesi gereken URL 'yi belirttiğinizden emin olun. Uygulamanız ' dan güncelleşecektir `http://www.adatum.com/MyApp` , örneğin, dağıtım bildirimini oluşturma çağrınızdan şöyle görünebilir:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Program aracılığıyla güncelleştirmeleri denetleyen bir uygulamayı dağıtmak için MageUI.exe kullanma

- [Izlenecek yol: bir ClickOnce uygulamasını el ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi Mage.exe kullanarak uygulamanızı dağıtmaya yönelik yönergeleri izleyin. **Dağıtım seçenekleri** sekmesinde, **Başlangıç konumu** alanını ClickOnce 'ın güncelleştirmeleri denetlemesi gereken uygulama bildirimi olarak ayarlayın. **Güncelleştirme seçenekleri** sekmesinde, **Bu uygulamanın güncelleştirmeleri denetlemesi gerekir** onay kutusunu temizleyin.

## <a name="net-framework-security"></a>.NET Framework Güvenliği
 Uygulamanızın programlı güncelleştirme kullanması için tam güven izinlerine sahip olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)