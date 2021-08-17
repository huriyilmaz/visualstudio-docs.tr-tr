---
title: ClickOnce uygulama için güncelleştirmeleri yönetme | Microsoft Docs
description: güncelleştirmeleri otomatik olarak veya ClickOnce uygulamalarınız için programlı olarak denetlemeye yönelik seçenekler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 988fc33a7f8d4f2d535a55fac636340c6dfb93ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089985"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>nasıl yapılır: ClickOnce bir uygulama için güncelleştirmeleri yönetme
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamalar güncelleştirmeleri otomatik olarak veya programlı bir şekilde denetleyebilir. Bir geliştirici olarak, güncelleştirme denetimlerinin ne zaman ve nasıl gerçekleştirileceğini, güncelleştirmelerin zorunlu olup olmadığını ve uygulamanın güncelleştirmeleri denetlemesi gereken yeri belirtme konusunda çok sayıda esnekliğe sahip olursunuz.

 Uygulamayı, uygulama başlamadan önce otomatik olarak güncelleştirmeleri denetlemek üzere veya uygulama başladıktan sonra ayarlanan aralıklarda otomatik olarak denetleyecek şekilde yapılandırabilirsiniz. Ayrıca, gerekli en düşük sürümü belirtebilirsiniz; diğer bir deyişle, kullanıcının sürümü gereken sürümden düşükse bir güncelleştirme yüklenir.

 Uygulamayı, Kullanıcı isteği gibi bir olaya göre program aracılığıyla güncelleştirmeleri denetlemek üzere yapılandırabilirsiniz. Bu konudaki "güncelleştirmeleri programlı olarak denetlemek Için" yordamı, <xref:System.Deployment.Application.ApplicationDeployment> bir olaya göre güncelleştirmeleri denetlemek için sınıfını kullanan kodu nasıl yazacağınızı gösterir.

 Ayrıca, uygulamanızı tek bir konumdan dağıtabilir ve başka bir konumdan güncelleştirebilirsiniz. "Farklı bir güncelleştirme konumu belirtmek Için" yordamına bakın.

 daha fazla bilgi için bkz. [ClickOnce güncelleştirme stratejisi seçme](../deployment/choosing-a-clickonce-update-strategy.md).

 güncelleştirme davranışı, **Project tasarımcısının** **yayımla** sayfasından erişilebilen **uygulama güncelleştirmeleri** iletişim kutusunda yönetilir.

### <a name="to-check-for-updates-before-the-application-starts"></a>Uygulama başlamadan önce güncelleştirmeleri denetlemek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.

4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun seçili olduğundan emin olun.

5. **Uygulamanın güncelleştirmeleri denetlemesi gereken zaman Seç** bölümünde, **uygulama başlamadan önce**' yi seçin. Bu, ağa bağlı kullanıcıların her zaman en son güncelleştirmelerle uygulamayı çalıştırmasını sağlar.

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Uygulama başladıktan sonra arka planda güncelleştirmeleri denetlemek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.

4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun seçili olduğundan emin olun.

5. **Uygulamanın güncelleştirmeleri denetlemesi gereken zaman Seç bölümünde**, **uygulama başladıktan sonra** öğesini seçin. Uygulama bu şekilde daha hızlı başlayacaktır ve sonra arka planda güncelleştirmeleri denetlecektir ve yalnızca bir güncelleştirme kullanılabilir olduğunda kullanıcıya bildirilir. Yüklendikten sonra, güncelleştirmeler uygulama yeniden başlatılana kadar etkili olmaz.

6. **Uygulamanın güncelleştirmeleri hangi sıklıkla denetlemesi gerektiğini belirtin** bölümünde, **uygulamanın her çalıştırılışında** (varsayılan) onay seçeneğini belirleyin veya **her** birini işaretleyin ve bir sayı ve zaman aralığı girin.

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Uygulama için gerekli en düşük sürümü belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.

4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun seçili olduğundan emin olun.

5. **Bu uygulama için gerekli en düşük sürümü belirtin** onay kutusunu seçin ve ardından uygulama için **ana**, **İkincil**, **derleme** ve **Düzeltme** numaralarını girin.

### <a name="to-specify-a-different-update-location"></a>Farklı bir güncelleştirme konumu belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.

4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun seçili olduğundan emin olun.

5. **Güncelleştirme konumu** alanına, tam URL ile güncelleştirme konumunu, biçimini kullanarak *http://Hostname/ApplicationName* veya *\\ \server\applicationname* biçimini kullanarak bir UNC yolunu girin veya güncelleştirme konumuna göz atarak **göz** atın düğmesine tıklayın.

### <a name="to-check-for-updates-programmatically"></a>Güncelleştirmeleri program aracılığıyla denetlemek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Project** menüsünde **özellikler**' e tıklayın.

2. **Yayımla** sekmesine tıklayın.

3. **Güncelleştirmeler** düğmesine tıklayarak **uygulama güncelleştirmeleri** iletişim kutusunu açın.

4. **Uygulama güncelleştirmeleri** iletişim kutusunda **uygulamanın güncelleştirmeleri denetlemesi gereken** onay kutusunun temizlenmiş olduğundan emin olun. (isteğe bağlı olarak, güncelleştirmeleri programlı bir şekilde denetlemek için bu onay kutusunu seçebilirsiniz ve ayrıca ClickOnce çalışma zamanının güncelleştirmeleri otomatik olarak denetlemesini sağlayabilirsiniz.)

5. **Güncelleştirme konumu** alanına, tam URL ile güncelleştirme konumunu, biçimini kullanarak *http://Hostname/ApplicationName* veya *\\ \server\applicationname* biçimini kullanarak bir UNC yolunu girin veya güncelleştirme konumuna göz atarak **göz** atın düğmesine tıklayın. Güncelleştirme konumu, uygulamanın kendisi için güncelleştirilmiş bir sürümünü arayacağı yerdir.

6. kullanıcıların güncelleştirmeleri denetlemesini seçmesini sağlayacak bir Windows Form üzerinde düğme, menü öğesi veya diğer kullanıcı arabirimi öğesi oluşturun. Bu öğenin olay işleyicisinden, güncelleştirmeleri denetlemek ve yüklemek için bir yöntem çağırın. [nasıl yapılır: ClickOnce dağıtım apı 'sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)bölümünde, bu tür bir yöntem için Visual Basic ve Visual C# kodu örneği bulabilirsiniz.

7. Uygulamanızı oluşturun.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Uygulama güncelleştirmeleri iletişim kutusu](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))
- [ClickOnce güncelleştirme stratejisini seçme](../deployment/choosing-a-clickonce-update-strategy.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [nasıl yapılır: ClickOnce dağıtım apı 'sini kullanarak program aracılığıyla uygulama güncelleştirmelerini denetleme](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
