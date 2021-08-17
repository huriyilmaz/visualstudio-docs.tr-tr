---
title: ClickOnce uygulaması için varsayılan web sayfasını özelleştirme
description: uygulamanın adını ve diğer bilgileri içeren bir ClickOnce uygulamasını Web 'de yayımladığınızda oluşturulan web sayfası hakkında bilgi edinin.
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
ms.openlocfilehash: 2a1a3ae95889c3e57a2404090d7cf2db7a27e9a9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073844"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>nasıl yapılır: bir ClickOnce uygulaması için varsayılan Web sayfasını özelleştirme
bir ClickOnce uygulamasını web 'de yayımlarken, bir web sayfası otomatik olarak oluşturulur ve uygulamayla birlikte yayımlanır. Varsayılan sayfa, uygulamanın adını ve uygulamanın yükleneceği bağlantıları, önkoşulları yüklemeyi veya MSDN 'de yardım erişimini içerir.

> [!NOTE]
> Sayfada gördüğünüz gerçek bağlantılar, sayfanın görüntülendiği bilgisayara ve hangi önkoşulları dahil ettiğiniz üzerine bağlıdır.

 Web sayfası için varsayılan ad *Publish.htm*; **Project tasarımcısında** adı değiştirebilirsiniz. daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce bir uygulama için yayımlama sayfası belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 *Publish.htm* Web sayfası yalnızca daha yeni bir sürüm algılandığında yayımlanır.

> [!NOTE]
> **Yayımlama** ayarlarınızda yaptığınız değişiklikler, tek bir özel durumla *Publish.htm* sayfasını etkilemez: başlangıçta yayımlamadan sonra önkoşulları ekler veya kaldırırsanız, önkoşul listesi artık doğru olmaz. Değişiklikleri yansıtmak için önkoşul bağlantısı metnini düzenlemeniz gerekir.

### <a name="to-customize-the-publish-web-page"></a>Web 'i Yayımla sayfasını özelleştirmek için

1. ClickOnce uygulamanızı bir Web konumunda yayımlayın. daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulama yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Web sunucusunda, *Publish.htm* dosyasını Visual Web Tasarımcısı veya başka bir HTML düzenleyicisinde açın.

3. Sayfayı istediğiniz gibi özelleştirin ve kaydedin.

4. İsteğe bağlı. Visual Studio özelleştirilmiş web yayımlama sayfanızın üzerine yazmasını engellemek için, **yayımlama seçenekleri** iletişim kutusunda **her yayımladıktan sonra otomatik olarak dağıtım Web sayfası oluştur** seçeneğinin işaretini kaldırın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [nasıl yapılır: ClickOnce uygulamayla önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [nasıl yapılır: ClickOnce uygulaması için bir yayımlama sayfası belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)