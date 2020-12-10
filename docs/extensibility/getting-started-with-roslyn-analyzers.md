---
title: Roslyn çözümleyicilerine Başlarken | Microsoft Docs
description: Visual Studio 'da Roslyn Çözümleyicileri ile çalışmaya başlamak için bu kaynakları kullanın; bir öğretici ve birkaç örnek içerir.
ms.custom: SEO-VS-2020
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c63510083f227f617b2a11ddec07510ffd792433
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994362"
---
# <a name="get-started-with-roslyn-analyzers"></a>Roslyn Çözümleyicileri ile çalışmaya başlama

Visual Studio 'da canlı, proje tabanlı kod Çözümleyicileri sayesinde, API yazarları, NuGet paketlerinin bir parçası olarak etki alanına özgü kod analizini sevk edebilir. Bu çözümleyiciler .NET Compiler Platform (kod-adı "Roslyn") tarafından korunduğundan, satırı bitirmeden (sorunları çözmek için kodunuzu derlemek için daha fazla beklememeniz gerekmez) kodunuzda uyarı üretebilirler. Çözümleyiciler, kodunuzu hemen temizleyebilmeniz için Visual Studio ampul istemiyle otomatik bir kod düzeltmesini de yüzeylere açabilir.

## <a name="get-started"></a>başlarken

[Roslyn çözümleyicilerine genel bakış](../code-quality/roslyn-analyzers-overview.md)

[Öğretici: ilk çözümleyicinizi ve kod düzeltmesini yazma](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Kod düzeltmeleri ekleme Izlenecek yol: çözümleyici sorunları için kullanıcılara düzeltmeler sağlama](/archive/msdn-magazine/2015/february/csharp-adding-a-code-fix-to-your-roslyn-analyzer)

[Gerçek dünya Roslyn Çözümleyicisi](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) ve ayrıca [konuşabilirsiniz](https://channel9.msdn.com/events/Build/2015/3-725)

[GitHub 'daki birkaç örnek, üç tür çözümleyiciler halinde gruplandırılır](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET derleyicisi platform paketi sürüm başvurusu](roslyn-version-support.md)
- [GitHub OSS sitesinde daha fazla belge](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Roslyn Çözümleyicileri ile uygulanan FxCop kuralları](../code-quality/fxcop-rule-port-status.md)
