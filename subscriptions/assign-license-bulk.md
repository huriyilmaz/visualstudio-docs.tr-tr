---
title: Abonelikler için kullanıcı gruplarına lisans Visual Studio atama | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/21/2021
ms.topic: how-to
description: Yöneticilerin Toplu ekleme özelliğini veya Microsoft Azure Active Directory gruplarını kullanarak birden çok aboneye nasıl lisans Microsoft Azure Active Directory öğrenin
ms.openlocfilehash: 8b12103aa06cb6a5161ba92ee79d7b5d30c3211598dcf6598a6c4b62559a13ee
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121364721"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Birden çok kullanıcıya abonelik atama
Abonelikler Yönetim Portalı, kullanıcıları tek tek veya büyük gruplara eklemenize olanak sağlar.  Tek tek kullanıcıları eklemek için [bkz. Tek kullanıcı ekleme.](assign-license.md)

Büyük kullanıcı grupları eklemek için toplu ekleme özelliğini kullanabilir veya Microsoft Azure Active Directory (Azure AD) kullanıyorsa Azure AD gruplarını kullanabilirsiniz. Bu makalede her iki seçenek için de süreç açıklanmıştır.  Toplu ekleme özelliği hakkında daha fazla bilgi edinmek için bu videoyu izleyin veya okumaya devam okuyun. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Abonelikleri atamak için Toplu ekleme'yi kullanma
1. sayfasından Visual Studio Abonelikler Yönetim Portalı'nda oturum <https://manage.visualstudio.com> açın.

1. Aynı anda birden çok abone eklemek için Aboneleri Yönet **sekmesine** gidin. Ekle **sekmesini** ve ardından açılır **listelerde Toplu** ekle'yi seçin.  

1. Toplu ekleme, abone bilgilerini Microsoft Excel bir şablon kullanır. Birden Upload Abone ekle iletişim kutusunda İndir'i **seçerek** şablonu indirin.
   > [!div class="mx-imgBorder"]
   > ![Birden çok Excel karşıya yüklemek için uygulama şablonunu indirin](media/download-template-upload-subscribers.png "Toplu atama Excel için boş kaynak şablonunu indirin.")
   >
   > [!NOTE]
   > Bu şablonun her zaman en son sürümünü indirin. Daha eski bir sürüm kullanıyorsanız toplu karşıya yükleme başarısız olabilir.

1. Excel elektronik tabloda, alanları abonelik atamak istediğiniz kişilere ilişkin bilgilerle doldurun. (*Başvuru isteğe* bağlı bir alandır.) Bitirdikten sonra dosyayı yerel olarak kaydedin.

    > [!NOTE]
    > Şablonda yer alan alanlardan biri, yöneticilerin abonelerin yazılım indirme özelliğini etkinleştirmesini veya devre dışı bırakmasını sağlar.  İndirmeleri devre dışı bırakmak, ürün anahtarlarına erişimini de devre dışı bırakmanızı sağlar.

   Karşıya yüklemenin sorunsuz bir şekilde gerçekleştirilene yardımcı olması için aşağıdaki en iyi yöntemleri gözlemlemek gerekir:

    - Form alanlarından hiçbirinin virgül içermediğinden emin olun.
    - Form alanlarının önündeki ve sonundaki boşlukları kaldırın.
    - Kullanıcı adlarının iki bölümden ilk veya son adlar arasında fazladan boşluk içermey olduğundan emin olun (örneğin, bir kişinin "Maggie May" gibi iki parçalı bir adı varsa, sistem fazladan alanı kırpmayyacak olduğundan bu ad "MaggieMay" olarak yaz gelli.)
    - Tüm gerekli alanların tamamlandığından emin olun. 
    - Hata iletisi **sütununu** kontrol edin.  Herhangi bir hata listelenirse, dosyayı karşıya yüklemeden önce bu hataları düzeltin. 

1. Visual Studio Abonelikler Yönetim portalına geri gidin. Birden çok **Upload Iletişim kutusunda** Gözat'ı **seçin.**
   > [!div class="mx-imgBorder"]
   > ![Birden çok aboneyi karşıya yüklemek için kayıtlı şablonunuza göz atma](media/bulk-add-browse-saved-template.png "Dosya konuma göz atabilir veya sürükleyip bu iletişim kutusuna ebilirsiniz.")

