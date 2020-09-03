---
title: GitHub hesabınızla Visual Studio aboneliklerinde oturum açma | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 03/09/2020
ms.topic: conceptual
description: GitHub hesabınızla Visual Studio aboneliğinizde nasıl oturum kullanabileceğinizi öğrenin.
ms.openlocfilehash: 722eeae315a8b4a6bd93fb1048846b147b294afa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80233224"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>GitHub hesabınızla Visual Studio abonelikleriniz üzerinde oturum açma 

Visual Studio aboneliğinizde oturum açmak için kullandığınız adımlar, kullanmakta olduğunuz hesap türüne bağlıdır. Örneğin, bir Microsoft hesabı (MSA) veya işvereniniz veya okulunuz tarafından sağlanan bir e-posta adresi kullanıyor olabilirsiniz. 2019 Ocak itibariyle artık bazı aboneliklerde oturum açmak için GitHub hesabınızı da kullanabilirsiniz. 

Bu makale, GitHub hesabınızla oturum açmak için gereken adımları sağlar.

## <a name="signing-in-with-your-github-account"></a>GitHub hesabınızla oturum açma

GitHub kimlik desteği, mevcut GitHub hesabınızı yeni veya mevcut bir Microsoft hesabı kimlik bilgileri olarak kullanmanıza olanak tanır ve GitHub hesabınızı Microsoft hesabı ile bağlantılandırın. 

GitHub ile oturum açtığınızda Microsoft, GitHub hesabınızla ilişkili herhangi bir e-posta adresinin mevcut bir kişisel veya kurumsal Microsoft hesabı eşleşip eşleşmediğini denetler. Adres kurumsal hesabınızla eşleşiyorsa bunun yerine bu hesapta oturum açmanız istenir. Adres bir kişisel hesapla eşleşiyorsa, GitHub hesabınızı bu kişisel hesaba bir oturum açma yöntemi olarak ekleyeceğiz.

GitHub ve Microsoft hesabı kimlik bilgileriniz bağlantılarınızdan sonra, Azure siteleri, Office uygulamaları ve Xbox gibi kişisel Microsoft hesabı kullanılabilecek her yerde bu çoklu oturum açma bilgilerini kullanabilirsiniz. Bu hesaplar, Microsoft hesabı olarak Azure Active Directory Konuk oturum açma işlemleri için de kullanılabilir ve e-posta adresinin davette ile eşleştiği varsayılır.

> [!NOTE]
> GitHub kimliğini bir Microsoft hesabı bağlamak, Microsoft 'a herhangi bir kod erişimi vermez. Azure DevOps ve Visual Studio gibi uygulamalar kod Depolarınıza erişim gerektirdiğinde, bu erişim için belirli bir onay vermeniz istenir. 

