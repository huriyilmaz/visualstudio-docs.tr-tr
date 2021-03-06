---
title: Kullanıcılara Visual Studio abonelikleri atama | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 02/18/2021
ms.topic: conceptual
description: Yöneticilerin abonelere nasıl lisans atayabileceği hakkında bilgi edinin
ms.openlocfilehash: 3bfa1174a8655de27496c3138e1eab21e32c2f8d
ms.sourcegitcommit: 79a6be815244f1cfc7b4123afff29983fce0555c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102249554"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio abonelikleri yönetim portalı 'nda lisans atama
Visual Studio abonelikleri Yöneticisi olarak, bireysel kullanıcılara ve Kullanıcı gruplarına abonelik atamak için yönetim portalını kullanabilirsiniz.

Kullanıcı grupları için, abonelikleri nasıl atayacağınızı gösteren seçimleriniz vardır.  
- Her seferinde bir abonelik atayabilirsiniz.
- Ayrıca [toplu ekleme](assign-license-bulk.md) özelliğini kullanarak abone listelerini ve abonelik bilgilerini hızlıca ve kolayca karşıya yükleyebilirsiniz.
- Kuruluşunuz Microsoft Azure Active Directory (Azure AD) kullanıyorsa, Kullanıcı gruplarına [abonelik atamak Için Azure AD gruplarını kullanabilirsiniz](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) .  


## <a name="add-a-single-subscriber"></a>Tek bir abone ekleme
Abonelik avantajlarına erişebilmeleri için bir Visual Studio aboneliğini yeni bir kullanıcıya nasıl atayacağınızı öğrenmek için videoyu izleyin veya okuyun.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. [Yönetim portalında](https://manage.visualstudio.com)oturum açın.
2. Tek bir Visual Studio abonesi 'na bir lisans atamak için, tablonun en üstünde bulunan **Ekle**' yi seçin ve **bireysel abone**' i seçin.
   > [!div class="mx-imgBorder"]
   > ![Tek bir abone ekleme](_img/assign-license-add/add-subscriber-individual.png "Ekle ' yi seçin ve tek bir abonelik atamak için bireysel abone ' i seçin.")
3. Yeni abone için form alanlarına bilgi girin. Kuruluşunuz Azure Active Directory kullanıyorsa, **ad** alanı geçerli dizininizde kişileri bulmak için arama işlevi olarak davranır, böylece arama sonuçlarından doğru kullanıcıyı seçebilirsiniz. Bu kişiyi seçtikten sonra, oturum açma e-postası ve bildirim e-postası otomatik olarak doldurulur.  Abone kuruluşunuzda bulunmazsa, bildirim e-postası otomatik olarak doldurulur, ancak abonelikle ilgili e-postaların gönderileceği farklı bir e-posta adresini el ile eklemeniz gerekir.  E-posta hizmetiniz, oturum açma e-posta adreslerine gelen e-postaları engelliyorsa, aboneler ve Yöneticiler Microsoft 'tan gelen, abonelikle ilgili önemli e-postaları almak için farklı bir bildirim e-posta adresi belirtmeniz önemlidir.
   > [!div class="mx-imgBorder"]
   > ![Abone ayrıntıları](_img/assign-license-add/subscriber-details.png "Abone adı ve diğer ayrıntıları girin veya kiracı üyelerinden birini seçin.")

    > [!NOTE]
    > Bir abone adı girdiğinizde Azure Active Directory kiracının üyelerinin görünür olması için, yöneticinin kiracının bir üyesi olması gerekir. 


    Bu abonenin, [Visual Studio abonelikleri portalında](https://my.visualstudio.com?wt.mc_id=o~msft~docs)oturum açtıklarında yazılım indirmelerine erişimi olmasını Istiyorsanız **indirme ayarları** bölümünde indirmelerin etkin ' i açıp bırakmadığınızdan emin olun. İndirmeleri devre dışı bırakmayı seçerseniz, kullanıcının yazılım indirmelerine erişimi olmayacaktır.  Ürün anahtarlarına erişim de devre dışı bırakılır.  Abonenin abonelik kapsamındaki diğer tüm avantajlara erişimi olmaya devam edecektir.
   > [!div class="mx-imgBorder"]
   > ![İndirmelere erişim](media/access-to-downloads.png "Abone 'ya yazılım indirmelerine erişim sağlamak için ' Izin ver ' seçeneğini belirleyin.")

    Kendi başvuru notlarınızı aboneliğe eklemek istiyorsanız, **Başvuru Ekle** bölümünde bunu yapabilirsiniz.
   > [!div class="mx-imgBorder"]
   > ![Her aboneliğe kendi başvuru notlarınızı ekleyin](media/add-subscriber-reference-notes.png "Bu abonelikle ilgili notları kaydetmek için başvuru alanını kullanın.")

    Seçenekleri seçip abone için veri girmeyi tamamladığınızda, **abone Ekle** ' nin altında **Ekle** ' yi seçin.
   > [!div class="mx-imgBorder"]
   > ![Ekle düğmesini seçin](media/add-button.png "Bilgileri kaydetmek ve aboneliği aboneye atamak için Ekle ' yi seçin.")

## <a name="why-use-a-different-notification-email-address"></a>Neden farklı bir bildirim e-posta adresi kullanmalısınız?
Bazı kuruluşlar, e-posta hizmetlerini diğer etki alanlarından gelen e-postaları engelleyecek şekilde ayarladı.  Gelen e-postaların engellenmesi, aboneler ve yöneticilerin önemli iletişimleri kaçırmayacağı anlamına gelir:
- Aboneler, bir aboneliğin atandığı bir bildirim almaz.  Bu, bazı avantajlardan bazılarını etkinleştirmesini de engeller.  
- GitHub Enterprise ile Visual Studio abonelikleri atanmış aboneler, GitHub kuruluşunuza katılma davetini almaz, yani daveti kabul edemeyecektir. GitHub kuruluşunuza erişim kazanmak için e- **postayla gönderilen daveti kabul etmelidir** . 
- Yöneticilere bir sözleşmeye eklendiğinde bildirimde bulunulmayacak, aylık yönetici deyimlerini veya abonelikleri yönetme biçimini etkileyen özellik değişikliklerinin bildirimlerini alma.

Bir bildirim e-posta adresi kullanmak, abonelerin, oturum açma e-posta adreslerinin işlevlerini değiştirmeden abonelikleriyle ilgili önemli iletişimler almasına izin verir.  

## <a name="resend-assignment-emails"></a>Atama e-postalarını yeniden gönder
Bir abone ekledikten sonra, bir atama e-postası, daha fazla yönerge ile otomatik olarak yeni aboneye gönderilir. Atama e-postasını istediğiniz zaman, abone ' i seçip üst menüdeki yeniden **Gönder** düğmesini seçerek gönderebilirsiniz.  E-postaları birden çok kullanıcıya yeniden göndermek için, aboneleri seçerken **CTRL** tuşunu basılı tutun.  Yeniden **Gönder** düğmesini seçtiğinizde, bu abonelere yeniden göndermek istediğinizi onaylamanızı isteyen bir iletişim kutusu görürsünüz.  


## <a name="resources"></a>Kaynaklar
- Yardıma mı ihtiyacınız var?  [Abonelik desteğiyle](https://visualstudio.microsoft.com/subscriptions/support/)iletişim kurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Eklemek için çok sayıda kullanıcı mı var?  [Birden çok aboneye](assign-license-bulk.md)abonelik atamayı öğrenin.
