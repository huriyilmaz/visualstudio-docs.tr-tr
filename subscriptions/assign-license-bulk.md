---
title: Visual Studio abonelikleri için Kullanıcı gruplarına lisans atama | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 05/10/2020
ms.topic: how-to
description: Yöneticilerin toplu ekleme özelliğini veya Microsoft Azure Active Directory gruplarını kullanarak birden çok aboneye nasıl lisans atayabileceği hakkında bilgi edinin
ms.openlocfilehash: 459220c7fb2103da05f15607787390963863e622
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903288"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Birden çok kullanıcıya abonelik atama
Abonelikler yönetim portalı, kullanıcıları tek seferde veya büyük gruplar halinde eklemenize olanak tanır.  Bireysel kullanıcı eklemek için bkz. [tek kullanıcı ekleme](assign-license.md).

Büyük Kullanıcı gruplarını eklemek için toplu ekleme özelliğini kullanabilir veya kuruluşunuz Microsoft Azure Active Directory (Azure AD) kullanıyorsa Azure AD gruplarını kullanabilirsiniz. Bu makalede her iki seçenek için de işlem açıklanacaktır. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vxNq]

## <a name="use-bulk-add-to-assign-subscriptions"></a>Abonelik atamak için toplu ekleme kullanma
1. Üzerinde Visual Studio abonelikleri yönetim portalında oturum açın <https://manage.visualstudio.com> .

1. Aynı anda birden çok abone eklemek için, **aboneleri Yönet** sekmesine gidin. **Ekle** sekmesini ve ardından açılan kutuda **toplu Ekle** ' yi seçin.  

1. Toplu ekleme, abone bilgilerini karşıya yüklemek için bir Microsoft Excel şablonu kullanır. Birden çok aboneyi karşıya yükle iletişim kutusunda şablonu indirmek için **İndir** ' e tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Birden çok aboneyi karşıya yüklemek için Excel şablonunu indirin](media/download-template-upload-subscribers.png)
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

1. Visual Studio abonelikleri yönetim portalına dönün. **Birden çok aboneyi karşıya yükle** iletişim kutusunda, **görüntüle**' ye tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Birden çok aboneyi karşıya yüklemek için kaydedilmiş şablonunuz 'na gidin](media/bulk-add-browse-saved-template.png)

