---
title: Abonelikler yönetici Visual Studio tercihleri ayarlama
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 0fe9eaa4-f589-429e-a443-13bf86637d5a
ms.date: 05/18/2021
ms.topic: conceptual
description: Yönetim Portalı'nın dil, kişiler, abonelik düzeyi ve diğer dil tercihlerini ayarlamayı öğrenin
ms.openlocfilehash: 09ab16b077ac92fccc2f939a36a31136b11e7e1b
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128429001"
---
# <a name="set-preferences-for-your-agreements-in-the-admin-portal"></a>Yönetim portalında sözleşmeleriniz için tercihleri ayarlama
Süper yöneticiler, Yönetim Portalı'nın (yönetim portalı) her sözleşme için genel olarak uygulanacak belirli tercihlerini ayarlayabilecek.  Bu tercihler, abone eklerken yöneticileriniz için abonelik ayrıntılarını otomatik olarak doldurmakta ve yalnızca süper yöneticiler tarafından genel olarak değiştirilebilir.  

## <a name="access-preferences"></a>Erişim tercihleri
Tercihleri görüntülemek veya değiştirmek [için sözleşmede](https://manage.visualstudio.com) süper yönetici haklarına sahip bir oturum açma kimliği kullanarak yönetici portalında oturum açmanız gerekir.  

Tercihlerinizi ayarlamak için:
1. Süper yönetici ayrıcalıklarına sahip bir kimlikle yönetici portalında oturum açın.
2. Sol bölmede ayar simgesine tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Yönetici Tercihleri düğmesi](_img/admin-preferences/admin-preferences-button.png "Tercihleri görüntülemek için Yöneticileri Yönet'e ve ardından Sözleşme Tercihleri'ne tıklayın")

3. Sözleşme **Tercihleri'ne tıklayın.**
Sol tarafta bir panel açılır ve kullanılabilir tercihleriniz görüntülenir. 

   > [!div class="mx-imgBorder"]
   > ![Yönetici Tercihleri iletişim kutusu](_img/admin-preferences/admin-preferences-flyout-2.png "Tercihlerinizi ayarlayın ve Kaydet'e tıklayın")

## <a name="set-your-preferences"></a>Tercihlerinizi ayarlama
Şimdi kullanılabilir tercihlerin her birini ve etkilerini keşfederiz. 

### <a name="agreement"></a>Sözleşme
Süper yönetici olarak birden fazla sözleşmeniz varsa, genişletilmiş ayarlar panelinin sağ üst açılan menüsünden istediğiniz sözleşmeyi seçebilirsiniz.  Ayar aşağıdaki tercihler yalnızca bu sözleşme için geçerlidir.  Bireysel yöneticiler, abonelikleri atarken bu tercihlerden bazılarını büyük/küçük harf temelinde geçersiz kabilirsiniz. 

Oturum a0 için kullanılan e-posta adresiyle ilişkilendirilmiş yalnızca bir sözleşme varsa, genişletilmiş ayarlar panelinin sağ tarafından görüntülenir ve açılan liste devre dışı bırakılır. 

