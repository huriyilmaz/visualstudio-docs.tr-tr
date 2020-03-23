---
title: Visual Studio Aboneliklerine Oturum Açmak Takma Adları Kullanırken Başarısız Olabilir | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97bf7474-c6c2-49b3-b2c9-f1b2808eed1a
ms.date: 03/02/2020
ms.topic: conceptual
description: Takma adlar veya dost adlar kullanılırsa oturum açma başarısız olabilir
ms.openlocfilehash: 0f5ed4fe67dbd863a7ba4c22f10946cbeb1c36b0
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79509063"
---
# <a name="signing-into-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Visual Studio aboneliklerine oturum açma takma adlar kullanırken başarısız olabilir
Oturum açmak için kullanılan hesap türüne bağlı olarak, 'de oturum açmak [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)için kullanılabilir abonelikler doğru şekilde görüntülenmeyebilir. Olası nedenlerden biri, aboneliğin atandığı oturum açma kimliğinin yerine "takma adlar" veya "dost adlar" kullanılmasıdır. Buna "takma ad" denir.

## <a name="what-is-aliasing"></a>Takma ad nedir?
"Takma ad" terimi, Windows'da (veya Etkin Dizininizde) oturum açabilmek ve e-postaya erişmek için farklı kimliklere sahip olan kullanıcıları ifade eder.

Diğer adlarla, bir şirketin dizin oturum açma için bir Microsoft ÇevrimiçiJohnD@contoso.comHizmeti olduğunda karşılaşılan takma ad, ', ancak kullanıcılarJohn.Doe@contoso.come-posta hesaplarına takma adlar veya ' ' gibi uygun adlar kullanarak erişebilir. Kullanıcılarınızın aboneliklerine erişmek https://manage.visualstudio.com için yönetici portalında listelenen "Oturum Açma E-posta Adresi"ni kullandıklarından emin olun. 

## <a name="what-are-the-potential-issues"></a>Olası sorunlar nelerdir?

Abonenin hesap türüne bağlı olarak, iki sorundan biriyle karşılaşabilirler. 

### <a name="work-or-school-account-upn-mismatch-issue"></a>İş veya okul hesabı UPN uyumsuzluğu sorunu 
Bir şirketin UserPrincipalName (UPN) Birincil SMTP Adresi ile aynı olmadığı bir Active Directory kurulumu olduğunda bir UPN uyuşmazlığıyla karşılaşılabilir. 

#### <a name="how-to-detect-if-your-sign-in-address-is-impacted-by-a-upn-mismatch"></a>Oturum açma adresinizin UPN uyuşmazlığından etkilenip etkilenmedığını nasıl algılarım? 

1. Abonelik https://my.visualstudio.com/subscriptions atama e-postanızda belirtilen oturum açma adresini kullanarak oturum açın.

2. Sayfanın sağ üst kısmında listelenen oturum açma e-posta adresinin oturum açmada kullanılan adresle eşleştiğini doğrulayın.  Yoksa, UPN'iniz uyumsuzdur ve aboneliğinizi görüntüleyemeyeceksiniz. 

