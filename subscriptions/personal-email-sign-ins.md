---
title: VLSC 'de görünen kişisel e-postalar
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.assetid: 3f4b0528-03f0-4a02-b3c3-a39292a9bbe1
ms.date: 09/22/2020
ms.topic: conceptual
description: Visual Studio abonelikleri – My aboneleri için hotmail veya Gmail adreslerini görüyorum mi?
ms.openlocfilehash: dc2de6c852f39f789fb07358384ad490d13f137c
ms.sourcegitcommit: 4affcf2830337e6aba84621c3eda5faf5d0d4a01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91022680"
---
# <a name="visual-studio-subscriptions--why-do-i-see-personal-accounts-for-my-subscribers"></a>Visual Studio abonelikleri – aboneler için kişisel hesapları neden görüyorum?
Şirketler Toplu Lisanslama hizmeti Merkezi 'nden (VLSC) yeni Visual Studio [abonelikleri yönetim portalına](https://manage.visualstudio.com)geçirildikten sonra, Yöneticiler, bazı aboneler Için "oturum açma e-posta adresinin" hotmail veya Outlook gibi kişisel bir e-posta adresi gösterdiğini öğrenmektir.  

## <a name="cause"></a>Nedeni
Bu senaryo, eski MSDN abone deneyimiyle ilişkili oturum açma işlemlerinden dolayı oluşur. Kullanıcılar toplu lisans hizmeti Merkezi 'nden (VLSC), değişiklikler olmadan Visual Studio abonelikleri yönetim portalına geçirildi. Yöneticiler, kullanıcıların abonelik avantajlarına erişmek için kişisel hesapları kullandığını fark edemeyebilir. 2016 ' de tamamlanan Visual Studio abonesi geçişleri öncesinde, Visual Studio aboneliğini başarıyla kullanmak için iki eylem gerekiyordu:
1. "Atanan" Yönetici, iş veya okul e-posta adreslerini kullanarak tek bir abone için aboneliği "atandı".
2. Abone "etkinleştirildi".

Abone etkinleştirme işlemi sırasında: oturum açmak için bir Microsoft hesabı (MSA) gerekiyordu. Abone, iş veya okul hesabını (ör. bir MSA) yapmayı denemediyse tasha@contoso.com , yeni BIR MSA oluşturabilir veya var olan bir bu kişinin faydalanabilir. Bunun sonucunda "oturum açma e-posta adresi", "e-posta adresi atandı" olarak farklılık Açamıştı.

> [!NOTE]
> Üzerindeki modern abone deneyimi [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) hem iş/okul hem de Microsoft hesabı (MSA) kimlik türlerini destekler.

## <a name="solution"></a>Çözüm
Sorunu gidermek için, **e-postaları bağla** düğmesini seçmeniz yeterlidir ve sistem, MSAS olan hesapları, ilk ve son adı eşleştirmeden kuruluşunuzun Azure Active Directory (Azure AD) ile eşleştirmeyi dener. Bir hata varsa, eşleşmeyi sağ taraftaki **X** öğesine tıklayarak tüm eşleşmeyi kaldırabilirsiniz.  

Bunu nasıl düzelteceğinizi öğrenmek için bu videoyu izleyin veya okumaya devam edin. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4th6B]

> [!div class="mx-imgBorder"]
> ![E-postaları bağla düğmesi](_img/connect-emails/connect-emails-button.png "Kullanıcılarınıza Microsoft hesaplarıyla Azure Active Directory için e-postaları bağla ' ya tıklayın")

Ayrıca, hataları düzeltmek veya eksik bilgileri Azure AD 'nizden doldurmanız için **Arama dizinini** de kullanabilirsiniz. Tüm eşleşmeler doğru olursa, **geçerli kimlik** düğmesini seçerek tüm eşleşen girdileri seçebilirsiniz ve tek seferde seçebilirsiniz.  

> [!div class="mx-imgBorder"]
> ![E-postaların bağlantısını dışarı geçirin](_img/connect-emails/connect-emails-flyout.png "Azure AD kimlikleriyle eşleştirmek istediğiniz aboneleri seçin ve devam ' a tıklayın.")

İleri ' ye tıklayarak **devam edin** ve yapılacak değişikliklerin bir listesini alırsınız. Kabul ediyorsanız, **Kaydet** ' e tıklayın ve değişiklikler yapılır. Aboneliğiniz, bir dahaki sefer aboneliklerinde oturum açtıklarında değişiklik olduğunu bildiren bir ileti de alır.  Bu listede yalnızca Azure Active Directory eşleşen iki abone olduğuna dikkat edin.  Bizim örneğimizde, Frederick 'ın Azure AD 'de karşılık gelen bir adresi olmadığından Microsoft hesabı (MSA) bir iş hesabıyla eşleşmedi. 

> [!div class="mx-imgBorder"]
> ![E-postaları bağlama onayı](_img/connect-emails/connect-emails-confirm.png "Önerilen değişiklikleri uygulamak için devam ' a tıklayın ve ardından Kaydet ' e tıklayın.") 

> [!NOTE]
> Oturum açma e-posta adresini düzenlediğinizde, bu yalnızca abone tarafından tarihinde üzerinde oturum açmak için kullanılan e-postayı güncelleştirir https://my.visualstudio.com . Abone, diğer e-posta adresini kullanarak Azure veya Plurali gibi avantajları zaten etkinleştirmışsa, bunlara erişmek için bu e-posta adreslerini kullanmaya devam etmek gerekecektir. Eriştikleri yeni avantajlar için, yeni e-posta adresini kullanmaları gerekir. 

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

##  <a name="next-steps"></a>Sonraki adımlar
- Abone (ler) e-posta adreslerini güncelleştirdiyseniz, oturum açma bilgilerinin değiştiğini bildirmek isteyebilirsiniz.  Ayrıca, güncelleştirilmiş bilgileri içeren bir e-posta alırlar.
- Değişiklik yapması gerekebilecek herhangi bir oturum açma e-posta adresini aramak için kuruluşunuzdaki [abone listesini filtrelemek](search-license.md) yararlı olabilir.