### <a name="contact-email-address"></a>İletişim e-posta adresi
Bu tercih, abone portalının abonelikler sayfasındaki Yöneticime Başvur  düğmesini kullanarak aboneleriniz için yöneticilere [ulaşmanın](https://my.visualstudio.com/subscriptions) bir yolunu sağlar.  Bu tercih boş bırakılırsa, abone iletileri sözleşmede tüm yöneticilere ve süper yöneticilere ilettir.  Hedef kitlenizi bu iletişim e-postası için uyarlamak için bir grup e-posta diğer adı veya güvenlik grubu kullanılması önerilir. Ayrıca isterseniz bir kişinin e-posta adresini de girebilirsiniz.

> [!NOTE]
> Burada listeleyseniz e-posta adresi abonelere SAĞLANMAZ.  Bir abone, abone  portalında Yöneticime Başvur isteği göndererek, ileti aboneye ifşa etmeden diğer ada iletiliyor. 

### <a name="default-subscription-level"></a>Varsayılan abonelik düzeyi
Bir kullanıcıya abonelik atandığı zaman, sözleşmenize dahil olan abonelik düzeylerden hangilerinin varsayılan olarak seçileceklerini belirlemek için bu ayarı kullanabilirsiniz.  Yöneticiler bu ayarı sözleşmenizin herhangi bir abonelik düzeyiyle değiştirebilir. Bu, en yaygın seçiminizi tekrar tekrar yapmak zorunda kalmanızı önler. 

### <a name="default-communication-preferences"></a>Varsayılan iletişim tercihleri
Varsayılan iletişim dilini ve yerel ayarı, abonelik atama sürecini kolaylaştırabilirsiniz.  Örneğin, geliştirme takımınız yönetim takımınıza göre farklı bir ülkede yer aldısa, abonelerin konumu için en uygun tercihleri seçebilirsiniz. Bu ayarlar yine de tek tek aboneler için tüm yöneticiler tarafından değiştirilebilir. 

### <a name="default-external-subscribers-setting"></a>Varsayılan dış aboneler ayarı
Bu tercih, yöneticilerin, kuruluşun kiracısı/dizini dışından abone ekp ekley olup olmadığını karar vermenizi sağlar.  Bunu kapatıyorsanız, dış abonelere izin verilmez.  Bunu etkinleştirirseniz ve bir yönetici dış abone eklemeye çalışırsa, tercihlerini onaylaması ve aboneliği atamasına izin verilir. Yöneticiler bu ayarı geçersiz kamaz. 

### <a name="default-downloads-setting"></a>Varsayılan indirmeler ayarı
Varsayılan olarak etkin olan bu ayarın etkinleştirilmesi, yöneticiler yeni abonelikler oluşturdukları zaman abonelerin indirmelere erişmesini sağlar.  Yöneticiler, indirmeleri tek tek abonelik temelinde devre dışı bırakabilirsiniz.  İndirmelere erişimi devre dışı bırakmak ürün anahtarlarına erişimi de devre dışı bıraktır.  

### <a name="overallocation-notification"></a>Fazla konum bildirimi 
Sözleşmenize yapılan atamalar fazla yüklenmiş olduğunda e-posta almayı kabul edin. Bu e-posta bildirimi kişi e-posta adresine veya İletişim [e-posta](admin-preferences.md#contact-email-address)adresi yoksa sözleşmenizin tüm yöneticilerine gönderilir. Size bildirilecek eşiği yapılandırmak için açılan menüyü kullanın. 

 
## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q--can-i-disable-the-contact-email-address-so-subscribers-cannot-contact-admins"></a>S: Abonelerin yöneticilerle iletişim **kuramalarını etkinleştirmek için Kişi** e-posta adresini devre dışı bırakamaz musunuz?
A: Hayır- Bir güvenlik grubu, grup e-posta diğer adı veya tek bir e-posta adresi kullanılarak hangi yöneticilerle iletişim kurılacaklarını belirleyeseniz de özellik devre dışı bırakılamaz.

### <a name="q-if-i-answer-a-subscribers-email-will-they-have-my-email-address"></a>S: Abonenin e-postasına yanıt ve ardından e-posta adresimi alır musunuz?
A: Yanıtınız, kullanmakta olduğunuz e-posta istemcilerinden gelecektir. Abonenin aldığı yanıt, kullanmakta olduğunuz e-posta adresini gösterir.  Bu nedenle, bir grup diğer adıyla yanıt veriyorsanız grup diğer adını görebilirler.  Kendi e-posta adresinizden yanıt verirsiniz, bunu görebilirler.  

### <a name="q-where-can-i-find-out-more-about-the-contact-my-admin-feature-in-the-subscriber-portal"></a>S: Abone portalında Yöneticime **Başvur özelliği hakkında daha** fazla bilgi nereden edinebilirsiniz?
C: Yöneticime başvur [makalemize göz](contact-my-admin.md) atabilirsiniz. 

### <a name="q-if-we-dont-complete-the-contact-email-address-and-a-subscriber-uses-the-contact-my-admin-feature-who-receives-their-request"></a>S: kişi e-posta adresini tamamlamazsanız **ve** abone Yöneticime Başvur özelliğini **kullanırsa,** isteğini kim alır?
A: İletişim e-posta adresi tercihi'ne belirli bir **e-posta** adresi ayarlanmayacaksa, sözleşmede yer alan tüm yöneticiler isteği alır. 

## <a name="resources"></a>Kaynaklar
- [Visual Studio yönetim ve abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Abonelikleri yönetme hakkında daha fazla Visual Studio edinin.
- [Bireysel abonelikleri atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)