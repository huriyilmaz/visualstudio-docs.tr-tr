---
title: GitHub hesabınızla Visual Studio Aboneliklerine Oturum Açma | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/09/2020
ms.topic: conceptual
description: GitHub hesabınızla Visual Studio aboneliğinizde nasıl oturum açabilirsiniz öğrenin.
ms.openlocfilehash: a0a2f69ab3cbab3fdf6c35d9407a59a7c7d49eb1
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "78947090"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>GitHub hesabınızla Visual Studio aboneliğinde oturum açma 

Visual Studio aboneliğinizde oturum açma adımları kullandığınız hesabın türüne bağlıdır. Örneğin, bir Microsoft Hesabı (MSA) veya işvereniniz veya okulunuzun sağladığı bir e-posta adresi kullanıyor olabilirsiniz. Ocak 2019 itibariyle, artık github hesabınızı kullanarak bazı aboneliklerde oturum açabilirsiniz. 

Bu makalede, GitHub hesabınızla oturum açma adımları sağlanacaktır.

## <a name="signing-in-with-your-github-account"></a>GitHub hesabınızla oturum açma

GitHub kimlik desteği, varolan GitHub hesabınızı yeni veya varolan bir Microsoft hesabı için kimlik bilgisi olarak kullanmanıza olanak tanır ve GitHub hesabınızı Microsoft hesabınıza bağlar. 

GitHub ile oturum açtığınızda, Microsoft GitHub hesabınızla ilişkili e-posta adreslerinin varolan bir kişisel veya kurumsal Microsoft hesabıyla eşleşip eşleşmediğini denetler. Adres kurumsal hesabınızla eşleşirse, bunun yerine bu hesapta oturum açmanız istenir. Adres kişisel bir hesapla eşleşirse, github hesabınızı bu kişisel hesaba oturum açma yöntemi olarak ekleriz.

GitHub ve Microsoft hesap kimlik bilgileriniz bağlandıktan sonra, azure siteleri, Office uygulamaları ve Xbox gibi kişisel bir Microsoft hesabının kullanılabileceğiniz her yerde bu tek oturum açma'yı kullanabilirsiniz. Bu hesaplar, e-posta adresinin davettekiyle eşleştiğini varsayarak Azure Active Directory konuk oturum açma ları için de kullanılabilir.

> [!NOTE]
> GitHub kimliğini bir Microsoft hesabına bağlamak Microsoft'a herhangi bir kod erişimi vermez. Azure DevOps ve Visual Studio gibi uygulamalar kod depolarınıza erişim gerektirdiğinde, bu erişim için özel izin almanız istenir. 

