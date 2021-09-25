---
title: GitHub hesabınızla abonelikler Visual Studio için oturum açma | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 1bdcb3c9-bba1-4e25-a609-9d7e539d78e0
ms.date: 03/08/2021
ms.topic: conceptual
description: GitHub hesabınızla Visual Studio abonelikleriniz üzerinde nasıl oturum kullanabileceğinizi öğrenin.
ms.openlocfilehash: d57eb9c68a21fd7e68eda23efa3b194f8f0fb203
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428252"
---
# <a name="signing-in-to-visual-studio-subscriptions-with-your-github-account"></a>GitHub hesabınızla abonelikler Visual Studio için oturum açma 
Visual Studio aboneliğinizde oturum açma adımları, kullanmakta olduğunuz hesap türüne bağlıdır. Örneğin, bir Microsoft hesabı (MSA) veya işvereniniz veya okulunuz tarafından sağlanan bir e-posta adresi kullanıyor olabilirsiniz. 2019 ocak itibariyle artık bazı aboneliklerde oturum açmak için GitHub hesabınızı da kullanabilirsiniz. 

bu makale GitHub hesabınızla oturum açmak için gereken adımları sağlar.

## <a name="signing-in-with-your-github-account"></a>GitHub hesabınızla oturum açma

GitHub kimlik desteği, mevcut GitHub hesabınızı yeni veya mevcut bir Microsoft hesabı kimlik bilgisi olarak kullanmanıza olanak tanır ve GitHub hesabınızı Microsoft hesabı ile bağlantılandırın. 

GitHub ile oturum açtığınızda, Microsoft, GitHub hesabınızla ilişkili herhangi bir e-posta adresinin mevcut bir kişisel veya kurumsal Microsoft hesabı eşleşip eşleşmediğini denetler. Adres kurumsal hesabınızla eşleşiyorsa bunun yerine bu hesapta oturum açmanız istenir. adres bir kişisel hesapla eşleşiyorsa, bu kişisel hesaba bir oturum açma yöntemi olarak GitHub hesabınızı ekleyeceğiz.

GitHub ve Microsoft hesabı kimlik bilgilerinizi bağladığınızda, Azure siteleri, Office uygulamaları ve Xbox gibi kişisel Microsoft hesabı kullanılabilen her yerde bu çoklu oturum açma bilgilerini kullanabilirsiniz. bu hesaplar ayrıca, Microsoft hesabı olarak Azure Active Directory konuk oturum açma işlemleri için kullanılabilir ve e-posta adresinin davette ile eşleştiği varsayılır.

> [!NOTE]
> bir GitHub kimliğini Microsoft hesabı bağlamak, Microsoft 'a herhangi bir kod erişimi vermez. Azure DevOps ve Visual Studio gibi uygulamalar kod depolarınıza erişim gerektirdiğinde, bu erişim için belirli bir onay vermeniz istenir. 

### <a name="frequently-asked-questions"></a>Sık sorulan sorular
aşağıdaki sss 'ler, Visual Studio aboneliklerde oturum açmak için GitHub hesabı kimlik bilgilerinizin kullanımıyla ilgili olarak karşılaşabileceğiniz soruları ele alabilir.