> [!div class="mx-imgBorder"]
> ![Oturum aç e-posta adresi](_img//aliasing/sign-in-email.png)

#### <a name="how-to-fix-a-upn-mismatch"></a>UPN uyuşmazlığı nasıl giderilir?

1. Görsel Stüdyo Yönetim Yönetimi portalına erişin[https://manage.visualstudio.com](https://manage.visualstudio.com) 

2. UPN uyuşmazlığı sorunu olan aboneyi bulun. (Filtre [Filter](search-license.md) özelliği abone bulmayı kolaylaştırabilir.)

3. Oturum açma posta adresini abonenin UPN'si ile değiştirme 

0. Değişiklikleri kaydetme 

0. UPN'yi kullanarak abone portalından çıkış yapmalarını ve yeniden erişmelerini aboneye bildirin 

### <a name="personal-account-aliasing-issue"></a>Kişisel hesap takma sorunu

Visual Studio Abonelikleri portalında oturum açmak için kullanılan e-posta adresi abonelikle ilişkili e-posta adresiyle eşleşmiyorsa, kişisel abonelik hesapları da sorunlarla karşılaşabilir. 

#### <a name="how-to-detect-if-your-personal-subscription-account-is-impacted-by-an-aliasing-issue"></a>Kişisel abonelik hesabınızın diğer ad sorunundan etkilenip etkilenmedığını nasıl algılarınız?

1. Oturum aç[https://my.visualstudio.com/subscriptions](https://my.visualstudio.com/subscriptions)

0. Sayfanın sağ üst kısmında listelenen oturum açma e-posta adresinin oturum açmada kullanılan adresle eşleştiğini doğrulayın.  Oturum açmış e-posta adresi, web sitesine erişmek için kullanılan e-posta adresiyle aynı değilse, hesabınızla takma ad arasında bir çakışma vardır.

#### <a name="how-to-fix-an-alias-issue"></a>Diğer ad sorunu nasıl giderilir?

Visual Studio platformu, abonelik ayrıntılarını göstermek için birincil diğer adı önceliklendir. 

1. **Microsoft'ta nasıl oturum açabileceğinizi yönet'e**gidin. İstenirse Microsoft hesabınızda oturum açın. 

2. Hesap takma adları altında, aboneliği atamak için kullanılan e-posta adresinin yanında birincil adresi **yap'ı** seçin. 

> [!div class="mx-imgBorder"]
> ![Birincil e-posta adresini ayarlama](_img//aliasing/account-aliases.png)

3. Visual Studio Abonelikleri portalından çıkış (https://my.visualstudio.com) 

4. Şimdi birincil diğer ad olarak yapılandırılması gereken aboneliği atamak için kullanılan hesabı kullanarak yeniden oturum açın. 

## <a name="preventing-aliasing-issues"></a>Diğer ad sorunlarını önleme

Bir yönetici olarak, abonelerinizin [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)başarılı bir oturum açma deneyimine sahip olmasını sağlamak için iki seçenek vardır.
- İlk seçenek (önerilir), Visual Studio Abonelikleri portalı için oturum açma olarak dizin hesabından https://my.visualstudio.comyararlanmaktır.  
- İkinci seçenek (daha az güvenli), abonelerinizin dizin e-posta adresinden farklı bir e-posta adresi kullanarak oturum açmalarına izin vermektir.

Bu seçeneklerin her ikisi de aşağıdaki adımları tamamlayarak yönetici portalında yapılandırılır:  
1. Oturum aç[https://manage.visualstudio.com](https://manage.visualstudio.com) 

0. Tek bir kullanıcıyı değiştiriyorsanız, tablodaki kullanıcıyı seçin ve değiştirmek için sağ tıklatın. Bu, oturum açma e-posta adresini değiştirebileceğiniz bir panel açar. Oturum açma e-posta adresi alanında gerekli güncellemeleri yapın. Kaydet'i tıklatın ve değişiklikler etkili olur.  

0. Bu değişiklikleri çok sayıda kullanıcıda yapmanız gerekiyorsa, toplu edit özelliğini kullanabilirsiniz. Daha fazla bilgi için [toplu edit makalesini kullanarak birden çok aboneyi edit'i](https://docs.microsoft.com/visualstudio/subscriptions/edit-license#edit-multiple-subscribers-using-bulk-edit) okuyun.

> [!NOTE]
> Hem bireysel hem de toplu değişiklikler için, aboneleroturum açma e-posta adreslerinin değiştiği yönergeleri içeren bir e-posta alır ve güncelleştirilmiş e-posta adresini kullanarak oturum açmaları gerekir. Abonenin diğer oturum açma adresi altında daha önce etkinleştirilmiş avantajlar etkinleştirdiyse, bunlara erişmek için diğer oturum açma adresini kullanmaya devam etmesi gerektiğini de unutmayın.  

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
- [Maksimum kullanımı belirleme](maximum-usage.md)


