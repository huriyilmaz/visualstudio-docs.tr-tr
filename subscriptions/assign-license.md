---
title: kullanıcılara Visual Studio abonelikleri atama | Microsoft Docs
author: evanwindom
ms.author: cabuschl
manager: cabuschl
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 10/25/2021
ms.topic: conceptual
description: Yöneticilerin abonelere nasıl lisans atayabileceği hakkında bilgi edinin
ms.openlocfilehash: 1a7273122a2949c3a519c00aae7cc464c0664d26
ms.sourcegitcommit: 4efdab6a579b31927c42531bb3f7fdd92890e4ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2021
ms.locfileid: "130350787"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio abonelikleri yönetim portalı 'nda lisans atama
Visual Studio abonelikleri yöneticisi olarak, bireysel kullanıcılara ve kullanıcı gruplarına abonelik atamak için yönetim portalını kullanabilirsiniz.

Kullanıcı grupları için, abonelikleri nasıl atayacağınızı gösteren seçimleriniz vardır.  
- Her seferinde bir abonelik atayabilirsiniz.
- Ayrıca [toplu ekleme](assign-license-bulk.md) özelliğini kullanarak abone listelerini ve abonelik bilgilerini hızlıca ve kolayca karşıya yükleyebilirsiniz.
- kuruluşunuz Microsoft Azure Active Directory (azure ad) kullanıyorsa, kullanıcı gruplarına [abonelik atamak için Azure ad gruplarını kullanabilirsiniz](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) .  


