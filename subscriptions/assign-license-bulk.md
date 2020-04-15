---
title: Visual Studio abonelikleri için kullanıcı gruplarına lisans atama | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: c2853359-18fd-4be4-97a6-02230c862f92
ms.date: 03/02/2020
ms.topic: conceptual
description: Toplu ekleme özelliğini veya Microsoft Azure Etkin Dizin gruplarını kullanarak yöneticilerin birden çok aboneye nasıl lisans atayabileceğini öğrenin
ms.openlocfilehash: a7742049cdda2568504e54d2c83259bb4a262819
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385519"
---
# <a name="assign-subscriptions-to-multiple-users"></a>Birden çok kullanıcıya abonelik atama
Abonelikyönetimi Portalı, kullanıcıları tek seferde veya büyük gruplar halinde eklemenize olanak tanır.  Tek tek kullanıcıları eklemek için [bkz.](assign-license.md)

Büyük kullanıcı grupları eklemek için toplu ekleme özelliğini kullanabilirsiniz veya kuruluşunuz Microsoft Azure Etkin Dizini (Azure AD) kullanıyorsa Azure REKLAM gruplarını kullanabilirsiniz. Bu makalede, her iki seçenek için işlem açıklanacaktır. 

## <a name="use-bulk-add-to-assign-subscriptions"></a>Abonelik atamak için Toplu ekleme kullanma
1. Visual Studio Abonelikleri Yönetim Portalı'na https://manage.visualstudio.comgiriş .

2. Aynı anda birden fazla abone eklemek için **Aboneleri Yönet** sekmesine **Bulk add** gidin. **Add**  

2. Toplu ekleme, abone bilgilerini yüklemek için bir Microsoft Excel şablonu kullanır. Çoklu Abone Yükle iletişim kutusunda, şablonu indirmek için **İndir'i** tıklatın.
   > [!div class="mx-imgBorder"]
   > ![Birden çok abone yüklemek için Excel şablonuna indirin](media/download-template-upload-subscribers.png)
   >
   > [!NOTE]
   > Her zaman bu şablonun en son sürümünü indirin. Eski bir sürüm kullanıyorsanız, toplu yüklemeniz başarısız olabilir.

3. Excel elektronik tablosunda, alanları abonelik atamak istediğiniz kişilerin bilgileriyle doldurun. (*Başvuru* isteğe bağlı bir alandır.) Bittikten sonra dosyayı yerel olarak kaydedin.

   Sorunsuz bir yükleme sağlamaya yardımcı olmak için aşağıdaki en iyi uygulamaları gözlemleyin:

    - Form alanlarının hiçbirinin virgül içermediğinden emin olun.
    - Form alanlarından önceki ve sonra boşlukları kaldırın.
    - Kullanıcı adlarının iki parçalı ad veya soyad arasında fazladan boşluk içermediğinden emin olun (örneğin, bir kişinin "Maggie May" gibi iki parçalı bir adı varsa, sistem fazladan alanı kırpmayeceğinden "MaggieMay" olarak yazılmalıdır.)
    - Gerekli tüm alanların tamamlandığından emin olun. 
    - Hata **iletisi** sütununa bakın.  Herhangi bir hata listelenirse, dosyayı yüklemeye çalışmadan önce bunları çözün. 

4. Visual Studio Abonelikleri Yönetimi portalına geri dönün. Çoklu **Abone Yükle** iletişim kutusunda **Gözat'ı**tıklatın.
   > [!div class="mx-imgBorder"]
   > ![Birden fazla abone yüklemek için kayıtlı şablonunuza göz atın](media/bulk-add-browse-saved-template.png)

5. Kaydettiğiniz Excel dosyasına gidin ve ardından **Tamam'ı**tıklatın.
   > [!div class="mx-imgBorder"]
   > ![Birden çok abone yüklemek için Excel şablonuna yükleme](media/bulk-upload-subscribers.png)

    Yükleme ilerleme iletişim kutusu görüntülenir.

    Şablon hatalar içeriyorsa, yükleme başarısız olur ve şablonu düzeltip toplu yüklemeyi yeniden denemeniz için hatalar gösterilir.
   > [!div class="mx-imgBorder"]
   > ![Birden çok abonenin yüklenmesi başarısız olursa hata iletisi](_img/assign-license-bulk/bulk-add-upload-failure.png)

   Bir hatayla karşılaşırsanız aşağıdaki adımları izleyin:
   1. Oluşturduğunuz Excel dosyasını açın, sorunları düzeltin ve dosyayı kaydedin.
   0. Yöneticilik Portalına geri dön ve **Ekle'yi**seçin.
   0. **Toplu ekle'yi**seçin.
   0. Excel dosyasını zaten kaydettiğiniz için şablonu indirmeniz gerekmez.  **Gözat'ı**tıklatın, kaydettiğiniz dosyayı bulun ve **Aç'ı**tıklatın.
   0. **Tamam**'a tıklayın.


    Yükleme başarılı olduğunda, abonelerin listesini ve bir onay iletisini görürsünüz.
   > [!div class="mx-imgBorder"]
   > ![Birden fazla abonenin yüklenmesi başarılı olursa onay iletisi](_img/assign-license-bulk/bulk-add-upload-success.png)

