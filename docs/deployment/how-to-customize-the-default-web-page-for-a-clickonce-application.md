---
title: Uygulama için varsayılan web ClickOnce özelleştirme
description: Uygulamanın adını ve diğer bilgileri içeren ClickOnce web uygulaması yayımlarken oluşturulan Web sayfası hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 5185d3b49d8d1accaae7055f8bd073f9a25007dc92adff8c0978de957a55c284
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121403964"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Nasıl kullanılır: Bir uygulama için varsayılan Web ClickOnce özelleştirme
Bir web ClickOnce Web'de yayımlarken, bir Web sayfası otomatik olarak oluşturulur ve uygulamayla birlikte yayımlanır. Varsayılan sayfa uygulamanın adını ve uygulamayı yükleme, önkoşulları yükleme veya MSDN'de erişim yardımı bağlantılarını içerir.

> [!NOTE]
> Sayfada gördüğünüz gerçek bağlantılar, sayfanın görüntü bulunduğu bilgisayara ve hangi önkoşullara sahip olduğunuz bilgisayara bağlıdır.

 Web sayfası için varsayılan ad *Publish.htm;* Project **Designer'da Project değiştirebilirsiniz.** Daha fazla bilgi için, [bkz. How to: Specify a publish page for a ClickOnce application](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 Publish.htm Web sayfası yalnızca daha yeni bir sürüm algılandığında yayımlanır.

> [!NOTE]
> Yayımlama ayarlarınıza yaptığınız  değişiklikler *Publish.htm* sayfasını etkilemez; tek bir istisna vardır: önkoşulları ilk yayımlamadan sonra ekler veya kaldırırsanız, önkoşul listesi artık doğru olmaz. Değişiklikleri yansıtmak için önkoşul bağlantısının metnini düzenlemeniz gerekir.

### <a name="to-customize-the-publish-web-page"></a>Web'i yayımlama sayfasını özelleştirmek için

1. Uygulama ClickOnce Web konuma yayımlayın. Daha fazla bilgi için [bkz. Yayımlama Sihirbazı'nı ClickOnce uygulama yayımlama.](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)

2. Web sunucusunda, webPublish.htm *Web* Tasarımcısı'nda veya başka bir HTML düzenleyicisinde açın.

3. Sayfayı istediğiniz gibi özelleştirin ve kaydedin.

4. İsteğe bağlı. Özelleştirilmiş yayımlama Visual Studio üzerine yazmamanızı önlemek için, Yayımlama Seçenekleri iletişim kutusundaki Her yayımlamadan sonra Dağıtım **Web** sayfasını otomatik olarak oluştur **seçeneğinin işaretini** kaldırın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Uygulama ClickOnce yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl kurulur: ClickOnce uygulamasıyla önkoşulları yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Nasıl ClickOnce: Uygulama için yayımlama sayfası belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)