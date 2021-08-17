---
title: Visual Studio MPSA 'da abonelikler | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/21/2021
ms.topic: conceptual
description: Microsoft ürün ve hizmet sözleşmesi 'nde (mpsa) Visual Studio aboneliklerini yönetme hakkında bilgi edinin
ms.openlocfilehash: 2cc01a90bbdaa1a627dc076593fad6756cb0b0c28a4a4b859883bff63f6f33d8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121421550"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Microsoft ürün ve hizmet anlaşmasındaki (mpsa) abonelikler Visual Studio
mpsa programı aracılığıyla Visual Studio abonelikleri satın aldıysanız, Visual Studio bir abonelik yöneticisi ve kullanıcılarınıza abonelik atama yapabilmeniz için bilmeniz gereken birkaç nokta vardır. zaten yönetici olarak ayarladıysanız, Visual Studio abonelikleri [yönetim portalına](https://manage.visualstudio.com/)doğrudan gidebilirsiniz.

MPSA müşterileri, Toplu Lisanslama hizmeti Merkezi 'ne (VLSC) benzer işlevleri destekleyen [Iş Merkezi](https://businessaccount.microsoft.com/Customer)adlı bir portalda MPSA aracılığıyla satın alınan varlıkları yönetir. Bunlar, lisans özetinizi, siparişlerinizi, yüklemelerinizi, anahtarlarınızı, kullanıcılarınızı vb. görüntülemeyi içerir. ancak, mpsa 'daki Visual Studio abonelikler Cloud Services çok benzer şekilde davranır. Iş Merkezi aynı zamanda Microsoft hesapları (MSA) yerine oturum açmak için iş hesapları kullanır. kuruluşunuz Office 365 veya Azure Active Directory gibi bulut hizmetleri kullanıyorsa ve e-postanız bu iki hizmetin bir parçasıysa, zaten bir iş hesabıdır. Bu, mevcut parolanızla Iş Merkezi 'ne kaydetmenizi sağlar. Kuruluşunuz bulut hizmetlerini kullanmıyor ve e-postanız bir iş hesabı değilse, Iş merkezine kaydolmak için kullanabilirsiniz.

ayrıca, Visual Studio abonelikleri [yönetim portalı](https://manage.visualstudio.com/) , Visual Studio abonelikleri yöneticisi olduktan sonra abonelikleri atayacaksınız. mpsa 'da Visual Studio aboneliklerin, Visual Studio abonelikleri yönetim portalı olan ilgili yönetim portalına sağlanması gerekir. Bunu yapmak için satın alma hesabınızı bir kiracıyla (örn. contoso.onmicrosoft.com) ilişkilendirmeniz gerekir.

Kiracıların yönettiği iki tür kiracılar ve yönetilmeyen kiracılar olduğunu unutmayın. Yönetilen kiracı, kuruluş içindeki Yöneticiler tarafından zaten yönetilen bir kiracıya başvurur.

Yönetilmeyen bir kiracı, hiçbir yönetici atanmamış ve Office 365 gibi çevrimiçi hizmetler için kullanılamaz. Yönetilmeyen kiracılar iş merkezine iş hesabı olmayan bir e-posta ile kaydedilirken de oluşturulur. Iş merkezine kaydolurken bir parola oluşturmanız istenirse, e-postanız iş hesabı olmadığı ve yönetilmeyen bir kiracı oluşturduğu anlamına gelir.

kiracı ilişkilendirmesini tamamlamadan önce Visual Studio abonelik yöneticisi olmaya yönelik birkaç gereksinim/adım aşağıda verilmiştir.

## <a name="pre-tenant-association-managed-tenant"></a>Kiracı öncesi ilişkilendirme (yönetilen kiracı)
- Iş merkezinde kayıtlı bir kullanıcı olmanız gerekir.
- Bir Kullanıcı Yöneticisi (en az) veya bir parçası olduğunuz kiracının içinde genel yönetici olmanız gerekir. (Şirketiniz zaten Cloud Services kullanıyorsa bu geçerlidir). rolün Visual Studio bir abonelik yöneticisi olması gerekir.
- Satın alma hesabınızı kiracınızla ilişkilendirebilmek için bir parçası olan kiracıda bir genel yönetici olmanız gerekir.
- Iş Merkezi 'nde bir hesap yöneticisi veya hesap yöneticisi olmanız gerekir.
- [Azure](https://portal.azure.com/) 'daki Kullanıcı profilinizde (ve diğer herhangi bir Kullanıcı) bulunan "ülke veya bölge" alanının, bölgenize (ör. ABD, CA, vb.) bağlı olarak uygun şekilde doldurulması gerekir. 

> [!NOTE]
> Visual Studio abonelikleri yöneticileri yapmak istediğiniz tüm kullanıcıların, yalnızca 2 ve 5 ölçütlerine uyması gereken iş merkezindeki kullanıcılar olması gerekmez.

Yukarıdaki ölçütleri karşıladıktan sonra, aşağıdaki adımları izleyerek satın alma hesabınızı kiracınızla ilişkilendirmeye devam edebilirsiniz.
1. [Iş merkezinde](https://businessaccount.microsoft.com/Customer)oturum açın.
2. **Hesap** sekmesine tıklayın ve **etki alanlarını ilişkilendir**' i seçin.
3. **Satın alma hesabınızı** seçin (birden fazla varsa).
4. **Kiracınızı** seçin (örnek: contoso.onmicrosoft.com).
5. **Etki alanını ilişkilendir**' e tıklayın.

ilişkilendirmeden, ölçütlere uyan tüm kullanıcılar genellikle dakikalar içinde Visual Studio abonelikleri yöneticileri olarak temin eder. Ancak, 24 saate kadar zaman alabilir. kiracınız sağlandıktan sonra, Visual Studio abonelikleri yönetim portalına erişebileceksiniz. Bu, 24 saatten uzun sürerse, [Iş Merkezi desteğiyle](https://businessaccount.microsoft.com/Customer/ContactUs)iletişim kurun.

> [!NOTE]
> 2 ve 5. adımlarda (ilişkilendirmeden sonra) ölçütlere uyan yeni kullanıcılar varsa MPSA desteğiyle iletişim kurmanız gerekir. mpsa desteği, yeni Visual Studio abonelikleri yöneticilerinin sağlanması için yardım sağlar.

## <a name="tenant-association-unmanaged"></a>Kiracı ilişkilendirmesi (yönetilmeyen)
iş merkezine, yukarıda açıklandığı gibi, iş hesabı olmayan ("Azure AD" Azure Active Directory kayıtlı değil) bir e-posta ile kaydolduysanız, kiracı ilişkilendirmesi biraz farklı olur. "Etki alanı alma" olarak adlandırılan işlemleri gerçekleştirmeniz gerekecektir. Bu işlem sırasında, kiracınızı Yönetilmeyenden yönetilene değiştirecek genel yönetici yaparsınız.

Bu işlemle ilgili daha ayrıntılı bir açıklama için [hızlı başlangıç kılavuzlarını](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx)kullanabilirsiniz. *"Kurulum ve çevrimiçi hizmetlerinizi kullanma"* adlı Kılavuzu, bir etki alanı üzerinden alma sırasında size kılavuzluk edecek şekilde indirin. Bu işlem tamamlandıktan sonra, satın alma hesabınız kiracınızla de ilişkilendirilir.

> [!NOTE]
> Etki alanı alma işlemini tamamladığınızda, önceki kiracı Ilişkilendirmesi (yönetilen) bölümündeki beş adımdan gelen ölçütlere uymalısınız. ölçütler karşılandıktan sonra, yalnızca ek Visual Studio abonelikleri yöneticilerine sağlamak üzere mpsa desteğiyle iletişim kurmanız gerekir.

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio aboneliklerinin yönetimi hakkında yardım için, [Visual Studio abonelik desteğiyle](https://aka.ms/vsadminhelp)iletişim kurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Ayrı abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)