---
title: Belirli GUID'leri Visual Studio abonelere | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.date: 03/19/2021
ms.topic: conceptual
description: Yöneticilerin abonelere abonelik GUID'lerini nasıl belirliyebilirsiniz?
ms.openlocfilehash: a0721029186605c6b9a277c9eb95a370a086d7d2
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725486"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Visual Studio Abonelikler Yönetim Portalı'Visual Studio belirli abonelikleri atama

Yöneticiler artık Visual Studio Abonelikler Yönetim Portalı'ni kullanarak bireysel abonelere belirli abonelikler atayabilirsiniz.  Bu, kuruluşun bir aboneliğe kısa bir süre için erişmesi gereken geçici personel veya satıcılara sahip olduğu durumlarda yararlı olabilir.  Yöneticiler zaten kısmen kullanılmış bir abonelik atayarak yeni aboneliklerini daha uzun süreli kullanım için bırakabilirsiniz.  

Kullanıcılara belirli abonelik GUID'lerini atama hakkında bilgi edinmek için videoyu izleyin veya okumaya devam etmeyi öğrenin. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Kullanıcılara belirli abonelik GUID'leri atama

Kişilere belirli abonelikleri atama işlemi, belirli bir aboneliğe genel olarak Benzersiz Tanımlayıcılar (GUID) atamak için mevcut iki yönetici işleminin tek tek kullanıcılara atanma sürecini içerir.  Üç adımlı işlem, geçerli abonelik ve atamaların listesini dışarı aktarmayı, atamak istediğiniz guid'leri belirlemek için bu listeyi kullanmayı ve ardından toplu ekleme işlemini kullanarak yeni atamaları karşıya yükleme işlemini içerir.

### <a name="export-your-subscriptions-information"></a>Abonelik bilgilerini dışarı aktarma

Dışarı aktarma işlemini gerçekleştirmek için:
1. Yönetim Portalı'da [oturum açın.](https://manage.visualstudio.com)
2. Dışarı **Aktar sekmesini** seçin. Dosya yerel makinenize indirecek. Dosya, kullanıcı aboneliklerinizi içeren sözleşmenin adını ve dışarı aktarma tarihini içerir.
> [!div class="mx-imgBorder"]
> ![Aboneleri dışarı aktarma](_img/exporting-subscriptions/exporting-subscriptions.png "Abone bilgileriyle atanan aboneliklerin listesini kaydetmek için Dışarı Aktar'a tıklayın.")

### <a name="identify-the-guids-you-want-to-assign"></a>Atamak istediğiniz GUID'leri belirleme

Dışarı Aktarma aracını daha önce kullandıysanız, üretilen elektronik tabloya yeni alanların ekli olduğunu fark edin.  Bunlar her aboneliğin durumunu ve kullanıcılara hangilerini atamak istediğinizi belirlemenize yardımcı olur.  

- **Abonelik Durumu:** Bu alan "atanan" veya "atanmamış" durumunu gösterir.  Bir aboneliğin durumu "atandı" ise, abonelikle ilişkili ad, e-posta gibi kullanıcı bilgileri de olur. 
- **Kullanım Durumu:** Kullanım durumu "yeni", yani bir kullanıcıya atanmadığı anlamına gelir veya belirli bir noktada kullanıcıya atandığı anlamına gelen "kullanıldı" anlamına gelir.  

Tek tek kullanıcılara hangi abonelikleri atamak istediğinizi belirlemek için bu alanlardaki değerleri ve elektronik tabloyu diğer bilgileri kullanabilirsiniz. Listeyi durum, abonelik düzeyi Excel sona erme tarihi gibi ölçütlere göre daraltmaya yardımcı olması için bu filtreyi uygulamanıza yardımcı olabilir. 

### <a name="upload-your-new-assignments"></a>Upload atamalarınızı düzenleme

Son adım Toplu ekleme şablonunu **indirmek,** atamak istediğiniz abonelikler için gerekli bilgileri doldurmak ve şablonu karşıya yüklemektir.  Bu sürecin eksiksiz bir açıklaması için Lütfen Birden çok [kullanıcı ekleme makalemize](assign-license-bulk.md) bakın.  

> [!IMPORTANT]
> Karşıya yüklemenin başarılı olduğundan emin olmak için lütfen şunların doğru olduğundan emin olun:
> - Toplu ekle'yi seçerek iletişim kutusunda bağlantılı şablonu **kullanıyorsanız.**  Şablonun tüm gerekli alanları içerene kadar yerel olarak depolanmış bir kopyasını kullanmayın.  Eski bir şablon kullanmak karşıya yüklemenin başarısız olmasına neden olur. 
> - Şablonda Gerekli **olarak gösterilen** tüm alanlar tamamlandı.
> - Hata iletisi sütununda hiçbir **hata listelenmiyor.**
> - Her GUID şablonda yalnızca bir kez kullanılır. 
> - Şablonda abonelik düzeyi, dışarı aktarıldı listesinde GUID'nin aboneliğiyle eştir. 
> - GUID zaten dışarı aktarıldı listesinde başka bir kullanıcıya atanmamış. 

## <a name="frequently-asked-questions"></a>Sık sorulan sorular
### <a name="q-how-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>S: Nasıl yaparım? bir kullanıcıya atanmış olan aboneliği nasıl değiştirebilirsiniz?
A: Bir kullanıcıya atanan GUID'i değiştirmek için önce o kullanıcının aboneliğini silmeniz gerekir.  Daha fazla bilgi için lütfen [Abonelikleri silme makalemize](delete-license.md) bakın.  Bu kullanıcının aboneliğini sildikten sonra, listeyi dışarı aktarın ve yeni abonelik bilgilerini karşıya yükleyin.  

## <a name="resources"></a>Kaynaklar
- [Abonelik desteği](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio belgeleri](/visualstudio/)
- [Azure DevOps belgeleri](/azure/devops/)
- [Azure belgeleri](/azure/)
- [Microsoft 365 belgeleri](/microsoft-365/)

## <a name="next-steps"></a>Sonraki adımlar
Kullanıcılara abonelik atadınız, şimdi de diğer yönetici görevlerini nasıl gerçekleştireceklerini öğrenin.
- [Bireysel abonelikleri atama](assign-license.md)
- [Birden çok abonelik atama](assign-license-bulk.md)
- [Abonelikleri düzenleme](edit-license.md)
- [Abonelikleri silme](delete-license.md)
- [En fazla kullanımı belirleme](maximum-usage.md)
