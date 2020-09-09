---
title: MPSA 'da Visual Studio abonelikleri | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 09/03/2020
ms.topic: conceptual
description: Microsoft ürün ve hizmet sözleşmesi 'nde (MPSA) Visual Studio aboneliklerini yönetme hakkında bilgi edinin
ms.openlocfilehash: 9d26bccebb11a59933c37ec0f29a9b6e30e86c5b
ms.sourcegitcommit: f8d14fab194fcb30658f23f700da07d35ffc9d4a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89561396"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Microsoft ürün ve hizmet anlaşmasındaki (MPSA) Visual Studio abonelikleri
MPSA programı aracılığıyla Visual Studio abonelikleri satın aldıysanız, Visual Studio abonelikleri Yöneticisi olmaya ve kullanıcılarınıza abonelik atamadan önce bilmeniz gereken birkaç nokta vardır. Zaten yönetici olarak ayarladıysanız, doğrudan Visual Studio abonelikleri [Yönetim portalına](https://manage.visualstudio.com/)gidebilirsiniz.

MPSA müşterileri, Toplu Lisanslama hizmeti Merkezi 'ne (VLSC) benzer işlevleri destekleyen [Iş Merkezi](https://businessaccount.microsoft.com/Customer)adlı bir portalda MPSA aracılığıyla satın alınan varlıkları yönetir. Bunlar, lisans özetinizi, siparişlerinizi, yüklemelerinizi, anahtarlarınızı, kullanıcılarınızı vb. görüntülemeyi içerir. Ancak, MPSA 'daki Visual Studio abonelikleri Cloud Services benzer şekilde davranır. Iş Merkezi aynı zamanda Microsoft hesapları (MSA) yerine oturum açmak için iş hesapları kullanır. Kuruluşunuz Office 365 veya Azure Active Directory gibi bulut Hizmetleri kullanıyorsa ve e-postanız bu iki hizmetin bir parçasıysa, zaten bir iş hesabıdır. Bu, mevcut parolanızla Iş Merkezi 'ne kaydetmenizi sağlar. Kuruluşunuz bulut hizmetlerini kullanmıyor ve e-postanız bir iş hesabı değilse, Iş merkezine kaydolmak için kullanabilirsiniz.

Ayrıca, Visual Studio abonelikleri [Yönetim Portalı](https://manage.visualstudio.com/) , bir Visual Studio abonelikleri Yöneticisi olduktan sonra abonelikleri atayacaksınız. MPSA 'da, Visual Studio aboneliklerinin Visual Studio abonelikleri yönetim portalı olan ilgili yönetim portalına sağlanması gerekir. Bunu yapmak için satın alma hesabınızı bir kiracıyla (örn. contoso.onmicrosoft.com) ilişkilendirmeniz gerekir.

Kiracıların yönettiği iki tür kiracılar ve yönetilmeyen kiracılar olduğunu lütfen unutmayın. Yönetilen kiracı, kuruluş içindeki Yöneticiler tarafından zaten yönetilen bir kiracıya başvurur.

Yönetilmeyen bir kiracı, hiçbir yönetici atanmamış ve Office 365 gibi çevrimiçi hizmetler için kullanılabilir olmayan bir kiracıya sahip değildir. Yönetilmeyen kiracılar iş merkezine iş hesabı olmayan bir e-posta ile kaydedilirken de oluşturulur. Iş merkezine kaydolurken bir parola oluşturmanız istenirse, e-postanız iş hesabı olmadığı ve yönetilmeyen bir kiracı oluşturduğu anlamına gelir.

Kiracı ilişkilendirmesini tamamlamadan önce Visual Studio abonelikleri Yöneticisi olmaya yönelik birkaç gereksinim/adım aşağıda verilmiştir.

## <a name="pre-tenant-association-managed-tenant"></a>Kiracı öncesi ilişkilendirme (yönetilen kiracı)
- Iş merkezinde kayıtlı bir kullanıcı olmanız gerekir.
- Bir Kullanıcı Yöneticisi (en az) veya bir parçası olduğunuz kiracının içinde genel yönetici olmanız gerekir. (Şirketiniz zaten Cloud Services kullanıyorsa bu geçerlidir). Her iki rolün de bir Visual Studio abonelikleri Yöneticisi olması gerekir.
- Satın alma hesabınızı kiracınızla ilişkilendirebilmek için bir parçası olan kiracıda bir genel yönetici olmanız gerekir.
- Iş Merkezi 'nde bir hesap yöneticisi veya hesap yöneticisi olmanız gerekir.
- [Azure](https://portal.azure.com/) 'daki Kullanıcı profilinizde (ve diğer herhangi bir Kullanıcı) bulunan "ülke veya bölge" alanının, bölgenize (ör. ABD, CA, vb.) bağlı olarak uygun şekilde doldurulması gerekir. 

> [!NOTE]
> Visual Studio abonelikleri yöneticileri yapmak istediğiniz tüm kullanıcıların, yalnızca 2 ve 5 ölçütlerine uyması gereken Iş merkezinde kullanıcılar olması gerekmez.

Yukarıdaki kriterleri karşıladıktan sonra, aşağıdaki adımları izleyerek satın alma hesabınızı kiracınızla ilişkilendirmeye devam edebilirsiniz.
1. [Iş merkezinde](https://businessaccount.microsoft.com/Customer)oturum açın.
2. **Hesap** sekmesine tıklayın ve **etki alanlarını ilişkilendir**' i seçin.
3. **Satın alma hesabınızı** seçin (birden fazla varsa).
4. **Kiracınızı** (ör. contoso.onmicrosoft.com) seçin.
5. **Etki alanını ilişkilendir**' e tıklayın.

İlişkilendirmede, ölçütlere uyan tüm kullanıcılar genellikle dakikalar içinde Visual Studio abonelikleri Yöneticisi olarak temin eder. Ancak, 24 saate kadar zaman alabilir. Kiracınız sağlandıktan sonra Visual Studio abonelikleri yönetim portalına erişebileceksiniz. Bu, 24 saatten uzun sürerse lütfen şu adımları kullanarak MPSA desteğine başvurun:
1. Bağlan <https://www.microsoft.com/licensing/mpsa/default>
2. Sayfanın üst kısmındaki **daha fazla** menüye tıklayın. 
3. **Destek** seçin
4. **Lisans desteğini** seçin
5. Gereksinimlerinize en uygun destek seçeneğini belirleyin. 

> [!NOTE]
> 2 ve 5. adımlarda (ilişkilendirmeden sonra) ölçütlere uyan yeni kullanıcılar varsa MPSA desteğiyle iletişim kurmanız gerekir. MPSA desteği, yeni Visual Studio abonelikleri yöneticilerini sağlamaya yönelik yardım sağlayacaktır.

## <a name="tenant-association-unmanaged"></a>Kiracı ilişkilendirmesi (yönetilmeyen)
Iş merkezine, yukarıda açıklandığı gibi, iş hesabı olmayan ("Azure AD" Azure Active Directory kayıtlı değil) bir e-posta ile kaydolduysanız, kiracı ilişkilendirmesi biraz farklı olur. "Etki alanı alma" olarak adlandırılan işlemleri gerçekleştirmeniz gerekecektir. Bu işlem sırasında, kiracınızı yönetilmeyecek şekilde değiştirecek genel yönetici yaparsınız.

Bu işlemle ilgili daha ayrıntılı bir açıklama için [hızlı başlangıç kılavuzlarını](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx)kullanabilirsiniz. Lütfen *"Kurulum ve çevrimiçi hizmetlerinizi kullanma"* adlı Kılavuzu indirerek bir etki alanı alma sırasında size rehberlik edecek şekilde indirin. Bu işlem tamamlandıktan sonra, satın alma hesabınız kiracınızla de ilişkilendirilir.

> [!NOTE]
> Etki alanı alma işlemini tamamladıktan sonra, kiracı Ilişkilendirmesi (yönetilen) bölümündeki beş adımdan oluşan ölçütlere uymalısınız. Ölçütler karşılandıktan sonra, yalnızca ek Visual Studio abonelikleri yöneticileri sağlamak için MPSA desteğiyle iletişim kurmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Ayrı abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)
