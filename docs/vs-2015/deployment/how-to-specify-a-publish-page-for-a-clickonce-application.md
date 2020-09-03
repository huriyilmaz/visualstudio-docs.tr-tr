---
title: 'Nasıl yapılır: ClickOnce uygulaması için bir yayımlama sayfası belirtme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63356c6eb423ddead54290cc11c865a5102f55f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202166"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce Uygulaması için bir Yayımlama Sayfası Belirtme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir uygulamayı yayımlarken [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] , uygulama ile birlikte varsayılan bir Web sayfası (publish.htm) oluşturulup yayımlanır. Bu sayfa, uygulamanın adını, uygulamayı yüklemeye yönelik bağlantıyı ve/veya önkoşulları ve bir Yardım konusunun bağlantısını içerir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Projeniz için **Yayımla sayfası** özelliği, uygulamanız için Web sayfası için bir ad belirtmenizi sağlar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
 Yayımla sayfası belirtilmişse, bir sonraki yayımladıktan sonra yayımlama konumuna kopyalanacaktır; yeniden yayımladığınızda üzerine yazılmaz. Sayfanın görünümünü özelleştirmek istiyorsanız, değişikliklerinizi kaybetme hakkında endişelenmeden bunu yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce varsayılan Web sayfasını özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 **Yayımla sayfası** özelliği, **Proje Tasarımcısı**' nın **Yayımla** bölmesinden erişilebilen **Yayımla Seçenekleri** iletişim kutusunda ayarlanabilir.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>ClickOnce uygulaması için özel bir Web sayfası belirtmek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** bölmesini seçin.  
  
3. **Yayımla Seçenekleri** iletişim kutusunu açmak için **Seçenekler** düğmesine tıklayın.  
  
4. **Dağıtım**' ye tıklayın.  
  
5. **Yayımla Seçenekleri** iletişim kutusunda, Yayımla ' nın **ardından dağıtım Web sayfasını aç** onay kutusunun seçili olduğundan emin olun (varsayılan olarak seçilmelidir).  
  
6. **Dağıtım Web sayfası:** kutusuna Web sayfanızın adını girin ve ardından **Tamam**' a tıklayın.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Yayımla sayfasının her yayımlaışınızda başlatılmasını engellemek için  
  
1. **Çözüm Gezgini**' de bir proje seçiliyken, **Proje** menüsünde **Özellikler**' e tıklayın.  
  
2. **Yayımla** bölmesini seçin.  
  
3. **Yayımla Seçenekleri** iletişim kutusunu açmak için **Seçenekler** düğmesine tıklayın.  
  
4. **Dağıtım**' ye tıklayın.  
  
5. **Yayımla Seçenekleri** iletişim kutusunda, **yayımlamadan sonra dağıtım Web sayfasını aç** onay kutusunu temizleyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)   
 [Nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Nasıl yapılır: ClickOnce Varsayılan Web Sayfasını Özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
