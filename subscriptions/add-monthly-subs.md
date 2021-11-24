---
title: Abonelik yönetim portalına yeni aylık abonelikler | Microsoft Docs
author: evanwindom
ms.author: amast
manager: amast
ms.assetid: 36f0d9f1-fe28-469f-a54c-dc46638270a8
ms.date: 10/08/2021
ms.topic: how-to
description: Abonelikler Yönetim Portalı'Visual Studio yeni aylık satın alma hakkında bilgi edinin
ms.openlocfilehash: add6e5d575e1aa950faf555fa193f0ea432aad00
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132994929"
---
# <a name="add-new-monthly-visual-studio-subscriptions-to-the-subscriptions-administration-portal"></a>Abonelikler Yönetim Visual Studio yeni aylık abonelikler ekleme
Azure aboneliği kullanarak yeni Visual Studio abonelikler satın aldığınız zaman, bunları kullanıcılara atamak için Abonelikler Yönetim Portalı'ne eklemeniz gerekir.  

## <a name="how-do-i-know-if-i-need-to-add-my-subscriptions"></a>Nasıl yaparım? eklemem gereksin mi?
Aylık abonelik ekleme adımları, ne tür aboneliklere sahip olduğunu ve yeni yönetici olup olmadığınıza bağlıdır.
- Yeni yöneticiyseniz, Abonelikler Yönetim portalında ilk kez oturum aken Kullanıcı Erişimi Yöneticisi haklarına sahip olduğunuz Azure aboneliklerini kontrol ederiz.  Sizin için aylık abonelikler bulursak bunları otomatik olarak ekleyebilirsiniz. 
- Daha önce aylık abonelikler eklediy veya yönettıysanız, her oturum açmada yeni aylık abonelikleri kontrol etmek için bu abonelikleri kontrol edin. 
- Toplu Lisanslama aracılığıyla alınan abonelikler için zaten yöneticiyseniz ancak daha önce aylık abonelikler eklemediyseniz veya yönettiyseniz, bunları aşağıda sağlanan adımları kullanarak eklemeniz gerekir.

## <a name="how-to-add-monthly-subscriptions"></a>Aylık abonelik ekleme
1. Sayfasından Abonelik yönetimi portalında oturum açın <https://manage.visualstudio.com>
1. Aboneleri **yönet sekmesinde** Anlaşma ekle açılan **listesinden** seçim yapın 
1. Açılan **listeden Yeni aylık** abonelikler'i seçin
   > [!div class="mx-imgBorder"]
   > ![Yeni aylık abonelikler ekleme açılan listesinde](_img/add-monthly-subs/add-subs-drop-down.png "'Anlaşma ekle'yi ve ardından 'Yeni aylık abonelikler'i seçin.")
1. Sistem, Kullanıcı Erişimi Yöneticisi haklarına sahip olduğunuz tüm Azure aboneliklerini aratır ve bu Azure abonelikleriyle Visual Studio abonelikleri içeri aktaracak.
1. Kullanıcı Erişimi Yöneticisi haklarına sahip olmadığınız veya uygun Azure abonelikleri bulunsa da Visual Studio azure abonelikleri bulunamasa aşağıdaki iletiyi alırsınız:
   > [!div class="mx-imgBorder"]
   > ![Yeni aylık abonelik bulunamadı](_img/add-monthly-subs/no-subs-found.png "Kullanılabilir Azure aboneliği veya abonelik Visual Studio belirten hata iletisi.")
1. Yeni aylık abonelikler bulunursa bir onay iletisi alırsınız
   > [!div class="mx-imgBorder"]
   > ![Abonelikler onay iletisi eklendi](_img/add-monthly-subs/subs-added-confirmation.png "Onay iletisi, ekleydniz abonelikleri görüntüler.")

## <a name="things-to-keep-in-mind"></a>Akılda tutulması gereken noktalar
- Yeni aylık abonelik ekleme seçeneği yalnızca ilk kez satın aldığınız zaman kullanılabilir.  Aylık abonelikleri eklediktan sonra portalda her oturum açmada yeni abonelikleri kontrol edersiniz. 
- Yeni abonelikler bulunursa abonelere zaten atanmış olduklarını görebilirsiniz.  Bunun nedeni, Azure aboneliğine erişimi olan başka yöneticiler de olduğu ve yeni yönetici aboneliklerini kullanıcılara Visual Studio vardır.  Bunları portala da eklediniz, artık bu abonelikleri yönetebilirsiniz. 

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio Aboneliklerinin yönetimiyle ilgili yardım için, Visual Studio [abonelik desteği ile iletişim kurun.](https://aka.ms/vsadminhelp)

## <a name="next-steps"></a>Sonraki adımlar
Abonelikleri eklediklerine göre, bunları kullanıcılara atamaya hazırsınız.  Bunu çeşitli yollarla yapabilirsiniz:
- [Abonelikleri ayrı ayrı atama](assign-license.md)
- [Birden çok kullanıcıya abonelik atama](assign-license-bulk.md)
- [Belirli kullanıcılara belirli abonelikler atama](assign-guid.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)