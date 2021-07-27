---
title: Abonelikler için süper yönetici Visual Studio rolleri
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 03/19/2021
ms.topic: conceptual
description: Süper yönetici ve yönetici rolleri ve yönetici atama hakkında bilgi edinin.
ms.openlocfilehash: c5997004f50b78ba8484be51f3e5dd5a22aa868e
ms.sourcegitcommit: d5c038792da2c86436750380633ee80c39e4c4ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2021
ms.locfileid: "114597055"
---
# <a name="super-admins-and-admins-for-visual-studio-subscription-agreements"></a>Abonelik sözleşmelerini yenilemek için Visual Studio ve yöneticiler

Toplu Lisanslama müşterileri için Abonelikler Visual Studio Portal'da iki farklı rol vardır. Bu roller, VLSC'de önceden mevcut olan Birincil/Bildirimler Kişi rolü ve Abonelik Yöneticisi rolüne benzer.

**Süper yöneticiler:** Bir kuruluş ilk kez ayarlanırsa Birincil veya Bildirim İlgili Kişisi varsayılan olarak süper yönetici olur. Birincil veya Bildirimler İlgili Kişisi, ek süper yöneticiler veya yöneticiler atamayı seçebilir. Süper yönetici hem diğer yöneticileri hem de aboneleri ekleyebilir ve kaldırabilir. Sistemde ikiden fazla süper yönetici varsa, süper yönetici güvenlik için son ikisi dışında hepsini silebilir.

**Yöneticiler:** Bir yönetici yalnızca süper yönetici tarafından atanabilir. Bir yönetici, aboneleri yalnızca süper yöneticinin atadığınız sözleşmelerde yönetebilir.

Yöneticileri yönetme hakkında bir tanıtım izleyin. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-admins"></a>Yönetici atama
Yeni yöneticiler (yöneticiler) atamak için:
1. Aboneliklerin satın alındığı sözleşmede süper yönetici olarak atanan bir https://manage.visualstudio.com e-posta adresini kullanarak oturum açma.
2. Yöneticileri Yönet etiketli **sekmeye tıklayın.**
3. **Ekle**'ye tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Yönetici ekleme](_img/admin-roles/add-admins.png "Yöneticileri Yönet dikey penceresine ve ardından Yeni yöneticiler atamak için Ekle'ye tıklayın.")
4. Formu yeni yöneticinin bilgileriyle doldurun.  
   > [!div class="mx-imgBorder"]
   > ![Yönetici formu ekleme](_img/admin-roles/add-form.png "Yeni yönetici için oturum açma bilgilerini girin ve süper yönetici olup olmadığını seçin.  Ardından Ekle'ye tıklayın.")

   > [!NOTE]
   > Bu yöneticinin ek yönetici atayabilecek durumda olması için Süper Yönetici kutusunu **işaretleyin.**

5. Yeni yöneticiyi **atamak** için Ekle'ye tıklarsanız, yöneticiyi portalda oturum açmaları için davet eden bir e-posta alır.  

## <a name="resources"></a>Kaynaklar
- [Visual Studio yönetim ve abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Abonelik [atamayı öğrenin](assign-license.md)
- Abonelik avantajlarının tam aralığı hakkında daha [fazla bilgi](https://visualstudio.microsoft.com/vs/benefits/)
- [Anlaşma tercihlerini belirleme](admin-preferences.md)