---
title: Abonelik yönetim portalına yeni aylık Visual Studio abonelikleri ekleme | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 06/23/2020
ms.topic: how-to
description: Abonelik yönetim portalına yeni aylık Visual Studio abonelikleri satın alma hakkında bilgi edinin
ms.openlocfilehash: 778a3adbc9ca2117b0328a10d52904921bd0b80c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904705"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Yeni aylık Visual Studio aboneliklerini abonelikler yönetim portalına ekleme
Bir Azure aboneliği kullanarak yeni aylık Visual Studio abonelikleri satın aldığınızda kullanıcılara atamak için bunları abonelikler yönetim portalına eklemeniz gerekebilir.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Nasıl yaparım? aboneliklerimi eklemem gerekiyor mu?
Aylık abonelikler ekleme adımları, kuruluşunuzun zaten sahip olduğu abonelik türlerine ve yeni bir yönetici olup olmadığına bağlıdır.
- Yeni bir yöneticiniz varsa, abonelik yönetimi portalında ilk kez oturum açtığınızda kullanıcı erişimi yönetici haklarına sahip olduğunuz Azure aboneliklerini denetleriz.  Sizin için aylık abonelikler bulduk, bunları otomatik olarak ekleyeceğiz. 
- Aylık abonelikleri daha önce eklediyseniz veya yönetiyoruz, her oturum açışınızda yeni aylık abonelikler için denetim yapıyoruz. 
- Toplu Lisanslama aracılığıyla elde edilen abonelikler için zaten bir yöneticiyseniz, ancak daha önce bu aylık abonelikler eklenmemiş veya daha önce eklenmediyse, bunları aşağıda belirtilen adımları kullanarak eklemeniz gerekir.

## <a name="how-to-add-monthly-subscriptions"></a>Aylık abonelikler ekleme
1. Konumundaki abonelikler yönetim portalında oturum açın<https://manage.visualstudio.com>
1. **Aboneleri Yönet** sekmesinde **Yeni anlaşma** açılan ' yı seçin. 
1. Açılan kutudan **yeni aylık abonelikler** seçin
   > [!div class="mx-imgBorder"]
   > ![Yeni aylık abonelik Ekle açılan](_img/add-monthly-subs/add-subs-drop-down.png)
1. Sistem, üzerinde Kullanıcı erişimi olan yönetici haklarına sahip olduğunuz herhangi bir Azure aboneliğini arar ve bu Azure abonelikleriyle satın alınan tüm Visual Studio aboneliklerini içeri aktaracaktır.
1. Üzerinde Kullanıcı erişimi yönetici haklarına sahip olduğunuz bir Azure aboneliği bulunursa veya uygun Azure abonelikleri bulunursa ancak Visual Studio abonelikleri bulunamazsa, şu iletiyi alırsınız:
   > [!div class="mx-imgBorder"]
   > ![Yeni aylık abonelik bulunamadı](_img/add-monthly-subs/no-subs-found.png)
1. Yeni aylık abonelikler bulunursa, bir onay iletisi alırsınız
   > [!div class="mx-imgBorder"]
   > ![Abonelik eklendi onay iletisi](_img/add-monthly-subs/subs-added-confirmation.png)

## <a name="things-to-keep-in-mind"></a>Akılda tutulması gereken noktalar
- Yeni aylık abonelikler ekleme seçeneği, yalnızca ilk satın alma işleminde kullanılabilir olacaktır.  Aylık abonelikler ekledikten sonra portalda her oturum açışınızda yeni abonelikler denetliyoruz. 
- Yeni abonelikler bulunduğunda, bunların abonelere zaten atandığını görebilirsiniz.  Bunun nedeni, Azure aboneliğine erişimi olan başka Yöneticiler olduğundan ve kullanıcılara zaten yeni Visual Studio abonelikleri atamış olmalardır.  Ayrıca, bunları portala ekledığınıza göre, bu abonelikleri yönetebilirsiniz. 

## <a name="next-steps"></a>Sonraki adımlar
Artık abonelik eklemişseniz, bunları kullanıcılara atamaya hazırsınız demektir.  Bunu birkaç şekilde yapabilirsiniz:
- [Abonelikleri ayrı ayrı ata](assign-license.md)
- [Birden çok kullanıcıya abonelik atama](assign-license-bulk.md)
- [Belirli kullanıcılara belirli abonelikler atama](assign-guid.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)
