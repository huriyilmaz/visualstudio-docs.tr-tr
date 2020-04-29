---
title: Yönetim portalında abonelikleri düzenleyin | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 97ac8e4d-7a03-42f8-98cb-15bcaa90ef65
ms.date: 03/03/2020
ms.topic: conceptual
description: Yöneticilerin abonelik atamalarını nasıl düzenleyebileceğinizi öğrenin.
ms.openlocfilehash: a0f72bf6a6561060fd4eddcf2fc11f0f4cf97f15
ms.sourcegitcommit: 1b7412f1a5b039b2b294c6001013f399ea7aa5bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82564231"
---
# <a name="edit-visual-studio-subscription-assignments"></a>Visual Studio abonelik atamalarını Düzenle
Bir abonelik Yöneticisi olarak, kuruluşunuzdaki kişilere atanan aboneliklerde değişiklikler yapabilirsiniz.  Bu makale, yapabileceğiniz değişiklik türlerini açıklar ve gerekli adımları sağlar.

   > [!NOTE]
   > Azure Active Directory bir grup aracılığıyla atanan bir abonenin abonelik ayrıntılarını değiştirmeniz gerekiyorsa, bunları gruptan kaldırmanız ve tek tek yönetim portalına eklemeniz gerekir.  

## <a name="change-subscriber-information"></a>Abone bilgilerini değiştirme
Hataları düzeltmek veya bilgileri güncelleştirmek için bir abonenin bilgilerini düzenleyebilirsiniz.

Bir aboneyi düzenlemek için, farenizi onun üzerine getirdiğinizde abonenin e-posta adresinin yanında görünen üç nokta (...) simgesini seçin. Bir açılan menü görüntülenir.  Abonenin ayrıntılarını değiştirmek için **Düzenle** ' yi seçin. 
> [!div class="mx-imgBorder"]
> ![Düzenlemek için abone seçin](_img/edit-license/select-subscriber.png)

Abonenin adı, soyadı, abonelik düzeyi, e-posta adresi, ülke, dil, indirmeler ve başvuru alanını güncelleştirebilirsiniz. Abonenin bilgilerini düzenleyin ve **Kaydet**' e tıklayın.

## <a name="edit-multiple-subscribers-using-bulk-edit"></a>Toplu düzenleme kullanarak birden çok aboneyi düzenleme


Toplu düzenleme işlemini kullanarak, aynı anda birden çok aboneyi düzenleyebilirsiniz. Bu özellik öncelikle Kurumsal e-posta adresi değişikliklerinden veya bir kuruluşun indirmelere erişimi kısıtlamaya karar verdiği kuruluşlarda kullanılır.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vkAF]

   > [!IMPORTANT]
   > Abonelik düzeyleri (örn. Enterprise, Professional, vs.) ve abonelik GUID 'Leri toplu düzenleme kullanılarak değiştirilemez.  Kullanıcılarınıza belirli abonelik GUID 'Leri atamanız gerekiyorsa, abonelik KIMLIĞINI seçerek kullanıcı ekleme işlemini kullanın. Toplu düzenleme şablonunda bu öğelerle değiştirilen bir karşıya yüklemeyi denerseniz karşıya yükleme başarısız olur.

1. Birden çok aboneyi aynı anda düzenlemek için, aboneler sekmesine gidin. Üstteki şeritte **toplu düzenleme**' ye tıklayın.

2. Toplu düzenleme, abone bilgilerinde düzenlemeler yapmak için bir Excel şablonu kullanır. Toplu düzenleme kutusunda, tüm bilgileri de dahil olmak üzere geçerli aboneler listesini indirmek için **Bu Excel 'ı dışarı aktar** ' a tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Bir lisansı düzenleme-toplu düzenlemeler listesini dışarı aktarma](_img/edit-license/edit-license-bulk-edit-export.png)

3. Daha sonra, dosyayı kolayca bulabilmek ve karşıya yüklemeden önce gerekli değişiklikleri yapabilmek için dosyayı yerel olarak kaydedin. Başarılı bir karşıya yükleme işlemi sağlamak için, toplu düzenleme dosyasındaki **abonelik düzeyini veya ABONELIK GUID 'sini düzenlemeyin** , yüklemenin başarısız olmasına neden olur.

4. Visual Studio abonelikleri yönetim portalına dönün ve toplu düzenleme iletişim kutusunda, **Araştır**' a tıklayın. Kaydettiğiniz Excel dosyasını seçin ve **Tamam**' a tıklayın. Karşıya yükleme ilerlemesini ekranda görürsünüz.
   > [!div class="mx-imgBorder"]
   > ![Lisans-toplu düzenleme dosya yükleme](_img/edit-license/edit-license-bulk-file-upload1.png)

5. Dosyayı karşıya yükledikten sonra, başarılı olduğunu bildiren bir bildirim görürsünüz. Bu noktada, düzenlemeleriniz abone bilgilerine yansıtılır.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Belirli bir abonelik KIMLIĞI atanması mı gerekiyor? Abonelik KIMLIĞI atamaya göz atın. 
- Belirli bir aboneliği bulma konusunda yardım için [bir abonelik aramaya](search-license.md)göz atın.
- Aboneliklerinizin bir listesini oluşturmanız mı gerekiyor?  [Dışarı aktarma abonelikleri](exporting-subscriptions.md)göz atın.