#### <a name="q-i-forgot-my-github-password--how-can-i-access-my-account-now"></a>s: GitHub parolamı unuttum.  Hesabımı şimdi nasıl erişebilirim?
y: [parolanızı sıfırlamak](https://github.com/password_reset)için GitHub hesabınızı kurtarabilirsiniz. veya, [hesabınızı kurtarırken](https://account.live.com/password/reset)GitHub hesabınızın e-posta adresini girerek GitHub bağlantılı Microsoft hesabı kurtarabilirsiniz.

#### <a name="q-i-deleted-my-github-account--how-can-i-access-my-microsoft-account-msa-now"></a>s: GitHub hesabımı sildim.  Microsoft hesabı (MSA) şimdi nasıl erişebilirim?
y: MSA üzerinde parola, Authenticator uygulaması veya güvenlik anahtarı gibi başka bir kimlik bilgileriniz yoksa, ona iliştirilmiş e-posta adresini kullanarak Microsoft hesabı kurtarabilirsiniz. Başlamak için [Hesabınızı kurtarma](https://account.live.com/password/reset)bölümüne gidin. Daha sonra oturumunuzu nasıl imzalayabileceğinizi bilmemiz için hesabınıza bir parola eklemeniz gerekir. 

#### <a name="q-theres-no-sign-in-with-github-option-on-the-sign-in-page--how-can-i-use-my-github-credentials-to-sign-in"></a>s: oturum açma sayfasında "GitHub ile oturum aç" seçeneği yoktur.  oturum açmak için GitHub kimlik bilgilerimi nasıl kullanabilirim?
A: GitHub bağlantılı Microsoft hesabı oluşturduğunuzda seçtiğiniz GitHub hesabı e-posta adresini yazın. size bakacağız ve oturum açma için GitHub size göndereceğiz. ya da oturum açma sayfasında oturum açma seçenekleri bağlantısı varsa, bu bağlantıyı tıklattıktan sonra gösterilen **GitHub oturum aç** düğmesini kullanın. 

#### <a name="q-i-cant-sign-in-to-some-of-my-apps-and-products-with-github--why"></a>S: GitHub olan uygulamalarımın ve ürünlerimde oturum açamıyorum.  Neden?
y: tüm Microsoft ürünleri, oturum açma sayfasından (örneğin, Xbox konsolları) GitHub. com ' A erişemez. bunun yerine, bağlı GitHub hesabınızdan e-posta adresini yazdığınızda, gerçekten siz olduğunu doğrulayabilmemiz için bu adrese bir kod göndereceğiz. Yalnızca farklı bir oturum açma yöntemiyle aynı hesapta oturum açtınız. 

#### <a name="q--ive-added-a-password-to-the-microsoft-account-i-have-linked-to-my-github-account--will-that-cause-a-problem"></a>s: GitHub hesabımı bağladım Microsoft hesabı bir parola ekledim.  Soruna neden olacak mı?
Y: hiç değil. bu, GitHub parolanızı değiştirmez; Microsoft hesabı oturum açmak için yalnızca başka bir yoldur. e-posta adresinizi kullanarak oturum açtığınızda, Microsoft hesabı parolanızla oturum açma seçeneğini sunacağız veya oturum açmak için GitHub. bir parola eklemeniz gerekiyorsa, GitHub hesabınızın parolalarından farklı olduğundan emin olmanızı önemle öneririz.

#### <a name="q-i-want-to-add-the-authenticator-app-to-the-account-i-created-using-github--can-i-do-that"></a>s: Authenticator uygulamayı GitHub kullanarak oluşturduğum hesaba eklemek istiyorum.  Bunu yapabilir miyim?
Y: sorun yok — uygulamayı indirip e-posta adresinizi kullanarak oturum açmanız yeterlidir. e-posta adresinizle oturum açtığınızda, kimlik bilgileriniz olarak [Authenticator uygulamasını](https://www.microsoft.com/p/microsoft-authenticator/9nblgggzmcj6) veya GitHub seçmeniz istenir.

#### <a name="q-ive-enabled-two-factor-authentication-on-both-my-github-and-microsoft-accounts-msa-but-when-i-sign-in-to-my-msa-im-still-asked-to-authenticate-twice--why"></a>s: hem GitHub hem de Microsoft hesapları (msa) üzerinde iki öğeli kimlik doğrulamayı etkinleştirdim, ancak MSA 'da oturum açarken, hala iki kez kimlik doğrulaması yapacağım.  Neden?
y: güvenlik kısıtlamaları nedeniyle, iki adımlı doğrulama etkin olsa bile, Microsoft, GitHub ile tek faktörlü doğrulama olarak oturum açmayı sayar. Bu nedenle, Microsoft hesabı için tekrar kimlik doğrulaması yapmanız gerekir. 

#### <a name="q--how-can-i-tell-if-my-microsoft-account-and-github-accounts-are-linked"></a>s: Microsoft hesabı ve GitHub hesaplarından bağlantı olup olmadığını nasıl anlayabilirim?
y: hesap diğer adınızı (e-posta adresi, telefon numarası, Skype adı) kullanarak oturum açtığınızda, hesabınız için tüm oturum açma yöntemlerini göstereceğiz. burada GitHub görmüyorsanız, henüz ayarlayamazsınız.

#### <a name="q--how-can-i-unlink-my-microsoft-and-github-accounts"></a>s: Microsoft ve GitHub hesaplarından nasıl bağlantıyı nasıl kaldırabilirim? 
A: account.microsoft.com 'in [güvenlik sekmesine](https://account.microsoft.com/security) gidin ve GitHub hesabınızın bağlantısını kaldırmak için **gelişmiş güvenlik seçenekleri** ' ne tıklayın. GitHub hesabınızın bağlantısı kesmek, oturum açma yöntemi olarak bu uygulamayı kaldırır ve Visual Studio tüm GitHub depolara erişimi kaldırır. diğer Microsoft ürünleri GitHub hesabınıza ayrı erişim isteğinde bulunabilir, bu nedenle buradaki erişimin kaldırılması tüm ürünlerde erişimi kaldırmaz. burada listelenen uygulamalardan izin iptal etmek için GitHub profilinizin [uygulama izinleri](https://github.com/settings/applications) sayfasına gidin.

#### <a name="q--i-try-to-use-my-github-account-to-sign-in-but-im-prompted-that-i-already-have-a-microsoft-identity-that-i-should-use-instead--whats-happening"></a>s: oturum açmak için GitHub hesabımı kullanmaya çalışıyorum, ancak bunun yerine kullanılması gereken bir Microsoft kimliği zaten var mı?  Ne oluyor?
y: GitHub hesabınızda bir Azure Active Directory e-posta adresiniz varsa, Azure 'a erişebilen ve GitHub kodunuzu kullanarak cı işlem hatlarını çalıştıran bir Microsoft kimliğiniz zaten var. Bu hesabın kullanılması, Azure kaynaklarınızın ve derleme işlem hatlarınızın kurumsal sınırlarınızda kalmasını sağlar. bununla birlikte, kişisel çalışma yapıyorsanız, GitHub hesabınıza kişisel bir e-posta adresi koyabilmeniz önerilir, böylece her zaman bu hesaba erişebilirsiniz. Bunu yaptıktan sonra yeniden oturum açmayı deneyin ve iş veya okul hesabınızda oturum açmanız istendiğinde **farklı bir e-posta adresi kullan** ' ı seçin. Bu, kişisel e-posta adresini kullanarak yeni bir Microsoft hesabı oluşturmanızı sağlar.

## <a name="resources"></a>Kaynaklar
- Visual Studio abonelikleriyle ilgili satış, abonelik, hesap ve faturalandırma konusunda yardım için bkz. Visual Studio [abonelikleri desteği](https://aka.ms/vssubscriberhelp).

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Abonelikler portalında başarıyla oturum açtıktan sonra avantajlar sayfasını ziyaret etmenizi https://my.visualstudio.com/benefits ve size sunulan harika araçları, hizmetleri ve teklifleri keşfetmenizi öneririz.