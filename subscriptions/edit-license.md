---
title: Yönetim Visual Studio sayfasındaki abonelikleri | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/21/2021
ms.topic: how-to
description: Yöneticilerin abonelik atamalarını nasıl düzenleyemezlerini öğrenin.
ms.openlocfilehash: a545a276714c7fb21d9adc966b2ef0c9e250250c
ms.sourcegitcommit: da19ed1e48259b219c61c4cb9e98b006004a5766
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2021
ms.locfileid: "128052837"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Abonelik Visual Studio düzenleme
Abonelik yöneticisi olarak, kuruluş içindeki kişilere atanan aboneliklerde değişiklik yapabilirsiniz.  Bu makalede, ne tür değişiklikler yaptığınız ele alınarak gerekli adımlar velanmıştır.

   > [!NOTE]
   > Azure Active Directory Grubu aracılığıyla atanan abonenin abonelik ayrıntılarını değiştirmeniz gerekirse, bunları gruptan kaldırmanız ve Yönetim Portalı'nda ayrı ayrı eklemeniz gerekir.  

## <a name="change-subscriber-information"></a>Abone bilgilerini değiştirme
Hataları düzeltmek veya bilgileri güncelleştirmek için abonenin bilgilerini düzenleyebilirsiniz.

Aboneyi düzenlemek için farenizi üzerine gelindiğinde abonenin e-posta adresinin yanında görünen üç noktayı (...) seçin. Açılan liste görüntülenir.  **Abonenin** ayrıntılarını değiştirmek için Düzenle'yi seçin. 
> [!div class="mx-imgBorder"]
> ![Düzenlemek istediğiniz aboneyi seçin](_img/edit-license/select-subscriber.png "Üç nokta seçeneğine tıklayın ve Düzenle'yi seçin.")

Abonenin adını, soyadını, abonelik düzeyini, e-posta adresini, ülkeyi, dili, indirmeleri ve başvuru alanını güncelleştirebilirsiniz. Abonenin bilgilerini düzenleyin ve Kaydet'e **tıklayın.**

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Toplu düzenleme kullanarak birden çok aboneyi düzenleme

Toplu düzenleme işlemini kullanarak aynı anda birden çok aboneyi düzenleyebilirsiniz. Bu özellik öncelikli olarak kurumsal e-posta adresi değişikliklerini geçen veya bir kuruluşun indirmelere erişimi kısıtlamaya karar vermiş olduğu kuruluşlar için kullanılır.

Toplu düzenleme kullanarak birden çok aboneyi düzenleme hakkında bilgi edinmek için bu videoyu izleyin veya okumaya devam etmeyi öğrenin. 
<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

> [!NOTE]
> Şablonda abonelik GUID'lerini değiştirme. Belirli abonelik GUID'lerini [atama hakkında makalemize bakın.](assign-guid.md)

1. Aynı anda birden çok aboneyi düzenlemek için Aboneler sekmesine gidin. Üstteki şeritte Toplu **Düzenle'ye tıklayın.**

2. Toplu düzenleme, abone Excel düzenlemek için bir şablon kullanır. Toplu Düzenleme kutusunda Bu **Excel'i dışarı aktar'a** tıklar ve tüm bilgileri dahil olmak üzere geçerli abone listesini indirin.
   > [!div class="mx-imgBorder"]
   > ![Lisansı Düzenleme - Toplu Düzenleme Listesini Dışarı Aktarma](_img/edit-license/edit-license-bulk-edit-export.png "Geçerli aboneliklerin listesini oluşturmak için Bu Excel'i dışarı aktar'a tıklayın.")

3. Ardından dosyayı kolayca bulmak ve karşıya yüklemeden önce gerekli değişiklikleri yapmak için dosyayı yerel olarak kaydedin. 

4. Visual Studio Abonelikler Yönetim portalına geri dönüp Toplu Düzenle iletişim kutusunda Gözat'a **tıklayın.** Kaydedtikleri Excel dosyasını seçin ve Tamam'a **tıklayın.** Karşıya yükleme ilerlemesini ekranda görürsünüz.
   > [!div class="mx-imgBorder"]
   > ![Lisansı Düzenleme - Toplu Dosya Upload](_img/edit-license/edit-license-bulk-file-upload1.png "Tamamlanmış dosyanın bulunduğu konuma Excel seçin ve Tamam'a tıklayın.")

5. Dosyayı karşıya yükledikten sonra başarılı olduğunu size bildiren bir bildirim alırsınız. Bu noktada, düzenlemeleriniz abone bilgilerine yansıtıldı.

## <a name="resources"></a>Kaynaklar
- [Abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Belirli bir abonelik kimliği atamanız mı gerekiyor? Abonelik kimliği atama'ya göz atabilirsiniz. 
- Belirli bir aboneliği bulma konusunda yardım için Abonelik [arama'ya göz atabilirsiniz.](search-license.md)
- Tüm aboneliklerin listesini oluşturmanız mı gerekiyor?  Abonelikleri dışarı [aktarma'ya göz at.](exporting-subscriptions.md)