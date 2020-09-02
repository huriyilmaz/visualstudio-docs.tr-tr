---
title: Hata ayıklayıcı bağlamları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56825fe299147e60c5ed9dfcefa491a427ab59e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738966"
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
