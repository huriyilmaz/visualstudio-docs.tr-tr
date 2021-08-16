---
title: Visual Studio aboneliğinde oturum açma | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 02/19/2021
ms.topic: conceptual
description: Visual Studio aboneliklerde oturum aken ortaya çıkabilecek sorunlar hakkında bilgi edinin
ms.openlocfilehash: 2ed8bcbb06231953da9ab42a1f310fd680c7a629eca696b56da1a81bb9a3b69e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121364435"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Visual Studio oturum açma sorunları
Visual Studio aboneliğinizi kullanmak için önce oturum açmanız gerekir.  Aboneliğinize bağlı olarak, bunu bir Microsoft hesabı (MSA) veya Azure Active Directory (AAD) kimliğiyle ayarlayabilirsiniz.  Bu makalede, aboneliğiniz oturum arken karşılaşabilirsiniz bazı sorunlar ele alınarak hazırlanmıştır.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Microsoft Hesapları (MSA) iş/okul e-posta adresleri kullanılarak oluşturulamaz
E-posta etki alanı Azure AD'de yapılandırıldığında iş/okul e-posta adresi kullanarak yeni bir kişisel Microsoft Hesabı (MSA) oluşturma özelliğine artık izin verilmez. Bu ne anlama geliyor? Microsoft'un Azure AD'ye bağlı Microsoft 365 veya diğer iş hizmetlerini kullanıyorsa ve Azure AD kiracınıza bir etki alanı adı eklediyebilirsiniz, kullanıcılar artık etki alanınıza bir e-posta adresi Microsoft hesabı yeni bir kişisel hizmet oluşturamaz.

### <a name="why-was-this-change-made"></a>Bu değişiklik neden yapıldı?
Kullanıcı adı olarak iş adresine sahip kişisel bir Microsoft Hesabına sahip olmak, hem son kullanıcılar hem de IT departmanları için soruna neden olur. Örnek:
- Kullanıcılar, kişisel Microsoft hesabı iş uyumlu olduğunu ve iş belgelerini kendi iş alanlarına kaydeden uyumlu olduklarını OneDrive
- Bir kuruluştan ayrılmakta olan kullanıcılar genellikle iş e-posta adreslerine erişimi kaybeder. Bunu yaptıklarında, parolalarını unutmaları Microsoft hesabı kişisel kimlik bilgilerine geri dönemleri mümkün olmayacaktır. Diğer taraftan, KENDI IT departmanı parolalarını sıfırlar ve eski çalışanların kişisel hesabına girebilir.
- IT departmanları, hesap sahipliği ve güvenliğiyle ilgili yanlış bir algıya sahip olur. Ancak kullanıcıların iş e-posta adreslerine yalnızca bir kez kod gidiş dönüşleri gerekir ve gelecekte herhangi bir zamanda hesaplarını yeniden adlandırabilir.

