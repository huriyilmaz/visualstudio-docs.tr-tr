---
title: Visual Studio abonelikleri için Kullanıcı gruplarına lisans atama | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 02/26/2020
ms.topic: conceptual
description: Yöneticilerin toplu ekleme özelliğini veya Microsoft Azure Active Directory gruplarını kullanarak birden çok aboneye nasıl lisans atayabileceği hakkında bilgi edinin
ms.openlocfilehash: a9bb8e1d96b3448a4ba803b7e6348057635950b4
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634635"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Birden çok kullanıcıya abonelik atama
Abonelikler yönetim portalı, kullanıcıları tek seferde veya büyük gruplar halinde eklemenize olanak tanır.  Bireysel kullanıcı eklemek için bkz. [tek kullanıcı ekleme](assign-license.md).

Büyük Kullanıcı gruplarını eklemek için toplu ekleme özelliğini kullanabilir veya kuruluşunuz Microsoft Azure Active Directory (Azure AD) kullanıyorsa Azure AD gruplarını kullanabilirsiniz. Bu makalede her iki seçenek için de işlem açıklanacaktır. 


## <a name="use-bulk-add-to-assign-subscriptions"></a>Abonelik atamak için toplu ekleme kullanma
1. https://manage.visualstudio.comadresindeki Visual Studio abonelikleri yönetim portalında oturum açın.

2. Aynı anda birden çok abone eklemek için, **aboneleri Yönet** sekmesine gidin. **Ekle** sekmesini ve ardından açılan kutuda **toplu Ekle** ' yi seçin.  

