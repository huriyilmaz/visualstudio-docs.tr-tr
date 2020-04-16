---
title: "Nasıl yapilir: ClickOnce Dağıtım API'sini Kullanarak Uygulama Güncelleştirmelerini Programlı Olarak Denetleyin | Microsoft Dokümanlar"
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
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444990"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Nasıl yapılır: ClickOnce Dağıtım API'sini Kullanarak Program Aracılığıyla Uygulama Güncelleştirmelerini Denetleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce, bir uygulamayı dağıtıldıktan sonra güncelleştirmenin iki yolunu sağlar. İlk yöntemde, belirli aralıklarla güncelleştirmeleri otomatik olarak denetlemek için ClickOnce dağıtımını yapılandırabilirsiniz. İkinci yöntemde, kullanıcı isteği gibi <xref:System.Deployment.Application.ApplicationDeployment> bir olayı temel alan güncelleştirmeleri denetlemek için sınıfı kullanan kod yazabilirsiniz.  
  
 Aşağıdaki yordamlar programlı güncelleştirme gerçekleştirmek için bazı kodlar gösterir ve programlı güncelleştirme denetimlerini etkinleştirmek için ClickOnce dağıtımınızı nasıl yapılandırıştırılacak açıklar.  
  
 ClickOnce uygulamasını programlı olarak güncelleştirmek için güncelleştirmeler için bir konum belirtmeniz gerekir. Bu bazen dağıtım sağlayıcısı olarak adlandırılır. Bu özelliği ayarlama hakkında daha fazla bilgi için [clickonce güncelleme stratejisi seçme'ye](../deployment/choosing-a-clickonce-update-strategy.md)bakın.  
  
> [!NOTE]
> Uygulamanızı bir konumdan dağıtmak ancak başka bir konumdan güncelleştirmek için aşağıda açıklanan tekniği de kullanabilirsiniz. Daha fazla bilgi için [bkz: Dağıtım Güncelleştirmeleri için Alternatif Konum belirtin.](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)  
  
### <a name="to-check-for-updates-programmatically"></a>Güncelleştirmeleri programlı olarak denetlemek için  
  
1. Tercih ettiğiniz komut satırı veya görsel araçları kullanarak yeni bir Windows Forms uygulaması oluşturun.  
  
2. Güncelleştirmeleri denetlemek için kullanıcılarınızın seçmesini istediğiniz düğme, menü öğesi veya diğer kullanıcı arabirim öğesini oluşturun. Bu öğenin olay işleyicisinden güncelleştirmeleri denetlemek ve yüklemek için aşağıdaki yöntemi arayın.  
  
     [!code-cpp[ClickOnceAPI#6](../snippets/cpp/VS_Snippets_Winforms/ClickOnceAPI/cpp/form1.cpp#6)]
     [!code-csharp[ClickOnceAPI#6](../snippets/csharp/VS_Snippets_Winforms/ClickOnceAPI/CS/Form1.cs#6)]
     [!code-vb[ClickOnceAPI#6](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnceAPI/VB/Form1.vb#6)]  
  
3. Başvurunuzu derlein.  
  
### <a name="using-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Güncelleştirmeleri programlı olarak denetleyen bir uygulamayı dağıtmak için Mage.exe'yi kullanma  
  
- Walkthrough'da açıklandığı gibi Mage.exe kullanarak uygulamanızı dağıtma yönergelerini [izleyin: ClickOnce Uygulamasını El Ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Dağıtım bildirimini oluşturmak için Mage.exe'yi ararken, komut `providerUrl`satırı anahtarını kullandığınızdan emin olun ve ClickOnce'nin güncelleştirmeleri denetlemesi gereken URL'yi belirtin. `http://www.adatum.com/MyApp`Örneğin, uygulamanız güncellenirse, dağıtım bildirimini oluşturma çağrınız aşağıdaki gibi görünebilir:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Güncelleştirmeleri programlı olarak denetleyen bir uygulamayı dağıtmak için MageUI.exe'yi kullanma  
  
- Walkthrough'da açıklandığı gibi Mage.exe kullanarak uygulamanızı dağıtma yönergelerini [izleyin: ClickOnce Uygulamasını El Ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Dağıtım **Seçenekleri** sekmesinde, **Başlangıç Konumu** alanını uygulama bildirimine ayarlayın ClickOnce güncelleştirmeleri denetlemelidir. Güncelleştirme **Seçenekleri** sekmesinde, güncelleştirmeler onay kutusunu **denetlemesi gereken bu uygulamayı** temizleyin.  
  
## <a name="net-framework-security"></a>.NET Framework Güvenliği  
 Uygulamanızın programlı güncelleştirmeyi kullanmak için tam güven izinlerine sahip olması gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapilir: Dağıtım Güncelleştirmeleri için Alternatif Konum Belirt](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [ClickOnce Güncelleme Stratejisi Seçme](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce Uygulamalarını Yayımlama](../deployment/publishing-clickonce-applications.md)
