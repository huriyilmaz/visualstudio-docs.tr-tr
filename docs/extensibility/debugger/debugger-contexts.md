---
title: Hata ayıklayıcı bağlamları | Microsoft Docs
description: 'Visual Studio hata ayıklama altyapısının farklı bağlamlarda nasıl çalıştığını öğrenin: kod bağlamı, belge bağlamı veya konumu ve ifade değerlendirme bağlamı.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5103561a420c3836f60a22790335522a83798966
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903677"
---
# <a name="debugger-contexts"></a>Hata ayıklayıcı bağlamları
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklama içinde, hata ayıklama altyapısı (de) çeşitli farklı bağlamlarda aynı anda aşağıdaki şekilde çalışır:

- Bir programın yürütme akışındaki geçerli konumu açıklayan kod bağlamı.

- Kaynak belge içindeki geçerli konumu açıklayan belge bağlamı veya konumu.

- İfade değerlendirmesinin gerçekleştiği bağlamı açıklayan ifade değerlendirme bağlamı.

## <a name="in-this-section"></a>Bu bölümde
 [Kod bağlamı](../../extensibility/debugger/code-context.md) Kod bağlamını, bugünün çalışma zamanı mimarilerinde, geleneksel olmayan dillerde ve kodun yönergelerle gösterilemediği, ancak başka bazı yollarla bir programın yönerge akışında bir adres olarak ele alır.

 [Belge konumu](../../extensibility/debugger/document-position.md) Visual Studio Hata ayıklamasında, IDE olarak bilinen bir kaynak dosyasındaki konumun bir soyutlaması aracılığıyla belge konumunu tanımlar.

 [Belge bağlamı](../../extensibility/debugger/document-context.md) Kaynak dosyayla ilgili olarak Visual Studio Hata ayıklamasında hangi belge bağlamının temsil ettiğini açıklar. Ayrıca, sembol işleyicisinin bir kod bağlamını belgeleme bağlamına nasıl eşlediğini açıklar.

 [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md) Visual Studio 'da bir ifade değerlendirme bağlamı hakkında bilgi sağlar. Örneğin, yığın çerçevesiyle ilişkili bir ifade değerlendirme bağlamı yerel değişkenleri, yöntem parametrelerini ve sınıf üyelerini değerlendirmek için bağlam sağlar.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimarisi kavramlarını açıklar.

 [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md) Hata ayıklama altyapısı (DE), ifade değerlendiricisi (EE) ve sembol işleyici (SH) dahil Visual Studio hata ayıklama bileşenlerine genel bakış sağlar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Bir program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
