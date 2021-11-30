---
title: birden çok kullanıcıya Visual Studio abonelikleri atama | Microsoft Docs
author: evanwindom
ms.author: amast
manager: shve
ms.date: 10/21/2021
ms.topic: conceptual
description: Yöneticilerin tek seferde birden çok aboneliği nasıl atayabileceği hakkında bilgi edinin.
ms.openlocfilehash: de94a3990a69e4ca99b2d55243faad3ae842d45d
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133258004"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Birden çok kullanıcıya abonelik atama
Abonelikler yönetim portalı, kullanıcıları tek seferde veya büyük gruplar halinde eklemenize olanak tanır.  Bireysel kullanıcı eklemek için bkz. [tek kullanıcı ekleme](assign-license.md).

büyük kullanıcı gruplarını eklemek için toplu ekleme özelliğini kullanabilir veya kuruluşunuz Microsoft Azure Active Directory (azure ad) kullanıyorsa Azure ad gruplarını kullanabilirsiniz. Bu makalede her iki seçenek için de işlem açıklanacaktır.  Toplu ekleme özelliği hakkında daha fazla bilgi edinmek için bu videoyu izleyin veya okumaya devam edin. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Abonelik atamak için toplu ekleme kullanma
1. ' de Visual Studio abonelikleri yönetim portalında oturum açın <https://manage.visualstudio.com> .

1. Tek seferde birden çok abone eklemek için, **aboneleri Yönet** sekmesine gidin. **Ekle** sekmesini ve ardından açılan kutuda **toplu Ekle** ' yi seçin.  

1. toplu ekleme abone bilgilerini karşıya yüklemek için bir Microsoft Excel şablonu kullanır. birden çok abone Upload iletişim kutusunda, şablonu indirmek için **indir** ' i seçin.
   > [!div class="mx-imgBorder"]
   > ![birden çok aboneyi karşıya yüklemek için Excel şablonunu indirin](media/download-template-upload-subscribers.png "Toplu atama Excel için boş kaynak şablonunu indirin.")
   >
   > [!NOTE]
   > Bu şablonun en son sürümünü her zaman indirin. Daha eski bir sürüm kullanıyorsanız toplu karşıya yükleme işlemi başarısız olabilir.

1. Excel elektronik tablosunda, abonelik atamak istediğiniz kişilerin bilgilerini içeren alanları doldurun. (*Başvuru* isteğe bağlı bir alandır.) İşiniz bittiğinde dosyayı yerel olarak kaydedin.

    > [!NOTE]
    > Şablondaki alanlardan biri yöneticilerin, abonelerin yazılım indirme yeteneğini etkinleştirmesine veya devre dışı bırakmasına olanak sağlar.  İndirmelerin devre dışı bırakılması, ürün anahtarlarına erişimini de devre dışı bırakır.

   Düzgün bir karşıya yükleme sağlamaya yardımcı olmak için aşağıdaki en iyi yöntemleri inceleyin:

    - Form alanlarından hiçbirinin virgül içermediğinden emin olun.
    - Form alanlarının önündeki ve sonundaki boşlukları kaldırın.
    - Kullanıcının adlarının iki parçalı ad veya soyadı arasında fazladan boşluk olmadığından emin olun (örneğin, bir kişi "Mıknatılis Mayıs" gibi iki bölümden oluşan bir ada sahipse, sistem ek alanı kırpmadığından "Mıknatıgiemay" olarak yazılmalıdır.)
    - Tüm gerekli alanların tamamlandığından emin olun. 
    - **Hata iletisi** sütununu kontrol edin.  Herhangi bir hata listeleniyorsa, dosyayı karşıya yüklemeyi denemeden önce bunları çözün. 

