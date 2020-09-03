---
title: Visual Studio aboneliklerine lisans atama | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 03/02/2020
ms.topic: conceptual
description: Yöneticilerin abonelere nasıl lisans atayabileceği hakkında bilgi edinin
ms.openlocfilehash: aa3c219a605b552ea1c4b785ff8fb1f92edf04ac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88249472"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio abonelikleri yönetim portalı 'nda lisans atama
Visual Studio abonelikleri Yöneticisi olarak, bireysel kullanıcılara ve Kullanıcı gruplarına abonelik atamak için yönetim portalını kullanabilirsiniz.

Kullanıcı grupları için, abonelikleri nasıl atayacağınızı gösteren seçimleriniz vardır.  
- Her seferinde bir abonelik atayabilirsiniz.
- Ayrıca [toplu ekleme](assign-license-bulk.md) özelliğini kullanarak abone listelerini ve abonelik bilgilerini hızlıca ve kolayca karşıya yükleyebilirsiniz.
- Kuruluşunuz Microsoft Azure Active Directory (Azure AD) kullanıyorsa, Kullanıcı gruplarına [abonelik atamak Için Azure AD gruplarını kullanabilirsiniz](https://docs.microsoft.com/visualstudio/subscriptions/assign-license-bulk#use-azure-active-directory-groups-to-assign-subscriptions) .  


## <a name="add-a-single-subscriber"></a>Tek bir abone ekleme
Abonelik avantajlarına erişebilmeleri için bir Visual Studio aboneliğini yeni bir kullanıcıya atama hakkında daha fazla bilgiyi burada bulabilirsiniz.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. [Yönetim portalında](https://manage.visualstudio.com)oturum açın.
2. Tek bir Visual Studio abonesi 'na bir lisans atamak için, tablonun en üstünde bulunan **Ekle**' yi seçin ve **bireysel abone**' i seçin.
   > [!div class="mx-imgBorder"]
   > ![Tek bir abone ekleme](_img/assign-license-add/add-subscriber-individual.png "Ekle ' yi seçin ve tek bir abonelik atamak için bireysel abone ' i seçin.")
3. Yeni abone için form alanlarına bilgi girin. Kuruluşunuz Azure Active Directory kullanıyorsa, **ad** alanı geçerli dizininizde kişileri bulmak için arama işlevi olarak davranır, böylece arama sonuçlarından doğru kullanıcıyı seçebilirsiniz. Bu kişiyi seçtikten sonra, oturum açma e-postası ve bildirim e-postası otomatik olarak doldurulur.
   > [!div class="mx-imgBorder"]
   > ![Abone ayrıntıları](_img/assign-license-add/subscriber-details.png "Abone adı ve diğer ayrıntıları girin veya kiracı üyelerinden birini seçin.")

    > [!NOTE]
    > Bir abone adı girdiğinizde Azure Active Directory kiracının üyelerinin görünür olması için, yöneticinin kiracının bir üyesi olması gerekir. 


    Bu abonenin, [Visual Studio abonelikleri portalında](https://my.visualstudio.com?wt.mc_id=o~msft~docs)oturum açtıklarında yazılım indirmelerine erişimi olmasını Istiyorsanız **indirme ayarları** bölümünde indirmelerin etkin ' i açıp bırakmadığınızdan emin olun. İndirmeleri devre dışı bırakmayı seçerseniz, kullanıcının yazılım indirmelerine erişimi olmayacaktır.  Ürün anahtarlarına erişim de devre dışı bırakılır.  Abonenin abonelik kapsamındaki diğer tüm avantajlara erişimi olmaya devam edecektir.
   > [!div class="mx-imgBorder"]
   > ! [İndirmelere erişim] (medya/access-to-downloads.png "" Izin ver "i, abone için yazılım indirmelerine erişim sağlamak için seçin.")

    Kendi başvuru notlarınızı aboneliğe eklemek istiyorsanız, **Başvuru Ekle** bölümünde bunu yapabilirsiniz.
   > [!div class="mx-imgBorder"]
   > ![Her aboneliğe kendi başvuru notlarınızı ekleyin](media/add-subscriber-reference-notes.png "Bu abonelikle ilgili notları kaydetmek için başvuru alanını kullanın.")

    Seçenekleri seçip abone için veri girmeyi tamamladığınızda, **abone Ekle** ' nin altında **Ekle** ' yi seçin.
   > [!div class="mx-imgBorder"]
   > ![Ekle düğmesini seçin](media/add-button.png "Bilgileri kaydetmek ve aboneliği aboneye atamak için Ekle ' yi seçin.")

## <a name="resend-assignment-emails"></a>Atama e-postalarını yeniden gönder
Bir abone ekledikten sonra, bir atama e-postası, daha fazla yönerge ile otomatik olarak yeni aboneye gönderilir. Atama e-postasını istediğiniz zaman, abone ' i seçip üst menüdeki yeniden **Gönder** düğmesini seçerek gönderebilirsiniz.  E-postaları birden çok kullanıcıya yeniden göndermek için, aboneleri seçerken **CTRL** tuşunu basılı tutun.  Yeniden **Gönder** düğmesini seçtiğinizde, bu abonelere yeniden göndermek istediğinizi onaylamanızı isteyen bir iletişim kutusu görürsünüz.  

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)


## <a name="next-steps"></a>Sonraki adımlar
- Eklemek için çok sayıda kullanıcı mı var?  [Birden çok aboneye](assign-license-bulk.md)abonelik atamayı öğrenin.
- Yardıma mı ihtiyacınız var?  [Visual Studio yönetim ve abonelikler desteğiyle](https://visualstudio.microsoft.com/support/support-overview-vs)iletişim kurun.