1. Kendi Excel dosyanın üzerine gidin ve Tamam'ı **seçin.**
   > [!div class="mx-imgBorder"]
   > ![Upload abone Excel için şablon oluşturma](media/bulk-upload-subscribers.png "Verilerinizin yer alan şablonu burada görünür.  Karşıya yüklemeye başlamak için Tamam'ı seçin.")

    Karşıya yükleme ilerleme durumu iletişim kutusu görüntülenir.

    Şablon hata içeriyorsa, karşıya yükleme başarısız olur ve şablonu düzeltin ve toplu karşıya yüklemeyi yeniden denemeniz için hatalar gösterilir.
   > [!div class="mx-imgBorder"]
   > ![Birden çok abonenin karşıya yüklemesi başarısız olursa hata iletisi](_img/assign-license-bulk/bulk-add-upload-failure.png "Karşıya yüklediğiniz dosyada hatalar varsa bu ileti görüntülenir.  Hataları giderin ve Toplu ekleme işlemini yeniden gerçekleştirin.")

   Hatayla karşılaşırsanız şu adımları izleyin:
   1. Oluşturduğunuz Excel dosyasını açın, sorunları düzeltin ve dosyayı kaydedin.
   0. Yönetim Portalı'ne geri dönüp hata iletisini açın.
   0. **Ekle'yi seçin.**
   0. Toplu **ekle'yi seçin.**
   0. Excel dosyası zaten kayıtlı olduğu için şablonu indirmeniz gerek değildir.  **Gözat'ı** seçin, yeni kaydedilen dosyayı bulun ve Aç'ı **seçin.**
   0. **Tamam**’ı seçin.


    Karşıya yükleme başarılı olduğunda abonelerin listesini ve bir onay iletisi görüntülenir.
   > [!div class="mx-imgBorder"]
   > ![Birden çok abonenin karşıya yüklemesi başarılı olursa onay iletisi](_img/assign-license-bulk/bulk-add-upload-success.png "Karşıya yükleme işleminiz başarıyla tamamlandığında bir onay iletisi alırsınız.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Abonelik Azure Active Directory grupları kullanma 
Bu özelliğin kullanımı, abonelik atamalarınızı takip etmenizi kolaylaştırır. Abonelikler Azure Active Directory gruplarında bulunan tüm kişilere bir abonelik atanması için Abonelikler Yönetim Portalı'nda güvenlik grupları eklemeniz gerekir. Bunu kolaylaştırmak için, kişiler kuruluştan ayrılarak kuruluştan Azure Active Directory aboneliklere erişimi de kaldırılır. 


> [!IMPORTANT]
>
> Abone eklemek için Azure AD gruplarının kullanımı için aşağıdaki sınırlamalar geçerlidir:
> - Yönetici portalına başlangıçta bir grup eklerken yöneticinin AAD kiracısına üye olması gerekir.  Grup eklendikten sonra, grupların üyeliğinde yapılan değişiklikler yönetici katılımı gerektirmez. 
> - Gruplar en az bir üye içermeli.  Boş gruplar desteklenmiyor.
> - Tüm kullanıcıların grubun en üst düzeyinde olması gerekir.  İç içe gruplar desteklenmiyor.
> - Yalnızca güvenilen sözleşmeler de destekler. (Yalnızca abonelikleri 'fazla alan' olarak kabul eden sözleşmelere güvenebilirsiniz.)
> - Grubun tüm üyelerinin Azure AD hesabıyla ilişkilendirilmiş bir e-posta adresi olması gerekir.
> - Bildirimler için ayrı e-posta adresleri, Azure AD grupları kullanılarak eklenen abonelikler için desteklanmaz.  

Yeni grup özelliğini kullanarak abone ekleme hakkında daha fazla bilgi edinmek için bu videoyu izleyin Azure Active Directory okuyun. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Visual Studio Abonelikler Yönetim Portalı'nda oturum [https://manage.visualstudio.com](https://manage.visualstudio.com) açın.

2. Aynı anda birden çok abone eklemek için Aboneleri yönet **sekmesine** gidin.

3. Ekle **sekmesini** ve ardından açılan **Azure Active Directory** Grup'a tıklayın.  

   > [!div class="mx-imgBorder"]
   > ![Azure AD kullanarak toplu ekleme seçme](_img/assign-license-bulk/bulk-add-aad.png "Azure AD kullanarak toplu ekleme özelliğini seçen aboneleri Azure Active Directory seçin.")

4. Form alanına eklemek istediğiniz Azure AD grubunun adını girmeye başlama. Bu işlem, kuruluş içindeki kullanılabilir Azure AD gruplarını aratır. 

5. Grubu seçerek alan otomatik olarak grup adıyla doldurmaktır. Eklemeden önce bu gruptaki kullanıcıları görüntüleme seçeneğiniz vardır. Ardından, grubun abonelik düzeyini, indirme haklarını ve iletişim tercihlerini seçebilirsiniz. Isterseniz başvuru alanına ayrıntılar abilirsiniz. 

   > [!div class="mx-imgBorder"]
   > ![Azure AD grubu seçin](_img/assign-license-bulk/bulk-add-aad-details.png "Bu gruptan abone eklemek için Azure AD grubu adının adını seçin.")

6. **Ekle'yi** ve ardından **Onayla'ya tıklayın.** 

7. Eklenen grubu görmek için kullanıcı listenizin en altına kaydırın.  

8. Grubun **üyelerini görüntülemek için** Aboneleri görüntüle'yi seçin. Gruptaki aboneler hakkında ayrıntıları görüntüleyemezsiniz, ancak abonelerde veya atanan aboneliklerde herhangi bir düzenleme olamaz.    

> [!NOTE]
> Abonelikleri daha sonra bir Azure AD grubunun parçası olarak eklenen kullanıcılara tek tek atadıysanız, abonelikler grubun bir parçası olarak eklenir ve artık tek tek listelenmiyor. Ancak bireysel abonelik farklı bir abonelik düzeyine sahipse iki aboneliği olur.  Örnek: Bir kullanıcının tek bir Visual Studio Professional aboneliği varsa ve bu kullanıcı kendi aboneliklerini atadığınız Visual Studio Enterprise grubun üyesi ise her ikisi de olur.  
>
> Aboneyi atanmış abonelikleri Azure Active Directory bir gruptan kaldırırsanız, güncelleştirmenin yönetici portalında yansıtilmesi 24 saate kadar sürebilir. 


## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>S: Abone eklemek için Azure Active Directory seçeneğini neden göremiyorum?
Y: Özellik şu anda yalnızca güvenilen sözleşmelere sahip kuruluşlar tarafından kullanılabilir.  Anlaşma **bilgilerini görüntülemek** için Ayrıntılar düğmesini seçin.

   > [!div class="mx-imgBorder"]
   > ![Ayrıntılar düğmesine tıklayın](_img/assign-license-bulk/bulk-add-agreement.png "Ne tür bir sözleşmeye sahip olduğunu görmek için Ayrıntılar düğmesine tıklayın")

### <a name="q-i-added-users-to-my-azure-active-directory-group-but-they-dont-have-subscriptions-yet-why"></a>S: Kullanıcı grubuma Azure Active Directory ama henüz abonelikleri yok. Neden? 
A: Değişiklikler doğrudan Azure Active Directory aboneliklerin çok hızlı bir şekilde atanacak olması gerekir, ancak değişiklikler bir on-in-on Active Directory'de yapıldı ise, önce abonelikleri Azure Active Directory. Değişiklikler, active directory'nizin nasıl yapılandırıldıklarına bağlı olarak 24 saate kadar sürebilir. 24 saat içinde destek ekibimiz sorunları [gidermeye yardımcı olabilir.](https://aka.ms/vsadminhelp) 

### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-active-directory-group"></a>S: Bir grup içinde atanacak birden çok abonelik Azure Active Directory seçebilir miyim?
A: Hayır -- gruptaki herkes aynı abonelik düzeyini alır.

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-active-directory-group"></a>S: Bir kullanıcı grubuna eklenen kişilerin abone ayrıntılarını Azure Active Directory miyim?
A: Hayır -- Tek bir abonenin bilgilerini değiştirmek için, bunları güvenlik grubundan kaldırmanız Azure Active Directory bireysel olarak bir abonelik atamanız gerekir.

### <a name="q-can-i-add-separate-notification-email-addresses-for-members-of-an-azure-active-directory-group"></a>S: Bir grup üyesinin üyeleri için ayrı bildirim e-posta Azure Active Directory ekleyebilir miyim?
A: Hayır – Bildirim grupları kullanılarak eklenen abonelikler için ayrı e-posta Azure Active Directory destekleniyor. Tüm e-postalar birincil e-postaya (kullanıcı asıl adı) gönderilir

## <a name="resources"></a>Kaynaklar
- [Visual Studio yönetim ve abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Ek olarak yalnızca bir veya iki aboneniz mi var? Tek kullanıcı [ekleme'ye göz at](assign-license.md)
