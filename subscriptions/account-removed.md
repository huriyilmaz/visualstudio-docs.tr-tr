---
title: Microsoft tarafından silinen Visual Studio abonelik atamaları | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: f853ed9d-3543-4f5f-a754-92381ee03523
ms.date: 10/08/2021
ms.topic: how-to
description: Microsoft 'un bir aboneliği sildiği bir bildirim gördüğünüzde ne anlama geldiğini öğrenin.
ms.openlocfilehash: 2d19598081b2aa27eb9f3666348e9732a67773ad
ms.sourcegitcommit: 5f1e0171626e13bb2c5a6825e28dde48061208a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2021
ms.locfileid: "129704683"
---
# <a name="why-does-my-dashboard-shows-microsoft-removed-a-subscriber"></a>Panom neden Microsoft 'un abonesini kaldırdı? 
[Yönetici portalındaki](https://manage.visualstudio.com)panonun **son değişiklikler** bölümünde, aboneliklerin kaldırıldığını ve nedenin "hesap kapatıldı" olarak gösterildiğini görebilirsiniz.  Bunun iki nedeni olabilir.  

## <a name="subscribers-request-closure-of-their-microsoft-accounts"></a>Aboneler Microsoft hesaplarının kapatılmasını ister
Bir abone, aboneliklerinde oturum açmak için kullanılan bir Microsoft hesabı (MSA) kapanışı isterse, MSA kapalıyken abonelik kaldırılır.  

Bir hesabı kapatmadan önce göz önünde bulundurmanız gereken önemli noktalar hakkında daha fazla bilgi için, bkz. [Microsoft hesabı nasıl kapatılabilir](https://support.microsoft.com/account-billing/how-to-close-your-microsoft-account-c1b2d13f-4de6-6e1b-4a31-d9d668849979).

## <a name="subscribers-are-removed-from-azure-active-directory-tenant"></a>aboneler Azure Active Directory kiracıdan kaldırılır
aboneliği bir Azure Active Directory (Azure AD) grubu kullanılarak otomatik olarak atanan bir abone söz konusu gruptan kaldırıldığında, abonelik otomatik olarak kaldırılır.  

## <a name="what-happens-when-the-account-is-closed"></a>Hesap kapatıldığında ne olur?
Abonelik kaldırılırsa, abone abonelik erişimini hemen kaybedecektir.  Bir abone Azure AD grubundan kaldırılırsa, abonelik bilgileri 180 gün içinde kalıcı olarak kaldırılır.  Bir abone kendi MSA 'u kapatırsa, bilgileri hemen kaldırılır.  

## <a name="resources"></a>Kaynaklar
- Yöneticiler için [abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Bir aboneliğin silinmesine gerek kalmadan değiştirilsin mi?  [Abonelikleri nasıl düzenleyeceğinizi](edit-license.md)öğrenin.
- Belirli bir aboneliği bulmak için [bir abonelik aramaya](search-license.md)göz atın.
- Aboneliklerinizin bir listesini oluşturmanız mı gerekiyor?  Bkz. [abonelikleri dışarı aktarma](exporting-subscriptions.md).
- [Abonelikleri silmeyi](delete-license.md)öğrenin. 

