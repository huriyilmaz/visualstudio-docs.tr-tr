---
title: Diğer adlar kullanılırken Visual Studio aboneliklerinde oturum açma başarısız olabilir | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/14/2020
ms.topic: conceptual
description: Diğer adlar veya kolay adlar kullanılıyorsa oturum açma başarısız olabilir
ms.openlocfilehash: dff48852e566522ad01ee07bd46cda72b8e1e249
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77276625"
---
# <a name="signing-in-to-visual-studio-subscriptions-may-fail-when-using-aliases"></a>Diğer adlar kullanılırken Visual Studio aboneliklerinde oturum açma başarısız olabilir
Oturum açmak için kullanılan hesap türüne bağlı olarak, [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)için oturum açarken kullanılabilir abonelikler doğru görüntülenmeyebilir. Olası bir neden, aboneliğin atandığı oturum açma kimliği yerine "diğer adlar" veya "kolay adlar" in kullanılması olabilir. Bu "diğer ad" olarak adlandırılır.

## <a name="what-is-aliasing"></a>Diğer ad nedir?
"Diğer ad" terimi, Windows 'da (veya Active Directory) oturum açmak ve e-postaya erişmek için farklı kimliklere sahip kullanıcılar anlamına gelir.

Şirket, 'olivia@contoso.com' gibi dizin oturum açma işlemi için bir Microsoft Online hizmetine sahip olduğunda, diğer adlara de rastlanır, ancak kullanıcılar e-posta hesaplarına 'OliviaG@contoso.com' gibi diğer adlar veya kolay adlar kullanarak erişebilirler. Kullanıcılarınızın aboneliklerine erişmek için https://manage.visualstudio.com adresindeki Visual Studio abonelikleri yönetim portalı 'nda listelenen "oturum açma e-posta adresini" kullanarak oturum açmasını sağlayın

## <a name="as-an-administrator-what-options-do-i-have"></a>Yönetici olarak hangi seçeneklere sahip mıyım?

Abonenin hesap türüne bağlı olarak, aşağıdaki ilgili çözümü bulun:

### <a name="work-or-school-account-upn-mismatch-issue"></a>İş veya okul hesabı UPN uyumsuzluğu sorunu

Bir compnay 'nin, UPN 'nin birincil SMTP adresiyle aynı olmadığı bir etkin diretory ayarlandığında, bir Kullanıcı asıl adı (UPN) uyumsuzluğu ile uyuşmazlık olabilir. 

#### <a name="how-to-detect-if-a-users-sign-in-address-has-a-upn-mismatch"></a>Kullanıcının oturum açma adresinin UPN uyumsuzluğu olup olmadığını algılama

Kullanıcının aşağıdaki adımları tamamlamasını sağlayabilirsiniz:

1. Abonelik atama e-postasında bahsedilen oturum açma adresini kullanarak https://my.visualstudio.com oturum açın.  

    > [!NOTE]
    > Aboneliklerinde abonelik atama e-postası yoksa, yönetim portalı içinden yeniden gönderebilirsiniz.  

2. **Abonelikler** sekmesine tıklayın.
3. E-posta adresinin görüntülenen sağ üst köşede görüntülendiğini doğrulayın ve "oturum açtınız..." , abonelik atama e-postasındaki oturum açma e-posta adresiyle aynıdır.  Değilse, abonelik avantajlarına erişemez. 

   > [!div class="mx-imgBorder"]
   > ![abonelikler sayfası](_img/aliasing/aliasing-subscriptions-page.png)

#### <a name="how-to-correct-the-upn-mismatch"></a>UPN uyuşmazlığını Düzeltme

1. Visual Studio yönetim yönetim portalına https://manage.visualstudio.com adresinden erişin 

2. UPN uyuşmazlığını sorunu olan kullanıcıyı bulun.  Çok sayıda aboneliğiniz varsa [filtre](search-license.md) özelliği bunu daha kolay hale getirir. 

3. Oturum açma e-posta adresini kullanıcının UPN 'si ile değiştirin.

4. Değişiklikleri Kaydet 

5. Kullanıcıdan abone portalının oturumunu açmasını isteyin ve UPN 'yi kullanarak tekrar oturum açın.   

### <a name="personal-account-aliasing-issue"></a>Kişisel hesap diğer ad sorunları

Diğer ad sorunları da kişisel hesapları etkileyebilir. 

#### <a name="how-to-detect-if-a-personal-account-has-an-aliasing-issue"></a>Kişisel hesabın bir diğer ad sorunu olup olmadığını algılama

1. https://my.visualstudio.comoturum açın.

2. **Abonelikler** sekmesine tıklayın ve oturum açtığınız adresi denetleyin. 

3. Oturum açılan e-posta adresi, Web sitesine erişmek için kullanılan e-posta adresiyle aynı değilse, hesabınız ve diğer ad arasında bir çakışma vardır. 

#### <a name="how-to-fix-a-personal-account-aliasing-issue"></a>Kişisel hesap diğer ad sorununu çözme

Visual Studio abonelikleri platformu, birincil diğer adı abonelik ayrıntılarını gösterecek şekilde önceliklendirir.  Bu sorunu çözmek için, birincil diğer adınızla oturum açmak üzere farklı bir e-posta diğer adı oluşturmanız gerekir. 

1. [Microsoft 'ta nasıl oturum açabileceğinizi yönetmek](https://go.microsoft.com/fwlink/p/?linkid=842796)için gidin.
2. İstenirse Microsoft hesabı oturum açın. 
3. Hesap diğer adları ' nın altında, aboneliği atamak için kullanılan e-posta adresinin yanındaki **birincil yap** ' ı seçin. 
4. Hesap diğer adları ' nın altında, aboneliği atamak için kullanılan e-posta adresinin yanındaki birincil yap ' ı seçin. 
5. Visual Studio abone portalı oturumunu kapat (https://my.visualstudio.com) 
6. Yeni birincil diğer adı kullanarak portala tekrar erişin. 

### <a name="ensure-a-successful-experience-for-your-users"></a>Kullanıcılarınız için başarılı bir deneyim sağlayın

Yönetici olarak, abonelerinizin https://my.visualstudio.comiçin başarılı bir oturum açma deneyimine sahip olmasını sağlamaya yönelik iki seçenek vardır. 

- İlk seçenek (önerilir) https://manage.visualstudio.comoturum açma adresi olarak dizin hesabından faydalanır.
- İkinci seçenek (daha az güvenli), daha az güvenli olan ikinci seçenek, abonelerin Dizin e-posta adresinden farklı bir e-posta adresi kullanarak oturum açmalarına izin vermektir.

Her iki seçenek de yönetim portalında aşağıdaki adımları tamamlayarak yapılandırılır:

1. https://manage.visualstudio.com oturum aç 

2. Tek bir kullanıcıyı değiştirirseniz, tabloda bu kullanıcı ' yı seçin ve düzenlemek için sağ tıklayın. Bu, oturum açma e-posta adresini değiştirebileceğiniz bir panel açar.  

3. Oturum açma e-posta adresi alanında gerekli güncelleştirmeleri yapın. 

4. Kaydet ' e tıkladığınızda değişiklikler geçerli olur.  
Bu değişiklikleri büyük miktarda kullanıcıya yapmanız gerekirse toplu düzenleme özelliğinden yararlanabilirsiniz. Bu süreç hakkında daha fazla bilgi için [abonelikleri Düzenle]] (Edit-license.md) makalesinin **toplu düzenleme kullanarak birden çok aboneyi Düzenle** bölümünü okuyun.  

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Ayrı abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)
