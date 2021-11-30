---
title: Abonelikler Visual Studio Portal sayfasında abonelik atamalarını | Microsoft Docs
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: e49242bc-e9f2-49e8-8caa-f574d508aba6
ms.date: 03/21/2021
ms.topic: how-to
description: Yöneticilerin abonelik atamalarını nasıl sileceklerini Visual Studio Abonelikler Yönetim Portalı'nın
ms.openlocfilehash: ebe9e7b6669c70cbe8a01881b57b67ec94dd43d6
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133256574"
---
# <a name="delete-assignments-in-visual-studio-subscriptions"></a>Aboneliklerde atamaları Visual Studio silme
Abonenin şirketten ayrılmaları, bir projeyi tamamlamaları veya yeni bir iş rolüne geçmeleri gibi bir abonelik Visual Studio aboneliğe ihtiyaç kalmadan aboneliğini kaldırabilir ve başka birine atabilirsiniz. Aboneliği yeniden asanız tüm abone avantajlarının sıfırlanmayacak olduğunu lütfen unutmayın.  Yeni kullanıcı, sahipsiz anahtarları talep etmek ve önceden talep edilen anahtarları görüntülemek mümkün olacak ancak talep sınırları **sıfırlanmaz.**  Enterprise Sözleşmesi (EA) olan kuruluşlarda, pluralsight eğitimi gibi özgün kullanıcı tarafından kullanılan tüm avantajlar sıfırlanır. 
> [!Important]
> Abonelikler yalnızca aboneliğin son atandığı zamandan bu yana en az 90 gün geçmişse farklı kullanıcılara atanabilir.  Örneğin, bir abonelik 1 Haziran'da aboneye atanmışsa, en az 30 Ağustos'a kadar yeni aboneye atanamaz. 

Atamaları silmeyi öğrenmek için bu videoyu izleyin veya okumaya devam etmeyi öğrenin.  

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yG2q]

## <a name="delete-a-subscription-assignment"></a>Abonelik ataması silme
1. Kaldırmak istediğiniz abonenin adına tıklayın. Kaldırma için birden çok abone seçmek için abone adının sol tarafından daireye tıklar ve her birini seçersiniz.  Alternatif olarak, **CTRL** tuşunu basılı tutabilir ve kaldırmak istediğiniz abonelere tıklar. Bir abone aralığını kaldırmak için ilk aboneye tıklayın, **Shift** tuşuna basın ve son aboneye tıklayın.  Tüm **aboneleri seçmek ve kaldırmak** için CTRL + A tuşlarına basın. Bu örnekte üç abone (Kai, Kai ve Kai) silinecektir. 
2. Seçili aboneleri silmek için Sil'e **tıklayın.**
3. Silme işlemini onaylamanızı isteyen ileti göründüğünde Tamam'a **tıklayın.**
   > [!div class="mx-imgBorder"]
   > ![Aboneleri silme](_img/delete-license/delete-subscribers.png "Silmek istediğiniz kullanıcı veya kullanıcılarını seçin ve Sil'e tıklayın. Birden çok abone seçmek için CTRL ve Shift tuşlarını kullanabilirsiniz.")

   > [!NOTE]
   > Şablon kullanarak toplu silme kullanılamaz. 
   >
   > Azure Active Directory Güvenlik Grupları aracılığıyla abonelik atamaları eklediyseniz, silme işleminin yönetici portalında güncelleştirilmiş olması 24 saate kadar sürebilir.  Abonelikleri [yönetmek için](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) kaynak gruplarını kullanma hakkında daha Azure Active Directory makalemize bakın. 

## <a name="resources"></a>Kaynaklar
- [Abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Bir aboneliği silmeden değiştirmek mi gerekiyor?  Abonelikleri [düzenlemeyi öğrenin](edit-license.md)
- Belirli bir aboneliği bulma konusunda yardım için Abonelik [arama'ya göz atabilirsiniz.](search-license.md)
- Tüm aboneliklerin listesini oluşturmanız mı gerekiyor?  Lütfen [bkz. Abonelikleri dışarı aktarma.](exporting-subscriptions.md)