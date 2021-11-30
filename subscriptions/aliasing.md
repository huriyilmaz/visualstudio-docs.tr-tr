---
title: Visual Studio aboneliklerinde oturum açmak, diğer adlar kullanılırken başarısız olabilir | Microsoft Docs
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/19/2021
ms.topic: conceptual
description: Diğer adlar veya kolay adlar kullanılıyorsa oturum açma başarısız olabilir
ms.openlocfilehash: 418969a73200f9f5c6fb3e9536b27182efd7b034
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133256288"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>diğer adlar kullanılırken Visual Studio aboneliklerinde oturum açma başarısız olabilir
Oturum açmak için kullanılan hesap türüne bağlı olarak, kullanılabilir abonelikler ' de oturum açarken doğru görüntülenmeyebilir [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) . Olası bir neden, aboneliğin atandığı oturum açma kimliği yerine "diğer adlar" veya "kolay adlar" in kullanılması olabilir. Bu "diğer ad" olarak adlandırılır.

## <a name="what-is-aliasing"></a>Diğer ad nedir?
"diğer ad" terimi, Windows (veya Active Directory) oturum açmak ve e-postaya erişmek için farklı kimliklere sahip kullanıcılar anlamına gelir.

Şirket, ' ' gibi dizin oturum açma işlemi için Microsoft Online hizmetine sahip JohnD@contoso.com olsa da diğer adlara ve kullanıcılara ' ' gibi diğer adlar veya kolay adlar kullanarak e-posta hesaplarına erişebilirler John.Doe@contoso.com . Kullanıcılarınızın aboneliklerine erişmek için, yönetim portalı 'nda listelenen "oturum açma e-posta adresini" kullandığınızdan emin olun https://manage.visualstudio.com . 

## <a name="what-are-the-potential-issues"></a>Olası sorunlar nelerdir?

Abonenin hesap türüne bağlı olarak, iki sorunlardan biriyle karşılaşabilirler. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>İş veya okul hesabı UPN uyumsuzluğu sorunu 
Bir şirket, UserPrincipalName (UPN) birincil SMTP adresi ile aynı olmayan bir Active Directory ayarlandığında UPN uyuşmazlığına rastlabilir. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Oturum açma adresinizin UPN uyuşmazlığından etkilenip etkilenmediğinizi algılama 

1. https://my.visualstudio.com/subscriptionsAbonelik atama e-postanız bölümünde bahsedilen oturum açma adresini kullanarak oturum açın.

2. Sayfanın sağ üst köşesindeki adınızın üzerine tıklayın.  Bu, profilinizi açar.  Profilinizde listelenen oturum açma e-posta adresinin, oturum açmak için kullandığınız adresle eşleştiğinden emin olun.  Aksi takdirde, UPN 'niz uyuşmaz ve aboneliğinizi görüntüleyemezsiniz. 

> [!div class="mx-imgBorder"]
> ![Oturum açma e-posta adresi](_img//aliasing/sign-in-email.png "Profilinizde görünen e-posta adresinin, oturum açmak için kullandığınız bir adresle eşleştiğinden emin olun.")

#### <a name="how-to-fix-a-upn-mismatch"></a>UPN uyuşmazlığını çözme

1. Visual Studio yönetim yönetim portalına erişin[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. UPN uyumsuzluğu sorununa sahip abonenin konumunu bulun. ( [Filtre](search-license.md) özelliği abone bulmayı kolaylaştırabilir.)

3. Oturum açma posta adresini abonenin UPN 'si olarak değiştirme 

0. Değişiklikleri kaydedin 

0. Abone portalı oturumunu kapatıp UPN 'yi kullanarak yeniden erişmeyi bildirin 

### <a name="personal-account-aliasing-issue"></a>Kişisel hesap diğer ad sorunları

Visual Studio abonelikleri portalında oturum açmak için kullanılan e-posta adresi abonelikle ilişkili e-posta adresiyle eşleşmiyorsa, kişisel abonelik hesapları da sorunlarla karşılaşabilir. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Kişisel abonelik hesabınızın bir diğer ad sorunuyla etkilenip etkilenmediğinizi algılama

1. Oturum açmak için [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Sayfanın sağ üst kısmında listelenen oturum açma e-posta adresinin, oturum açmak için kullandığınız adresle eşleştiğini doğrulayın.  Oturum açılan e-posta adresi, Web sitesine erişmek için kullanılan e-posta adresiyle aynı değilse, hesabınız ve diğer ad arasında bir çakışma vardır.

#### <a name="how-to-fix-an-alias-issue"></a>Diğer ad sorununu çözme

Visual Studio platformu, abonelik ayrıntılarını göstermek için birincil diğer adı önceliklendirir. 

1. **Microsoft 'ta nasıl oturum açabileceğinizi yönetmek** için gidin. İstenirse Microsoft hesabı oturum açın. 

2. Hesap diğer adları ' nın altında, aboneliği atamak için kullanılan e-posta adresinin yanındaki **birincil yap** ' ı seçin. 

> [!div class="mx-imgBorder"]
> ![Birincil e-posta adresini ayarlama](_img//aliasing/account-aliases.png "Abonelikleriniz için birincil diğer ad seçmek üzere birincil yap bağlantısını kullanın.")

3. Visual Studio abonelikleri portalının oturumunu kapatın (https://my.visualstudio.com) 

4. Şimdi birincil diğer ad olarak yapılandırılması gereken aboneliği atamak için kullanılan hesabı kullanarak yeniden oturum açın. 

## <a name="preventing-aliasing-issues"></a>Diğer ad sorunlarını önler

Yönetici olarak, abonelerinizin üzerinde başarılı bir oturum açma deneyimine sahip olmasını sağlamaya yönelik iki seçenek vardır [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) .
- ilk seçenek (önerilir), ' de Visual Studio abonelikleri portalının oturum açma adı olarak dizin hesabından faydalanır https://my.visualstudio.com .  
- İkinci seçenek (daha az güvenli), abonelerin Dizin e-posta adresinden farklı bir e-posta adresi kullanarak oturum açmalarına izin vermektir.

Bu seçeneklerin her ikisi de aşağıdaki adımları tamamlayarak yönetim portalında yapılandırılır:  
1. Oturum aç [https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Tek bir kullanıcıyı değiştirirseniz, tabloda bu kullanıcı ' yı seçin ve düzenlemek için sağ tıklayın. Bu, oturum açma e-posta adresini değiştirebileceğiniz bir panel açar. Oturum açma e-posta adresi alanında gerekli güncelleştirmeleri yapın. Kaydet ' e tıkladığınızda değişiklikler geçerli olur.  

0. Bu değişiklikleri büyük miktarda kullanıcıya yapmanız gerekirse toplu düzenleme özelliğinden yararlanabilirsiniz. Daha fazla bilgi için [toplu düzenleme kullanarak birden çok aboneyi Düzenle](./edit-license.md#edit-multiple-subscribers-using-bulk-edit) makalesini okuyun.

> [!NOTE]
> Bireysel ve toplu değişiklikler için abonelere, oturum açma e-posta adresinin değiştiği ve güncelleştirilmiş e-posta adresini kullanarak oturum açması gereken yönergeler içeren bir e-posta gönderilir. Abone, daha önce diğer oturum açma adresi altında daha fazla avantaj sunduklarında, bunlara erişmek için diğer oturum açma adresini kullanmaya devam etmek için de önemlidir.  

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
- [En fazla kullanımı belirleme](maximum-usage.md)