---
title: Kaynak Kontrol VSPackage Uygulanıp Uygulanmayacağını Belirleme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8707f3c1ced1cc2df9d3ae77280fc8779874a837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708715"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>Bir kaynak denetimi VSPackage uygulanıp uygulanmayacağını belirleme
Bu bölümde, kaynak kontrol çözümlerini genişletmek için kaynak denetimi eklentileri ve kaynak denetimi VSPackages seçeneklerini ayrıntılı olarak ele alır ve uygun bir entegrasyon yolu seçme konusunda geniş yönergeler sunar.

## <a name="small-source-control-solution-with-limited-resources"></a>Sınırlı kaynaklara sahip küçük kaynak kontrol çözümü
 Sınırlı kaynaklarınız varsa ve kaynak denetim paketi yazma yüküyle yüklenemiyorsa, Kaynak Denetimi Eklentisi API tabanlı eklentiler oluşturabilirsiniz. Daha fazla bilgi için [Kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)e bakın.

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Zengin bir özellik setine sahip büyük kaynak kontrol çözümü
 Kaynak Denetimi Eklentisi API'sini kullanarak yeterince yakalanmayan zengin bir kaynak denetim modeli sağlayan bir kaynak denetim çözümcetmek istiyorsanız, bir kaynak denetim paketini tümleştirme yolu olarak düşünebilirsiniz. Bu, özellikle kaynak denetimi olaylarını özel bir şekilde işleyebilir diye Kaynak Denetim Bağdaştırıcı Paketi'ni (kaynak denetimi eklentileriyle iletişim kuranarak ve temel bir kaynak denetimi kullanıcı arabirimi sağlayan) kendi paketiyle değiştirmek isterseniz geçerlidir. Zaten tatmin edici bir kaynak denetimi UI varsa ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]bu deneyimi korumak istiyorsanız, kaynak denetim paketi seçeneği sadece bunu yapmanızı sağlar. Kaynak kontrol paketi genel değildir ve yalnızca IDE ile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kullanılmak üzere tasarlanmıştır.

 Kaynak denetim mantığı ve Kullanıcı Arabirimi üzerinde esneklik ve daha zengin denetim sağlayan bir kaynak denetim çözümü uygulamak istiyorsanız, kaynak denetim paketi tümleştirme rotasını tercih edebilirsiniz. Şunları yapabilirsiniz:

1. Kendi kaynak denetimivsPackage kaydedin [(Kayıt ve seçim](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)bakın).

2. Varsayılan kaynak denetimi kullanıcı arabirimini özel kullanıcı arabiriminizle değiştirin [(Bkz. Özel kullanıcı arabirimi).](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

3. Kullanılacak glifleri belirtin ve Çözüm Gezgini glyph olaylarını işleyin (bkz. [Glyph denetimi).](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Sorgu Tut Ve Sorgu Kaydet olayları (bkz. [Sorgu Tut Sorgu kaydet](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)).

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
