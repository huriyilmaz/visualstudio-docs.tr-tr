---
title: Microsoft Ürün ve Hizmet Sözleşmesinde (MPSA)' daki Visual Studio abonelikleri| Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Microsoft Ürün ve Hizmet Sözleşmesinde (MPSA) Visual Studio abonelikleri
ms.openlocfilehash: e4416bfab95bd7d1c38c392bfbf9efee9a06fc7f
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78410255"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Microsoft Ürün ve Hizmet Sözleşmesinde (MPSA) Visual Studio abonelikleri
MPSA programı aracılığıyla Visual Studio Abonelikleri satın aldıysanız, Visual Studio abonelikleri yöneticisi olmadan ve kullanıcılarınıza abonelik atamadan önce dikkat edilmesi gereken birkaç şey vardır. Zaten bir yönetici olarak kurulduysanız, doğrudan Visual Studio abonelikleri [Yönetim Portalı'na](https://manage.visualstudio.com/)gidebilirsiniz.

MPSA müşterileri artık MPSA aracılığıyla satın alınan [varlıkları,](https://businessaccount.microsoft.com/Customer)Toplu LisansLama Hizmet Merkezi'ne (VLSC) benzer işlevleri destekleyen İş Merkezi adlı yeni bir portalda yönetiyor. Bunlar arasında Lisans Özetinizi, Siparişlerinizi, İndirmelerinizi, Anahtarlarınızı, Kullanıcılarınızı vb. görüntülemeniz yer alır. Ancak, MPSA'daki Visual Studio abonelikleri Bulut Hizmetleri'ne çok benzer. İş Merkezi, Microsoft Hesapları (MSA) yerine oturum açma için iş hesaplarını da kullanır. Kuruluşunuz Office 365 veya Azure Etkin Dizini gibi bulut hizmetlerini kullanıyorsa ve e-postanız bu iki hizmetten birinin parçasıysa, bu zaten bir iş hesabıdır. Bu, mevcut şifrenizle İş Merkezi'ne kaydolmanızı sağlar. Kuruluşunuz bulut hizmetlerini kullanmıyorsa ve e-postanız bir iş hesabı değilse, bu hizmeti İş Merkezi'ne kaydolmak için kullanabilirsiniz.

Buna ek olarak, Visual Studio abonelikleri [Yönetim Portalı,](https://manage.visualstudio.com/) Visual Studio abonelikleri yöneticisi olduktan sonra abonelere aboneliklerin atanacağı yerdir. MPSA'da Visual Studio abonelikleri, Visual Studio Abonelikleri Yönetim Portalı olan ilgili yönetim portallarına sağlanmalıdır. Bunu yapmak için Satınalma Hesabınızı kiracıyla ilişkilendirmeniz gerekir (örn. contoso.onmicrosoft.com).

Yönetilen kiracılar ve yönetilmeyen kiracılar olmak gibi iki tür kiracı olduğunu lütfen unutmayın. Yönetilen kiracı, kuruluş içindeki yöneticiler tarafından zaten yönetilen bir kiracıyı ifade eder.

Yönetilmeyen bir kiracı, herhangi bir yönetici atanmadan kiracıdır ve Office 365 gibi Çevrimiçi Hizmetler için kullanılamaz. Yönetilmeyen kiracılar, Iş Merkezi'ne iş hesabı olmayan bir e-postayla kaydolurken de oluşturulur. İş Merkezi'ne kaydolurken parola oluşturmanız istenirse, bu e-postanızın bir iş hesabı olmadığı ve yönetilmeyen bir kiracı oluşturduğu anlamına gelir.

Kiracı ilişkilendirmesini tamamlamadan önce Visual Studio Abonelikleri yöneticisi olmak için gereken birkaç gereksinim/adım aşağıda veda edilmiştir.

## <a name="pre-tenant-association-managed-tenant"></a>Ön kiracı derneği (yönetilen kiracı)
- İş Merkezi'ne kayıtlı bir kullanıcı olmalısınız.
- Parçası olduğunuz kiracının içinde Kullanıcı Yöneticisi (en azından) veya Global Yönetici olmalısınız. (Şirketiniz bulut hizmetlerini zaten kullanıyorsa bu geçerlidir). Visual Studio abonelikleri yöneticisi olmak için her iki rolün de gereklidir.
- Satınalma Hesabınızı kiracınızla ilişkilendirebilmek için kiracıda Global Yönetici olmalısınız.
- İş Merkezi'nde Hesap Yöneticisi veya Hesap Yöneticisi olmalısınız.
- [Azure'daki](https://portal.azure.com/) kullanıcı profilinizdeki (ve diğer tüm kullanıcı) "Ülke veya Bölge" alanının bölgenize (ABD, CA, vb.) bağlı olarak uygun şekilde doldurulması gerekir. 

> [!NOTE]
> Visual Studio abonelikleri yapmak istediğiniz kullanıcıların Yalnızca 2 ve 5 kriterlerini karşılamaları gerektiğinden, İş Merkezi'nde kullanıcı olmaları gerekmez.

Yukarıdaki kriterleri karşıladıktan sonra aşağıdaki adımları izleyerek Satın Alma Hesabınızı kiracınızla ilişkilendirmeye devam edebilirsiniz.
1. [İş Merkezi'ne](https://businessaccount.microsoft.com/Customer)giriş yapın.
2. **Hesap** sekmesine tıklayın ve **Etki Alanlarını Ilişkilendir'i**seçin.
3. **Satınalma Hesabınızı** seçin (birden fazla hesabınız varsa).
4. **Kiracınızı** seçin (yani contoso.onmicrosoft.com).
5. **Etki Alanını Ilişkilendir'i**tıklatın.

İlişkilendirme üzerine, ölçütleri karşılayan tüm kullanıcılar genellikle birkaç dakika içinde Visual Studio abonelikleri yöneticileri olarak sağlanacaktır. Ancak, zaman zaman 24 saat kadar sürebilir. Kiracınız tedarik edildikten sonra Visual Studio Abonelikleri Yönetim Portalı'na erişebileceksiniz. Bu işlem 24 saatten uzun sürerse, lütfen aşağıdaki adımları kullanarak MPSA Desteği'ne başvurun:
1. Bağlantı kurunhttps://www.microsoft.com/licensing/mpsa/default
2. Sayfanın üst kısmındaki **Diğer** menüsünü tıklatın. 
3. **Destek** Seçin
4. **Lisanslama desteği** seçin
5. İhtiyaçlarınıza en uygun destek seçeneğini seçin. 

> [!NOTE]
> 2 ve 5 adımlarında (ilişkilendirmeden sonra) ölçütleri karşılayan yeni kullanıcılar varsa, MPSA Desteği'ne başvurmanız gerekir. MPSA Desteği, yeni Visual Studio Abonelikleri yöneticilerinin sağlanmasına yardımcı olacaktır.

## <a name="tenant-association-unmanaged"></a>Kiracı ilişkilendirme (yönetilmeyen)
İş Merkezi'ne iş hesabı olmayan bir e-postayla (Azure Etkin Dizini "Azure AD"'de kayıtlı olmayan) kaydolduysanız, kiracı ilişkisi biraz farklı olacaktır. "Etki alanı devralma" adı verilen şeyi gerçekleştirmeniz gerekir. Bu işlem sırasında kendinizi, kiracınızı yönetilmeyenden yönetilene çevirecek Olan Küresel Yönetici yapacaksınız.

Bu işlem için daha ayrıntılı bir açıklama için [Hızlı Başlangıç kılavuzlarını](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx)kullanabilirsiniz. Lütfen bir etki alanı devralma yoluyla size rehberlik edecek *"Kurulum ve Çevrimiçi Hizmetleri nizi Kullanın"* adlı kılavuzu indirin. Bu tamamlandığında Satın Alma Hesabınız da kiracınızla ilişkilendirilecektir.

> [!NOTE]
> Etki alanı devralma işlemini tamamladıktan sonra, Ön Kiracı İlişkisi (Yönetilen) bölümündeki beş adımdaki ölçütlere uymanız gerekir. Ölçütler karşılandıktan sonra, ek Visual Studio abonelikleri yöneticilerini sağlamak için yalnızca MPSA Destek ile iletişime geçmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Tek tek abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [Maksimum kullanımı belirleme](maximum-usage.md)