2. Toplu ekleme, abone bilgilerini karşıya yüklemek için bir Microsoft Excel şablonu kullanır. Birden çok aboneyi karşıya yükle iletişim kutusunda şablonu indirmek için **İndir** ' e tıklayın.
   > [!div class="mx-imgBorder"]
   > ![birden çok aboneyi karşıya yüklemek için Excel şablonunu Indirin](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Bu şablonun en son sürümünü her zaman indirin. Daha eski bir sürüm kullanıyorsanız toplu karşıya yükleme işlemi başarısız olabilir.

3. Excel elektronik tablosunda, abonelik atamak istediğiniz kişilerin bilgilerini içeren alanları doldurun. (*Başvuru* isteğe bağlı bir alandır.) İşiniz bittiğinde dosyayı yerel olarak kaydedin.

   Düzgün bir karşıya yükleme sağlamaya yardımcı olmak için aşağıdaki en iyi yöntemleri inceleyin:

    - Form alanlarının hiçbirinin virgüller içermediğinden emin olun.
    - Form alanlarından önce ve sonra boşlukları kaldır.
    - Kullanıcının adlarının iki parçalı ad veya soyadı arasında fazladan boşluk olmadığından emin olun (örneğin, bir kişi "Mıknatılis Mayıs" gibi iki bölümden oluşan bir ada sahipse, sistem ek alanı kırpmadığından "Mıknatıgiemay" olarak yazılmalıdır.)
    - Tüm gerekli alanların tamamlandığından emin olun. 
    - **Hata iletisi** sütununu kontrol edin.  Herhangi bir hata listeleniyorsa, dosyayı karşıya yüklemeyi denemeden önce bunları çözün. 

4. Visual Studio abonelikleri yönetim portalına dönün. **Birden çok aboneyi karşıya yükle** iletişim kutusunda, **görüntüle**' ye tıklayın.
   > [!div class="mx-imgBorder"]
   > ![birden çok aboneyi karşıya yüklemek için kaydettiğiniz şablona gidin](media/bulk-add-browse-saved-template.png)

5. Kaydettiğiniz Excel dosyasına gidin ve ardından **Tamam**' a tıklayın.
   > [!div class="mx-imgBorder"]
   > ![birden çok aboneyi karşıya yüklemek için Excel şablonunu karşıya yükleyin](media/bulk-upload-subscribers.png)

    Karşıya yükleme ilerleme durumu iletişim kutusu görüntülenir.

    Şablonda hatalar varsa, karşıya yükleme başarısız olur ve şablonu düzeltebilmeniz ve toplu karşıya yüklemeyi yeniden denemeniz için hatalar gösterilir.
   > [!div class="mx-imgBorder"]
   > birden çok aboneye yükleme başarısız olursa hata iletisi ![](media/bulk-add-template-failed.png)

    Karşıya yükleme başarılı olduğunda, aboneler listesini ve bir onay iletisi görürsünüz.
   > [!div class="mx-imgBorder"]
   > birden çok abonelerin karşıya yüklenmesi başarılı olursa ![onay iletisi](media/bulk-add-template-success.png)

## <a name="use-azure-ad-groups-to-assign-subscriptions"></a>Azure AD gruplarını kullanarak abonelik atama 
Bu özelliğin kullanılması, abonelik atamalarınızın üstünde kalmasını kolaylaştırır. Abonelikler yönetim portalına Azure AD güvenlik grupları ekleyebilirsiniz. Bu, gruptaki tüm bireylere bir abonelik atanmasını güvence altına alacak. Daha kolay hale getirmek için, bireyler kuruluştan ayrıldığınızda ve Azure AD 'den kaldırıldığında, aboneliklerde erişimleri de kaldırılır.

> [!NOTE]
> Bu özellik, aşamalar halinde dağıtılmakta olduğundan, kuruluşunuz için hemen kullanılabilirlik olmayabilir.   

> [!IMPORTANT]
> Aboneler eklemek için Azure AD gruplarının kullanımı için aşağıdaki sınırlamalar geçerlidir:
> - Grupların en az bir üye içermesi gerekir.  Boş gruplar desteklenmiyor.
> - Gruplar 1.000 'den az kullanıcı içermelidir.
> - Tüm kullanıcılar grubun en üst düzeyinde olmalıdır.  İç içe gruplar desteklenmiyor.
> - Yalnızca güvenilen anlaşmalar desteklenir.
> - Grubun tüm üyelerinin Azure AD hesabıyla ilişkilendirilmiş bir e-posta adresi olmalıdır.


1. [https://manage.visualstudio.com](https://manage.visualstudio.com)adresindeki Visual Studio abonelikleri Yönetim Portalı ' nda oturum açın.

2. Tek seferde birden çok abone eklemek için, **aboneleri Yönet** sekmesine gidin.

3. **Ekle** sekmesini ve ardından açılan kutuda **Azure Active Directory grubu** ' nu seçin.  

   > [!div class="mx-imgBorder"]
   > Azure AD 'Yi kullanarak toplu ekleme ![](_img/assign-license-bulk/bulk-add-aad.png)


4. Form alanına eklemek istediğiniz Azure AD grubunun adını girmeye başlayın. Bu işlem, kuruluşunuzda kullanılabilir Azure AD gruplarını arayacak. 

5. Grubu seçtiğinizde, alanı otomatik olarak grup adıyla doldurulur. Bu gruptaki kullanıcıları eklemeden önce görüntüleme seçeneğine sahip olursunuz. Daha sonra, grup için abonelik düzeyini, indirme haklarını ve iletişim tercihlerini seçebilirsiniz. İsterseniz başvuru alanına ayrıntılar ekleyebilirsiniz. 

   > [!div class="mx-imgBorder"]
   > Azure AD 'Yi kullanarak toplu ekleme ![](_img/assign-license-bulk/bulk-add-aad-details.png)

6. **Ekle** ' ye ve ardından **Onayla**' ya tıklayın. 

7. Eklenen grubu görmek için, Kullanıcı listenizin en altına gidin.  

8. Grubun üyelerini görüntülemek için **aboneleri görüntüle** ' yi seçin. Gruptaki aboneler hakkındaki ayrıntıları görüntüleyebilirsiniz, ancak abonelere veya atandıkları aboneliklerde herhangi bir düzenleme yapamazsınız.    

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>S: bir Azure AD grubunda atanmak üzere birden çok abonelik düzeyi seçebilir miyim? 
Y: Hayır-gruptaki herkes aynı aboneliği alır. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>S: bir Azure AD grubuna eklenen kişilerin abone ayrıntılarını düzenleyebilir miyim?  
Y: Hayır – bireysel bir abonenin bilgilerini değiştirmek Için bunları Azure AD güvenlik grubundan kaldırmanız ve ayrı ayrı tek bir aboneliğe atamanız gerekir.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-add-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>S: birini Azure AD güvenlik grubumu ekledim, ancak bunları abonelikler yönetim portalı 'nda eklemem ve bir aboneliği yok. Neden?  
Y: kuruluşunuzun Azure AD 'yi nasıl yapılandırdığına bağlı olarak, kullanıcının eklenebilmesi için en fazla 24 saat gecikmeyle karşılaşabilirsiniz. 24 saatten uzun bir süredir, [desteğe başvurun](https://visualstudio.microsoft.com/support/support-overview-vs).  


## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Eklemek için yalnızca bir veya iki abone mi var?  [Tek Kullanıcı Ekle](assign-license.md) 'ye göz atın
- Yardıma mı ihtiyacınız var? [Visual Studio yönetim ve abonelikler desteğiyle](https://visualstudio.microsoft.com/support/support-overview-vs)iletişim kurun.



