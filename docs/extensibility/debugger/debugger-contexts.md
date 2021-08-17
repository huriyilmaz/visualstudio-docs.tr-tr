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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2d4df19ac3287788010a9db54cd1f237aaf13089b16e418068cbcd334dfc2cb3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121343285"
---
# <a name="debugger-contexts"></a>Hata ayıklayıcı bağlamları
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklama içinde, hata ayıklama altyapısı (de) çeşitli farklı bağlamlarda aynı anda aşağıdaki şekilde çalışır:

- Bir programın yürütme akışındaki geçerli konumu açıklayan kod bağlamı.

- Kaynak belge içindeki geçerli konumu açıklayan belge bağlamı veya konumu.

- İfade değerlendirmesinin gerçekleştiği bağlamı açıklayan ifade değerlendirme bağlamı.

## <a name="in-this-section"></a>Bu bölümde
 [Kod bağlamı](../../extensibility/debugger/code-context.md) Kod bağlamını, bugünün çalışma zamanı mimarilerinde, geleneksel olmayan dillerde ve kodun yönergelerle gösterilemediği, ancak başka bazı yollarla bir programın yönerge akışında bir adres olarak ele alır.

 [Belge konumu](../../extensibility/debugger/document-position.md) bir kaynak dosyasındaki bir konuma ıde tarafından bilinen bir soyutlama yoluyla Visual Studio hata ayıklamada belge konumunu tanımlar.

 [Belge bağlamı](../../extensibility/debugger/document-context.md) kaynak dosyayla ilgili olarak Visual Studio hata ayıklama bölümünde belge bağlamını temsil eder. Ayrıca, sembol işleyicisinin bir kod bağlamını belgeleme bağlamına nasıl eşlediğini açıklar.

 [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md) Visual Studio bir ifade değerlendirme bağlamı hakkında bilgi sağlar. Örneğin, yığın çerçevesiyle ilişkili bir ifade değerlendirme bağlamı yerel değişkenleri, yöntem parametrelerini ve sınıf üyelerini değerlendirmek için bağlam sağlar.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimarisi kavramlarını açıklar.

 [Hata ayıklama bileşenleri](../../extensibility/debugger/debugger-components.md) hata ayıklama altyapısını (DE), ifade değerlendirici (EE) ve sembol işleyicisini (SH) içeren Visual Studio hata ayıklama bileşenlerine genel bakış sağlar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Bir program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
