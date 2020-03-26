---
title: Visual Studio Aboneliklerine İmza Lama Sorunları | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 03/11/2020
ms.topic: conceptual
description: Visual Studio aboneliklerine oturum açarken ortaya çıkabilecek sorunlar hakkında bilgi edinin
ms.openlocfilehash: de27f64f1d5c83ed01a1e561f4921dbed53c479c
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233239"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Visual Studio aboneliklerinde oturum açma sorunları
Visual Studio aboneliğinizi kullanmak için öncelikle oturum açmanız gerekir.  Aboneliğinize bağlı olarak, bu hesabı bir Microsoft hesabı (MSA) veya Azure Etkin Dizin (AAD) kimliğiyle ayarlamış olabilirsiniz.  Bu makalede, aboneliğinizde oturum açmak sırasında karşılaşabileceğiniz bazı sorunlar tartışılmaktadır.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Microsoft Hesapları (MSA) iş/okul e-posta adresleri kullanılarak oluşturulamaz
E-posta etki alanı Azure AD'de yapılandırıldığında, iş/okul e-posta adresini kullanarak yeni bir kişisel Microsoft Hesabı (MSA) oluşturma özelliğine artık izin verilmez. Bu ne anlama geliyor? Kuruluşunuz Azure AD'ye dayanan Office 365 veya Microsoft'un diğer iş hizmetlerini kullanıyorsa ve Azure AD kiracınıza bir etki alanı adı eklediyseniz, kullanıcılar artık etki alanınızda bir e-posta adresi kullanarak yeni bir kişisel Microsoft hesabı oluşturamaz.

### <a name="why-was-this-change-made"></a>Bu değişiklik neden yapıldı?
Kullanıcı adı olarak iş adresi ne olan kişisel bir Microsoft Hesabı'na sahip olmak, son kullanıcılar ve BT departmanları için sorunlarla doludur. Örnek:
- Kullanıcılar kişisel Microsoft hesaplarının iş uyumlu olduğunu ve iş belgesini OneDrive'larına kaydettiklerinde uyumlu olduklarını düşünebilirler
- Kuruluştan ayrılan kullanıcılar genellikle iş e-posta adreslerine erişimlerini kaybederler. Bunu yaptıklarında, parolalarını unuturlarsa kişisel Microsoft hesabına geri dönemeyebilirler. Diğer taraftan, BT departmanları parolalarını sıfırlayabilir ve eski çalışanların kişisel hesabına girebiliyordu.
- BT departmanları yanlış bir hesap sahipliği ve güvenlik duygusuna sahiptir. Ancak kullanıcıların iş e-posta adreslerine bir kod göndere bakmaları gerekir ve gelecekte herhangi bir zamanda hesaplarını yeniden adlandırabilirler.

Durum özellikle aynı e-posta adresine sahip iki hesabı olan kullanıcılar için kafa karıştırıcıdır (biri Azure AD & bir Microsoft hesabı).

### <a name="what-does-this-experience-look-like"></a>Bu deneyim neye benziyor?
Bir iş veya okul e-posta adresine sahip bir Microsoft tüketici uygulamasına kaydolmaya çalışırsanız, aşağıdaki iletiyi görürsünüz.

   > [!div class="mx-imgBorder"]
   > ![İş e-postasıyla hesap oluşturamıyorum](_img/sign-in-issues/cannot-use-work-email.png)

