---
title: Yayımlama sayfası belirtme (ClickOnce uygulama)
description: Projeniz için Yayımlama Sayfası özelliğini ayarlamayı öğrenin. Bu özellik, uygulamanıza web sayfası ClickOnce sağlar.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: cfc043fc62bc99a8e292d89c9217dcb80e53f781
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146322"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Nasıl ClickOnce: Bir uygulama için yayımlama sayfası belirtme
Bir uygulamayı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlarken, uygulamayla birlikte publish.htm bir Web sayfası (publish.htm) oluşturulur ve yayımlanır. Bu sayfa uygulamanın adını, uygulamayı yükleme bağlantısını ve/veya önkoşulları ve açıklayan Yardım konusunun bağlantısını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] içerir. Projenizin **Sayfayı** Yayımla özelliği, uygulamanıza ait Web sayfası için bir ad belirtmenize olanak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sağlar.

 Yayımlama sayfası belirtildiktan sonra, bir sonraki yayımlama tarihinizi yayımla konumuna kopyalanır; yeniden yayımlarsanız üzerine yazılmaz. Sayfanın görünümünü özelleştirmek isterseniz, değişikliklerinizi kaybetme konusunda endişelenmeden bunu yapabilirsiniz. Daha fazla bilgi için [bkz. Nasıl ClickOnce Web sayfasını özelleştirme.](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)

 Sayfayı **Yayımla** özelliği, Yayımlama Seçenekleri **iletişim** kutusunda,  Project Tasarımcısı'nın **Yayımla bölmesinden erişilebilir.**

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Bir uygulama için özel bir Web ClickOnce belirtmek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **özellikler'Project** **tıklayın.**

2. Yayımla **bölmesini** seçin.

3. Seçenekleri **Yayımla** iletişim kutusunu açmak **için Seçenekler düğmesine** tıklayın.

4. **Dağıtım'a tıklayın.**

5. Yayımlama Seçenekleri **iletişim kutusunda,** Yayımlamadan sonra dağıtım **web** sayfasını aç onay kutusunun seçili olduğundan emin olun (varsayılan olarak seçilidir).

6. Dağıtım **web sayfası kutusuna** Web sayfasının adını girin ve tamam'a **tıklayın.**

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Yayımlama sayfasının her yayımlamada başlatılmasını önlemek için

1. içinde bir proje **seçiliyken Çözüm Gezgini** menüsünde **özellikler'Project** **tıklayın.**

2. Yayımla **bölmesini** seçin.

3. Seçenekleri **Yayımla** iletişim kutusunu açmak **için Seçenekler düğmesine** tıklayın.

4. **Dağıtım'a tıklayın.**

5. Yayımlama Seçenekleri **iletişim kutusunda,** Yayımlamadan sonra **dağıtım web sayfasını aç onay** kutusunun işaretini kaldırın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl ClickOnce: ClickOnce Sihirbazı'nı kullanarak bir uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Nasıl ClickOnce: ClickOnce Web sayfasını özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)