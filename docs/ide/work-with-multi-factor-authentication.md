---
title: Çok faktörlü kimlik doğrulaması gerektiren hesapları kullanma
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Çok faktörlü kimlik doğrulaması Visual Studio hesaplarıyla bu kimlik doğrulamasını kullanmayı öğrenin.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 2788894a98dd0433fcc191a37665dd1df0333c3e
ms.sourcegitcommit: 022ac348337f77c899996ac81060a969ebfb64bb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2021
ms.locfileid: "128133815"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Çok faktörlü Visual Studio kimlik doğrulaması gerektiren hesaplarla kimlik doğrulamasını kullanma

Dış konuk kullanıcılarla işbirliği yapmak için, uygulamalarınızı ve verilerinizi çok faktörlü kimlik doğrulaması **(MFA)** gibi koşullu erişim (CA) ilkeleriyle korumak iyi bir **fikirdir.**  

Etkinleştirildikten sonra konuk kullanıcıların kaynaklarınıza erişmek için bir kullanıcı adı ve paroladan fazlası gerekir ve ek güvenlik gereksinimlerini karşılaması gerekir. MFA ilkeleri, tıpkı kendi kuruluşunuzun üyeleri için etkinleştirildiği şekilde, kiracı, uygulama veya bireysel konuk kullanıcı düzeyinde uygulanabilir. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>MFA Visual Studio deneyim nasıl etkileniyor?
16.6'dan önceki Visual Studio sürümlerinin, MFA gibi CA ilkelerini etkinleştirmiş ve iki veya daha fazla kiracıyla ilişkili hesaplarla birlikte kullanılırken kimlik doğrulaması deneyimleri düşürülmüş olabilir.

Bu sorunlar, örnek örneğinizin Visual Studio kez yeniden kimlik doğrulamayı istemine neden olabilir. Aynı oturum sırasında bile önceden kimliği doğrulanmış kiracılar için kimlik bilgilerinizi yeniden girmeniz Visual Studio olabilir.

## <a name="using-visual-studio-with-mfa-policies"></a>MFA Visual Studio ile uygulama kullanma
16.6 yayında, Visual Studio 2019'a kullanıcıların MFA gibi CA ilkeleriyle güvenli kaynaklara erişmelerini kolaylaştıran yeni özellikler ekledik. Bu gelişmiş iş akışını kullanmak için, hesap ekleme ve yeniden kimlik doğrulama mekanizması olarak sisteminizin varsayılan web tarayıcısını Visual Studio gerekir.  

> [!WARNING]
> Bu iş akışının kullanılamama durumu düzeyi düşürülmüş bir deneyim tetikleyerek hesap ekleme veya yeniden kimlik doğrulama Visual Studio olabilir. 

### <a name="enabling-system-web-browser"></a>Sistem web tarayıcısını etkinleştirme

> [!NOTE] 
> En iyi deneyim için, bu iş akışına devam etmeden önce sistem varsayılan web tarayıcısı verilerini temizlemenizi öneririz. Buna ek olarak, çalışma alanınıza İş veya okul Windows 10 Ayarlar erişim altında İş veya Okul hesaplarınız **varsa,** bunların doğrulanmış olduğunu doğrulayın.

Bu iş akışını etkinleştirmek için Visual Studio'nin Seçenekler iletişim kutusuna **(Araçlar > Seçenekler...)** gidin, Hesaplar sekmesini seçin ve Şu komutu kullanarak hesap ekle ve yeniden kimlik doğrulama altında Sistem  **web** tarayıcısını **seçin:** açılır listesinde. 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Menüden sistem web tarayıcısı'ı seçin.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>MFA ilkeleriyle ek hesaplarda oturum açma 
Sistem web tarayıcısı iş akışı etkinleştirildikten sonra, Hesap Ayarlar iletişim kutusu (Dosya > Hesabı Ayarlar...) aracılığıyla normalde olduğu gibi Visual Studio'da oturum **açabilirsiniz veya Ayarlar.**   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Visual Studio'a yeni bir kişiselleştirme hesabı Visual Studio." border="false":::

Bu eylem, sisteminizin varsayılan web tarayıcısını açar, hesapta oturum açmanızı ve gerekli MFA ilkelerini doğrulamanızı sorar.