### <a name="frequently-asked-questions"></a>Sık sorulan sorular
Aşağıdaki SSS, Visual Studio aboneliklerinde oturum açmak için GitHub hesabı kimlik bilgilerinizin kullanımıyla ilgili olarak karşılaşabileceğiniz soruları ele alabilir.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>S: GitHub Parolamı unuttum.  Hesabımı şimdi nasıl erişebilirim?
Y: [parolanızı sıfırlamak](https://github.com/password_reset)için GitHub hesabınızı kurtarabilirsiniz. Ya da, GitHub hesabınızın e-posta adresini [Hesabınızı kurtararak](https://account.live.com/password/reset)girerek GitHub ile bağlantılı Microsoft hesabı kurtarabilirsiniz.

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>S: GitHub hesabımı sildim.  Microsoft hesabı (MSA) şimdi nasıl erişebilirim?
Y: MSA üzerinde başka bir kimlik bilgileriniz yoksa (parola, kimlik doğrulayıcı uygulaması veya güvenlik anahtarı gibi), ona iliştirilmiş e-posta adresini kullanarak Microsoft hesabı kurtarabilirsiniz. Başlamak için [Hesabınızı kurtarma](https://account.live.com/password/reset)bölümüne gidin. Daha sonra oturumunuzu nasıl imzalayabileceğinizi bilmemiz için hesabınıza bir parola eklemeniz gerekir. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>S: oturum açma sayfasında "GitHub ile oturum aç" seçeneği yoktur.  GitHub kimlik bilgilerimi nasıl oturum açmak için nasıl kullanabilirim?
Y: GitHub ile bağlantılı Microsoft hesabı oluştururken seçtiğiniz GitHub hesabı e-posta adresini yazın. Oturum açmak için sizi GitHub 'a göndereceğiz. Ya da oturum açma sayfasında bir oturum açma seçenekleri bağlantısı varsa, bu bağlantıyı tıklattıktan sonra gösterilen **GitHub Ile oturum aç** düğmesini kullanın. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>S: bazı Uygulamalarım ve ürünlerimde GitHub ile oturum açamıyorum.  Neden?
Y: tüm Microsoft ürünleri, GitHub.com oturum açma sayfasından (örneğin, Xbox konsolları) erişebilir. Bunun yerine, bağlantılı GitHub hesabınızdan e-posta adresini yazdığınızda, gerçekten siz olduğunu doğrulayabilmemiz için bu adrese bir kod göndereceğiz. Yalnızca farklı bir oturum açma yöntemiyle aynı hesapta oturum açtınız. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>S: GitHub hesabımı bağladım Microsoft hesabı bir parola ekledim.  Soruna neden olacak mı?
Y: hiç değil. Bu, GitHub parolanızı değiştirmez; Microsoft hesabı oturum açmak için yalnızca başka bir yoldur. E-posta adresinizi kullanarak oturum açtığınızda, size Microsoft hesabı parolanızla oturum açma veya kayıt için GitHub 'a bağlanma seçeneğini sunacağız. Bir parola eklemeniz gerekiyorsa GitHub hesabınızın parolalarından farklı olduğundan emin olmak kesinlikle önerilir.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>S: kimlik doğrulayıcı uygulamasını GitHub kullanarak oluşturduğum hesaba eklemek istiyorum.  Bunu yapabilir miyim?
Y: sorun yok — uygulamayı indirip e-posta adresinizi kullanarak oturum açmanız yeterlidir. E-posta adresinizle oturum açtığınızda kimlik bilgileriniz olarak kimlik [Doğrulayıcı uygulamasını](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) veya GitHub ' ı seçmeniz istenir.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>S: hem GitHub hem de Microsoft accounts (MSA) üzerinde iki öğeli kimlik doğrulamayı etkinleştirdim, ancak MSA 'da oturum açarken, hala iki kez kimlik doğrulaması istedim.  Neden?
Y: güvenlik kısıtlamaları nedeniyle, iki adımlı doğrulama etkin olsa bile, Microsoft, GitHub ile bir tek etmenli doğrulama olarak oturum açmayı sayar. Bu nedenle, Microsoft hesabı için tekrar kimlik doğrulaması yapmanız gerekir. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>S: Microsoft hesabı ve GitHub hesaplarım bağlantılı olup olmadığını nasıl anlayabilirim?
Y: hesap diğer adınızı (e-posta adresi, telefon numarası, Skype adı) kullanarak oturum açtığınızda, hesabınız için tüm oturum açma yöntemlerini göstereceğiz. GitHub 'ı orada görmüyorsanız, henüz kurmadınız.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>S: Microsoft ve GitHub hesaplarından nasıl bağlantıyı nasıl kaldırabilirim? 
Y: account.microsoft.com ' un [Güvenlik sekmesine](https://account.microsoft.com/security) gidin ve GitHub Hesabınızın bağlantısını kaldırmak Için **daha fazla güvenlik seçenekleri ' ne** tıklayın. GitHub hesabınızın bağlantısı kesmek, bu hesabı bir oturum açma yöntemi olarak kaldırır ve Visual Studio 'daki herhangi bir GitHub depolarına erişimi kaldırır. Diğer Microsoft ürünleri, GitHub hesabınıza ayrı olarak erişim isteğinde bulunabilir, bu nedenle buradaki erişimin kaldırılması tüm ürünlerde erişimi kaldırmaz. Burada listelenen uygulamalardan izin iptal etmek için GitHub profilinizin [Uygulama izinleri](https://github.com/settings/applications) sayfasına gidin.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>S: kayıt açmak için GitHub hesabımı kullanmaya çalışıyorum, ancak bunun yerine kullandığım bir Microsoft kimliği zaten var.  Ne oluyor?
Y: GitHub hesabınızda bir Azure Active Directory e-posta adresiniz varsa, bu, Azure 'a erişebilen ve GitHub kodunuzu kullanarak CI işlem hatlarını çalıştıran bir Microsoft kimliğiniz zaten var demektir. Bu hesabın kullanılması, Azure kaynaklarınızın ve derleme işlem hatlarınızın kurumsal sınırlarınızda kalmasını sağlar. Bununla birlikte, kişisel işler gerçekleştiriyorsanız, bu hesaba her zaman erişebilmenizi sağlamak için GitHub hesabınıza kişisel bir e-posta adresi koymayı öneririz. Bunu yaptıktan sonra yeniden oturum açmayı deneyin ve iş veya okul hesabınızda oturum açmanız istendiğinde **farklı bir e-posta adresi kullan** ' ı seçin. Bu, kişisel e-posta adresini kullanarak yeni bir Microsoft hesabı oluşturmanızı sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Abonelikler portalında başarıyla oturum açtıktan sonra avantajlar sayfasını ziyaret etmenizi https://my.visualstudio.com/benefits ve size sunulan harika araçları, hizmetleri ve teklifleri keşfetmenizi öneririz.  
