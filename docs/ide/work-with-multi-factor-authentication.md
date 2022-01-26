---
title: Oturum açma Visual Studio çok faktörlü kimlik doğrulaması
titleSuffix: ''
ms.date: 01/24/2020
ms.custom: SEO-VS-2022
ms.topic: how-to
description: Çok faktörlü kimlik Visual Studio (MFA) gerektiren hesaplarda kimlik doğrulamasını kullanmayı öğrenin.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 32ce99b4fa85a422b71e6e345611361d4e9afec0
ms.sourcegitcommit: 5a48e8cfd442b8070eaf0bda3a5946681ea4cf97
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2022
ms.locfileid: "137778882"
---
# <a name="work-with-accounts-that-require-multi-factor-authentication-mfa"></a>Çok faktörlü kimlik doğrulaması (MFA) gerektiren hesaplarla çalışma

Bu makalede, çok faktörlü kimlik doğrulaması (MFA) Visual Studio hesaplarıyla bu hesapları nasıl kullanabileceğini öğrenirsiniz.

## <a name="why-enable-mfa-policies"></a>MFA ilkeleri neden etkinleştiriliyor?

Dış konuk kullanıcılarla işbirliği yapmak için, uygulamalarınızı ve verilerinizi çok faktörlü kimlik doğrulaması **(MFA)** gibi koşullu erişim (CA) ilkeleriyle korumak iyi bir **fikirdir.**  

Etkinleştirildikten sonra konuk kullanıcıların kaynaklarınıza erişmek için bir kullanıcı adı ve paroladan fazlası gerekir ve ek güvenlik gereksinimlerini karşılaması gerekir. MFA ilkeleri, tıpkı kendi kuruluşunuzun üyeleri için etkinleştirildiği şekilde, kiracı, uygulama veya bireysel konuk kullanıcı düzeyinde uygulanabilir. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>MFA ilke Visual Studio deneyim nasıl etkileniyor?
16.6'dan önceki Visual Studio sürümleri, MFA gibi CA ilkelerini etkinleştirmiş ve iki veya daha fazla kiracıyla ilişkili hesaplarla birlikte kullanılırken, kimlik doğrulaması deneyimleri düşürülmüş olabilir.

Bu sorunlar, örnek örneğinizin Visual Studio kez yeniden kimlik doğrulamayı istemine neden olabilir. Daha önce kimliği doğrulanmış kiracılar için aynı oturum sırasında bile kimlik bilgilerinizi yeniden girmeniz Visual Studio olabilir.

## <a name="using-visual-studio-with-mfa-policies"></a>MFA Visual Studio ile uygulama kullanma
16.6 yayında, Visual Studio 2019'a kullanıcıların MFA gibi CA ilkeleriyle güvenli kaynaklara erişmelerini kolaylaştıran yeni özellikler ekledik. Bu gelişmiş iş akışını kullanmak için, hesap ekleme ve yeniden kimlik doğrulama mekanizması olarak sisteminizin varsayılan web tarayıcısını Visual Studio gerekir.  

> [!WARNING]
> Bu iş akışının kullanılamama durumu düzeyi düşürülmüş bir deneyim tetikleyerek hesap ekleme veya yeniden kimlik doğrulama Visual Studio olabilir. 

### <a name="enabling-system-web-browser"></a>Sistem web tarayıcısını etkinleştirme

> [!NOTE] 
> En iyi deneyim için, bu iş akışına devam etmeden önce sistem varsayılan web tarayıcısı verilerini temizlemenizi öneririz. Ayrıca, çalışma alanınıza İş veya Okul hesaplarınız Windows 10 Ayarlar veya okula erişim altında **varsa,** bunların doğrulanmış olduğunu doğrulayın.

Bu iş akışını etkinleştirmek için Visual Studio'nin Seçenekler iletişim kutusuna **(Araçlar > Seçenekler...)** gidin, Hesaplar sekmesini seçin ve Şu komutu kullanarak hesap ekle ve yeniden kimlik doğrulama altında Sistem  **web** tarayıcısını **seçin:** açılır listesinde. 

:::image type="content" source="media/vs-2022/select-system-web-browser.png" alt-text="Menüden sistem web tarayıcısı'ı seçin.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>MFA ilkeleriyle ek hesaplarda oturum açma 
Sistem web tarayıcısı iş akışı etkinleştirildikten sonra, Hesap Ayarlar iletişim kutusu (Dosya > Hesabı Ayarlar...) aracılığıyla normalde olduğu gibi Visual Studio'de **oturum açabilirsiniz veya Ayarlar.**   
</br>
:::image type="content" source="media/vs-2022/add-personalization-account.png" alt-text="Visual Studio'a yeni bir kişiselleştirme hesabı Visual Studio." border="false":::