Bu durum, aynı e-posta adresine sahip iki hesabı olan (biri Azure AD'de, biri azure & biri Microsoft hesabı).

### <a name="what-does-this-experience-look-like"></a>Bu deneyim nasıl görünüyor?
İş veya okul e-posta adresiyle bir Microsoft tüketici uygulamasına kaydolmaya çalışırsanız aşağıdaki iletiyi görebilirsiniz.

   > [!div class="mx-imgBorder"]
   > ![İş e-postası ile hesap oluşturulamadı](_img/sign-in-issues/cannot-use-work-email.png "Hesap oluşturmak için bir kullanıcı adı ve parola girin.")

Ancak, kişisel ve iş/okul hesaplarını destekleyen bir Microsoft uygulamasına kaydolmaya çalışırsanız şu iletiyi görüyor olun:

   > [!div class="mx-imgBorder"]
   > ![Desteklenen iş/okul hesapları](_img/sign-in-issues/existing-account.png "Buraya bir iş veya okul e-posta adresiyle kaydolasınız...")

### <a name="are-existing-accounts-affected"></a>Mevcut hesaplar etkilendi mi?
Burada açıklanan kaydolma bloğu yalnızca yeni hesapların oluşturulmasını önler. İş/okul e-posta adresine sahip bir Microsoft Hesabı olan kullanıcıları etkilemez. Bu durumda zatenysanız, kişisel bir dosyanın adını daha kolay Microsoft hesabı. Bu [destek makalesi,](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) basit adım adım kılavuz sağlar. Kişisel bilgilerinizi yeniden Microsoft hesabı, kullanıcı adını değiştirmek anlamına gelir ve iş e-postanızı veya kullanıcı adı gibi iş hizmetlerde oturum açma Microsoft 365. Ayrıca kişisel bilgilerinizi de etkilemez; yalnızca oturum açma yollarınızı değiştirir. Başka bir (kişisel) e-posta adresi kullanabilir, Microsoft'tan yeni bir e-posta adresi edinebilirsiniz veya telefon @outlook.com numaranızı yeni bir kullanıcı adı olarak kullanabilirsiniz.

> [!NOTE]
> IT departmanınız iş/okul e-postanız Microsoft hesabı kişisel bir hesap oluşturmanızı istediyseniz (örneğin, Premier Destek gibi Microsoft iş hizmetlerine erişmeniz) ve ardından, hesabınız yeniden başlamadan önce yönetici takımıyla iletişim açın.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Oturum açma adresinin silinmesi aboneliğe erişimi önleyebilirsiniz
Aboneliğiniz ile ilişkili bir veya daha fazla kimliği (MSA veya AAD) silerseniz, kullanıcı adınız ve oturum açma kimliğiniz de dahil olmak üzere abone bilgileri anonim olarak işlenecek ve bu da aboneliğinize erişimin kaybedilebilir.

Abonelik erişiminizin etkilenmelerini önlemek için bu tekniklerden birini kullanın.
- Tek bir kimlik yönetim sistemi (MSA veya AAD) dağıtın ancak her ikisini birden dağıtın.
- AAD ve MSA kimliklerini kiracı aracılığıyla ilişkilendirme.

## <a name="signing-in-may-fail-when-using-aliases"></a>Diğer adlar kullanırken oturum açma başarısız olabilir
Oturum açma için kullanılan hesap türüne bağlı olarak, kullanılabilir abonelikler'de oturum aken doğru [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) görüntülenmeyebilirsiniz. Olası nedenlerden biri, aboneliğin atandığı oturum açma kimliği yerine "diğer adların" veya "kolay adların" kullanımıdır. Buna "diğer ad" denir.

### <a name="what-is-aliasing"></a>Diğer ad nedir?
"Diğer ad" terimi, Windows 'de (veya Active Directory'niz) oturum açma ve e-postaya erişmek için farklı kimliklere sahip olan kullanıcıları ifade eder.

Diğer adlar, bir şirketin gibi dizin oturum açma bilgileri için bir Microsoft Online Hizmeti olduğunda ancak kullanıcılar e-posta hesaplarına gibi kolay adlar veya diğer adlar kullanarak erişerek JohnD@contoso.com John.Doe@contoso.com karşılaşabilirsiniz. Aboneliklerini Toplu Lisanslama Hizmet Merkezi (VLSC) aracılığıyla yöneten birçok müşteri için, sağlanan e-posta adresi ( ) "İş veya Okul Hesabı" seçeneği aracılığıyla başarılı kimlik doğrulaması için gereken dizin adresi ( ) ile eşleşmeyerek başarısız bir oturum açma deneyimiyle John.Doe@contoso.com JohnD@contoso.com sonuçlanabilirsiniz.

### <a name="what-options-do-i-have"></a>Hangi seçeneklerim var?
Abone açısından bakıldığında, önce yöneticinizle birlikte çalışarak şirket kimlik yapılandırmasını anlamanız önemlidir. Gerekirse yöneticinizin hesap ayarlarınızı yönetici portallarından güncelleştirmesi veya şirket e-posta adresinizi kullanarak bir Microsoft Hesabı (MSA) oluşturmanız gerekebilir. MSA oluşturma adımlarını atmadan önce, bu eylemi uygulamayla ilgili ilkeler veya sorunlar hakkında yöneticinizle konuşun.

## <a name="resources"></a>Kaynaklar
- Abonelikler için satış, abonelikler, hesaplar ve faturalama Visual Studio yardım için bkz. Visual Studio [Abonelikler desteği.](https://aka.ms/vssubscriberhelp) 

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- AAD içinde [MSA ve AAD hesaplarını bağlamayı](/azure/active-directory/b2b/add-users-administrator) öğrenin.
- Anonimleştirme hakkında daha [fazla bilgi.](anonymization.md)