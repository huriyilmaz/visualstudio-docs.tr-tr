---
title: Yönetim Portalı'ndaki abonelikleri edin | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/03/2020
ms.topic: conceptual
description: Yöneticilerin abonelik atamalarını nasıl güncelleyebilirlerini öğrenin.
ms.openlocfilehash: d145d556467b4eecec787fe409b4faa45945bec0
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232553"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Visual Studio abonelik atamalarını edit
Abonelik yöneticisi olarak, kuruluşunuzdaki kişilere atanan aboneliklerde değişiklik yapabilirsiniz.  Bu makalede, yapabileceğiniz değişiklik türleri tartışılır ve gerekli adımları sağlar.

   > [!NOTE]
   > Azure Active Directory Group aracılığıyla atanan bir abonenin abonelik ayrıntılarını değiştirmeniz gerekiyorsa, bunları gruptan kaldırmanız ve bunları Tek tek Yönetim Portalına eklemeniz gerekir.  

## <a name="change-subscriber-information"></a>Abone bilgilerini değiştirme
Hataları düzeltmek veya bilgileri güncellemek için abonebilgilerini güncelleyebilirsiniz.

Bir aboneyi yeniden sağlamak için, farenizi üzerinde gezinirken abonenin e-posta adresinin yanında görünen elipsleri (...) seçin. Bir açılır düşüş görüntülenir.  Abonenin ayrıntılarını değiştirmek için **Edit'i** seçin. 
> [!div class="mx-imgBorder"]
> ![Ediniçin aboneyi seçin](_img/edit-license/select-subscriber.png)

Abonenin adını, soyadını, abonelik düzeyini, e-posta adresini, ülkesini, dilini, indirmelerini ve başvuru alanını güncelleyebilirsiniz. Abonenin bilgilerini edin ve **Kaydet'i**tıklatın.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Toplu edit kullanarak birden çok aboneyi edin
Toplu dönüştürme işlemini kullanarak aynı anda birden çok aboneyi yeniden edinebilirsiniz. Bu özellik, öncelikle kurumsal e-posta adresi değişikliklerinden geçmekte olan kuruluşlar veya bir kuruluş indirmelere erişimi kısıtlamaya karar verdiyse için kullanılır.

   > [!IMPORTANT]
   > Abonelik düzeyleri (örneğin Kurumsal, Profesyonel, vb.) ve abonelik GUID'leri Toplu düzenlendik kullanılarak değiştirilemez.  Kullanıcılarınıza belirli abonelik GUID'leri atamanız gerekiyorsa, abonelik kimliğini seçerek kullanıcı eklemek için işlemi kullanın. Toplu edit şablonunda değiştirilen bu öğelerle yükleme girişiminde bulunmazsanız, yükleme başarısız olur.

1. Aynı anda birden çok aboneyi güncellemek için Aboneler sekmesine gidin. Üstteki şeritte Toplu **Edit'i**tıklatın.

2. Toplu edit, abone bilgilerinde yapılan ları yapmak için bir Excel şablonu kullanır. Toplu Edit kutusunda, tüm bilgilerini içeren abonelerin geçerli listesini indirmek için **bu exceli dışa** aktar'ı tıklatın.
   > [!div class="mx-imgBorder"]
   > ![Lisans Düzenleme - İhracat Toplu Düzenler Listesi](_img/edit-license/edit-license-bulk-edit-export.png)

3. Ardından, dosyayı kolayca bulabilmeniz ve yüklemeden önce gerekli değişiklikleri yapabilmeniz için dosyayı yerel olarak kaydedin. Başarılı bir yükleme sağlamak için, toplu yükleme **dosyasındaki abonelik düzeyini veya abonelik GUID'ini,** yüklemenin başarısız olmasına neden olacağından, toplu yükleme dosyasında da yükleme yapmayın.

4. Visual Studio Abonelikleri Yönetimi portalına ve Toplu Edit iletişim kutusuna **dön, Gözat'ı**tıklatın. Kaydettiğiniz Excel dosyasını seçin ve **Tamam'ı**tıklatın. Yükleme ilerlemesini ekranda göreceksiniz.
   > [!div class="mx-imgBorder"]
   > ![Lisans Düzenleme - Toplu Düzenleme Dosya Yükleme](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Dosyayı yükledikten sonra, dosyanın başarılı olduğunu bildiren bir bildirim görürsünüz. Bu noktada, ediniminiz abone bilgilerine yansıtılacaktır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Belirli bir abonelik kimliği atamanız mı gerekiyor? Abonelik kimliği atama yı kullanıma çekin. 
- Belirli bir aboneliği bulma da yardımcı olmak [için, abonelik ara'ya](search-license.md)göz atın.
- Tüm aboneliklerinizin bir listesini oluşturmanız mı gerekiyor?  [Dışa Aktarma aboneliklerine](exporting-subscriptions.md)göz atın.


