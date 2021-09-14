---
title: Hata Ayıklayıcı Bağlamları | Microsoft Docs
description: 'Hata ayıklama altyapısının Visual Studio bağlamlar içinde nasıl çalışma olduğunu öğrenin: kod bağlamı, belge bağlamı veya konumu ve ifade değerlendirme bağlamı.'
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
ms.openlocfilehash: d7c06855b7ec216ec90d77fc0c0b9968d8da1be1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725846"
---
# <a name="debugger-contexts"></a>Hata ayıklayıcısı bağlamları
Hata [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ayıklamada, hata ayıklama altyapısı (DE) aşağıdaki gibi birkaç farklı bağlam içinde aynı anda çalışır:

- Bir programın yürütme akışındaki geçerli konumu açıklayan kod bağlamı.

- Kaynak belge içindeki geçerli konumu açıklayan belge bağlamı veya konumu.

- İfade değerlendirmenin hangi bağlamda olduğunu açıklayan ifade değerlendirme bağlamı.

## <a name="in-this-section"></a>Bu bölümde
 [Kod bağlamı](../../extensibility/debugger/code-context.md) Kod bağlamını, günümüzün çalışma zamanı mimarilerinde, kodun yönergelerle değil başka bir şekilde temsili mümkün olmayan dillerdeki çalışma zamanı mimarilerinde bir adres olarak ele alınmaktadır.

 [Belge konumu](../../extensibility/debugger/document-position.md) IDE tarafından Visual Studio kaynak dosyada bir konumun soyutlaması ile hata ayıklama sırasında belge konumunu tanımlar.

 [Belge bağlamı](../../extensibility/debugger/document-context.md) Bir kaynak dosyayla ilgili olarak Visual Studio hata ayıklamada hangi belge bağlamının temsil ettiğini tartışır. Ayrıca sembol işleyicisi bir kod bağlamını belge bağlamıyla nasıl eşlemektedir?

 [İfade değerlendirme bağlamı](../../extensibility/debugger/expression-evaluation-context.md) Verilerde ifade değerlendirme bağlamı hakkında bilgi Visual Studio. Örneğin, bir yığın çerçevesiyle ilişkili ifade değerlendirme bağlamı yerel değişkenlerin, yöntem parametrelerinin ve sınıf üyelerinin değerlendirilmesi için bağlam sağlar.

## <a name="related-sections"></a>İlgili bölümler
 [Hata ayıklama kavramları](../../extensibility/debugger/debugger-concepts.md) Ana hata ayıklama mimari kavramlarını açıklar.

 [Bileşenlerde hata ayıklama](../../extensibility/debugger/debugger-components.md) Hata ayıklama altyapısı (DE), ifade değerlendirici (EE) ve sembol işleyicisi (SH) dahil olmak Visual Studio hata ayıklama bileşenlerine genel bir bakış sağlar.

 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md) Program başlatma ve ifadeleri değerlendirme gibi çeşitli hata ayıklama görevlerinin bağlantılarını içerir.
