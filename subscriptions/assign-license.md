---
title: Kullanıcılara Visual Studio abonelikleri | Microsoft Docs
author: evanwindom
ms.author: amast
manager: amast
ms.assetid: 4e529a43-7aed-4eee-895d-862a631952df
ms.date: 10/25/2021
ms.topic: conceptual
description: Yöneticilerin abonelere lisans atamasını öğrenin
ms.openlocfilehash: 0b20fe2cdf0561bebbc7023146313cdeb3bf4fa1
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132995740"
---
# <a name="assign-licenses-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio Abonelikleri Yönetim Portalı'Visual Studio lisans atama
Bir Visual Studio yöneticisi olarak, bireysel kullanıcılara ve kullanıcı gruplarına abonelik atamak için yönetici portalını kullanabilirsiniz.

Kullanıcı grupları için abonelik atama seçenekleriniz vardır.  
- Abonelikleri tek tek atabilirsiniz.
- Ayrıca Toplu ekleme özelliğini kullanarak abone listelerini ve abonelik bilgilerini hızlı ve kolay bir şekilde [karşıya yükleyebilirsiniz.](assign-license-bulk.md)
- Kuruluşta Microsoft Azure Active Directory (Azure AD) kullanıyorsa, [kullanıcı gruplarına](./assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) abonelik atamak için Azure AD gruplarını kullanabilirsiniz.  


## <a name="add-a-single-subscriber"></a>Tek abone ekleme
Yeni bir kullanıcıya abonelik avantajlarına erişmek için Visual Studio aboneliği atamayı öğrenmek için videoyu izleyin veya okumaya devam edin.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vpPh]


1. Yönetici portalında [oturum açın.](https://manage.visualstudio.com)
2. Tek bir aboneye lisans atamak Visual Studio, tablonun üst kısmında Ekle'yi **ve** ardından Bireysel **abone'yi seçin.**
   > [!div class="mx-imgBorder"]
   > ![Tek abone ekleme](_img/assign-license-add/add-subscriber-individual.png "Ekle'yi ve ardından Tek abone'yi seçerek tek bir abonelik attayabilirsiniz.")
3. Sağda bir fly-out paneli görüntülenir.  Bilgileri yeni abonenin form alanlarına girin. 
   - Kuruluş bir Azure Active Directory kullanıyorsa, **Arama** Azure Active Directory kutusuna abonenin adını yazarak ölçütlerinize uyan tüm Azure AD grup üyelerinin adlarını geri alır.  Bu kişiyi seçmenizin ardından oturum açma e-postası ve bildirim e-postası otomatik olarak yüklenir.  
   - Abone, kuruluşta bulunamasa, Ad alanına abonenin adını **girebilirsiniz.**  
   - Abonenizin oturum açmasını istediğiniz e-posta adresini girin.  Ayrıca İletişim almak  için farklı bir bildirim e-postası ekle bağlantısına tıklar ve abonelerin ve yöneticilerin Microsoft'tan abonelikle ilgili önemli e-postaları aldıracak şekilde farklı bir bildirim e-posta adresi belirtebilirsiniz.
      > [!div class="mx-imgBorder"]
      > ![Abone ayrıntıları](_img/assign-license-add/subscriber-details.png "Abone adını ve diğer ayrıntıları girin veya kiracı üyelerinden birini seçin.")

      > [!NOTE]
      > Bir kiracının üyelerinin Azure Active Directory bir abone adı girerken görünür olması için yöneticinin kiracının bir üyesi olması gerekir. 
   - Bu kullanıcıya atamak istediğiniz abonelik düzeyini seçin.  (Liste yalnızca sözleşmenizin bir parçası olarak satın alınan abonelik düzeylerini içerir.)  
   - Bu abonenin Visual Studio Abonelikler [Portalı'Visual Studio](https://my.visualstudio.com?wt.mc_id=o~msft~docs)yazılım indirmelerine erişmesine izin verirseniz, İndirme aboneliklerini indir bölümünde indirmeler iki durumlu Ayarlar **olun.** İndirmeleri devre dışı bırakmayı seçerseniz, kullanıcının yazılım indirmelerine veya ürün anahtarlarına erişimi olmaz.  Abone, aboneliğe dahil edilen diğer tüm avantajlara erişmeye devam ediyor.
     > [!div class="mx-imgBorder"]
     > ![İndirmelere erişim](media/access-to-downloads.png "Aboneye yazılım indirme erişimi sağlamak için 'İzin Ver'i seçin.")

   - Aboneliğe kendi başvuru notlarınızı eklemek için Başvuru ekle bölümünde **bunu yapabiliriz.**
      > [!div class="mx-imgBorder"]
      > ![Her aboneliğe kendi başvuru notlarınızı ekleme](media/add-subscriber-reference-notes.png "Bu abonelikle ilgili notları kaydetmek için Başvuru alanını kullanın.")

    Seçenekleri seçmeyi ve aboneye veri girmeyi tamamlayın, Abone Ekle seçeneğinin alt kısmında **Ekle'yi** seçin. 
      > [!div class="mx-imgBorder"]
      > ![Ekle düğmesini seçin](media/add-button.png "Bilgileri kaydetmek ve aboneliği aboneye atamak için Ekle'yi seçin.")

## <a name="why-use-a-different-notification-email-address"></a>Neden farklı bir bildirim e-posta adresi kullanasınız?
Bazı kuruluşlar, diğer etki alanlarından gelen e-postaları engellemek için e-posta hizmetlerini ayarlamış.  Gelen e-postaları engellemek, abonelerin ve yöneticilerin önemli iletişimleri kaçırması anlamına gelir:
  - Aboneler, abonelik atandığı hakkında bildirim almaz.  Bu, dahil edilen bazı avantajları etkinleştirmelerini de önler.  
  - Visual Studio aboneliğine GitHub Enterprise aboneler, GitHub kuruluşa katılma davetini almaz, yani daveti kabul etmezler. **E-posta ile gönderilen daveti kabul** etmeleri gerekir. Bu davet, GitHub erişim elde eder. 
  - Yöneticiler bir sözleşmeye ekleniyorsa, abonelikleri yönetme yolunu etkileyen aylık yönetici bildirimleri veya özellik değişiklikleri bildirimleriyle ilgili bildirim alır.

Bildirim e-posta adresi kullanmak, abonelerin oturum açma e-posta adreslerinin işlevselliğini değiştirmeden abonelikleri hakkında önemli iletişimler almalarına izin verme seçeneği sağlar.  

## <a name="resend-assignment-emails"></a>Atama e-postalarını yeniden gönder
Aboneyi ekledikten sonra, yeni aboneye ek yönergeler içeren bir atama e-postası otomatik olarak gönderilir. Aboneyi ve ardından üst menüyü yeniden gönder düğmesini seçerek atama **e-postalarını** istediğiniz zaman yeniden gönderebilirsiniz.  E-postaları birden çok kullanıcıya yeniden göndermek için aboneleri **seçerken Ctrl** tuşunu basılı tutun.  Yeniden **e-postala düğmesini** seçerek bu abonelere yeniden sormak istediğinizden emin olmak istediğiniz bir iletişim kutusu görüntülenir.  


## <a name="resources"></a>Kaynaklar
- Yardıma mı ihtiyacınız var?  Abonelikler [Desteği'ne başvurun.](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
- Eklemek istediğiniz çok fazla kullanıcı var mı?  Birden çok aboneye abonelik [atamayı öğrenin.](assign-license-bulk.md)
