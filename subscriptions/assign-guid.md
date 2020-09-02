---
title: Visual Studio abonelerine belirli GUID 'Ler atama | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Yöneticilerin abonelere nasıl özel abonelik GUID 'SI olabileceğini öğrenin
ms.openlocfilehash: e6c50239721d810964f2b95e0ec3509999d2f4d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "87235192"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio abonelikleri yönetim portalı 'nda belirli abonelikleri atama

Yöneticiler artık bireysel abonelere belirli abonelikler atamak için Visual Studio abonelikleri yönetim portalını kullanabilir.  Bu, kuruluşun kısa bir süre için aboneliğe erişmesi gereken geçici personeli veya satıcıları olduğu durumlarda yararlı olabilir.  Yöneticiler, daha önce kısmen kullanılan bir abonelik atayabilir ve daha uzun süreli kullanım için yeni aboneliklerini bırakır.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Kullanıcılara belirli abonelik GUID 'Leri atama

Kişilere belirli abonelikler atama süreci, bireysel kullanıcılara genel olarak benzersiz tanımlayıcılar (GUID 'Ler) atamak için mevcut iki yönetim işleminin kullanılmasını içerir.  Üç adımlı işlem, geçerli aboneliklerinizin ve atamalarınızın listesini, atamak istediğiniz belirli GUID 'Leri tanımlamak için kullanarak ve ardından yeni atamaları karşıya yüklemek için toplu ekleme işlemini kullanarak, bu listeyi kullanarak dışarı aktarmayı içerir.

### <a name="export-your-subscriptions-information"></a>Abonelik bilgilerinizi dışarı aktarın

Dışarı aktarma işlemini gerçekleştirmek için:
1. [Yönetim portalında](https://manage.visualstudio.com)oturum açın.
2. **Dışarı aktar** sekmesini seçin. bu dosya yerel makinenize indirilir. Dosya, Kullanıcı aboneliklerinizi içeren sözleşmenin adının yanı sıra dışarı aktarma tarihini de içerecektir.
> [!div class="mx-imgBorder"]
> ![Aboneleri dışarı aktar](_img/exporting-subscriptions/exporting-subscriptions.png "Abone bilgileriyle atanan aboneliklerinizin listesini kaydetmek için dışarı aktar ' a tıklayın.")

### <a name="identify-the-guids-you-want-to-assign"></a>Atamak istediğiniz GUID 'Leri belirler

Önceden verme aracını kullandıysanız, oluşturulan elektronik tabloya yeni alanların eklendiğini fark edeceksiniz.  Bunlar, her aboneliğin durumunu ve kullanıcılara atamak istediğinizi belirlemenize yardımcı olur.  

- **Abonelik durumu**: Bu alan "atanmış" veya "atanmamış" olduğunu gösterir.  Bir abonelikte "atanmış" durumu varsa, bu, ad, e-posta vb. gibi kullanıcı bilgilerine de sahip olur. 
- **Kullanım durumu**: kullanım durumu "yeni" olarak, bir kullanıcıya hiçbir zaman atanmamış olduğunu veya bir kullanıcıya bir noktada atanmış olduğunu gösteren "kullanılan" anlamına gelir.  

Bireysel kullanıcılara hangi aboneliklerde atamak istediğinizi öğrenmek için bu alanlardaki değerleri, elektronik tablodaki diğer bilgilerle birlikte kullanabilirsiniz. Listeyi durum, abonelik düzeyi, sona erme tarihi vb. ile daraltmaya yardımcı olmak için Excel 'de bir filtre uygulayabilirsiniz. 

### <a name="upload-your-new-assignments"></a>Yeni atamalarınızı karşıya yükleyin

Son adım, **toplu ekleme** şablonunu indirmenin yanı sıra atamak istediğiniz abonelikler için gerekli bilgileri doldurmanızı ve şablonu karşıya yüklemenizi sağlar.  Bu işlemin tamamen açıklaması için lütfen bkz. [birden çok kullanıcı ekleme](assign-license-bulk.md) makalesi.  

> [!IMPORTANT]
> Başarılı bir karşıya yükleme sağlamak için lütfen şunları yaptığınızdan emin olun:
> - **Toplu Ekle**' yi seçtiğinizde iletişim kutusunda bağlantılı şablonu kullanıyorsunuz.  Tüm gerekli alanları içeremeyeceği için şablonun yerel olarak depolanmış bir kopyasını kullanmayın.  Eski bir şablon kullanmak, karşıya yüklemenin başarısız olmasına neden olur. 
> - Şablonda **gerekli** olarak gösterilen tüm alanlar tamamlanmıştır.
> - **Hata iletisi** sütununda listelenen bir hata yok.
> - Her GUID, şablonda yalnızca bir kez kullanılır. 
> - Şablondaki abonelik düzeyi, dışarıya aktarılmış listedeki GUID 'in aboneliğiyle eşleşir. 
> - GUID, zaten dışarıya alınmış listedeki başka bir kullanıcıya atanmamış. 

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>Soru-cevap kullanıcısına şu anda hangi aboneliğin atandığını nasıl değiştirebilirim?
Y: bir kullanıcıya hangi GUID 'nin atandığını değiştirmek istiyorsanız, önce bu kullanıcı için aboneliği silmeniz gerekir.  Daha fazla bilgi için lütfen [abonelik silme](delete-license.md) makalemizi inceleyin.  Bu Kullanıcı için aboneliği sildikten sonra, listeyi dışarı aktarmak ve yeni abonelik bilgilerini karşıya yüklemek için yukarıda özetlenen işlemi kullanın.  

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Artık kullanıcılara abonelikler atadıktan sonra, diğer yönetim görevlerinin nasıl gerçekleştirileceğini öğrenin.
- [Ayrı abonelikler atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)


