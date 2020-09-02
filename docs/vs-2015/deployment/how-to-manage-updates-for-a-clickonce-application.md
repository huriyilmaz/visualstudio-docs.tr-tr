---
title: 'Nasıl yapılır: ClickOnce uygulaması için güncelleştirmeleri yönetme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0754d816104832f92a0be8d754046d1ee18e7a09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697646"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulaması için Güncelleştirmeleri Yönetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulamalar güncelleştirmeleri otomatik olarak veya programlı bir şekilde denetleyebilir. Bir geliştirici olarak, güncelleştirme denetimlerinin ne zaman ve nasıl gerçekleştirileceğini, güncelleştirmelerin zorunlu olup olmadığını ve uygulamanın güncelleştirmeleri denetlemesi gereken yeri belirtme konusunda çok sayıda esnekliğe sahip olursunuz.  
  
 Uygulamayı, uygulama başlamadan önce otomatik olarak güncelleştirmeleri denetlemek üzere veya uygulama başladıktan sonra ayarlanan aralıklarda otomatik olarak denetleyecek şekilde yapılandırabilirsiniz. Ayrıca, gerekli en düşük sürümü belirtebilirsiniz; diğer bir deyişle, kullanıcının sürümü gereken sürümden düşükse bir güncelleştirme yüklenir.  
  
 Uygulamayı, Kullanıcı isteği gibi bir olaya göre program aracılığıyla güncelleştirmeleri denetlemek üzere yapılandırabilirsiniz. Bu konudaki "güncelleştirmeleri programlı olarak denetlemek Için" yordamı, <xref:System.Deployment.Application.ApplicationDeployment> bir olaya göre güncelleştirmeleri denetlemek için sınıfını kullanan kodu nasıl yazacağınızı gösterir.  
  
 Ayrıca, uygulamanızı tek bir konumdan dağıtabilir ve başka bir konumdan güncelleştirebilirsiniz. "Farklı bir güncelleştirme konumu belirtmek Için" yordamına bakın.  
  
 Daha fazla bilgi için bkz. [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Güncelleştirme davranışı, **Proje Tasarımcısı** ' nın **Yayımla** sayfasında bulunan **uygulama güncelleştirmeleri** iletişim kutusunda yönetilir.  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Uygulama başlamadan önce güncelleştirmeleri denetlemek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.  
  
4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun seçili olduğundan emin olun.  
  
5. **Uygulamanın güncelleştirmeleri denetlemesi gereken zaman Seç** bölümünde, **uygulama başlamadan önce**' yi seçin. Bu, ağa bağlı kullanıcıların her zaman en son güncelleştirmelerle uygulamayı çalıştırmasını sağlar.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Uygulama başladıktan sonra arka planda güncelleştirmeleri denetlemek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.  
  
4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun seçili olduğundan emin olun.  
  
5. **Uygulamanın güncelleştirmeleri denetlemesi gereken zaman Seç bölümünde**, **uygulama başladıktan sonra**öğesini seçin. Uygulama bu şekilde daha hızlı başlayacaktır ve sonra arka planda güncelleştirmeleri denetlecektir ve yalnızca bir güncelleştirme kullanılabilir olduğunda kullanıcıya bildirilir. Yüklendikten sonra, güncelleştirmeler uygulama yeniden başlatılana kadar etkili olmaz.  
  
6. **Uygulamanın güncelleştirmeleri hangi sıklıkla denetlemesi gerektiğini belirtin** bölümünde, **uygulamanın her çalıştırılışında** (varsayılan) onay seçeneğini belirleyin veya **her** birini işaretleyin ve bir sayı ve zaman aralığı girin.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Uygulama için gerekli en düşük sürümü belirtmek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.  
  
4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun seçili olduğundan emin olun.  
  
5. **Bu uygulama için gerekli en düşük sürümü belirtin** onay kutusunu seçin ve ardından uygulama için **ana**, **İkincil**, **derleme**ve **Düzeltme** numaralarını girin.  
  
### <a name="to-specify-a-different-update-location"></a>Farklı bir güncelleştirme konumu belirtmek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.  
  
4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun seçili olduğundan emin olun.  
  
5. **Güncelleştirme konumu** alanına, tam URL ile güncelleştirme konumunu, biçimini kullanarak http://Hostname/ApplicationName veya \server\applicationname BIÇIMINI kullanarak bir UNC yolunu girin \\ veya güncelleştirme konumuna göz atarak **göz** atın düğmesine tıklayın.  
  
### <a name="to-check-for-updates-programmatically"></a>Güncelleştirmeleri program aracılığıyla denetlemek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** sekmesine tıklayın.  
  
3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.  
  
4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun temizlenmiş olduğundan emin olun. (İsteğe bağlı olarak, güncelleştirmeleri programlı olarak denetlemek ve ayrıca ClickOnce çalışma zamanının güncelleştirmeleri otomatik olarak denetlemesini sağlamak için bu onay kutusunu seçebilirsiniz.)  
  
5. **Güncelleştirme konumu** alanına, tam URL ile güncelleştirme konumunu, biçimini kullanarak http://Hostname/ApplicationName veya \server\applicationname BIÇIMINI kullanarak bir UNC yolunu girin \\ veya güncelleştirme konumuna göz atarak **göz** atın düğmesine tıklayın. Güncelleştirme konumu, uygulamanın kendisi için güncelleştirilmiş bir sürümünü arayacağı yerdir.  
  
6. Kullanıcıların güncelleştirmeleri denetlemesini seçmesini sağlayacak bir Windows formunda düğme, menü öğesi veya diğer kullanıcı arabirimi öğesi oluşturun. Bu öğenin olay işleyicisinden, güncelleştirmeleri denetlemek ve yüklemek için bir yöntem çağırın. [Nasıl yapılır: ClickOnce DAĞıTıM API 'Sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)bölümünde, bu tür bir yöntem için Visual Basic ve Visual C# kodu örneği bulabilirsiniz.  
  
7. Uygulamanızı oluşturun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Uygulama güncelleştirmeleri Iletişim kutusu](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md)   
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Nasıl yapılır: ClickOnce Dağıtım API'sini Kullanarak Program Aracılığıyla Uygulama Güncelleştirmelerini Denetleme](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
