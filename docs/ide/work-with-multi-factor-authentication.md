---
title: Visual Studio oturum açma bilgileriyle çok faktörlü kimlik doğrulaması
titleSuffix: ''
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: how-to
description: Visual Studio multi-factor authentication gerektiren hesaplarla nasıl kullanacağınızı öğrenin.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9f67ee7b1c9237dd056a29abd2097d9b13eeeee7
ms.sourcegitcommit: bfae1f88c278835e26f3200cfced769be3191fc4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2021
ms.locfileid: "132535119"
---
# <a name="use-visual-studio-with-accounts-that-require-multi-factor-authentication-mfa"></a>multi-factor authentication (MFA) gerektiren hesaplarla Visual Studio kullanma

Dış Konuk kullanıcılarıyla işbirliği yaparken, **çok faktörlü kimlik doğrulaması (MFA)** gibi **koşullu erişim (CA)** ilkeleriyle uygulamalarınızı ve verilerinizi korumak iyi bir fikirdir.  

Etkinleştirildikten sonra, konuk kullanıcıların kaynaklarınıza erişmesi için yalnızca bir Kullanıcı adı ve parola gerekir ve ek güvenlik gereksinimlerini karşılaması gerekir. MFA ilkeleri, tıpkı kendi kuruluşunuzun üyeleri için etkinleştirildiği şekilde, kiracı, uygulama veya bireysel konuk kullanıcı düzeyinde uygulanabilir. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>Visual Studio deneyimi MFA ilkelerinden nasıl etkilenir?
16,6 ' dan önceki Visual Studio sürümlerinde, MFA gibi CA ilkelerini destekleyen ve iki veya daha fazla kiracı ile ilişkili olan hesaplarla birlikte kullanıldığında kimlik doğrulama deneyimleri azalabilir.

bu sorunlar Visual Studio örneğinizin günde birden çok kez yeniden kimlik doğrulaması yapılmasına neden olabilir. aynı Visual Studio oturumunun kursu sırasında bile, önceden kimliği doğrulanmış kiracılar için kimlik bilgilerinizi yeniden girmeniz gerekebilir.

## <a name="using-visual-studio-with-mfa-policies"></a>MFA ilkeleriyle Visual Studio kullanma
16,6 sürümünde, kullanıcıların MFA gibi CA ilkeleri aracılığıyla güvenli hale getirilmiş kaynaklara nasıl erişebildiğine yönelik yeni yetenekler 2019 Visual Studio ekledik. bu geliştirilmiş iş akışını kullanmak için, Visual Studio hesaplarını eklemek ve yeniden kimlik doğrulaması yapmak için sisteminizin varsayılan web tarayıcısını kullanmayı tercih etmeniz gerekir.  

> [!WARNING]
> bu iş akışının kullanılması, Visual Studio hesaplarını eklerken veya yeniden doğrularken birden fazla ek kimlik doğrulama isteminde ortaya çıkan düşürülmüş bir deneyimi tetikleyemeyebilir. 

### <a name="enabling-system-web-browser"></a>Sistem Web tarayıcısını etkinleştirme

> [!NOTE] 
> En iyi deneyim için, bu iş akışına devam etmeden önce sisteminizin varsayılan Web tarayıcısı verilerini temizlemeniz önerilir. ayrıca, Windows 10 iş **veya okul** kapsamında Ayarlar iş veya okul hesaplarınız varsa lütfen düzgün şekilde doğrulandıklarından emin olun.

bu iş akışını etkinleştirmek için Visual Studio seçenekleri iletişim kutusuna **(araçlar > seçenekler...)** gidin, **hesaplar** sekmesini seçin ve **hesapları ekleme ve yeniden kimlik doğrulaması altında:** açılan menüsünden **sistem web tarayıcısı** ' nı seçin. 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Menüden sistem Web tarayıcısı ' nı seçin.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>MFA ilkeleriyle ek hesaplar üzerinde oturum açma 
sistem web tarayıcısı iş akışı etkinleştirildikten sonra, hesap Ayarlar iletişim kutusu **(dosya > hesabı Ayarlar...)** aracılığıyla Visual Studio oturum açabilir veya hesabı ekleyebilirsiniz.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Visual Studio yeni bir kişiselleştirme hesabı ekleyin." border="false":::

Bu eylem, sisteminizin varsayılan Web tarayıcısını açar, hesabınızda oturum açmanızı ve gerekli MFA ilkelerini doğrulamanızı ister.