## <a name="add-a-single-subscriber"></a>Tek bir abone ekleme
abonelik avantajlarına erişebilmeleri için yeni bir kullanıcıya Visual Studio aboneliğini nasıl atayacağınızı öğrenmek için videoyu izleyin veya okuyun.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. [Yönetim portalında](https://manage.visualstudio.com)oturum açın.
2. tek bir Visual Studio aboneye bir lisans atamak için, tablonun üst kısmında **ekle**' yi seçin ve **bireysel abone**' i seçin.
   > [!div class="mx-imgBorder"]
   > ![Tek bir abone ekleme](_img/assign-license-add/add-subscriber-individual.png "Ekle ' yi seçin ve tek bir abonelik atamak için bireysel abone ' i seçin.")
3. Bir uçarak çıkış paneli sağ tarafta görüntülenir.  Yeni abone için form alanlarına bilgi girin. 
   - kuruluşunuz Azure Active Directory kullanıyorsa, **arama Azure Active Directory** kutusuna abonenin adını yazmak, ölçütlerinizle eşleşen herhangi bir Azure AD grubu üyesinin adlarını döndürür.  Bu kişiyi seçtikten sonra, oturum açma e-postası ve bildirim e-postası otomatik olarak doldurulur.  
   - Abone kuruluşunuzda bulunamazsa, abone adının **adını ad** alanına girebilirsiniz.  
   - Abonenin oturum açmasını sağlamak için kullanmak istediğiniz e-posta adresini girin.  Ayrıca, **iletişim almak için farklı bir bildirim e-postası Ekle** ' ye tıklayabilir ve farklı bir bildirim e-posta adresi belirtebilirsiniz. böylece aboneler ve Yöneticiler Microsoft 'tan alınan önemli e-postaları alır.
      > [!div class="mx-imgBorder"]
      > ![Abone ayrıntıları](_img/assign-license-add/subscriber-details.png "Abone adı ve diğer ayrıntıları girin veya kiracı üyelerinden birini seçin.")

      > [!NOTE]
      > bir abone adı girdiğinizde Azure Active Directory kiracının üyelerinin görünür olması için, yöneticinin kiracının bir üyesi olması gerekir. 
   - Bu kullanıcıya atamak istediğiniz abonelik düzeyini seçin.  (Liste yalnızca anlaşmanızın bir parçası olarak satın alınan abonelik düzeylerini içerir.)  
   - bu abonenin [Visual Studio abonelikleri portalında](https://my.visualstudio.com?wt.mc_id=o~msft~docs)oturum açtıklarında yazılım indirmelerine erişimi olmasını istiyorsanız, **indirme Ayarlar** bölümünde indirmelerin etkin ' i açıp bırakmadığınızdan emin olun. İndirmeleri devre dışı bırakmayı seçerseniz, kullanıcının Yazılım İndirmeleri veya ürün anahtarlarına erişimi olmayacaktır.  Abonenin abonelik kapsamındaki diğer tüm avantajlara erişimi olmaya devam edecektir.
     > [!div class="mx-imgBorder"]
     > ![İndirmelere erişim](media/access-to-downloads.png "Abone 'ya yazılım indirmelerine erişim sağlamak için ' Izin ver ' seçeneğini belirleyin.")

   - Kendi başvuru notlarınızı aboneliğe eklemek istiyorsanız, **Başvuru Ekle** bölümünde bunu yapabilirsiniz.
      > [!div class="mx-imgBorder"]
      > ![Her aboneliğe kendi başvuru notlarınızı ekleyin](media/add-subscriber-reference-notes.png "Bu abonelikle ilgili notları kaydetmek için başvuru alanını kullanın.")

    Seçenekleri seçip abone için veri girmeyi tamamladığınızda, **abone Ekle** ' nin altında **Ekle** ' yi seçin.
      > [!div class="mx-imgBorder"]
      > ![Ekle düğmesini seçin](media/add-button.png "Bilgileri kaydetmek ve aboneliği aboneye atamak için Ekle ' yi seçin.")

## <a name="why-use-a-different-notification-email-address"></a>Neden farklı bir bildirim e-posta adresi kullanmalısınız?
Bazı kuruluşlar, e-posta hizmetlerini diğer etki alanlarından gelen e-postaları engelleyecek şekilde ayarladı.  Gelen e-postaların engellenmesi, aboneler ve yöneticilerin önemli iletişimleri kaçırmayacağı anlamına gelir:
  - Aboneler, bir aboneliğin atandığı bir bildirim almaz.  Bu, bazı avantajlardan bazılarını etkinleştirmesini de engeller.  
  - GitHub Enterprise sahip abonelikler Visual Studio atanmış aboneler GitHub kuruluşunuza katılma davetini almaz, yani daveti kabul edemeyecektir. GitHub kuruluşunuza erişim kazanmak için e- **postayla gönderilen daveti kabul etmelidir** . 
  - Yöneticilere bir sözleşmeye eklendiğinde bildirimde bulunulmayacak, aylık yönetici deyimlerini veya abonelikleri yönetme biçimini etkileyen özellik değişikliklerinin bildirimlerini alma.

Bir bildirim e-posta adresi kullanmak, abonelerin, oturum açma e-posta adreslerinin işlevlerini değiştirmeden abonelikleriyle ilgili önemli iletişimler almasına izin verir.  

## <a name="resend-assignment-emails"></a>Atama e-postalarını yeniden gönder
Bir abone ekledikten sonra, bir atama e-postası, daha fazla yönerge ile otomatik olarak yeni aboneye gönderilir. Atama e-postasını istediğiniz zaman, abone ' i seçip üst menüdeki yeniden **Gönder** düğmesini seçerek gönderebilirsiniz.  E-postaları birden çok kullanıcıya yeniden göndermek için, aboneleri seçerken **CTRL** tuşunu basılı tutun.  Yeniden **Gönder** düğmesini seçtiğinizde, bu abonelere yeniden göndermek istediğinizi onaylamanızı isteyen bir iletişim kutusu görürsünüz.  


## <a name="resources"></a>Kaynaklar
- Yardıma mı ihtiyacınız var?  [Abonelik desteğiyle](https://aka.ms/vsadminhelp)iletişim kurun.

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Eklemek için çok sayıda kullanıcı mı var?  [Birden çok aboneye](assign-license-bulk.md)abonelik atamayı öğrenin.
