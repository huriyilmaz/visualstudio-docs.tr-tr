---
title: Başlarken Çözümleyicileri ile | Microsoft Docs
description: Bu kaynakları kullanarak bir öğretici ve birkaç örnek içeren Visual Studio roslyn çözümleyicilerini kullanmaya başlama.
ms.custom: SEO-VS-2020
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d3ced34fdf54c6177aec9a500b9782a8a116d25d
ms.sourcegitcommit: fc874be3fe4637a23997b4ef2d99a2ee9a499581
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "135517716"
---
# <a name="get-started-with-roslyn-analyzers"></a>Kullanmaya başlayın çözümleyicileri ile birlikte

Api yazarları, Visual Studio'daki canlı, proje tabanlı kod çözümleyicileri ile etki alanına özgü kod analizini kendi NuGet gönderebilirsiniz. Bu çözümleyiciler .NET Compiler Platform (kod adı "Roslyn") olduğundan, siz satırı tamamlayana kadar bile siz yazarak kodunda uyarılar üretebilirler (artık sorunları bulmak için kodunuzu derlemek için beklemenize gerek yoktur). Çözümleyiciler ayrıca kodunuzu hemen temizlemenize izin Visual Studio ampul istemi aracılığıyla otomatik bir kod düzeltmesi ortaya çıkarabilir.

## <a name="get-started"></a>başlarken

[Roslyn çözümleyicilere genel bakış](../code-quality/roslyn-analyzers-overview.md)

[Öğretici: İlk çözümleyicinizi ve kod düzeltmenizi yazma](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Kod düzeltmeleri ekleme Adım adım kılavuz: Çözümleyici sorunları için kullanıcılara düzeltmeler sağlama](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Gerçek dünya Roslyn çözümleyicisi](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md)

[Üç çözümleyici GitHub gruplara göre kümeler üzerinde birkaç örnek](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET derleyici platform paketi sürüm başvurusu](roslyn-version-support.md)
- [GitHub OSS sitesinde daha fazla belge](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Roslyn çözümleyicileriyle uygulanan FxCop kuralları](../code-quality/fxcop-rule-port-status.md)
