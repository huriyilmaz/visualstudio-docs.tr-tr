---
title: "Nasıl yapılır: ClickOnce dağıtım API 'sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5250e719cce945bdcce90a9d49d2ed8c27555612
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444990"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Nasıl yapılır: ClickOnce Dağıtım API'sini Kullanarak Program Aracılığıyla Uygulama Güncelleştirmelerini Denetleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce, bir uygulamayı dağıtıldıktan sonra güncelleştirmek için iki yol sağlar. İlk yöntemde, belirli aralıklarda güncelleştirmeleri otomatik olarak denetlemek için ClickOnce dağıtımını yapılandırabilirsiniz. İkinci yöntemde, <xref:System.Deployment.Application.ApplicationDeployment> bir Kullanıcı isteği gibi bir olaya göre güncelleştirmeleri denetlemek için sınıfını kullanan kodu yazabilirsiniz.  
  
 Aşağıdaki yordamlarda, programlı güncelleştirme gerçekleştirmeye yönelik bazı kodlar gösterilmektedir ve ayrıca, programlı güncelleştirme denetimlerini etkinleştirmek için ClickOnce dağıtımınızın nasıl yapılandırılacağı açıklanır.  
  
 Bir ClickOnce uygulamasını programlı bir şekilde güncelleştirmek için, güncelleştirmeler için bir konum belirtmeniz gerekir. Bu, bazen bir dağıtım sağlayıcısı olarak adlandırılır. Bu özelliği ayarlama hakkında daha fazla bilgi için bkz. [ClickOnce Update stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
> Uygulamanızı tek bir konumdan dağıtmak, ancak başka bir konumdan güncelleştirmek için aşağıda açıklanan tekniği de kullanabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: dağıtım güncelleştirmeleri Için alternatif bir konum belirtme](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### <a name="to-check-for-updates-programmatically"></a>Güncelleştirmeleri program aracılığıyla denetlemek için  
  
1. Tercih ettiğiniz komut satırı veya görsel araçları kullanarak yeni bir Windows Forms uygulaması oluşturun.  
  
2. Kullanıcılarınızın güncelleştirmeleri denetlemek için seçmesini istediğiniz düğme, menü öğesi veya diğer kullanıcı arabirimi öğelerini oluşturun. Bu öğenin olay işleyicisinden, güncelleştirmeleri denetlemek ve yüklemek için aşağıdaki yöntemi çağırın.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. Uygulamanızı derleyin.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Program aracılığıyla güncelleştirmeleri denetleyen bir uygulamayı dağıtmak için Mage.exe kullanma  
  
- [Izlenecek yol: bir ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi Mage.exe kullanarak uygulamanızı dağıtmaya yönelik yönergeleri izleyin. Dağıtım bildirimini oluşturmak için Mage.exe çağırırken, komut satırı anahtarını kullandığınızdan `providerUrl` ve ClickOnce 'ın güncelleştirmeleri denetlemesi gereken URL 'yi belirttiğinizden emin olun. Uygulamanız ' dan güncelleşecektir `http://www.adatum.com/MyApp` , örneğin, dağıtım bildirimini oluşturma çağrınızdan şöyle görünebilir:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Program aracılığıyla güncelleştirmeleri denetleyen bir uygulamayı dağıtmak için MageUI.exe kullanma  
  
- [Izlenecek yol: bir ClickOnce uygulamasını El Ile dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)bölümünde açıklandığı gibi Mage.exe kullanarak uygulamanızı dağıtmaya yönelik yönergeleri izleyin. **Dağıtım seçenekleri** sekmesinde, **Başlangıç konumu** alanını ClickOnce 'ın güncelleştirmeleri denetlemesi gereken uygulama bildirimi olarak ayarlayın. **Güncelleştirme seçenekleri** sekmesinde, **Bu uygulamanın güncelleştirmeleri denetlemesi gerekir** onay kutusunu temizleyin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulamanızın programlı güncelleştirme kullanması için tam güven izinlerine sahip olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: dağıtım güncelleştirmeleri için alternatif bir konum belirtme](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce Uygulamalarını Yayımlama](../deployment/publishing-clickonce-applications.md)
