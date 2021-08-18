---
title: VSPackage kaynak denetimi ne zaman uygulanır?
description: Kaynak denetimi çözümlerini genişletmek için kullanılabilen kaynak denetimi eklentileri ve kaynak denetimi VSPackage'ları Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5e16803a570c845e9283debcfb9e8d388b1cdd20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124665"
---
# <a name="determine-whether-to-implement-a-source-control-vspackage"></a>VSPackage kaynak denetimi uygulamanın gerekip gerek olmadığını belirleme

Bu bölümde, kaynak denetimi çözümlerini genişletmek için kaynak denetimi eklentileri ve kaynak denetimi VSPackage'ları seçenekleri ayrıntılı bir şekilde ele alındı ve uygun bir tümleştirme yolu seçme hakkında geniş yönergeler sağmaktadır.

## <a name="small-source-control-solution-with-limited-resources"></a>Sınırlı kaynaklara sahip küçük kaynak denetimi çözümü

 Sınırlı kaynaklarınız varsa ve kaynak denetim paketi yazma yüküyle yük altında olamazsanız, Kaynak Denetimi Eklentisi API tabanlı eklentiler oluşturabilirsiniz. Bu sayede kaynak denetim paketleriyle yan yana çalışabilirsiniz ve isteğe bağlı olarak kaynak denetimi eklentileri ile paketler arasında geçiş sabilirsiniz. Daha fazla bilgi için [bkz. Kayıt ve seçimi.](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

## <a name="large-source-control-solution-with-a-rich-feature-set"></a>Zengin özellik kümesine sahip büyük kaynak denetimi çözümü

 Kaynak Denetimi Eklentisi API'si kullanılarak yeterince yakalanması gereken zengin bir kaynak denetim modeli sağlayan bir kaynak denetimi çözümü uygulamak için tümleştirme yolu olarak bir kaynak denetim paketi düşünebilirsiniz. Bu durum özellikle kaynak denetim olaylarını özel bir şekilde işlemek için Kaynak Denetim Bağdaştırıcısı Paketini (kaynak denetim eklentileriyle iletişim kurar ve temel bir kaynak denetimi kullanıcı arabirimi sağlar) kendi kaynak denetimi arabiriminiz ile değiştirirken geçerlidir. Zaten tatmin edici bir kaynak denetimi kullanıcı arabiriminiz varsa ve bu deneyimi içinde korumak için [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kaynak denetim paketi seçeneği tam olarak bunu yapmanizi sağlar. Kaynak denetim paketi genel değildir ve yalnızca IDE ile kullanım [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] için tasarlanmıştır.

 Kaynak denetimi mantığı ve kullanıcı arabirimi üzerinde esneklik ve daha zengin denetim sağlayan bir kaynak denetimi çözümü uygulamak isterseniz, kaynak denetim paketi tümleştirme yolunu tercih edersiniz. Seçenekleriniz şunlardır:

1. Kendi kaynak denetimi VSPackage'nızı kaydetme (bkz. [Kayıt ve seçim).](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)

2. Varsayılan kaynak denetimi kullanıcı arabirimini özel kullanıcı arabiriminiz ile değiştirin [(bkz. Özel kullanıcı arabirimi).](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)

3. Kullanılacak glyph'leri belirtme ve Çözüm Gezgini işleme (bkz. [Glyph denetimi).](../../extensibility/internals/glyph-control-source-control-vspackage.md)

4. Sorgu Düzenleme ve Sorgu Kaydetme olaylarını işleme (bkz. [Sorgu Düzenleme Sorgu Kaydetme).](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Kaynak denetimi eklentisi oluşturma](../../extensibility/internals/creating-a-source-control-plug-in.md)
