---
title: Visual Studio abonelerine belirli GUID'ler atama | Microsoft Dokümanlar
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Yöneticilerin abonelere özel abonelik GUID'i nasıl kullanabileceğini öğrenin
ms.openlocfilehash: e2e8cd4f5d07f218fc23c0b7b6f28ababc25263f
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072599"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio Abonelikleri Yönetim Portalı'na belirli abonelikler atama

Yöneticiler artık bireysel abonelere belirli abonelikler atamak için Visual Studio Abonelikleri Yönetim Portalı'nı kullanabilirler.  Bu, kuruluşun kısa bir süre için aboneliğe erişilmesi gereken geçici personeli veya satıcıları olduğu durumlarda yararlı olabilir.  Yöneticiler, yeni aboneliklerini uzun süreli kullanım için bırakarak kısmen kullanılmış bir abonelik atayabilir.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Kullanıcılara belirli abonelik GUID'leri atama

Bireylere belirli abonelikler atama işlemi, bireysel kullanıcılara belirli abonelik Globally Benzersiz Tanımlayıcılar (GUIDs) atamak için iki mevcut yönetim sürecinden yararlanmayı içerir.  Üç adımlı işlem, geçerli aboneliklerinizin ve atamalarınızın bir listesini dışa aktarmayı, bu listeyi atamak istediğiniz belirli GUID'leri tanımlamak için kullanmayı ve ardından yeni atamaları yüklemek için toplu ekleme işlemini kullanmayı içerir.

### <a name="export-your-subscriptions-information"></a>Abonelik bilgilerinizi dışa aktarma

Dışa aktarmayı gerçekleştirmek için:
1. [İdare Portalı'nda](https://manage.visualstudio.com)oturum açın.
2. **Dışa Aktar** sekmesini seçin ve dosya yerel makinenize indirilir. Dosya, kullanıcı aboneliklerinizi içeren sözleşmenin adını ve dışa aktarma tarihini içerir.
> [!div class="mx-imgBorder"]
> ![İhracat aboneleri](_img/exporting-subscriptions/exporting-subscriptions.png)

### <a name="identify-the-guids-you-want-to-assign"></a>Atamak istediğiniz GUID'leri tanımlama

Dışa Aktarma aracını daha önce kullandıysanız, üretilen elektronik tabloya yeni alanların eklendiğini fark edeceksiniz.  Bunlar, her aboneliğin durumunu ve kullanıcılara hangilerini atamak istediğinizi belirlemenize yardımcı olur.  

- **Abonelik Durumu**: Bu alan "atanmış" veya "atanmamış" olarak belirtilir.  Bir aboneliğin "atanmış" statüsü varsa, ad, e-posta vb. gibi kullanıcı bilgileriyle ilişkili dir. 
- **Kullanım Durumu**: Kullanım durumu, bir kullanıcıya hiç atanmamış olduğu anlamına gelen "yeni"yi veya bir noktada kullanıcıya atandığını gösteren "kullanılmış" anlamına gelir.  

Tek tek kullanıcılara hangi abonelikleri atamak istediğinizi belirlemek için bu alanlardaki değerleri elektronik tablodaki diğer bilgilerle birlikte kullanabilirsiniz. Listeyi duruma, abonelik düzeyine, son kullanma tarihine vb. göre daraltmaya yardımcı olmak için Excel'de bir filtre uygulayabilirsiniz. 

### <a name="upload-your-new-assignments"></a>Yeni atamalarınızı yükleyin

Son **adım, Toplu ekleme** şablonuna indirgin, atamak istediğiniz abonelikler için gerekli bilgileri doldurmak ve şablonu yüklemektir.  Bu işlemin tam bir açıklaması için lütfen [birden çok kullanıcı ekle](assign-license-bulk.md) makalemize bakın.  

> [!IMPORTANT]
> Başarılı bir yükleme sağlamak için lütfen aşağıdakileri yapın:
> - **Toplu ekle'yi**seçtiğinizde iletişim kutusunda bağlı şablonu kullanıyorsunuz.  Gerekli tüm alanları içermeyebileceğinden şablonun yerel olarak depolanmış bir kopyasını kullanmayın.  Eski bir şablon kullanmak yüklemenin başarısız olmasını neden olur. 
> - Şablonda **Gerekli** olarak gösterilen tüm alanlar tamamlandı.
> - **Hata iletisi** sütununda listelenen hata yok.
> - Her GUID şablonda yalnızca bir kez kullanılır. 
> - Şablondaki abonelik düzeyi, dışa aktarılan lar listesindeki GUID aboneliğiyle eşleşir. 
> - GUID, dışa aktarılan lar listesindeki başka bir kullanıcıya zaten atanmamış. 

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>S: Şu anda tek bir kullanıcıya atanan aboneliği nasıl değiştiririm?
C: Bir kullanıcıya hangi GUID'nin atandığını değiştirmek istiyorsanız, öncelikle o kullanıcının aboneliğini silmeniz gerekir.  Daha fazla bilgi için lütfen [abonelikleri sil](delete-license.md) makalemize bakın.  Söz kullanıcının aboneliğini siledikten sonra, listeyi dışa aktarmak ve yeni abonelik bilgilerini yüklemek için yukarıda özetlenen işlemi kullanın.  

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Artık kullanıcılara abonelikler atadığınıza göre, diğer yönetim görevlerini nasıl gerçekleştireceklerini öğrenin.
- [Tek tek abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [Maksimum kullanımı belirleme](maximum-usage.md)