Bu eylem, sisteminizin varsayılan web tarayıcısını açar, hesapta oturum açmanızı ve gerekli MFA ilkelerini doğrulamanızı sorar.

Oturum açma işlemi sırasında oturum açık kalmanız istendiğinde ek bir istem alırsınız. Bu istem büyük olasılıkla bir hesabın oturum açması için ikinci kez kullanılırken ortaya çıktı. Kimlik bilgilerinizi yeniden girme ihtiyacı en aza indirmek için Evet'i seçmeniz önerilir **çünkü** bu, kimlik bilgilerinizin tarayıcı oturumlarında korunmasını sağlar.

:::image type="content" source="media/vs-2022/keep-me-signed-in.png" alt-text="Oturum mu alasınız?":::

Geliştirme etkinliklerinize ve kaynak yapılandırmanıza bağlı olarak, oturum sırasında kimlik bilgilerinizi yeniden girmeniz istenebilirsiniz. Bu durum, yeni bir kaynak eklerken veya daha önce CA/MFA yetkilendirme gereksinimlerini karşılamadan kaynağa erişmeyi deneyebilirsiniz.

## <a name="reauthenticating-an-account"></a>Hesabı yeniden kimlik doğrulaması
Hesabınızla ilgili bir sorun varsa Visual Studio kimlik bilgilerinizi yeniden girmenizi isteyebilirsiniz.  

:::image type="content" source="media/vs-2022/reauthenticate-account.png" alt-text="Hesap hesaplarınızı yeniden Visual Studio olun.":::

Kimlik bilgilerinizi **yeniden girin'e tıklarsanız,** sistemin varsayılan web tarayıcısı açılır ve kimlik bilgilerinizi otomatik olarak yenilemeye çalışırsınız. Başarısız olursa, hesabınızla oturum açmanız ve gerekli CA/MFA ilkelerini doğrulamanız istener.

> [!NOTE] 
> En iyi deneyim için, kaynaklarınız için tüm CA/MFA ilkeleri doğrulandıktan sonra tarayıcınızı açık tutabilirsiniz. Tarayıcının kapatılması, önceden yerleşik MFA durumunun kaybetmesi ile sonuçlansa da ek yetkilendirme istemleri istendiğinde ortaya çıktı.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Visual Studio'de belirli bir Azure Active Directory kiracı kullanmayı Visual Studio

Visual Studio 2019 sürüm 16.6 ve üzeri, kiracıları tek tek veya genel olarak filtreleme esnekliğini sunar ve kiracıları kiracılardan etkili bir şekilde Visual Studio. Filtreleme, bu kiracıda kimlik doğrulaması yapma ihtiyacının ortadan kaldırılmasına ek olarak ilişkili kaynaklara erişilamay anlamına gelir.

Bu işlevsellik, birden çok kiracınız olduğunda ama belirli bir alt kümeyi hedefleerek geliştirme ortamınızı iyileştirmek istediğiniz zaman kullanışlıdır. Ayrıca, belirli bir CA/MFA ilkesi doğrulanamadık durumlarda da yardımcı olabilir çünkü rahatsız olan kiracıyı filtreleyesiniz. 

### <a name="how-to-filter-out-all-tenants"></a>Tüm kiracıları filtreleme
Tüm kiracıları genel olarak filtrelemek için Hesap Ayarlar iletişim kutusunu (Dosya > Hesabı **Ayarlar... >** Hesabı seçenekleri) açın ve Tüm Azure **Etkin** Dizinlerde Kimlik Doğrula onay kutusunun seçimini kaldırın.

Bu seçeneğin işaretini kaldırmak, yalnızca hesabın varsayılan kiracısı ile kimlik doğrulamasını sağlar. Ayrıca, hesabınız konuk olabileceği diğer kiracılarla ilişkilendirilmiş kaynaklara erişe anlamına gelir.

### <a name="how-to-filter-out-individual-tenants"></a>Tek tek kiracıları filtreleme
Visual Studio hesabınızla ilişkili kiracıları filtrelemek için Hesap Ayarlar iletişim kutusunu **(Dosya > Hesabı Ayarlar...) açın** ve Filtre **uygula'ya tıklayın.** 
</br>
</br>

:::image type="content" source="media/vs-2022/apply-filter.png" alt-text="Filtre uygulama." border="false":::

**Hesabınızla** kullanmak istediğiniz kiracıları seçmenize olanak sağlayan Hesap filtre iletişim kutusu görüntülenir. 

:::image type="content" source="media/vs-2022/select-filter-account.png" alt-text="Filtre için hesap seçin.":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'de oturum açma](signing-in-to-visual-studio.md)
- [Mac için Visual Studio'de oturum açma](/visualstudio/mac/signing-in)
- [Birden çok kullanıcı hesabıyla çalışma](work-with-multiple-user-accounts.md)
