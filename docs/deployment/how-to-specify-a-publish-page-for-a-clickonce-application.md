---
title: ClickOnce uygulaması için bir yayımlama sayfası belirtme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf7178a6b5456d048421533b8497682d69c2ee0
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85381970"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için bir yayımlama sayfası belirtme
Bir uygulamayı yayımlarken [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , uygulama ile birlikte varsayılan bir Web sayfası (publish.htm) oluşturulup yayımlanır. Bu sayfa, uygulamanın adını, uygulamayı yüklemeye yönelik bağlantıyı ve/veya önkoşulları ve bir Yardım konusunun bağlantısını içerir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Projeniz için **Yayımla sayfası** özelliği, uygulamanız için Web sayfası için bir ad belirtmenizi sağlar [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .

 Yayımla sayfası belirtilmişse, bir sonraki yayımladıktan sonra yayımlama konumuna kopyalanacaktır; yeniden yayımladığınızda üzerine yazılmaz. Sayfanın görünümünü özelleştirmek istiyorsanız, değişikliklerinizi kaybetme hakkında endişelenmeden bunu yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce varsayılan Web sayfasını özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 **Yayımla sayfası** özelliği, **Proje Tasarımcısı**' nın **Yayımla** bölmesinden erişilebilen **Yayımla Seçenekleri** iletişim kutusunda ayarlanabilir.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>ClickOnce uygulaması için özel bir Web sayfası belirtmek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** bölmesini seçin.

3. **Yayımla Seçenekleri** iletişim kutusunu açmak için **Seçenekler** düğmesine tıklayın.

4. **Dağıtım**' ye tıklayın.

5. **Yayımla Seçenekleri** iletişim kutusunda, Yayımla ' nın **ardından dağıtım Web sayfasını aç** onay kutusunun seçili olduğundan emin olun (varsayılan olarak seçilmelidir).

6. **Dağıtım Web sayfası** kutusuna Web sayfanızın adını girin ve ardından **Tamam**' a tıklayın.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Yayımla sayfasının her yayımlaışınızda başlatılmasını engellemek için

1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.

2. **Yayımla** bölmesini seçin.

3. **Yayımla Seçenekleri** iletişim kutusunu açmak için **Seçenekler** düğmesine tıklayın.

4. **Dağıtım**' ye tıklayın.

5. **Yayımla Seçenekleri** iletişim kutusunda, **yayımlamadan sonra dağıtım Web sayfasını aç** onay kutusunu temizleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Nasıl yapılır: ClickOnce varsayılan Web sayfasını özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)