Oturum açma işlemi sırasında, oturum açmanızı isteyip istemediğinizi soran bir ek istem alabilirsiniz. Bu istem muhtemelen, oturum açmak için bir hesabın kullanıldığı ikinci zamanı gösterir. Kimlik bilgilerinizi yeniden girme gereksinimini en aza indirmek için **Evet**' i seçmenizi öneririz. Bu, kimlik bilgilerinizin tarayıcı oturumlarında korunmasını sağlar.

:::image type="content" source="media/kmsi.png" alt-text="Oturum açık kalsın mı?":::

Geliştirme etkinliklerinizi ve kaynak yapılandırmanıza bağlı olarak, oturumunuz sırasında kimlik bilgilerinizi yeniden girmeniz istenebilir. Bu, yeni bir kaynak eklediğinizde veya daha önce CA/MFA yetkilendirme gereksinimlerini karşılamadan bir kaynağa erişmeyi denediğinizde ortaya çıkabilir.

## <a name="reauthenticating-an-account"></a>Bir hesabı yeniden doğrularken  
hesabınızla ilgili bir sorun varsa Visual Studio hesap kimlik bilgilerinizi yeniden girmeniz istenebilir.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Visual Studio hesabınızı yeniden doğrula.":::

Yeniden girmeye tıkladığınızda, **kimlik bilgileriniz** sisteminizin varsayılan Web tarayıcısını açar ve kimlik bilgilerinizi otomatik olarak yenilemeyi dener. Başarısız olursa hesabınızda oturum açmanız ve gerekli CA/MFA ilkesini doğrulamanız istenir.

> [!NOTE] 
> En iyi deneyim için, kaynaklarınız için tüm CA/MFA ilkeleri doğrulanmadan tarayıcınızı açık tutun. Tarayıcının kapatılması, önceden oluşturulmuş MFA durumunun kaybolmasına neden olabilir ve ek yetkilendirme istemleri isteyebilir.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Visual Studio içinde belirli bir Azure Active Directory kiracının kullanımını devre dışı bırakma

Visual Studio 2019 sürüm 16,6, kiracıların tek tek veya küresel olarak filtreleneceği esnekliği sunar ve bunları Visual Studio etkin bir şekilde gizler. Filtreleme, bu kiracıyla kimlik doğrulaması gereksinimini ortadan kaldırır, ancak aynı zamanda ilişkili kaynaklara erişemeyeceksiniz.

Bu işlevsellik, birden çok kiracının olması ve belirli bir alt kümeyi hedefleyerek geliştirme ortamınızı iyileştirmek istediğinizde yararlıdır. Ayrıca, soruna neden olan kiracıyı filtreleyebileceğiniz için belirli bir CA/MFA ilkesini doğrulayamıyorum, örneklerde da yardımcı olabilir. 

### <a name="how-to-filter-out-all-tenants"></a>Tüm kiracıların nasıl filtreleneceği
tüm kiracıların genel olarak filtreleneceği, hesap Ayarlar iletişim kutusunu **(dosya > hesabı Ayarlar...)** açın ve **tüm Azure Active directory 'lerde kimlik doğrula** onay kutusunun işaretini kaldırın.

Bu seçeneğin seçimini kaldırmak, yalnızca hesabın varsayılan kiracısıyla kimlik doğrulaması yapabilmenizi sağlar. Ayrıca, hesabınız üzerinde Konuk olabilecek diğer kiracılar ile ilişkili herhangi bir kaynağa erişemeyeceksiniz.

### <a name="how-to-filter-out-individual-tenants"></a>Tek kiracılar nasıl filtreleneceği
Visual Studio hesabınızla ilişkili kiracılarını filtrelemek için, hesap Ayarlar iletişim kutusunu **(dosya > hesap Ayarlar...)** açın ve **filtre uygula**' ya tıklayın. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Filtre Uygula." border="false":::

Hesap **iletişim kutusu** görüntülenir ve hesabınızla birlikte kullanmak istediğiniz kiracılar ' ı seçmenize olanak sağlar. 

:::image type="content" source="media/select-filter-account.png" alt-text="Filtrelenecek hesabı seçin.":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
- [Mac için Visual Studio oturum açın](/visualstudio/mac/signing-in)
- [Birden çok kullanıcı hesabıyla çalışma](work-with-multiple-user-accounts.md)