### <a name="frequently-asked-questions"></a>Sık sorulan sorular
Aşağıdaki SSS'ler, Visual Studio aboneliklerinde oturum açmak için GitHub hesap kimlik bilgilerinizin kullanımıyla ilgili karşılaşabileceğiniz soruları yanıtlar.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>S: GitHub şifremi unuttum.  Hesabıma şimdi nasıl erişebilirim?
C: [Parolanızı Sıfırla'ya](https://github.com/password_reset)giderek GitHub hesabınızı kurtarabilirsiniz. Veya, GitHub hesabınızın e-posta adresini hesabınızı [kurtar'a](https://account.live.com/password/reset)girerek GitHub'a bağlı Microsoft hesabınızı kurtarabilirsiniz.

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>S: GitHub hesabımı sildim.  Microsoft hesabıma (MSA) şimdi nasıl erişebilirim?
C: MSA'nızda başka kimlik bilgileriniz yoksa (parola, Authenticator uygulaması veya güvenlik anahtarı gibi), bağlı e-posta adresini kullanarak Microsoft hesabınızı kurtarabilirsiniz. Başlamak için hesabınızı [kurtar'a](https://account.live.com/password/reset)gidin. Daha sonra nasıl oturum açacağını bilmemiz için hesabınıza bir parola eklemeniz gerekir. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>S: Oturum açma sayfasında "GitHub ile oturum aç" seçeneği yoktur.  Oturum açtım için GitHub kimlik bilgilerimi nasıl kullanabilirim?
C: GitHub'a bağlı Microsoft hesabınızı oluşturduğunuzda seçtiğiniz GitHub hesabı e-posta adresini yazın. Sizi arayıp oturum açmanız için GitHub'a göndereceğiz. Veya oturum açma sayfasında Oturum Açma seçenekleri bağlantısı varsa, bu bağlantıyı tıklattıktan sonra gösterilen **GitHub ile Oturum Aç** düğmesini kullanın. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>S: GitHub ile bazı uygulamalarımda ve ürünlerimde oturum açamıyorum.  Neden?
C: Tüm Microsoft ürünleri oturum açma sayfalarından (örneğin, Xbox konsolları) GitHub.com erişemez. Bunun yerine, bağlı GitHub hesabınızdan e-posta adresini yazdığınızda, bu adrese bir kod göndeririz, böylece gerçekten siz olduğunuzu doğrulayabiliriz. Farklı bir oturum açma yöntemiyle yine aynı hesapta oturum açabilirsiniz. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>S: GitHub hesabıma bağlı olduğum Microsoft hesabına bir parola ekledim.  Bu bir soruna neden olur mu?
C: Hiç de değil. Bu, GitHub parolanızı değiştirmez; Microsoft hesabınızda oturum açmanın başka bir yolu daha olur. E-posta adresinizi kullanarak oturum açtığınızda, size Microsoft hesap parolanızla oturum açma veya oturum açmanız için GitHub'a gitme seçeneği sunacağız. Parola eklemeniz gerekiyorsa, Parola'nın GitHub hesabınızın parolasından farklı olduğundan emin olmanızönerilir.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>S: GitHub kullanarak oluşturduğum hesaba Authenticator uygulamasını eklemek istiyorum.  Bunu yapabilir miyim?
C: Sorun değil — sadece uygulamayı indirin ve e-posta adresinizi kullanarak oturum açın. E-posta adresinizle oturum açtığınızda, kimlik bilgileriniz olarak [Authenticator uygulamasını](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) veya GitHub'ı seçmeniz istenir.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>S: Hem GitHub hem de Microsoft hesaplarımda (MSA) iki faktörlü kimlik doğrulamayı etkinleştirdim, ancak MSA'mda oturum açtığınızda yine de iki kez kimlik doğrulamam istenir.  Neden?
C: Güvenlik kısıtlamaları nedeniyle Microsoft, orada etkinleştirilen iki aşamalı doğrulama nız olsa bile GitHub ile oturum açmanızı tek faktörlü bir doğrulama olarak sayar. Bu nedenle, Microsoft hesabınız için yeniden kimlik doğrulamanız gerekir. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>S: Microsoft hesabımın ve GitHub hesabımın bağlantılı olup olmadığını nasıl anlayabilirim?
C: Hesap takma adınızı (e-posta adresi, telefon numarası, Skype adı) kullanarak oturum açtığınızda, hesabınız için tüm oturum açma yöntemlerini gösteririz. GitHub'ı orada göremiyorsanız, henüz ayarlamamışsınızdır.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>S: Microsoft ve GitHub hesaplarıma bağlantıyı nasıl açabilirim? 
C: account.microsoft.com [Güvenlik sekmesine](https://account.microsoft.com/security) gidin ve GitHub hesabınızın bağlantısını çıkarmak için **daha fazla güvenlik seçeneğini** tıklatın. GitHub hesabınızın bağlantısının kaldırılması, hesabı oturum açma yöntemi olarak kaldırır ve Visual Studio'daki tüm GitHub depolarına erişimi kaldırır. Diğer Microsoft ürünleri GitHub hesabınıza ayrı olarak erişilmesini istemiş olabilir, bu nedenle buradaki erişimi kaldırmak tüm ürünlerdeki erişimi kaldırmaz. Orada listelenen uygulamaların onayını iptal etmek için GitHub profilinizin [uygulama izinleri](https://github.com/settings/applications) sayfasına gidin.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>S: Oturum açmam için GitHub hesabımı kullanmaya çalışıyorum, ancak bunun yerine kullanmam gereken bir Microsoft kimliğine zaten sahip olmam istenir.  Ne oluyor?
C: GitHub hesabınızda bir Azure Active Directory e-posta adresiniz varsa, bu, GitHub kodunuzu kullanarak Azure'a erişebilen ve CI ardışık hatlar hattını çalıştırabilen bir Microsoft kimliğiniz olduğu anlamına gelir. Bu hesabı kullanmak, Azure kaynaklarınızın ve yapı ardışık hatlarınızın kuruluş sınırlarıiçinde kalmasını sağlar. Ancak, kişisel iş yapıyorsanız, github hesabınıza her zaman erişebilmeniz için kişisel bir e-posta adresi koymanızı öneririz. Bunu yaptıktan sonra, yeniden oturum açmayı deneyin ve iş veya okul hesabınızda oturum açmanız istendiğinde **farklı bir e-posta adresi kullanın'ı** seçin. Bu, bu kişisel e-posta adresini kullanarak yeni bir Microsoft hesabı oluşturmanıza olanak sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Abonelikler portalında başarılı bir şekilde oturum imzaladıktan sonra, avantajlar https://my.visualstudio.com/benefits sayfasını ziyaret etmenizi ve kullanabileceğiniz harika araçları, hizmetleri ve teklifleri keşfetmenizi öneririz.  
