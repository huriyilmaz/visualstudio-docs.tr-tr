---
title: Süresi dolan ve abonelik sözleşmelerini Visual Studio yönetici portalı | Microsoft Docs
author: evanwindom
ms.author: amast
manager: amast
ms.assetid: f38092ba-051c-4e58-97f5-4255dbe873ba
ms.date: 10/08/2021
ms.topic: conceptual
description: Bir sözleşmenin süresi dolduğunda yöneticiler için ne olacağını öğrenin
ms.openlocfilehash: e92dd6af6656dc9907ef3ff6d626c3360e338e19
ms.sourcegitcommit: a1c18c491e310b00a43e76a911f778e643cd8f8d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "132995380"
---
# <a name="admin-portal-changes-for-expired-agreements"></a>Süresi dolan sözleşmeler için yönetici portalı değişiklikleri
Satın almak için kullanılan Visual Studio süresi dolduğunda, sözleşme ve onun içinde atanan abonelikler sınırlı bir süre için kullanılabilir kalır.  Bu süre tüm sözleşmeler için aynı olmayacaktır ve bu sürenin uzunluğu hakkında daha belirli bilgiler, e-postalar aracılığıyla ve yönetim portalında gelen iletişimlerde sağlanır.  Şirket planlarına bağlı olarak, abonelere yardımcı olmak veya önemli bilgilerin kaybını önlemek için bazı eylemlerde bulunduğunuzda harekete geçebilirsiniz.

## <a name="expiration-timeline"></a>Süre sonu zaman çizelgesi 
Sözleşme sona erme zaman çizelgesi üç aşamadan oluşur:
- [Süre sonu öncesinde](#prior-to-expiration)
- [Süresi Doldu](#expired)
- [Devre dışı](#disabled)

### <a name="prior-to-expiration"></a>Süre sonu öncesinde
Sözleşmenizin sona ermesi tarihinden yaklaşık 120 gün önce, hem süre sonuyla ilgili bilgiler hem de şirket anlaşmalarını yenilemeyi planp planlamalarına bağlı olarak atılması gerekmesi gereken adımlar ile yöneticilere ve süper yöneticilere bildirim göndermeye başlayacağız. 

### <a name="expired"></a>Süresi doldu
Sözleşmeniz sona erme tarihine ulaştığında, yöneticiler ve aboneler sınırlı bir süre için erişime sahip olur.  Bu, şirketinize devam eden satın alma işlemlerini tamamlama fırsatı sağlamak ve hem yöneticilerin hem de abonelerin, şirketinizin sözleşmelerini yenilemesi veya yeni bir satın alma tercihi yapmaları durumunda önemli verileri korumak için uygun adımları atma fırsatı sağlamak için yapılır.  Yöneticiler, gelecekte kullanmak üzere abone listeleri gibi bilgilerin korunmasına yardımcı olmak üzere belirli bilgilerin bağlantılarıyla bu süre boyunca bildirim almaya devam edecektir.  Aboneler ayrıca mevcut Azure abonelikleri içinde oluşturdukları varlıklar gibi bilgileri koruma konusunda rehberlik sağlayan bildirimler almaya başlar.  

Bu aşamada hem yöneticiler hem de aboneler ilgili portallara erişmeye devam eder.  Yöneticiler yine de tüm abonelik yönetimi görevlerini gerçekleştirebilir.  Aboneler abonelik avantajlarına sınırsız erişime sahip olmaya devam eder.  

> [!IMPORTANT]
> Yöneticiler ve aboneler ilgili kaynaklara erişmeye devam edecek ancak bu süre dolmadan önce önemli verilerin önk altına alınması ve bilgilere erişimin kaybedilmeden önce hızlı bir şekilde eyleme geçek olması önemlidir.

### <a name="disabled"></a>Devre dışı
Sözleşmeniz süresi dolan sürenin sonuna ulaştığında:
- Yöneticiler ve süper yöneticiler, yönetici portalında süresi dolan sözleşmelere erişimi [kaybeder.](https://manage.visualstudio.com)  Anlaşma içindeki aboneliklerde hiçbir değişiklik yapmaları mümkün olmayacak.  (Yönetici portalında geçerli olan diğer sözleşmelere erişim etkilenmez.  Yardım [al](https://manage.visualstudio.com/gethelp) sayfası da kullanılabilir olmaya devam eder.)
- Aboneler, abone portalında süresi dolan aboneliğe [erişimi kaybeder.](https://my.visualstudio.com)  Başka bir sözleşmenin parçası olarak atanmış başka abonelikleri varsa, bu abonelikler etkilenmez. Visual Studio aboneliğinin devre dışı bırakıldığı otuz gün sonra, Visual Studio aboneliğine bağlı olan tüm Azure abonelikleri de kaldırılır, bu nedenle abonelerin Azure varlıklarını korumak isteyen başka bir geçerli aboneliğe taşıması çok önemlidir.  Azure'ın bu durumda abonelere yol bu konuda yardımcı olacak kendi bildirim işlemi vardır.  

## <a name="preserving-your-information"></a>Bilginizi koruma
Yönetici olarak, sözleşmenizin süresi dolsa veya yeni bir anlaşma satın aldıysanız tutmak istediğiniz bazı bilgiler vardır. 
- En fazla kullanım.  Sözleşmenizin ömrü boyunca atadığı abonelik sayısını anlamak, kuruma, ihtiyaçlar için doğru sayıda abonelik satın alma konusunda yardımcı olabilir.  Kullanımınızı [görüntülemek ve bir raporu yönetici](maximum-usage.md) portalında dışarı aktarabilirsiniz.  
- Abone listeniz.  [Geçerli sözleşmenize abonelerin listesini dışarı](exporting-subscriptions.md) aktarmanız, bu abonelikleri hızla yeni bir sözleşmeye taşımanıza yardımcı olabilir.  

## <a name="assisting-subscribers"></a>Abonelere yardımcı olmak
Aboneliklerinin süresinin dolmasına ilişkin bildirimler almaya başlayan aboneler, sorularınız için size ulaşabilirsiniz.  Bu soruların yanıtlarının bazıları elbette şirketin planına bağlıdır.  Şirketiniz anlaşmayı yenilemeyi veya yenisini satın almayı planlıyorsa, abonelerin şirketin süreçteki yerini anlarına yardımcı olabilir.  Şirketiniz yenilemeyi niyetli değilse, önemli bilgilerini kaydetme sürecinde onlara yol yardımcı olabilir.  Bir sözleşmenin süresi dolduğunda bireysel abonelerin nasıl etkileyecektir? öğrenmek yararlı olabilir. Daha fazla bilgi için [Aboneliklerin süresi dolduğunda](subscription-expiration.md) makalemize göz atabilirsiniz. 

## <a name="moving-to-a-new-agreement"></a>Yeni bir sözleşmeye taşıma
Şirketiniz yeni bir sözleşme satın [](migrate-subscriptions.md) aldısa, aboneleri yeni sözleşmede yeniden yapmak yerine yeni bir sözleşmeye taşımanız gerekir.  

## <a name="next-steps"></a>Sonraki adımlar
- Tek tek [abonelerin süresi](subscription-expiration.md) dolan sözleşmeler tarafından nasıl etkilen olduğunu öğrenin.
- Abone listenizi [dışarı aktarmayı öğrenin.](exporting-subscriptions.md)
- Abonelikleri [yeni bir sözleşmeye taşımayı öğrenin](migrate-subscriptions.md)
- Abonelik gruplarını [kullanarak aboneleri Azure Active Directory](assign-license-bulk.md#use-azure-active-directory-groups-to-assign-subscriptions) öğrenin.
