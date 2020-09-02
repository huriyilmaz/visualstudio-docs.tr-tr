---
title: ClickOnce uygulaması için varsayılan Web sayfasını özelleştirme
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ee4c1211840f17afe371961dea644372cd63efb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382477"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Nasıl yapılır: ClickOnce uygulaması için varsayılan Web sayfasını özelleştirme
Bir ClickOnce uygulamasını Web 'de yayımlarken, bir Web sayfası otomatik olarak oluşturulur ve uygulamayla birlikte yayımlanır. Varsayılan sayfa, uygulamanın adını ve uygulamanın yükleneceği bağlantıları, önkoşulları yüklemeyi veya MSDN 'de yardım erişimini içerir.

> [!NOTE]
> Sayfada gördüğünüz gerçek bağlantılar, sayfanın görüntülendiği bilgisayara ve hangi önkoşulları dahil ettiğiniz üzerine bağlıdır.

 Web sayfası için varsayılan ad *Publish.htm*; **Proje tasarımcısında**adı değiştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: ClickOnce uygulaması için bir yayımlama sayfası belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).

 *Publish.htm* Web sayfası yalnızca daha yeni bir sürüm algılandığında yayımlanır.

> [!NOTE]
> **Yayımlama** ayarlarınızda yaptığınız değişiklikler, tek bir özel durumla *Publish.htm* sayfasını etkilemez: başlangıçta yayımlamadan sonra önkoşulları ekler veya kaldırırsanız, önkoşul listesi artık doğru olmaz. Değişiklikleri yansıtmak için önkoşul bağlantısı metnini düzenlemeniz gerekir.

### <a name="to-customize-the-publish-web-page"></a>Web 'i Yayımla sayfasını özelleştirmek için

1. ClickOnce uygulamanızı bir Web konumunda yayımlayın. Daha fazla bilgi için bkz. [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

2. Web sunucusunda, *Publish.htm* dosyasını Visual Web Tasarımcısı veya başka bir HTML düzenleyicisinde açın.

3. Sayfayı istediğiniz gibi özelleştirin ve kaydedin.

4. İsteğe bağlı. Visual Studio 'Nun özelleştirilmiş yayımlama Web sayfanızın üzerine yazmasını engellemek için, **Yayımlama seçenekleri** iletişim kutusunda **her yayımladıktan sonra otomatik olarak dağıtım Web sayfası oluştur** seçeneğinin işaretini kaldırın.

## <a name="see-also"></a>Ayrıca bkz.
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md)
- [Nasıl yapılır: ClickOnce uygulamasıyla önkoşulları yüklemek](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Nasıl yapılır: ClickOnce uygulaması için bir yayımlama sayfası belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)