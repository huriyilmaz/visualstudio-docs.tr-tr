---
title: Hata Ayıklama Bağlamları | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738966"
---
# <a name="debugger-contexts"></a>Hata ayıklama bağlamları
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklamada hata ayıklama altyapısı (DE) aşağıdaki gibi birkaç farklı bağlam içinde aynı anda çalışır:

- Bir programın yürütme akışındaki geçerli konumu açıklayan kod bağlamı.

- Kaynak belgedeki geçerli konumu açıklayan belge bağlamı veya konumu.

- İfade değerlendirmenin gerçekleşeceği bağlamı açıklayan ifade değerlendirme bağlamı.

## <a name="in-this-section"></a>Bu bölümde
 [Kod bağlamı](../../extensibility/debugger/code-context.md) Kod bağlamını, kodun yönergelerle değil, başka yollarla temsil edilebildiği geleneksel olmayan dillere karşı bugünün çalışma zamanı mimarilerinde bir programın yönerge akışında bir adres olarak tartışır.

 [Belge konumu](../../extensibility/debugger/document-position.md) Visual Studio'daki belge durumunu, IDE tarafından bilinen bir kaynak dosyadaki bir pozisyonun soyutlanması yoluyla tanımlar.

 [Belge bağlamı](../../extensibility/debugger/document-context.md) Visual Studio'da bir kaynak dosyayla ilgili olarak hata ayıklamada hangi belge bağlamını temsil ettiğini tartışır. Ayrıca, sembol işleyicisinin bir kod bağlamını belgeleme bağlamına nasıl eşlenebildiğini de tartışır.

 [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md) Visual Studio'da ifade değerlendirme bağlamı hakkında bilgi sağlar. Örneğin, yığın çerçevesiyle ilişkili bir ifade değerlendirme bağlamı, yerel değişkenleri, yöntem parametrelerini ve sınıf üyelerini değerlendirmek için bağlamı sağlar.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramları açıklar.

 [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md) Hata ayıklama motoru (DE), ifade değerlendiricisi (EE) ve sembol işleyicisini (SH) içeren Visual Studio hata ayıklama bileşenlerine genel bir bakış sağlar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerine bağlantılar içerir.
