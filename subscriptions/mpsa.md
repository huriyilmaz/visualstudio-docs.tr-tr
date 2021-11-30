---
title: MPSA Visual Studio Abonelikleri | Microsoft Docs
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: b331c837-3524-42b7-820e-b4fdd5e12793
ms.date: 03/21/2021
ms.topic: conceptual
description: Microsoft Ürün ve Visual Studio Sözleşmesi'nde (MPSA) abonelikleri yönetme hakkında bilgi edinin
ms.openlocfilehash: c196ca15b02357b12066c8c5d4ea7a2dbbae958b
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133257589"
---
# <a name="visual-studio-subscriptions-in-a-microsoft-products-and-services-agreement-mpsa"></a>Visual Studio Ürün ve Hizmet Sözleşmesi'nde (MPSA) abonelikleri güncelleştirme
MPSA programı Visual Studio Abonelikler satın aldıysanız, Visual Studio abonelik yöneticisi olup kullanıcılarınıza abonelikler atamadan önce dikkat etmek istediğiniz birkaç şey vardır. Zaten yönetici olarak ayarlanmışsanız, doğrudan yönetici abonelikleri Yönetim Portalı'Visual Studio [gidebilirsiniz.](https://manage.visualstudio.com/)

MPSA müşterileri, MPSA aracılığıyla satın alınan [varlıkları, Toplu](https://businessaccount.microsoft.com/Customer)Lisanslama Hizmet Merkezi'ne (VLSC) benzer işlevleri destekleyen İş Merkezi adlı bir portalda yönetir. Bunlar Lisans Özeti, Siparişler, İndirmeler, Anahtarlar, Kullanıcılar vb. görüntülemeyi içerir. Ancak, MPSA Visual Studio abonelikleri diğer abonelikler gibi Cloud Services. İş Merkezi, Microsoft Hesapları (MSA) yerine oturum açma için iş hesaplarını da kullanır. Kuruluşta Office 365 veya Azure Active Directory gibi bulut hizmetleri kullanıyorsa ve e-postanız bu iki hizmetlerden herhangi biri ise zaten bir iş hesabıdır. Bu, mevcut parolanız ile İş Merkezi'ne kaydolmanıza olanak sağlar. Bulut hizmetleri kullanıyorsanız ve e-postanız bir iş hesabı yoksa, bunu İş Merkezi'ne kaydolmak için kullanabilirsiniz.

Ayrıca, Visual Studio [abonelikler Yönetim Portalı,](https://manage.visualstudio.com/) abonelik yöneticisi olduktan sonra abonelikleri Visual Studio olur. MPSA'da Visual Studio aboneliklerin ilgili yönetim portalına (Abonelikler Yönetim Portalı Visual Studio sağlanması gerekir. Bunu yapmak için Satın Alma Hesabı'nızı bir kiracıyla (örneğin, contoso.onmicrosoft.com).

İki tür kiracı olduğunu unutmayın: yönetilen kiracılar ve yönetilemeyen kiracılar. Yönetilen kiracı, kuruluş içindeki yöneticiler tarafından zaten yönetilen bir kiracıyı ifade eder.

Yönetlanmamış kiracı, yönetici atanmamış bir kiracıdır ve yönetici ataması gibi Çevrimiçi Hizmetler için Office 365. İş Merkezi'ne iş hesabı olmayan bir e-posta ile kaydolan, ayrıca, unmanaged kiracıları oluşturulur. İş Merkezi'ne kaydolarak bir parola oluşturmanız istenirse bu, e-postanız bir iş hesabı olmadığını ve bir kiracı oluşturduğu anlamına gelir.

Kiracı ilişkilendirmeyi tamamlamadan önce Abonelikler Visual Studio olmak için birkaç gereklilik/adım burada ve ardından.

## <a name="pre-tenant-association-managed-tenant"></a>Kiracı öncesi ilişkilendirme (yönetilen kiracı)
- İş Merkezi'ne kayıtlı bir kullanıcı olmak gerekir.
- Üyesi olduğunuz kiracıda Kullanıcı Yöneticisi (en azından) veya Genel Yönetici olmak gerekir. (Bu durum, şirketiniz zaten Cloud Services). Her iki rolün de abonelik yöneticisi Visual Studio olması gerekir.
- Satın Alma Hesabı'nızı kiracınız ile ilişkilendirmek için, parçası olduğunuz kiracıda Genel Yönetici olmak gerekir.
- İş Merkezi'nde Hesap Yöneticisi veya Hesap Yöneticisi olmak gerekir.
- [Azure'daki](https://portal.azure.com/) kullanıcı profili (ve diğer kullanıcılar) içindeki "Ülke veya Bölge" alanı, bölgenize (ABD, CA vb.) bağlı olarak uygun şekilde doldurulması gerekir. 

> [!NOTE]
> Abonelik yöneticisi olarak Visual Studio istediğiniz kullanıcıların İş Merkezi'nde kullanıcı olması gerekmez çünkü yalnızca 2 ve 5 ölçütlerini karşılamaları gerekir.

Yukarıdaki ölçütleri karşıladikten sonra, aşağıdaki adımları takip eden Satın Alma Hesabı'nızı kiracınız ile ilişkilendirmeye devam edebilirsiniz.
1. [İş Merkezi'nde oturum açma.](https://businessaccount.microsoft.com/Customer)
2. Hesap sekmesine tıklayın **ve** Etki Alanlarını **İşle'yi seçin.**
3. Satın Alma **Hesabı'nızı** seçin (birden fazla hesabınız varsa).
4. Kiracınızı **seçin** (örnek: contoso.onmicrosoft.com).
5. Etki Alanını **İşle'ye tıklayın.**

İlişkilenin ardından, ölçütlere uyan tüm kullanıcılar genellikle dakikalar Visual Studio abonelik yöneticileri olarak sağlar. Ancak bazen bu süre 24 saate kadar sürebilir. Kiracınız sağlandıktan sonra Abonelikler Yönetim Portalı'Visual Studio erişebilirsiniz. Bu 24 saat daha uzun sürerse İş Merkezi [desteğine başvurun.](https://businessaccount.microsoft.com/Customer/ContactUs)

> [!NOTE]
> 2. ve 5. adımlarda (ilişkilendirmeden sonra) ölçütlere uyan yeni kullanıcılar varsa MPSA Desteği'ne başvurabilirsiniz. MPSA Desteği, abonelik yöneticilerine yeni Visual Studio sağlar.

## <a name="tenant-association-unmanaged"></a>Kiracı ilişkilendirmesi (yönetimsiz)
Yukarıda açıklanan şekilde, İş Merkezi'ne bir iş hesabı (Azure Active Directory "Azure AD" içinde kayıtlı değil) bir e-posta ile kaydedilmişse, kiracı ilişkilendirmesi biraz farklı olur. "Etki alanı teslim alma" olarak adlandırılan işlemi gerçekleştirmeniz gerekir. Bu işlem sırasında, kiracınızı yönetilemeyenden yönetilene değiştirecek genel yönetici olarak değiştireceksiniz.

Bu işlemle ilgili daha ayrıntılı bir açıklama için hızlı başlangıç [kullanabilirsiniz.](https://www.microsoft.com/Licensing/existing-customer/business-center-training-and-resources.aspx) Bir etki alanı *teslim alma işlemi boyunca size yol göstermenizi* sağlar"Çevrimiçi Hizmetlerinizi Kurma ve Kullanma" adlı kılavuzu indirin. Bu tamamlandıktan sonra Satın Alma Hesabınız da kiracınız ile ilişkilendirilecek.

> [!NOTE]
> Etki alanı teslim alma işlemini tamamlarken, Kiracı Öncesi İlişkisi (Yönetilen) bölümündeki beş adımda yer alan ölçütlere uymanız gerekir. Ölçütler karşılandıktan sonra, abonelik yöneticilerine ek hizmet sağlamaları için yalnızca MPSA Desteği'ne Visual Studio gerekir.

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio Aboneliklerinin yönetimiyle ilgili yardım için, Visual Studio [ile iletişime geçin.](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Abonelikleri yönetme hakkında daha fazla Visual Studio edinin.
- [Bireysel abonelik atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)