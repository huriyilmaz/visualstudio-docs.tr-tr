---
title: Visual Studio aboneliklerini nasıl atayabilirim?
description: Son kullanıcılarınıza abonelikleri tek tek atayabilir veya Toplu ekleme özelliğini kullanıp daha fazla sayıda aboneyi bir kerede...
ms.faqid: group1_3
ms.topic: include
ms.assetid: 59eb35fd-ec94-41ce-b24c-a8a120976bac
author: CaityBuschlen
ms.author: cabuschl
ms.date: 09/30/2020
ms.openlocfilehash: 7493b261de24079b6b245d29749a908c54d341b1
ms.sourcegitcommit: c31815e140f2ec79e00a9a9a19900778ec11e860
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "91838315"
---
## <a name="how-do-i-assign-visual-studio-subscriptions"></a>Visual Studio aboneliklerini nasıl atayabilirim?

Son kullanıcılarınıza abonelikleri tek tek atayabilir veya Toplu ekleme özelliğini kullanıp daha fazla sayıda aboneyi bir kerede hızla ve kolayca karşıya yükleyebilirsiniz.

Abonelikleri tek tek atamak için:

1. [Manage.visualstudio.com](https://manage.visualstudio.com) adresinde sayfanın en üstündeki [Abonelikleri Yönet sekmesini](https://manage.visualstudio.com/subscribers) seçin
2. Ekle’yi seçin ve abonelik atamak istediğiniz kullanıcının adını ve e-posta adresini yazın.
    1. Kuruluşunuzda Azure Active Directory kullanıyorsa, ad alanı geçerli dizininizde kişi bulmak için arama yapar. Arama sonuçları arasından seçim yapabilir veya birini el ile ekleyebilirsiniz.
3. Abonenin [Visual Studio Abonelikler Portalı](https://my.visualstudio.com/)’nda oturum açtığında yazılım indirmelerine erişmesini istiyorsanız, İndirim ayarları bölümünde indirmeler düğmesini etkin olarak bıraktığınızdan emin olun.
4. Abonelerinize atama e-postasını hangi dilde göndereceğimizi bilmemiz için İletişim Tercihleri bölümünü tamamlayın.
5. Atamayla ilişkilendirilmiş notlar eklemek isterseniz Başvuru bölümünü kullanın.
6. Açılır panelin en altındaki Ekle’yi seçerek abonelik atamanızı tamamlayın. Aboneniz bir e-posta alır ve Visual Studio aboneliğini hemen kullanmaya başlayabilir (abonenizin etkinleştirme işlemi yapması gerekmez).

Abonelikleri toplu atamak için:

1. [Manage.visualstudio.com](https://manage.visualstudio.com) adresinde sayfanın en üstündeki [Abonelikleri Yönet sekmesini](https://manage.visualstudio.com/subscribers) seçin.
2. Toplu atama’yı seçin, Excel şablonunu indirin ve yerel bir kopyasını kaydedin.
3. Başvuru alanı dışındaki tüm alanlar gereklidir.
    1. Form alanlarından hiçbirinin virgül içermediğinden emin olun.
    2. Form alanlarının önündeki ve sonundaki boşlukları kaldırın.
    3. Adların veya soyadlarının iki bölümü (varsa) arasında ek boşluk olmamasına dikkat edin (örneğin, kişinin adı 'Fatma Gül' gibi iki bölümden oluşuyorsa 'FatmaGül' olarak yazılmalıdır).
4. [Manage.visualstudio.com](https://manage.visualstudio.com) adresine dönün, Toplu ekleme’yi seçin ve kaydedilmiş Excel şablonu kopyanızı karşıya yükleyin.
5. Karşıya yükleme başarılı olduğunda bir onay sayfası görürsünüz ve abone listeniz yeni abonelerinizle doldurulur. Aboneniz bir e-posta alır ve Visual Studio aboneliğini hemen kullanmaya başlayabilir (abonenizin etkinleştirme işlemi yapması gerekmez).

Abonelikleri hızla ve kolayca atama hakkında daha fazla bilgi edinmek için Visual Studio Abonelikleri Yönetici portalında abonelikleri atama konusuyla ilgili [diğer yazıları okuyun](../../../../assign-license.md#add-a-single-subscriber).  GitHub Enterprise ile Visual Studio aboneliklerini yönetme hakkında [daha fazla bilgi edinin](../../../../assign-github.md). 

## <a name="what-is-the-github-enterprise-setup-process"></a>GitHub Enterprise kurulum işlemi nasıldır? 

GitHub Enterprise, Visual Studio aboneliklerinden ayrı olarak kurulur ve yönetilir. GitHub Enterprise ile Visual Studio satın alındıktan sonra, manage.visualstudio.com'da sözleşme yapma işlemiyle paralel (ama ayrı) olarak GitHub Enterprise hesabı ayarlama işlemi başlatılır. Bu GitHub Enterprise hesabının oluşturulması biraz zaman alabilir.  

Şirketiniz GitHub Enterprise hesabını ayarladıktan sonra, kendilerine GitHub Enterprise ile Visual Studio abonelikleri atanan aboneler GitHub'dan Visual Studio aboneliklerinin bağlandığını bildiren bir e-posta alır. Aboneler bu e-postayı aldıktan sonra, uygun kuruluşuna davet almak için GitHub kuruluş yöneticilerine ulaşabilir. 

GitHub Enterprise ile Visual Studio aboneliklerini yönetme hakkında [daha fazla bilgi edinin](../../../../assign-github.md). GitHub Enterprise ayarlama işlemiyle ilgili diğer ayrıntılar için [abone belgelerine](../../../../access-github.md) bakın. 
