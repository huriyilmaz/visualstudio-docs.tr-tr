---
title: Visual Studio aboneliklerinde oturum açma sorunları | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 176c7f11-b19d-49e9-a6dd-b2e5da5e8480
ms.date: 03/11/2020
ms.topic: conceptual
description: Visual Studio aboneliklerinde oturum açarken meydana çıkabilecek sorunlar hakkında bilgi edinin
ms.openlocfilehash: 5d8a71115cd1a1aa7d850945806c22a64e7721cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88801886"
---
# <a name="issues-signing-in-to-visual-studio-subscriptions"></a>Visual Studio aboneliklerinde oturum açma sorunları
Visual Studio aboneliğinizi kullanmak için önce oturum açmalısınız.  Aboneliğinize bağlı olarak, bunu bir Microsoft hesabı (MSA) veya bir Azure Active Directory (AAD) kimliğiyle ayarlamış olabilirsiniz.  Bu makalede, aboneliğinizde oturum açarken karşılaşabileceğiniz bazı sorunlar ele alınmaktadır.

## <a name="microsoft-accounts-msa-cannot-be-created-using-workschool-email-addresses"></a>Microsoft hesapları (MSA) iş/okul e-posta adresleri kullanılarak oluşturulamıyor
E-posta etki alanı Azure AD 'de yapılandırıldığında, iş/okul e-posta adresi kullanarak yeni bir kişisel Microsoft hesabı (MSA) oluşturma olanağına artık izin verilmez. Bu ne anlama geliyor? Kuruluşunuz Microsoft 'un Azure AD 'ye bağlı Microsoft 365 veya diğer iş hizmetlerini kullanıyorsa ve Azure AD kiracınıza bir etki alanı adı eklediyseniz, kullanıcılar artık etki alanındaki bir e-posta adresini kullanarak yeni bir kişisel Microsoft hesabı oluşturamayacak.

### <a name="why-was-this-change-made"></a>Bu değişiklik neden yapıldı?
Kullanıcı adı olarak iş adresi olan bir kişisel Microsoft hesabına sahip olmak, son kullanıcılar ve BT departmanlarına benzer sorunlarla karşılaşır. Örneğin:
- Kullanıcılar kendi kişisel Microsoft hesabı, iş belgelerini OneDrive 'a kaydederken uyumlu olduğunu düşünebilir.
- Bir kuruluştan ayrılan kullanıcılar genellikle iş e-posta adreslerine erişimi kaybeder. Kullanıcılar, parolalarını unutduklarında kendi kişisel Microsoft hesabı geri yükleyemeyebilir. Çevirme tarafı, BT departmanının parolalarını sıfırlamasına ve eski çalışanların kişisel hesabına alabilirler.
- BT departmanlarının hesap sahipliğine ve güvenliğine ilişkin yanlış bir anlamı vardır. Ancak kullanıcıların, iş e-posta adreslerine yalnızca bir kez bir kod gidiş dönüş yapması ve bu hesabın hesabını gelecekte dilediğiniz zaman yeniden adlandırabilmeleri gerekir.

Bu durum özellikle aynı e-posta adresine sahip iki hesabı olan kullanıcılar için kafa karıştırıcı ' dır (Azure AD & bir Microsoft hesabı).

### <a name="what-does-this-experience-look-like"></a>Bu deneyim nasıl görünür?
İş veya okul e-posta adresiyle bir Microsoft tüketici uygulamasına kaydolmayı denerseniz, aşağıdaki iletiyi görürsünüz.

   > [!div class="mx-imgBorder"]
   > ![İş e-postası ile hesap oluşturulamıyor](_img/sign-in-issues/cannot-use-work-email.png)

Ancak, kişisel ve iş/okul hesaplarını destekleyen bir Microsoft uygulamasına kaydolmayı denerseniz şu iletiyi görmeniz gerekir:

   > [!div class="mx-imgBorder"]
   > ![Desteklenen iş/okul hesapları](_img/sign-in-issues/existing-account.png)