Ancak, kişisel ve iş/okul hesaplarını destekleyen bir Microsoft uygulamasına kaydolmaya çalışırsanız, şu iletiyi görmeniz gerekir:

   > [!div class="mx-imgBorder"]
   > ![Desteklenen iş/okul hesapları](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Varolan hesaplar etkileniyor mu?
Burada açıklanan kayıt bloğu yalnızca yeni hesapların oluşturulmasını engeller. İş/okul e-posta adresi olan bir Microsoft Hesabı olan kullanıcılar üzerinde hiçbir etkisi yoktur. Zaten bu durumdaysanız, kişisel bir Microsoft hesabının adını yeniden adlandırmayı kolaylaştırdık. Bu [destek makalesi](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) basit adım adım kılavuzluk sağlar. Kişisel Microsoft hesabınızı yeniden adlandırmak, kullanıcı adını değiştirmek anlamına gelir ve iş e-postanızı veya Office 365 gibi iş hizmetlerinde nasıl oturum açabileceğinizi etkilemez. Ayrıca kişisel eşyalarınızı etkilemez, sadece oturum açma şeklinizi değiştirir. Başka (kişisel) bir e-posta adresi @outlook.com kullanabilir, Microsoft'tan yeni bir e-posta adresi alabilir veya telefon numaranızı yeni bir kullanıcı adı olarak kullanabilirsiniz.

> [!NOTE]
> BT departmanınız, örneğin Premier Destek gibi Microsoft iş hizmetlerine erişmek için iş/okul e-postanızla birlikte kişisel bir Microsoft hesabı oluşturmanızı istediyse, hesabınızı yeniden adlandırmadan önce yönetici ekibinizle konuşun.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Oturum açma adresinin silmesi, aboneye erişimi engelleyebilir
Aboneliğinizle ilişkili bir veya daha fazla kimliği (MSA veya AAD) silerseniz, kullanıcı adınız ve oturum açma kimliğiniz de dahil olmak üzere abone bilgileriniz anonim hale getirilebilir ve bu da aboneliğinize erişimin kaybolmasına neden olabilir.

Abonelik erişiminizi etkilememek için bu tekniklerden birini kullanın.
- MSA veya AAD gibi tek bir kimlik yönetim sistemi konuşlandırın, ancak her ikisini birden devreye sayılmayın.
- AAD ve MSA kimliklerini kiracı aracılığıyla ilişkilendirin.

## <a name="signing-in-may-fail-when-using-aliases"></a>Diğer adlar kullanırken oturum açma başarısız olabilir
Oturum açmak için kullanılan hesap türüne bağlı olarak, 'de oturum açmak [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs)için kullanılabilir abonelikler doğru şekilde görüntülenmeyebilir. Olası nedenlerden biri, aboneliğin atandığı oturum açma kimliğinin yerine "takma adlar" veya "dost adlar" kullanılmasıdır. Buna "takma ad" denir.

### <a name="what-is-aliasing"></a>Takma ad nedir?
"Takma ad" terimi, Windows'da (veya Etkin Dizininizde) oturum açabilmek ve e-postaya erişmek için farklı kimliklere sahip olan kullanıcıları ifade eder.

Diğer adlarla, bir şirket kendi dizin oturum açma için bir Microsoft JohnD@contoso.comÇevrimiçi Hizmeti olduğunda karşılaşılabılabilir, ancak kullanıcılar e-posta hesaplarına takma adlar veya '. John.Doe@contoso.com Toplu Lisans Lama Hizmet Merkezi (VLSC) aracılığıyla aboneliklerini yöneten birçok müşteri için, sağlanan e-postaJohn.Doe@contoso.comadresi ()JohnD@contoso.com"İş veya Okul Hesabı" seçeneği aracılığıyla başarılı kimlik doğrulaması için gereken dizin adresiyle eşleşmediği için başarısız bir oturum açma deneyimine neden olabilir.

### <a name="what-options-do-i-have"></a>Ne gibi seçeneklerim var?
Abone açısından bakıldığında, şirketinizin kimlik yapılandırmasını anlamak için öncelikle yöneticinizle çalışmak önemlidir. Gerekirse, yöneticinizin hesap ayarlarınızı yönetim portalından güncellemesi gerekebilir veya kurumsal e-posta adresinizi kullanarak bir Microsoft Hesabı (MSA) oluşturmanız gerekebilir. Bir MSA oluşturmak için adımları atmadan önce, bu eylemi gerçekle ilgili herhangi bir ilke veya sorun la ilgili olarak yöneticinizle konuşun. 

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- [MsA ve AAD hesaplarını](/azure/active-directory/b2b/add-users-administrator) AAD içinde nasıl bağlayacaklarınız öğrenin.
- [Anonymization](anonymization.md)hakkında daha fazla bilgi edinin.
