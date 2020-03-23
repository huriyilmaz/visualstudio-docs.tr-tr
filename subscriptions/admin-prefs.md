---
title: Yönetim Portalında anlaşma tercihlerini ayarlama
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 03/17/2020
ms.topic: conceptual
description: İdare Portalı'ndaki dil, kişiler, abonelik düzeyi ve diğerleri için tercihleri nasıl ayarlayabilirsiniz öğrenin
ms.openlocfilehash: cbcf532620e958ca408d43295d2d4200d12ee0cd
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "79508764"
---
# <a name="set-preferences-for-your-agreements-in-the-administration-portal"></a>İdare Portalı'ndaki anlaşmalarınız için tercihleri ayarlayın
Süper yöneticiler, her anlaşma için küresel olarak uygulanacak Yönetim Portalı'nda (yönetici portalı) belirli tercihler belirleyebilirler.  Bu tercihler, yöneticilerinizin abone eklerken abonelik ayrıntılarını otomatik olarak doldurur ve yalnızca süper yöneticiler tarafından genel olarak değiştirilebilir.  

## <a name="access-preferences"></a>Erişim tercihleri
Tercihleri görüntülemek veya değiştirmek için anlaşmaüzerinde süper yönetici haklarına sahip bir oturum kimliği kullanarak [yönetici portalında](https://manage.visualstudio.com) oturum açmanız gerekir.  

Tercihlerinizi ayarlamak için:
1. Süper yönetici ayrıcalıklarına sahip bir kimlikle yönetici portalında oturum açın.
2. **Yöneticileri Yönet** sekmesine tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Yönetici Tercihleri düğmesi](_img/admin-prefs/admin-prefs-button.png)

3. **Anlaşma Tercihleri'ni**tıklatın.
Sağ tarafta bir panel açılacak ve mevcut tercihleriniz görüntülenecektir. 

   > [!div class="mx-imgBorder"]
   > ![Yönetici Tercihleri flyout iletişim kutusu](_img/admin-prefs/admin-prefs-flyout.png)

## <a name="set-your-preferences"></a>Tercihlerinizi ayarlama
Mevcut tercihlerin her birini ve etkilerini inceleyelim. 

### <a name="agreement"></a>Anlaşma
Süper yönetici olduğunuz birden fazla anlaşmanız varsa, açılan yolda istediğiniz anlaşmayı seçebilirsiniz.  Belirlediğiniz tercihler yalnızca bu anlaşma için geçerli olacaktır.  Tek tek yöneticiler, abonelik atarken bu tercihlerin bazılarını ayrı ayrı geçersiz kılabilir. 

Oturum açmanız için kullandığınız e-posta adresiyle ilişkili yalnızca bir anlaşma varsa, bu anlaşma görüntülenir ve açılır açılır durum devre dışı bırakılır. 

### <a name="contact-email-address"></a>İletişim e-posta adresi
Bu tercih, abonelerinizin abone portalının [abonelikler sayfasındaki](https://my.visualstudio.com/subscriptions) **Yöneticimle İletişim** düğmesini kullanarak yöneticilere ulaşmasını sağlar.  Bu tercih boş bırakılırsa, abone iletileri anlaşmadaki tüm yöneticilere ve süper yöneticilere iletilir.  Hedef kitlenizi bu kişi e-postasına uyarlamak için bir grup e-posta takma adı veya güvenlik grubu kullanmanızı öneririz. İsterseniz bir kişinin e-posta adresini de girin.

> [!NOTE]
> Burada listelediğiniz e-posta adresi abonelere VERILmeyecektir.  Bir abone, abone portalında **Yöneticimle İletişim** isteği gönderdiğinde, ileti aboneye ifşa edilmeden takma ada iletilir. 

### <a name="default-external-subscribers-setting"></a>Varsayılan harici abone ayarı
Bu tercih, yöneticilerin kuruluşunuzun kiracı/dizin dışından abone ekleyip eklemeyeceğine karar vermenize olanak tanır.  Bunu kapatırsanız, dışarıdan aboneye izin verilmeyen.  Bunu etkinleştirirken ve bir yönetici dışarıdan bir abone eklemeye çalışırsa, kendi lerinden seçimlerini onaylamaları istenir ve aboneliği atamalarına izin verilir. Yöneticiler bu ayarı geçersiz kılamaz. 

### <a name="default-downloads-setting"></a>Varsayılan indirme ayarı
Varsayılan olarak geçerli olan bu ayarı etkinleştirmek, yöneticiler yeni abonelikler oluşturduğunda abonelerin indirmelere erişmesini sağlar.  Yöneticiler, tek bir abonelik bazında indirmeleri devre dışı bırakabilir.  

### <a name="default-subscription-level"></a>Varsayılan abonelik düzeyi
Bu ayarı, bir abonelik kullanıcıya atandığında varsayılan olarak sözleşmenizde yer alan abonelik düzeylerinden hangilerinin seçili olduğunu belirlemek için kullanabilirsiniz.  Yöneticiler ayarı sözleşmenizdeki herhangi bir abonelik düzeyiyle değiştirebilir -- Bu, en yaygın seçiminizi tekrar tekrar yapmak zorunda kalmanızı önler. 

### <a name="default-communication-preferences"></a>Varsayılan iletişim tercihleri
Varsayılan iletişim dili ve yerel ayar, abonelik atama işlemini kolaylaştırabilir.  Örneğin, geliştirme ekibiniz yönetici ekibinizden farklı bir ülkede dayanıyorsa, abonelerin konumuna en uygun tercihleri ayarlayabilirsiniz. Bu ayarlar, bireysel aboneler için tüm yöneticiler tarafından değiştirilebilir. 

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-administrators"></a>S: Abonelerin yöneticilerle iletişim kuramamasından sonra **İlgili Kişi e-posta adresini** devre dışı edebilir miyim?
C: Hayır - bir güvenlik grubu, grup e-posta takma adı veya tek bir e-posta adresi kullanarak hangi yöneticilerle iletişime geçileceğini belirleyebilirken, özellik devre dışı tutulamaz.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>S: Bir abonenin e-postaadresine cevap verirsem, e-posta adresim onlarda olacak mı?
C: Yanıtınız kullandığınız e-posta istemcisinden geldiğinden, abonenin aldığı yanıt kullandığınız e-posta adresini gösterir.  Bu nedenle, bir grup diğer adını yanıtlarsanız, grup takma adını görürler.  Kendi e-posta adresinizden yanıt verirseniz, bunu görürler.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>S: Abone portalındaki **Yöneticimle İletişim** özelliği hakkında daha fazla bilgi nereden bulabilirim?
C: İletişim [yönetici makalemize](contact-my-admin.md) göz atın. 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>S: **İletişim e-posta adresini** tamamlamazsak ve bir abone **Yöneticimle İletişim** özelliğini kullanırsa, isteklerini kim alır?
C: **İletişim e-posta adresi** tercihinde belirli bir e-posta adresi belirlenmezse, anlaşmadaki tüm yöneticiler isteği alır. 

## <a name="resources"></a>Kaynaklar
- [Visual Studio Yönetim ve Abonelik Desteği](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Visual Studio aboneliklerini yönetme hakkında daha fazla bilgi edinin.
- [Tek tek abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Maksimum kullanımı belirleme](maximum-usage.md)