1. Kaydettiğiniz Excel dosyasına gidin ve ardından **Tamam**' a tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Birden çok aboneyi karşıya yüklemek için Excel şablonunu karşıya yükleyin](media/bulk-upload-subscribers.png)

    Karşıya yükleme ilerleme durumu iletişim kutusu görüntülenir.

    Şablonda hatalar varsa, karşıya yükleme başarısız olur ve şablonu düzeltebilmeniz ve toplu karşıya yüklemeyi yeniden denemeniz için hatalar gösterilir.
   > [!div class="mx-imgBorder"]
   > ![Birden çok aboneye yükleme başarısız olursa hata iletisi](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Bir hatayla karşılaşırsanız, şu adımları izleyin:
   1. Oluşturduğunuz Excel dosyasını açın, sorunları düzeltin ve dosyayı kaydedin.
   0. Yönetim portalına dönün ve **Ekle**' yi seçin.
   0. **Toplu Ekle**' yi seçin.
   0. Excel dosyası zaten kaydedildiğinden, şablonu indirmeniz gerekmez.  **Araştır**' a tıklayın, az önce kaydettiğiniz dosyayı bulun ve **Aç**' a tıklayın.
   0. **Tamam**'a tıklayın.


    Karşıya yükleme başarılı olduğunda, aboneler listesini ve bir onay iletisi görürsünüz.
   > [!div class="mx-imgBorder"]
   > ![Birden çok abonelerin karşıya yüklenmesi başarılı olursa onay iletisi](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Abonelikler atamak için Azure Active Directory grupları kullanma 
Bu özelliğin kullanılması, abonelik atamalarınızın üstünde kalmasını kolaylaştırır. Abonelikler yönetim portalına Azure Active Directory güvenlik grupları ekleyebilirsiniz. Bu, gruptaki tüm bireylere bir abonelik atanmasını güvence altına acaktır. Daha kolay hale getirmek için, bireyler kuruluştan ayrıldığınızda ve Azure Active Directory kaldırıldığında, aboneliklerde erişimleri de kaldırılır. 


> [!IMPORTANT]
>
> Aboneler eklemek için Azure AD gruplarının kullanımı için aşağıdaki sınırlamalar geçerlidir:
> - Yönetici, başlangıçta yönetim portalına bir grup eklerken AAD kiracısının bir üyesi olmalıdır.  Grup eklendikten sonra, grupların üyeliğinde yapılan değişiklikler yönetici katılımı gerektirmez. 
> - Grupların en az bir üye içermesi gerekir.  Boş gruplar desteklenmiyor.
> - Gruplar 1.000 'den az kullanıcı içermelidir. 
> - Tüm kullanıcılar grubun en üst düzeyinde olmalıdır.  İç içe gruplar desteklenmiyor.
> - Yalnızca güvenilen anlaşmalar desteklenir.
> - Grubun tüm üyelerinin Azure AD hesabıyla ilişkilendirilmiş bir e-posta adresi olmalıdır.
> - Azure AD grupları kullanılarak eklenen abonelikler için bildirimler için ayrı e-posta adresleri desteklenmez.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

1. Üzerinde Visual Studio abonelikleri Yönetim Portalı ' nda oturum açın [https://manage.visualstudio.com](https://manage.visualstudio.com) .

2. Tek seferde birden çok abone eklemek için, **aboneleri Yönet** sekmesine gidin.

3. **Ekle** sekmesini ve ardından açılan kutuda **Azure Active Directory grubu** ' nu seçin.  

   > [!div class="mx-imgBorder"]
   > ![Azure AD 'yi kullanarak toplu ekleme 'yi seçin](_img/assign-license-bulk/bulk-add-aad.png)

4. Form alanına eklemek istediğiniz Azure AD grubunun adını girmeye başlayın. Bu işlem, kuruluşunuzda kullanılabilir Azure AD gruplarını arayacak. 

5. Grubu seçtiğinizde, alanı otomatik olarak grup adıyla doldurulur. Bu gruptaki kullanıcıları eklemeden önce görüntüleme seçeneğine sahip olursunuz. Daha sonra, grup için abonelik düzeyini, indirme haklarını ve iletişim tercihlerini seçebilirsiniz. İsterseniz başvuru alanına ayrıntılar ekleyebilirsiniz. 

   > [!div class="mx-imgBorder"]
   > ![Azure AD 'yi kullanarak toplu ekleme 'yi seçin](_img/assign-license-bulk/bulk-add-aad-details.png)

6. **Ekle** ' ye ve ardından **Onayla**' ya tıklayın. 

7. Eklenen grubu görmek için, Kullanıcı listenizin en altına gidin.  

8. Grubun üyelerini görüntülemek için **aboneleri görüntüle** ' yi seçin. Gruptaki aboneler hakkındaki ayrıntıları görüntüleyebilirsiniz, ancak abonelere veya atandıkları aboneliklerde herhangi bir düzenleme yapamazsınız.    

> [!NOTE]
> Daha önce bir Azure AD grubunun parçası olarak eklenen kullanıcılara ayrı ayrı abonelik atadıysanız, bunlar grubun bir parçası olarak eklenir ve artık ayrı olarak listelenmez. Ancak, bireysel abonelik farklı bir abonelik düzeyi için ise iki abonelik olur.  Örnek: bir kullanıcının tek bir Visual Studio Professional aboneliği varsa ve Visual Studio Enterprise abonelikleri atadığınız bir grubun üyesiyse, her ikisi de olur.  


## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>S: bir Azure AD grubunda atanmak üzere birden çok abonelik düzeyi seçebilir miyim? 
Y: Hayır-gruptaki herkes aynı aboneliği alır. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>S: bir Azure AD grubuna eklenen kişilerin abone ayrıntılarını düzenleyebilir miyim?  
Y: Hayır-bireysel bir abonenin bilgilerini değiştirmek Için bunları Azure AD güvenlik grubundan kaldırmanız ve ayrı ayrı tek bir aboneliğe atamanız gerekir.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>S: birini Azure AD güvenlik grubumu ekledim, ancak bunları abonelikler yönetim portalına ekledim ve bir aboneliği yok. Neden?  
Y: kuruluşunuzun Azure AD 'yi nasıl yapılandırdığına bağlı olarak, kullanıcının eklenebilmesi için en fazla 24 saat gecikmeyle karşılaşabilirsiniz. 24 saatten uzun bir süredir, [desteğe başvurun](https://visualstudio.microsoft.com/support/support-overview-vs).  

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Eklemek için yalnızca bir veya iki abone mi var?  [Tek Kullanıcı Ekle](assign-license.md) 'ye göz atın
- Yardıma mı ihtiyacınız var? [Visual Studio yönetim ve abonelikler desteğiyle](https://visualstudio.microsoft.com/support/support-overview-vs)iletişim kurun.
