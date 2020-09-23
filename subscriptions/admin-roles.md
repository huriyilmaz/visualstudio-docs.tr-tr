---
title: Yönetim portalında süper yönetici ve yönetici rolleri
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 6601c395-f778-48c1-ab76-cf454b9193e4
ms.date: 09/21/2020
ms.topic: conceptual
description: Süper yönetici ve yönetici rolleri ve yöneticiler atama hakkında bilgi edinin.
ms.openlocfilehash: fc44845ed403e9bf942761203b75c2277fd1aff2
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022720"
---
# <a name="super-admins-and-administrators-for-visual-studio-subscription-agreements"></a>Visual Studio abonelik anlaşmaları için süper Yöneticiler ve Yöneticiler

Toplu lisanslama müşterileri için yeni Visual Studio abonelikleri yönetim portalında iki farklı rol vardır. Bu roller birincil/bildirim Iletişim rolü ve VLSC 'de var olan abonelik Yöneticisi rolü gibidir.

**Süper Yöneticiler:** Bir kuruluş ilk kez ayarlandığında, birincil veya bildirimler Ilgili kişisi varsayılan olarak bir süper yönetici haline gelir. Birincil veya bildirimler Ilgili kişisi, ek süper Yöneticiler veya Yöneticiler atamayı seçebilir. Süper yönetici, diğer yöneticileri ve aboneler ekleyebilir ve kaldırabilir. Sistemde ikiden fazla süper yönetici varsa, bir süper yönetici, güvenlikle ilgili olarak, son iki ' i de silebilir.

**Yöneticiler:** Yönetici yalnızca bir süper yönetici tarafından atanabilir. Bir yönetici yalnızca süper yönetici tarafından bu anlaşmalara atayan abonelikleri yönetebilir.

Yöneticilerin nasıl yönetileceği hakkında bir tanıtım izleyin. 
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6L]

## <a name="assigning-administrators"></a>Yöneticiler atama
Yeni Yöneticiler (Yöneticiler) atamak için:
1. https://manage.visualstudio.comAboneliklerin satın alındığı anlaşmada süper yönetici olarak atanmış bir e-posta adresi kullanarak oturum açın.
2. **Yöneticileri Yönet**etiketli sekmeye tıklayın.
3. **Ekle**'ye tıklayın.
   > [!div class="mx-imgBorder"]
   > ![Yönetici Ekle](_img/admin-roles/add-admins.png "Yöneticileri Yönet dikey penceresine tıklayın ve sonra yeni yöneticiler atamak için Ekle ' ye tıklayın.")
4. Formu yeni yönetici bilgileriyle doldurun.  
   > [!div class="mx-imgBorder"]
   > ![Yönetici formu Ekle](_img/admin-roles/add-form.png "Yeni yönetici için oturum açma bilgilerini girin ve bir süper yönetici yapıp yapmayacağını seçin.  Ardından Ekle ' ye tıklayın.")

   > [!NOTE]
   > Bu yöneticinin ek yöneticiler atayabilmesini istiyorsanız, **süper yönetici** kutusunu kontrol etmeyi unutmayın.

5. Yeni yönetici atamak için **Ekle** ' ye tıkladıktan sonra, portalda oturum açmak üzere bu kişilere davet eden bir e-posta gönderilir.  

## <a name="resources"></a>Kaynaklar
- [Visual Studio Yönetim ve Abonelik Desteği](https://visualstudio.microsoft.com/support/support-overview-vs)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)


## <a name="next-steps"></a>Sonraki adımlar
- [Aboneliklerin nasıl atanacağını](assign-license.md) öğrenin
- [Abonelik avantajlarının](https://visualstudio.microsoft.com/vs/benefits/) tam aralığı hakkında daha fazla bilgi edinin
- [Anlaşma tercihlerini belirleme](admin-prefs.md)