---
title: VLSC'de Visual Studio kişisel e-postalar
author: evanwindom
ms.author: amast
manager: shve
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 03/21/2021
ms.topic: conceptual
description: Visual Studio Abonelikler – Abonelerimin Hotmail veya Gmail Adreslerini Neden Görüyorum?
ms.openlocfilehash: 65da529625d39037ef0092bc56cafe05248bdd1a
ms.sourcegitcommit: 28168514c0c9472e852de35cceb4f95837669da6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "133255989"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Visual Studio abonelikler – Abonelerimin kişisel hesaplarını neden görüyorum?
Şirketler Toplu Lisanslama Hizmet Merkezi'den (VLSC) yeni Visual Studio Abonelikler Yönetim Portalı'ne geçtikten sonra [yöneticiler,](https://manage.visualstudio.com)bazı aboneler için "Oturum Açma E-posta Adresi"nin Hotmail veya Outlook gibi kişisel bir e-posta adresi gösterirken şaşırıyor.  

## <a name="cause"></a>Nedeni
Bu senaryo, eski MSDN abone deneyimiyle ilişkili oturum açma işlemleri nedeniyle oluşur. Kullanıcılar Toplu Lisans Hizmet Merkezi'den (VLSC) Visual Studio Abonelikler Yönetim Portalı'Visual Studio değişiklik yapmadan geçirildi. Yöneticiler, kullanıcıların abonelik avantajlarına erişmek için kişisel hesaplar kullanıyor olduğunu fark etmeyebilirsiniz. 2016 Visual Studio tamamlanan abone geçişlerinden önce, Visual Studio Aboneliğini başarıyla kullanmak için iki eylem vardı:
1. Yönetici, iş veya okul e-posta adresini kullanarak aboneliği tek bir aboneye "atadı".
2. Abone, aboneliği "etkinleştirdi".

Abone etkinleştirme işlemi sırasında: Oturum açma için bir Microsoft Hesabı (MSA) gereklidir. Abone, iş veya okul hesabını (örn. ) bir MSA yapmaya çalışmadı ise yeni bir MSA oluşturabilir veya mevcut bir tasha@contoso.com MSA'dan faydalanabilirsiniz. Bu da "Oturum Açma E-posta Adresi"nin "Atanan E-posta Adresi" ile aynı olmasıyla sonuçlandı.

> [!NOTE]
> üzerinde modern abone deneyimi hem [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) İş/Okul hem de Microsoft Hesabı (MSA) kimlik türlerini destekler.

## <a name="solution"></a>Çözüm
Sorunu düzeltmek için Bağlan  E-postaları düğmesini seçmeniz gerekir. Sistem, ad ve soyadı eşleşmesi temel alınarak hesapları MSA'larla, kuruluş Azure Active Directory 'de (Azure AD) mevcut kullanıcılarla eşleştirmeye çalışacak. Bir hata varsa, eşleşmenin sağ üst tarafından **X'e** tıklayarak eşleşmeleri kaldırabilirsiniz.  

Bu sorunu nasıl çözeceklerini öğrenmek için bu videoyu izleyin veya okumaya devam edin. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![Bağlan E-postaları Düğmesi](_img/connect-emails/connect-emails-button.png "Kullanıcılarınızı Bağlan Microsoft hesaplarıyla kendi kullanıcılarınızı aynı olacak şekilde değiştirmek için E-postalara Azure Active Directory")

Hataları düzeltmek veya Azure **AD'nizin** eksik bilgilerini doldurmak için Arama Dizinini de kullanabilirsiniz. Tüm eşleşmeler doğru görünüyorsa Geçerli kimlik  düğmesini seçerek tek tek seçmek yerine eşleşen tüm girişleri seçebilirsiniz.  

> [!div class="mx-imgBorder"]
> ![Bağlan E-postaLarını Dışarı Çıkma](_img/connect-emails/connect-emails-flyout.png "Azure AD kimlikleriyle hangi aboneleri eşleşmek istediğinizi seçin ve Devam'a tıklayın.")

Ardından **Devam'a** tıklayın. Bu, sizi yer alacak değişikliklerin listesine utur. Kabul ediyorsanız **Kaydet'e** tıklayın; değişiklikler yapılır. Aboneniz ayrıca aboneliğinde bir sonraki oturum açmalarında değişiklik hakkında bilgi alan bir ileti alır.  Bu listede yalnızca abonelikte eşlene iki abonenin Azure Active Directory olduğunu farkedersiniz.  Bizim örneğimizde, Zamank'ın Azure AD'de karşılık gelen bir adresi Microsoft hesabı hesabı (MSA) bir iş hesabıyla eşleşmedi. 

> [!div class="mx-imgBorder"]
> ![Bağlan E-posta Onayı](_img/connect-emails/connect-emails-confirm.png "Önerilen değişiklikleri uygulamak için Devam'a ve ardından Kaydet'e tıklayın.") 

> [!NOTE]
> Oturum açma e-posta adresini düzenleyseniz, bu yalnızca abone tarafından üzerinde aboneliğinde oturum açması için kullanılan e-postayı https://my.visualstudio.com günceller. Abone diğer e-posta adresini kullanarak Azure veya Pluralsight gibi avantajları zaten etkinleştirdi ise, aboneye erişmek için bu e-posta adreslerini kullanmaya devam etmek zorunda olur. Erişen yeni avantajlar için yeni e-posta adresini kullanmaları gerekir. 

## <a name="support-resources"></a>Destek kaynakları
- Visual Studio Aboneliklerinin yönetimiyle ilgili yardım için, Visual Studio [ile iletişime geçin.](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

##  <a name="next-steps"></a>Sonraki adımlar
- Abonelerin e-posta adreslerini güncellediyseniz, onlara oturum açma bilgilerini değiştirdiğini bildirmek istiyor olabilir.  Ayrıca güncelleştirilmiş bilgileri içeren bir e-posta da alırlar.
- Kuruluşta [abonelerin listesini filtrelemek,](search-license.md) değişmesi gereken oturum açma e-posta adreslerini aramanız yararlı olabilir.