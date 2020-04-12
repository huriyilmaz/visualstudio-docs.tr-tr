---
title: VLSC'de görüntülenen kişisel e-postalar
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 04/10/2020
ms.topic: conceptual
description: Visual Studio Abonelikleri – Abonelerim için Neden Hotmail veya Gmail Adreslerini Görüyorum?
ms.openlocfilehash: 44b18bd46d55349fae5a3ece03cee9fe93240148
ms.sourcegitcommit: 316dd2182dd56b0cbde49f0cd82e9f75baa2530f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2020
ms.locfileid: "81223690"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Visual Studio abonelikleri – Abonelerim için neden kişisel hesaplar görüyorum?
Şirketler Toplu LisansLama Hizmet Merkezi'nden (VLSC) yeni Visual Studio Abonelikleri Yönetim Portalı'na geçtikten sonra, yöneticiler bazı aboneler için "Oturum Açma E-posta Adresi"nin Hotmail veya Outlook gibi kişisel bir e-posta adresi gösterdiğini görünce [şaşırdılar.](https://manage.visualstudio.com)  

## <a name="cause"></a>Nedeni
Bu senaryo, eski MSDN abone deneyimiyle ilişkili oturum açma işlemleri nedeniyle oluşur. Kullanıcılar, Toplu Lisans Hizmet Merkezi'nden (VLSC) Visual Studio Abonelikleri Yönetim Portalı'na değişiklik yapılmadan geçirildi. Yöneticiler, kullanıcıların abonelik avantajlarına erişmek için kişisel hesapları kullandığının farkında olmayabilir. 2016 yılında tamamlanan Visual Studio abone geçişlerinden önce, Visual Studio Aboneliğini başarıyla kullanmak için iki eylem vardı:
1. Yönetici, iş veya okul e-posta adresini kullanarak aboneliği tek bir aboneye "atamıştır".
2. Abone aboneliği "etkinleştirdi".

Abone etkinleştirme işlemi sırasında: Oturum açmanız için bir Microsoft Hesabı (MSA) gerekiyordu. Abone, iş veya okul hesabını (örn. tasha@contoso.comMSA) yapmaya çalışmamışsa, yeni bir MSA oluşturabilir veya mevcut bir hesaptan yararlanabilir. Bu, "Oturum Açma E-posta Adresi"nin "E-posta Adresine Atanan" adreslerinden farklı olmasıyla sonuçlandı.

> [!NOTE]
> Hem İş/Okul [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) hem de Microsoft Hesabı (MSA) kimlik türlerini destekleyen modern abone deneyimi.

## <a name="solution"></a>Çözüm

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

Sorunu gidermek için **E-postaları Bağla** düğmesini seçmeniz yeterlidir ve sistem, hesaplarını kuruluşunuzun Azure Etkin Dizini'ndeki (Azure AD) ad ve soyadla eşleştirmeye dayalı olarak msa'larla eşleştirmeye çalışır. Bir hata varsa, maçın sağındaki **X'e** tıklayarak herhangi bir eşleşmeyi kaldırabilirsiniz.  

> [!div class="mx-imgBorder"]
> ![E-postaları Bağla Düğmesi](_img/connect-emails/connect-emails-button.png)

Hataları düzeltmek veya Azure AD'inizdeki eksik bilgileri doldurmak için **Arama Dizini'ni** de kullanabilirsiniz. Tüm eşleşmeler doğru görünüyorsa, teker teker seçmek yerine "Eşleşen tüm aboneleri seçin" seçeneğini belirleyebilirsiniz.  

> [!div class="mx-imgBorder"]
> ![E-postaları Fly-out bağlayın](_img/connect-emails/connect-emails-flyout.png)

Sonraki tıklayarak gerçekleşecek değişiklikleri özetleyen bir ekrana götürecek "devam" seçeneğini tıklatın. Kabul ederseniz, "kaydet"i tıklatın ve değişiklikler yapılacaktır. Aboneniz ayrıca, aboneliklerinde bir sonraki oturum açabildiklerinde değişikliği bildiren bir ileti de alır.   

> [!div class="mx-imgBorder"]
> ![E-postaları Onayla](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Oturum açma e-posta adresini düzenlediğiniz de bu yalnızca abonenin aboneliğinde oturum https://my.visualstudio.comaçmak için kullandığı e-postayı günceller. Abone, diğer e-posta adresini kullanarak Azure veya Pluralsight gibi avantajları zaten etkinleştirmişse, bunlara erişmek için bu e-posta adreslerini kullanmaya devam etmeleri gerekir. Eriştükleri yeni avantajlar için yeni e-posta adresini kullanmaları gerekir. 

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Sonraki adımlar
- Abonenin e-posta adresini(es) güncellediyseniz, oturum açma bilgilerinin değiştiğini onlara bildirmek isteyebilirsiniz.  Ayrıca güncelleştirilmiş bilgileri içeren bir e-posta alırlar.
- Değiştirilmesi gereken e-posta adreslerinde oturum açma yı aramak için kuruluşunuzdaki [abonelerin listesini filtrelemek](search-license.md) yararlı olabilir.  