Oturum açma işlemi sırasında oturum açık kalmanız istendiğinde ek bir istem alırsınız. Bu istem büyük olasılıkla bir hesabın oturum açması için ikinci kez kullanılırken ortaya çıktı. Kimlik bilgilerinizi yeniden girme ihtiyacı en aza indirmek için Evet'i seçmeniz önerilir **çünkü** bu, kimlik bilgilerinizin tarayıcı oturumlarında korunmasını sağlar.

:::image type="content" source="media/kmsi.png" alt-text="Oturum mu alasınız?":::

Geliştirme etkinliklerinize ve kaynak yapılandırmanıza bağlı olarak, oturum sırasında kimlik bilgilerinizi yeniden girmeniz istenebilirsiniz. Bu durum, yeni bir kaynak eklerken veya daha önce CA/MFA yetkilendirme gereksinimlerini karşılamadan kaynağa erişmeyi deneyebilirsiniz.

## <a name="reauthenticating-an-account"></a>Hesabı yeniden kimlik doğrulaması  
Hesabınızla ilgili bir sorun varsa Visual Studio kimlik bilgilerinizi yeniden girmenizi istemeniz gerekir.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Hesap hesaplarınızı yeniden Visual Studio olun.":::

Kimlik bilgilerinizi **yeniden girin'e tıklarsanız,** sistemin varsayılan web tarayıcısı açılır ve kimlik bilgilerinizi otomatik olarak yenilemeye çalışırsınız. Başarısız olursa, hesabınızla oturum açmanız ve gerekli CA/MFA ilkelerini doğrulamanız istener.

> [!NOTE] 
> En iyi deneyim için, kaynaklarınız için tüm CA/MFA ilkeleri doğrulandıktan sonra tarayıcınızı açık tutabilirsiniz. Tarayıcının kapatılması, önceden yerleşik MFA durumunun kaybetmesi ile sonuçlansa da ek yetkilendirme istemleri istemleri istendiğinde ortaya çıktı.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Visual Studio'de belirli bir Azure Active Directory kullanmayı Visual Studio

Visual Studio 2019 sürüm 16.6, kiracıları tek tek veya küresel olarak filtreleme esnekliğini, kiracılardan etkili bir şekilde gizleme Visual Studio. Filtreleme, bu kiracıda kimlik doğrulaması yapma ihtiyacının ortadan kaldırılmasına ek olarak ilişkili kaynaklara erişilamay anlamına gelir.

Bu işlev, birden çok kiracınız olduğunda ama belirli bir alt kümeyi hedefleerek geliştirme ortamınızı iyileştirmek istediğiniz zaman kullanışlıdır. Ayrıca, belirli bir CA/MFA ilkesi doğrulanamadık durumlarda da yardımcı olabilir çünkü rahatsız olan kiracıyı filtreleyesiniz. 

### <a name="how-to-filter-out-all-tenants"></a>Tüm kiracıları filtreleme
Tüm kiracıları genel olarak filtrelemek için Hesap Ayarlar iletişim kutusunu (Dosya > Hesabı **Ayarlar...) açın** ve Tüm Azure **Etkin** Dizinler Arasında Kimlik Doğrulaması onay kutusunun seçimini kaldırın.

Bu seçeneğin işaretini kaldırmak, yalnızca hesabın varsayılan kiracısı ile kimlik doğrulamasını sağlar. Ayrıca, hesabınız konuk olabileceği diğer kiracılarla ilişkilendirilmiş kaynaklara erişe anlamına gelir.

### <a name="how-to-filter-out-individual-tenants"></a>Tek tek kiracıları filtreleme
Visual Studio hesabınızla ilişkili kiracıları filtrelemek için Hesap Ayarlar iletişim kutusunu **(Dosya > Hesabı Ayarlar...) açın** ve Filtre **uygula'ya tıklayın.** 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Filtre uygulama." border="false":::

**Hesabınızla** kullanmak istediğiniz kiracıları seçmenize olanak sağlayan Hesap filtrele iletişim kutusu görüntülenir. 

:::image type="content" source="media/select-filter-account.png" alt-text="Filtre için hesap seçin.":::

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio’da oturum açma](signing-in-to-visual-studio.md)
- [Mac için Visual Studio'da oturum açma](/visualstudio/mac/signing-in)
- [Birden çok kullanıcı hesabıyla çalışma](work-with-multiple-user-accounts.md)