### <a name="are-existing-accounts-affected"></a>Mevcut hesaplar etkileniyor mu?
Burada açıklanan kaydolma bloğu yalnızca yeni hesapların oluşturulmasını engeller. Zaten bir iş/okul e-posta adresi olan bir Microsoft hesabına sahip olan kullanıcılar üzerinde hiçbir etkisi yoktur. Bu durumda zaten bir kişisel Microsoft hesabı yeniden adlandırmayı daha kolay hale getirdik. Bu [Destek makalesinde](https://windows.microsoft.com/en-US/Windows/rename-personal-microsoft-account) basit adım adım yönergeler sunulmaktadır. Kişisel Microsoft hesabı yeniden adlandırılması, Kullanıcı adının değiştirilmesi anlamına gelir ve iş e-postanızı veya Microsoft 365 gibi iş hizmetlerinde oturum açma şeklini etkilemez. Ayrıca, kişisel öğelerinizi etkilemez; yalnızca oturum açma şeklini değiştirir. Başka bir (kişisel) e-posta adresi kullanabilir, @outlook.com Microsoft 'tan yeni bir e-posta adresi alabilir veya telefon numaranızı yeni bir Kullanıcı adı olarak kullanabilirsiniz.

> [!NOTE]
> BT departmanınız, iş/okul e-postanız ile kişisel bir Microsoft hesabı oluşturmanız isteniyorsa (örneğin, Premier Destek gibi Microsoft iş hizmetlerine erişmek için), hesabınızı yeniden adlandırmadan önce yönetici ekibiniz ile konuşun.

## <a name="deleting-a-sign-in-address-may-prevent-access-to-a-subscription"></a>Bir oturum açma adresinin silinmesi, bir aboneliğe erişimi engelleyebilir
Aboneliğinizle ilişkili bir veya daha fazla kimliği (MSA veya AAD) silerseniz, Kullanıcı adınız ve oturum açma KIMLIĞINIZ dahil olmak üzere abone bilgileriniz anonim olarak oluşturulabilir ve aboneliğinize erişim kaybı ile sonuçlanır.

Abonelik erişiminizdeki etkileri önlemek için, aşağıdaki tekniklerden birini kullanın.
- Tek bir kimlik yönetimi sistemi (MSA veya AAD) dağıtın, ancak her ikisini birden kullanmayın.
- AAD ve MSA kimliklerini kiracı aracılığıyla ilişkilendirin.

## <a name="signing-in-may-fail-when-using-aliases"></a>Takma adlar kullanılırken oturum açma başarısız olabilir
Oturum açmak için kullanılan hesap türüne bağlı olarak, kullanılabilir abonelikler ' de oturum açarken doğru görüntülenmeyebilir [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) . Olası bir neden, aboneliğin atandığı oturum açma kimliği yerine "diğer adlar" veya "kolay adlar" in kullanılması olabilir. Bu "diğer ad" olarak adlandırılır.

### <a name="what-is-aliasing"></a>Diğer ad nedir?
"Diğer ad" terimi, Windows 'da (veya Active Directory) oturum açmak ve e-postaya erişmek için farklı kimliklere sahip kullanıcılar anlamına gelir.

Bir şirketin Dizin oturum açması için bir Microsoft Online hizmetine sahip olması gibi diğer JohnD@contoso.com adlara ve kullanıcılara gibi diğer adlar veya kolay adlar kullanarak e-posta hesaplarına erişim varsa, bu yana de erişilebilir John.Doe@contoso.com . Toplu Lisanslama Hizmet Merkezi (VLSC) üzerinden aboneliklerini yöneten birçok müşteri için, sunulan () e-posta adresi John.Doe@contoso.com JohnD@contoso.com "Iş veya okul hesabı" seçeneği aracılığıyla başarılı kimlik doğrulaması için gereken dizin adresiyle () eşleşmediğinden, bu işlem başarısız oturum açma deneyimine yol açabilir.

### <a name="what-options-do-i-have"></a>Hangi seçeneklere sahip mıyım?
Bir abone perspektifinden, şirketinizin kimlik yapılandırmasını anlamak için öncelikle yöneticinizle birlikte çalışmanız önemlidir. Gerekirse, yöneticinizin hesap ayarlarınızı yönetim portalından güncelleştirmesi veya şirket e-posta adresinizi kullanarak bir Microsoft hesabı (MSA) oluşturmanız gerekebilir. MSA oluşturma adımlarını uygulamadan önce, bu eylemi gerçekleştirmek için herhangi bir ilke veya sorunla ilgili olarak yöneticinizle görüşün. 

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- AAD içindeki [MSA ve AAD hesaplarını bağlamayı](/azure/active-directory/b2b/add-users-administrator) öğrenin.
- [Anonimleştirme](anonymization.md)hakkında daha fazla bilgi edinin.
