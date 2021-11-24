---
title: yönetim portalında Visual Studio aboneliklerini düzenleyin | Microsoft Docs
author: evanwindom
ms.author: amast
manager: amast
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/21/2021
ms.topic: how-to
description: Yöneticilerin abonelik atamalarını nasıl düzenleyebileceğinizi öğrenin.
ms.openlocfilehash: 2482b74f5407ff451a200382598657fa5ed65a30
ms.sourcegitcommit: 17202f3ac3f7f17ce3756b57dd56321f7254d1dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "133092885"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Visual Studio abonelik atamalarını düzenle
Abonelik Yöneticisi olarak, kuruluşunuzdaki kişilere atanan aboneliklerde değişiklikler yapabilirsiniz.  Bu makale, yapabileceğiniz değişiklik türlerini açıklar ve gerekli adımları sağlar.

   > [!NOTE]
   > Azure Active Directory bir grup aracılığıyla atanan bir abonenin abonelik ayrıntılarını değiştirmeniz gerekiyorsa, bunları gruptan kaldırmanız ve tek tek yönetim portalına eklemeniz gerekir.  

## <a name="change-subscriber-information"></a>Abone bilgilerini değiştirme
Hataları düzeltmek veya bilgileri güncelleştirmek için bir abonenin bilgilerini düzenleyebilirsiniz.

Bir aboneyi düzenlemek için, farenizi onun üzerine getirdiğinizde abonenin e-posta adresinin yanında görünen üç nokta (...) simgesini seçin. Bir açılan menü görüntülenir.  Abonenin ayrıntılarını değiştirmek için **Düzenle** ' yi seçin. 
> [!div class="mx-imgBorder"]
> ![Düzenlemek için abone seçin](_img/edit-license/select-subscriber.png "Üç noktaya tıklayın ve Düzenle ' yi seçin.")

Abonenin adı, soyadı, abonelik düzeyi, e-posta adresi, ülke, dil, indirmeler ve başvuru alanını güncelleştirebilirsiniz. Abonenin bilgilerini düzenleyin ve **Kaydet**' e tıklayın.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Toplu düzenleme kullanarak birden çok aboneyi düzenleme

Toplu düzenleme işlemini kullanarak, aynı anda birden çok aboneyi düzenleyebilirsiniz. Bu özellik öncelikle Kurumsal e-posta adresi değişikliklerinden veya bir kuruluşun indirmelere erişimi kısıtlamaya karar verdiği kuruluşlarda kullanılır.

Toplu düzenleme kullanarak birden çok aboneyi nasıl düzenleyeceğinizi öğrenmek için bu videoyu izleyin veya okumaya devam edin. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

> [!NOTE]
> Şablondaki abonelik GUID 'Lerini değiştirmeyin. Lütfen [belirli bir abonelik GUID 'leri atama](assign-guid.md)hakkında makalemize bakın.

1. Birden çok aboneyi aynı anda düzenlemek için, aboneler sekmesine gidin. Üstteki şeritte **toplu düzenleme**' ye tıklayın.

2. toplu düzenleme, abone bilgilerinde düzenlemeler yapmak için bir Excel şablonu kullanır. Toplu düzenleme kutusunda, tüm bilgileri de dahil olmak üzere geçerli aboneler listesini indirmek için **Bu Excel 'ı dışarı aktar** ' a tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Bir lisansı düzenleme-toplu düzenlemeler listesini dışarı aktarma](_img/edit-license/edit-license-bulk-edit-export.png "Geçerli aboneliklerinizin bir listesini oluşturmak için bu Excel 'i dışarı aktar ' a tıklayın.")

3. Daha sonra, dosyayı kolayca bulabilmek ve karşıya yüklemeden önce gerekli değişiklikleri yapabilmek için dosyayı yerel olarak kaydedin. 

4. Visual Studio abonelikleri yönetim portalına dönün ve toplu düzenleme iletişim kutusunda, **araştır**' a tıklayın. kaydettiğiniz Excel dosyasını seçin ve **tamam**' a tıklayın. Karşıya yükleme ilerlemesini ekranda görürsünüz.
   > [!div class="mx-imgBorder"]
   > ![Lisans-toplu düzenleme dosyasını düzenleme Upload](_img/edit-license/edit-license-bulk-file-upload1.png "tamamlanan Excel dosyanızın konumuna gidin, dosyayı seçin ve tamam ' a tıklayın.")

5. Dosyayı karşıya yükledikten sonra, başarılı olduğunu bildiren bir bildirim görürsünüz. Bu noktada, düzenlemeleriniz abone bilgilerine yansıtılır.

## <a name="resources"></a>Kaynaklar
- [Abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Belirli bir abonelik KIMLIĞI atanması mı gerekiyor? Abonelik KIMLIĞI atamaya göz atın. 
- Belirli bir aboneliği bulma konusunda yardım için [bir abonelik aramaya](search-license.md)göz atın.
- Aboneliklerinizin bir listesini oluşturmanız mı gerekiyor?  [Dışarı aktarma abonelikleri](exporting-subscriptions.md)göz atın.