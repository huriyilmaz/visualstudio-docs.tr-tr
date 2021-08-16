---
title: Diğer Adlar Visual Studio Aboneliklerde Oturum Açma Başarısız | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/19/2021
ms.topic: conceptual
description: Diğer adlar veya kolay adlar kullanılırsa oturum açma başarısız olabilir
ms.openlocfilehash: 84ee95c69a4dc271fccb3a34f758fde350a12bfc3b3e8c373cbb135914bbcc2f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381176"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Diğer adlar Visual Studio aboneliklerde oturum açma başarısız olabilir
Oturum açma için kullanılan hesap türüne bağlı olarak, kullanılabilir abonelikler'de oturum aken doğru [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) görüntülenmeyebilirsiniz. Olası nedenlerden biri, aboneliğin atandığı oturum açma kimliği yerine "diğer adların" veya "kolay adların" kullanımıdır. Buna "diğer ad" denir.

## <a name="what-is-aliasing"></a>Diğer ad nedir?
"Diğer ad" terimi, Windows 'de (veya Active Directory'niz) oturum açma ve e-postaya erişmek için farklı kimliklere sahip olan kullanıcıları ifade eder.

Diğer adlar, bir şirketin '' gibi dizin oturum açma bilgileri için bir Microsoft Online Hizmeti olduğunda ancak kullanıcılar e-posta hesaplarına diğer adlar veya kolay adlar (örneğin ' ' ) kullanarak JohnD@contoso.com erişenin. John.Doe@contoso.com Kullanıcılarınızı aboneliklerine erişmek için yönetici portalında listelenen "Oturum Açma E-posta Adresi"ni https://manage.visualstudio.com kullanmaya emin olun. 

## <a name="what-are-the-potential-issues"></a>Olası sorunlar nedir?

Abonenin hesap türüne bağlı olarak iki sorundan biri ile karşılaşabilirsiniz. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>İş veya okul hesabı UPN eşleşmesi sorunu 
Bir şirketin UserPrincipalName (UPN) Birincil SMTP Adresi ile aynı olduğu bir Active Directory ayarlanmış olduğunda BIR UPN eşleşmesi ile karşılaşabilirsiniz. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Oturum açma adresinizin UPN eşleşmesi eşleşmesi tarafından etkilenenin nasıl algılayabilirsiniz? 

1. Abonelik https://my.visualstudio.com/subscriptions ataması e-postanıza belirtilen oturum açma adresini kullanarak oturum açma.

2. Sayfanın sağ üst köşesinde adınıza tıklayın.  Bu, profilinizi açar.  Profilinizde listelenen oturum açma e-posta adresinin, oturum a0 için kullanılan adresle eşle eşle olduğunu doğrulayın.  Eşleşmezse, UPN'niz eşleşmez ve aboneliğinizi görüntüleyesiniz. 

