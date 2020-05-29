---
title: Multi-Factor Authentication gerektiren hesaplarla çalışma
ms.date: 05/27/2020
ms.topic: conceptual
description: Visual Studio 'Yu Multi-Factor Authentication gerektiren hesaplarla nasıl kullanacağınızı öğrenin.
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 696664aa5aa92a3e9a675df4803a3e65e3e81f36
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84185618"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Multi-Factor Authentication gerektiren hesaplarla Visual Studio 'Yu kullanma

Dış Konuk kullanıcılarıyla işbirliği yaparken, **çok faktörlü kimlik doğrulaması (MFA)** gibi **koşullu erişim (CA)** ilkeleriyle uygulamalarınızı ve verilerinizi korumak iyi bir fikirdir.  

Etkinleştirildikten sonra, konuk kullanıcıların kaynaklarınıza erişmesi için yalnızca bir Kullanıcı adı ve parola gerekir ve ek güvenlik gereksinimlerini karşılaması gerekir. MFA ilkeleri, tıpkı kendi kuruluşunuzun üyeleri için etkinleştirildiği şekilde, kiracı, uygulama veya bireysel konuk kullanıcı düzeyinde uygulanabilir. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>Visual Studio deneyimi MFA ilkelerinden nasıl etkilenir?
16,6 ' dan önceki Visual Studio sürümlerinde, MFA gibi CA ilkelerini destekleyen ve iki veya daha fazla kiracı ile ilişkili olan hesaplarla birlikte kullanıldığında kimlik doğrulama deneyimleri azalabilir.

Bu sorunlar, Visual Studio örneğinizin günde birden çok kez yeniden kimlik doğrulaması sormasına neden olabilir. Aynı Visual Studio oturumunun kursu sırasında bile, önceden kimliği doğrulanmış kiracılar için kimlik bilgilerinizi yeniden girmeniz gerekebilir.

## <a name="using-visual-studio-with-mfa-policies"></a>MFA ilkeleriyle Visual Studio 'Yu kullanma
16,6 sürümünde, kullanıcıların MFA gibi CA ilkeleri aracılığıyla güvenliği sağlanmış kaynaklara nasıl erişebileceğinizle ilgili yeni özellikleri Visual Studio 2019 ' e ekledik. Bu geliştirilmiş iş akışını kullanmak için, Visual Studio hesaplarını eklemek ve yeniden kimlik doğrulaması yapmak için sisteminizin varsayılan Web tarayıcısını kullanmayı tercih etmeniz gerekir.  

> [!WARNING]
> Bu iş akışının kullanılması, Visual Studio hesaplarını eklerken veya yeniden doğrularken birden fazla ek kimlik doğrulama isteminde ortaya çıkan, düşürülmüş bir deneyimi tetikleyemeyebilir. 

### <a name="enabling-system-web-browser"></a>Sistem Web tarayıcısını etkinleştirme  
Bu iş akışını etkinleştirmek için Visual Studio 'nun Seçenekler iletişim kutusuna **(araçlar > seçenekler...)** gidin, **hesaplar** sekmesini seçin ve **hesapları ekleme ve yeniden kimlik doğrulaması altında:** açılan menüsünden **sistem Web tarayıcısı** ' nı seçin. 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Menüden sistem Web tarayıcısı ' nı seçin.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>MFA ilkeleriyle ek hesaplar üzerinde oturum açma 
Sistem Web tarayıcısı iş akışı etkinleştirildikten sonra, hesap ayarları iletişim kutusu **(dosya > hesap ayarları...)** aracılığıyla, Visual Studio 'da oturum açabilir veya hesapları ekleyebilirsiniz.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Visual Studio 'ya yeni bir kişiselleştirme hesabı ekleyin." border="false":::

Bu eylem, sisteminizin varsayılan Web tarayıcısını açar, hesabınızda oturum açmanızı ve gerekli MFA ilkelerini doğrulamanızı ister. 

> [!NOTE] 
> Tarayıcınızı kapatmak ek yetkilendirme istemlerini tetikleyebilmesi için tarayıcınızı en iyi deneyim için tüm süreç boyunca açık tutun. 

## <a name="reauthenticating-an-account"></a>Bir hesabı yeniden doğrularken  
Hesabınızla ilgili bir sorun varsa, Visual Studio sizden hesap kimlik bilgilerinizi yeniden girmeniz istenebilir.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Visual Studio hesabınızı yeniden kimlik doğrulaması yapın.":::

Yeniden girmeye tıkladığınızda, **kimlik bilgileriniz** sisteminizin varsayılan Web tarayıcısını açar ve kimlik bilgilerinizi otomatik olarak yenilemeyi dener. Başarısız olursa hesabınızda oturum açmanız ve gerekli MFA ilkesini doğrulamanız istenir. 

> [!NOTE] 
> Tarayıcıyı kapatmak, ek yetkilendirme istemlerini tetikleyebilmesi için en iyi deneyim sayesinde tarayıcınızı tüm süreç boyunca açık tutun. 

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Visual Studio 'da belirli bir Azure Active Directory kiracının kullanımını devre dışı bırakma

Visual Studio 2019 sürüm 16,6, belirli kiracıların filtreleneceği esnekliği sunar. Bu, bunları Visual Studio 'dan gizler. Filtreleme, bu kiracıyla kimlik doğrulaması gereksinimini ortadan kaldırır, ancak aynı zamanda ilişkili kaynaklara erişemeyeceksiniz. 

Bu işlevsellik, birden çok kiracının olması ve belirli bir alt kümeyi hedefleyerek geliştirme ortamınızı iyileştirmek istediğinizde yararlıdır. Ayrıca, soruna neden olan kiracıyı filtreleyebileceğiniz için belirli bir CA/MFA ilkesini doğrulayamıyorum, örneklerde da yardımcı olabilir. 

### <a name="how-to-filter-out-a-tenant"></a>Bir kiracıyı filtreleme
Visual Studio hesabınızla ilişkili kiracılar filtrelemek için, hesap ayarları iletişim kutusunu **(dosya > hesap ayarları...)** açın ve **Filtre Uygula**' ya tıklayın. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Filtre Uygula." border="false":::

Hesap **iletişim kutusu** görüntülenir ve hesabınızla birlikte kullanmak istediğiniz kiracılar ' ı seçmenize olanak sağlar. 

:::image type="content" source="media/select-filter-account.png" alt-text="Filtrelenecek hesabı seçin.":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
- [Mac için Visual Studio oturum açın](/visualstudio/mac/signing-in)
- [Birden çok kullanıcı hesabıyla çalışma](work-with-multiple-user-accounts.md)