1. Visual Studio abonelikleri yönetim portalına geri dönün. **birden çok abone Upload** iletişim kutusunda, **araştır**' ı seçin.
   > [!div class="mx-imgBorder"]
   > ![Birden çok aboneyi karşıya yüklemek için kaydedilmiş şablonunuz 'na gidin](media/bulk-add-browse-saved-template.png "Dosya konuma göz atabilir veya sürükleyip bu iletişim kutusuna ebilirsiniz.")

1. kaydettiğiniz Excel dosyasına gidin ve ardından **tamam**' ı seçin.
   > [!div class="mx-imgBorder"]
   > ![birden çok aboneyi karşıya yüklemek için Excel şablonunu Upload](media/bulk-upload-subscribers.png "Verilerinizin yer alan şablonu burada görünür.  Karşıya yüklemeye başlamak için Tamam'ı seçin.")

    Karşıya yükleme ilerleme durumu iletişim kutusu görüntülenir.

    Şablonda hatalar varsa, karşıya yükleme başarısız olur ve şablonu düzeltebilmeniz ve toplu karşıya yüklemeyi yeniden denemeniz için hatalar gösterilir.
   > [!div class="mx-imgBorder"]
   > ![Birden çok aboneye yükleme başarısız olursa hata iletisi](_img/assign-license-bulk/bulk-add-upload-failure.png "Karşıya yüklediğiniz dosyada hatalar varsa bu ileti görüntülenir.  Hataları giderin ve Toplu ekleme işlemini yeniden gerçekleştirin.")

   Bir hatayla karşılaşırsanız, şu adımları izleyin:
   1. oluşturduğunuz Excel dosyasını açın, sorunları düzeltin ve dosyayı kaydedin.
   0. Yönetim portalına dönün ve hata iletisini kapatın.
   0. **Ekle**' yi seçin.
   0. **Toplu Ekle**' yi seçin.
   0. Excel dosyası zaten kaydedildiğinden, şablonu indirmeniz gerekmez.  **Araştır**' ı seçin, yeni kaydettiğiniz dosyayı bulun ve **Aç**' ı seçin.
   0. **Tamam**’ı seçin.


    Karşıya yükleme başarılı olduğunda, aboneler listesini ve bir onay iletisi görürsünüz.
   > [!div class="mx-imgBorder"]
   > ![Birden çok abonelerin karşıya yüklenmesi başarılı olursa onay iletisi](_img/assign-license-bulk/bulk-add-upload-success.png "Karşıya yükleme işleminiz başarıyla tamamlandığında bir onay iletisi alırsınız.")

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>abonelikler atamak için Azure Active Directory grupları kullanma 
Bu özelliğin kullanılması, abonelik atamalarınızın üstünde kalmasını kolaylaştırır. abonelikler yönetim portalına Azure Active Directory güvenlik grupları ekleyebilirsiniz. bu, gruptaki tüm bireylere bir abonelik atanmasını güvence altına acaktır. daha kolay hale getirmek için, bireyler kuruluştan ayrıldığınızda ve Azure Active Directory kaldırıldığında, aboneliklerde erişimleri de kaldırılır. 


> [!IMPORTANT]
>
> Aboneler eklemek için Azure AD gruplarının kullanımı için aşağıdaki sınırlamalar geçerlidir:
> - Yönetici, başlangıçta yönetici portalına bir grup eklerken Azure AD kiracının bir üyesi olmalıdır.  Grup eklendikten sonra, grupların üyeliğinde yapılan değişiklikler yönetici katılımı gerektirmez. 
> - Grupların en az bir üye içermesi gerekir.  Boş gruplar desteklenmiyor.
> - Tüm kullanıcılar grubun en üst düzeyinde olmalıdır.  İç içe gruplar desteklenmiyor.
> - Yalnızca güvenilen anlaşmalar desteklenir. (Yalnızca ' fazla ayırabilecek ' abonelikler olan anlaşmalar güvenilirdir.)
> - Grubun tüm üyelerinin Azure AD hesabıyla ilişkilendirilmiş bir e-posta adresi olmalıdır.
> - Azure AD grupları kullanılarak eklenen abonelikler için bildirimler için ayrı e-posta adresleri desteklenmez.  

Azure Active Directory grubu özelliğini kullanarak abone ekleme hakkında daha fazla bilgi edinmek için bu videoyu izleyin veya okumaya devam edin. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Visual Studio abonelikleri yönetim portalı ' nda oturum açın [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Tek seferde birden çok abone eklemek için, **aboneleri Yönet** sekmesine gidin.

3. **ekle** sekmesini ve ardından açılan kutuda **Azure Active Directory grubu** ' nu seçin.  

   > [!div class="mx-imgBorder"]
   > ![Azure AD 'yi kullanarak toplu ekleme 'yi seçin](_img/assign-license-bulk/bulk-add-aad.png "Azure AD'yi kullanarak toplu ekleme özelliğini seçen ve Azure Active Directory seçin.")

4. Sağ tarafta bir anında çıkış penceresi görünür.  Form alanına eklemek istediğiniz Azure AD grubunun adını girmeye başlayın. Bu işlem, kuruluşunuzda kullanılabilir Azure AD gruplarını arayacak. 

5. Grubu seçtiğinizde, alanı otomatik olarak grup adıyla doldurulur. Bu gruptaki kullanıcıları eklemeden önce görüntüleme seçeneğine sahip olursunuz. Daha sonra, grup için abonelik düzeyini, indirme haklarını ve iletişim tercihlerini seçebilirsiniz. İsterseniz başvuru alanına ayrıntılar ekleyebilirsiniz. 

   > [!div class="mx-imgBorder"]
   > ![Azure AD grubunuzu seçin](_img/assign-license-bulk/bulk-add-aad-details.png "Bu gruptan abone eklemek için Azure AD grubu adının adını seçin.")

6. **Ekle** ' yi ve ardından **Onayla**' yı seçin. 

7. Eklenen grubu görmek için, Kullanıcı listenizin en altına gidin.  

8. Grubun üyelerini görüntülemek için **aboneleri görüntüle** ' yi seçin. Gruptaki aboneler hakkındaki ayrıntıları görüntüleyebilirsiniz, ancak abonelere veya atandıkları aboneliklerde herhangi bir düzenleme yapamazsınız.    

> [!NOTE]
> Daha önce bir Azure AD grubunun parçası olarak eklenen kullanıcılara ayrı ayrı abonelik atadıysanız, bunlar grubun bir parçası olarak eklenir ve artık ayrı olarak listelenmez. Ancak, bireysel abonelik farklı bir abonelik düzeyi için ise iki abonelik olur.  örnek: bir kullanıcının tek bir Visual Studio Professional aboneliği varsa ve Visual Studio Enterprise abonelikleri atadığınız bir grubun üyesiyse, her ikisi de olur.  
>
> abonelikleri kendisine atanmış bir Azure Active Directory grubundan kaldırırsanız, güncelleştirmenin yönetici portalına yansıtılması 24 saate kadar sürebilir... 


## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="q-why-cant-i-see-the-option-to-use-azure-active-directory-groups-to-add-subscribers"></a>s: aboneler eklemek için Azure Active Directory gruplarını kullanma seçeneğini neden göremiyorum?
Y: Bu özellik şu anda yalnızca güvenilen sözleşmeleri olan kuruluşlar tarafından kullanılabilir.  Anlaşma bilgilerinizi göstermek için **Ayrıntılar** düğmesini seçin.

   > [!div class="mx-imgBorder"]
   > ![Ayrıntılar düğmesine tıklayın](_img/assign-license-bulk/bulk-add-agreement.png "Ne tür bir sözleşmeye sahip olduğunu görmek için Ayrıntılar düğmesine tıklayın")

### <a name="q-i-added-users-to-my-azure-active-directory-group-but-they-dont-have-subscriptions-yet-why"></a>s: Azure Active Directory grubumu kullanıcıları ekledim, ancak henüz abonelikleri yok. Neden? 
A: değişiklikler Azure Active Directory doğrudan yapılmışsa, abonelikler çok çabuk atanmalıdır, ancak değişiklikler bir şirket içi Active Directory yapılmışsa, önce Azure Active Directory için eşitlenmesi gerekir. Şirket içi Active Directory nasıl yapılandırıldığına bağlı olarak değişikliklerin yansıtılması 24 saate kadar sürebilir. 24 saatten daha uzun [bir süredir destek ekibimiz sorunları gidermenize yardımcı olabilir](https://aka.ms/vsadminhelp). 

### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-active-directory-group"></a>s: bir Azure Active Directory grubuna atamak için birden çok abonelik düzeyi seçebilir miyim?
Y: Hayır-gruptaki herkes aynı abonelik düzeyini alır.

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-active-directory-group"></a>s: bir Azure Active Directory grubuna eklenen kişilerin abone ayrıntılarını düzenleyebilir miyim?
y: hayır-bireysel bir abonenin bilgilerini değiştirmek için, Azure Active Directory güvenlik grubundan kaldırmanız ve bunları ayrı ayrı atamanız gerekir.

### <a name="q-can-i-add-separate-notification-email-addresses-for-members-of-an-azure-active-directory-group"></a>s: bir Azure Active Directory grubunun üyeleri için ayrı bildirim e-posta adresleri ekleyebilir miyim?
y: hayır – bildirimler için ayrı e-posta adresleri şu anda Azure Active Directory grupları kullanılarak eklenen abonelikler için desteklenmez. Tüm e-postalar birincil e-postaya gönderilecek (Kullanıcı asıl adı)

## <a name="resources"></a>Kaynaklar
- [Visual Studio yönetim ve abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Ek olarak yalnızca bir veya iki aboneniz mi var? Tek kullanıcı [ekleme'ye göz at](assign-license.md)