> [!div class="mx-imgBorder"]
> ![Oturum açma e-posta adresi](_img//aliasing/sign-in-email.png "Profilinizde görüntülenen e-posta adresinin oturum açma için kullanmak istediğiniz e-posta adresiyle eşlendiğinden emin olun.")

#### <a name="how-to-fix-a-upn-mismatch"></a>UPN eşleşmezliklerini düzeltme

1. Visual Studio Yönetim Yönetimi portalına erişme[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. UPN eşleşmesi sorunu olan aboneyi bulun. (Filtre [](search-license.md) özelliği abone bulmayı kolaylaştırabilirsiniz.)

3. Oturum açma posta adresini abonenin UPN'sini olarak değiştirme 

0. Değişiklikleri kaydedin 

0. Aboneyi abone portalında oturum açmasını ve UPN kullanarak yeniden erişmesi konusunda bilgilendirin 

### <a name="personal-account-aliasing-issue"></a>Kişisel hesap diğer ad sorunu

Kişisel abonelik hesapları, Visual Studio Abonelikler portalında oturum atılarken kullanılan e-posta adresinin abonelikle ilişkili e-posta adresiyle eşleşmezse de sorun yaşanabilirsiniz. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Kişisel abonelik hesabınız bir diğer ad sorunundan etkilenin mi olduğunu algılama

1. Oturum açma [https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Sayfanın sağ üst kısmında listelenen oturum açma e-posta adresinin oturum a0 için kullanılan adresle eşle olduğunu doğrulayın.  Oturum açın e-posta adresi web sitesine erişmek için kullanılan e-posta adresiyle aynı değilse hesabınızla diğer ad arasında bir çakışma vardır.

#### <a name="how-to-fix-an-alias-issue"></a>Diğer ad sorunu nasıl düzeltebilirim?

Bu Visual Studio platform, abonelik ayrıntılarını göstermek için birincil diğer adın önceliğe sahip olduğunu gösterir. 

1. **Microsoft'ta oturum açmalarınızı yönetme'ye gidin.** İstendiğinde Microsoft hesabı oturum açın. 

2. Hesap diğer adları'nın altında aboneliği **atamak için** kullanılan e-posta adresinin yanındaki Birincil olun'ı seçin. 

> [!div class="mx-imgBorder"]
> ![Birincil e-posta adresini ayarlama](_img//aliasing/account-aliases.png "Abonelikleriniz için birincil diğer adı seçmek üzere Birincil ad yapma bağlantısını kullanın.")

3. Visual Studio Abonelikler portalında oturum açın (https://my.visualstudio.com) 

4. Şimdi birincil diğer ad olarak yapılandırılması gereken aboneliği atamak için kullanılan hesabı kullanarak yeniden oturum açın. 

## <a name="preventing-aliasing-issues"></a>Diğer ad sorunlarını önleme

Yönetici olarak, abonelerinizi üzerinde başarılı bir oturum açma deneyimine sahip olduğundan emin olmak için iki seçenek [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) vardır.
- İlk seçenek (önerilen), sayfasındaki Abonelikler portalı için oturum Visual Studio hesabı olarak https://my.visualstudio.com kullanılmasıdır.  
- İkinci seçenek (daha az güvenli), abonelerin dizin e-posta adreslerinden farklı bir e-posta adresi kullanarak oturum açmasına izin vermektir.

Bu seçeneklerin ikisi de aşağıdaki adımlar tamamlayarak yönetici portalında yapılandırılır:  
1. Oturum açma [https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Tek bir kullanıcı değiştirerek tablodaki ilgili kullanıcıyı seçin ve düzenlemek için sağ tıklayın. Bu, oturum açma e-posta adresini değiştirerek bir panel açar. Oturum açma e-posta adresi alanında gerekli güncelleştirmeleri yapma. Kaydet'e tıklar ve değişiklikler etkili olur.  

0. Büyük miktarda kullanıcı için bu değişiklikleri yapmak zorundaysanız toplu düzenleme özelliğini kullanın. Daha fazla [bilgi için Toplu düzenleme kullanarak birden çok aboneyi](./edit-license.md#edit-multiple-subscribers-using-bulk-edit) düzenleme makalesine bakın.

> [!NOTE]
> Hem bireysel hem de toplu değişiklikler için aboneler, oturum açma e-posta adreslerinin değiştiğini ve güncelleştirilmiş e-posta adresini kullanarak oturum açmaları gereken yönergeleri içeren bir e-posta alır. Abonenin daha önce diğer oturum açma adresi altında avantajlar etkinleştirildiğinde, aboneye erişmek için diğer oturum açma adresini kullanmaya devam etmek zorunda olduğunu da unutmayın.  

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio Aboneliklerinin yönetimiyle ilgili yardım için, Visual Studio [abonelik desteği ile iletişim kurun.](https://aka.ms/vsadminhelp)

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
- [En fazla kullanımı belirleme](maximum-usage.md)