## <a name="use-azure-active-directory-groups-to-assign-subscriptions"></a>Abonelikatamak için Azure Etkin Dizin gruplarını kullanma 
Bu özelliği kullanmak, abonelik atamalarınızı en üstte kaltın. Abonelikler Yönetim Portalı'na, gruptaki tüm bireylerin bir abonelik atanır olmasını sağlayacak Azure Etkin Dizin Güvenlik Grupları ekleyebilirsiniz. Bunu kolaylaştırmak için, bireyler kuruluşunuzdan ayrılıp Azure Active Directory'den kaldırıldığında, aboneliklere erişimleri de kaldırılır. 


> [!IMPORTANT]
>
> Aşağıdaki sınırlamalar, abone eklemek için Azure REKLAM gruplarının kullanımı için geçerlidir:
> - Gruplar en az bir üye içermelidir.  Boş gruplar desteklenmez.
> - Grupların 1.000'den az kullanıcısı olmalıdır. 
> - Tüm kullanıcılar grubun en üst düzeyinde olmalıdır.  İç içe gruplar desteklenmez.
> - Yalnızca güvenilen anlaşmalar desteklenir.
> - Grubun tüm üyelerinin Azure AD hesaplarıyla ilişkili bir e-posta adresi olmalıdır.
> - Azure REKLAM grupları kullanılarak eklenen abonelikler için bildirimler için ayrı e-posta adresleri desteklenmez.  

1. Visual Studio Abonelikleri Yönetim Portalı'nda [https://manage.visualstudio.com](https://manage.visualstudio.com)oturum açın.

2. Aynı anda birden çok abone eklemek için **Aboneleri Yönet** sekmesine gidin.

3. **Ekle** sekmesini seçin ve açılan yolda **Azure Etkin Dizin grubunu** seçin.  

   > [!div class="mx-imgBorder"]
   > ![Azure AD'yi kullanarak toplu ekleme yi seçme](_img/assign-license-bulk/bulk-add-aad.png)

4. Form alanına eklemek istediğiniz Azure REKLAM grubunun adını girmeye başlayın. Bu, kuruluşunuzdaki kullanılabilir Azure REKLAM gruplarını arar. 

5. Grubu seçtiğinizde, alan otomatik olarak grup adı ile doldurulur. Eklemeden önce bu gruptaki kullanıcıları görüntüleme seçeneğiniz olacaktır. Ardından, grup için abonelik düzeyini, indirme haklarını ve iletişim tercihlerini seçebilirsiniz. İsterseniz başvuru alanına ayrıntıları ekleyebilirsiniz. 

   > [!div class="mx-imgBorder"]
   > ![Azure AD'yi kullanarak toplu ekleme yi seçme](_img/assign-license-bulk/bulk-add-aad-details.png)

6. **Ekle'yi** tıklatın ve sonra **Onayla'yı**. 

7. Eklenen grubu görmek için kullanıcı listenizin en altına gidin.  

8. Grup üyelerini görüntülemek için **aboneleri** Görüntüle'yi seçin. Gruptaki abonelerle ilgili ayrıntıları görüntüleyebilirsiniz, ancak abonelere veya atandıkları aboneliklerde herhangi bir değiştirme yapamazsınız.    

> [!NOTE]
> Abonelikleri daha sonra bir Azure REKLAM grubunun parçası olarak eklenen kullanıcılara ayrı ayrı atadıysanız, bunlar grubun bir parçası olarak eklenir ve artık tek tek listelenmez. Ancak, tek tek abonelik farklı bir abonelik düzeyi içinse, iki abonelik leri olacaktır.  Örnek: Bir kullanıcının tek bir Visual Studio Professional aboneliği varsa ve visual studio enterprise aboneliklerini atadığınız bir grubun üyesiyse, her ikisine de sahip olurlar.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4rvvW]

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q-can-i-choose-multiple-subscription-levels-to-be-assigned-within-an-azure-ad-group"></a>S: Bir Azure REKLAM grubuna atanacak birden çok abonelik düzeyi seçebilir miyim? 
C: Hayır -- gruptaki herkes aynı aboneliği alır. 

### <a name="q-can-i-edit-subscriber-details-of-individuals-added-in-an-azure-ad-group"></a>S: Azure REKLAM grubuna eklenen kişilerin abone bilgilerini edinebilir miyim?  
C: Hayır -- Tek bir abonenin bilgilerini değiştirmek için, bilgileri Azure AD güvenlik grubundan kaldırmanız ve bunları tek tek abone olarak atamanız gerekir.  

### <a name="q-i-added-someone-to-my-azure-ad-security-group-but-i-dont-see-them-added-in-the-subscriptions-administration-portal-and-they-dont-have-a-subscription-why-not"></a>S: Azure AD güvenlik grubuma birini ekledim, ancak Abonelikler Yönetimi Portalı'na eklenmelerini görmüyorum ve abonelikleri yok. Neden?  
C: Kuruluşunuzun Azure REKLAM'ı nasıl yapılandırdığına bağlı olarak, kullanıcının eklenmesinden önce 24 saate kadar gecikmeler görebilirsiniz. 24 saatten uzun bir süre olduysa [desteğe başvurun.](https://visualstudio.microsoft.com/support/support-overview-vs)  

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Ekleyecek sadece bir veya iki aboneniz mi var?  Tek [kullanıcı ekle'ye](assign-license.md) göz atın
- Yardıma mı ihtiyacınız var? İletişim [Görsel Stüdyo İdaresi ve Abonelikler Destek](https://visualstudio.microsoft.com/support/support-overview-vs).
