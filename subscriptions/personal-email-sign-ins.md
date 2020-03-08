---
title: VLSC 'de görünen kişisel e-postalar
author: evanwindom
ms.author: lank
manager: lank
ms.date: 03/03/2020
ms.topic: conceptual
description: Visual Studio abonelikleri – My aboneleri için hotmail veya Gmail adreslerini görüyorum mi?
ms.openlocfilehash: c4a3202bfb14246fa8057309de90bdc7c32db5df
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78410226"
---
# <a name="visual-studio-subscriptions--why-am-i-seeing-hotmail-or-gmail-addresses-for-my-subscribers"></a>Visual Studio abonelikleri – My aboneleri için hotmail veya Gmail adreslerini görüyorum mi?
Toplu Lisanslama hizmeti Merkezi 'nden (VLSC) yeni Visual Studio [abonelikleri yönetim portalına](https://manage.visualstudio.com)geçiş yaptıktan sonra Yöneticiler, bazı aboneler Için "oturum açma e-posta adresi" hotmail, Gmail veya Yahoo gibi üçüncü taraf e-posta adresini gösterir.  Daha fazla bilgi için [Bu videoya](https://www.youtube.com/watch?v=J61EYaVN-dQ&list=PLReL099Y5nReJhZ6o8CQFPSBgzGCHX99_&index=6)göz atın.

## <a name="cause"></a>Sebep
Bu senaryo, eski MSDN abone deneyimiyle ilişkili oturum açma işlemlerinden dolayı oluşur. Kullanıcılar toplu lisans hizmeti Merkezi 'nden (VLSC), değişiklikler olmadan Visual Studio abonelikleri yönetim portalına geçirildi. Yöneticiler, kullanıcıların abonelik avantajlarına erişmek için kişisel hesapları kullandığını fark edemeyebilir. 2016 ' de tamamlanan Visual Studio abonesi geçişleri öncesinde, Visual Studio aboneliğini başarıyla kullanmak için iki eylem gerekiyordu:
1. "Atanan" Yönetici, iş veya okul e-posta adreslerini kullanarak tek bir abone için aboneliği "atandı".
2. Abone "etkinleştirildi".

Abone etkinleştirme işlemi sırasında: oturum açmak için bir Microsoft hesabı (MSA) gerekiyordu. Abone, iş veya okul hesabını (ör. tasha@contoso.com) bir MSA olarak yapmaya çalışmadıysanız, yeni bir MSA oluşturabilir veya var olan bir MSA kullanabilir. Bunun sonucunda "oturum açma e-posta adresi", "e-posta adresi atandı" olarak farklılık Açamıştı.

> [!NOTE]
> [https://my.visualstudio.com](https://my.visualstudio.com?wt.mc_id=o~msft~docs) yeni abone deneyimi hem Iş/okul hem de Microsoft HESABı (MAA) kimlik türlerini destekler.

## <a name="solution"></a>Çözüm
Sorunu gidermek için, **e-postaları bağla** düğmesini seçmeniz yeterlidir ve sistem, MSAS olan hesapları, ilk ve son adı eşleştirmeden kuruluşunuzun Azure Active Directory (Azure AD) ile eşleştirmeyi dener. Bir hata varsa, eşleşmeyi sağ taraftaki **X** öğesine tıklayarak tüm eşleşmeyi kaldırabilirsiniz.  

> [!div class="mx-imgBorder"]
> ![Connect e-postaları düğmesi](_img/connect-emails/connect-emails-button.png)

Ayrıca, hataları düzeltmek veya eksik bilgileri Azure AD 'nizden doldurmanız için **Arama dizinini** de kullanabilirsiniz. Tüm eşleşmeler doğru görünebileceğinden, her seferinde birini seçmek yerine "tüm eşleşen aboneleri Seç" seçeneğini belirleyebilirsiniz.  

> [!div class="mx-imgBorder"]
> ![e-postaları bağlama](_img/connect-emails/connect-emails-flyout.png)

İleri ' ye tıklayarak "devam" a tıklayın. Bu işlem, yapılacak değişikliklerin yer aldığı bir ekrana götürür. Kabul ediyorsanız "Kaydet" e tıklayın ve değişiklikler yapılır. Aboneliğiniz, bir dahaki sefer aboneliklerinde oturum açtıklarında değişiklik olduğunu bildiren bir ileti de alır.   

> [!div class="mx-imgBorder"]
> ![Connect e-postaları onaylama](_img/connect-emails/connect-emails-confirm.png) 

> [!NOTE]
> Oturum açma e-posta adresini düzenlediğinizde, bu, yalnızca https://my.visualstudio.comaboneliklerinde oturum açmak için kullanılan e-postayı güncelleştirleridir. Abone, diğer e-posta adresini kullanarak Azure veya Plurali gibi avantajları zaten etkinleştirmışsa, bunlara erişmek için bu e-posta adreslerini kullanmaya devam etmek gerekecektir. Eriştikleri yeni avantajlar için, yeni e-posta adresini kullanmaları gerekir. 

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](https://docs.microsoft.com/visualstudio/)
- [Azure DevOps belgeleri](https://docs.microsoft.com/azure/devops/)
- [Azure belgeleri](https://docs.microsoft.com/azure/)
- [Microsoft 365 belgeleri](https://docs.microsoft.com/microsoft-365/)

##  <a name="next-steps"></a>Sonraki adımlar
- Abone (ler) e-posta adreslerini güncelleştirdiyseniz, oturum açma bilgilerinin değiştiğini bildirmek isteyebilirsiniz.  Ayrıca, güncelleştirilmiş bilgileri içeren bir e-posta alırlar.
- Değişiklik yapması gerekebilecek herhangi bir oturum açma e-posta adresini aramak için kuruluşunuzdaki [abone listesini filtrelemek](search-license.md) yararlı olabilir.  
