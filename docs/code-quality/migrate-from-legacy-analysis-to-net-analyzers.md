---
title: FxCop'tan kaynak analizine (.NET çözümleyicileri) geçiş
ms.custom: SEO-VS-2020
description: Kodu ilk kez analiz etmeyi veya ikili analizden (FxCop) kaynak analizini (.NET çözümleyicileri) kullanarak yönetilen kodu analiz etme yolunun yeni bir yolu olarak geçiş yapmayı öğrenin.
ms.date: 03/06/2020
ms.topic: conceptual
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- FxCop, migration
- legacy analysis, migration
- source code analysis, migration
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 06c25f9667b677a7afdf639a05442fbb8a49831e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113984"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Eski analizden (FxCop) kaynak analizine (.NET çözümleyicileri) geçiş

.NET Compiler Platform ("Roslyn") çözümleyicileri tarafından yapılan kaynak analizi, yönetilen kod [için eski](../code-quality/code-analysis-for-managed-code-overview.md) analizin yerini alır. .NET Core ve .NET Standard gibi daha yeni proje şablonları için eski analiz kullanılamaz.

Bir dizi Roslyn kod çözümleyicisi olan .NET çözümleyicileri için eski analiz (FxCop) kurallarının birçoğu zaten yeniden yazılmıştır. Roslyn çözümleyicileri, derleyici yürütme sırasında kaynak kodu tabanlı analizler çalıştırabilir. Çözümleyici sonuçları, derleyici sonuçlarıyla birlikte rapor edilir.

Eski analiz ile kaynak analizi arasındaki farklar hakkında daha fazla bilgi için aşağıdakilere bakın:

- [Kaynak kodu analiziyle eski analiz karşılaştırması](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [.NET çözümleyicileri hakkında SSS](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Geçiş

Kaynak analizine geçiş yapmak için [.NET çözümleyicilerini etkinleştirin veya yükleyin.](install-net-analyzers.md) Eski analiz kuralı ihlalleri gibi kaynak kodu analizi ihlalleri de kaynak kodundaki hata Visual Studio. Ayrıca kaynak kod analizi ihlalleri, kod düzenleyicisinde rahatsız olan kodun altında *geçişler* olarak da ortaya çıktı. Geçişin rengi, kuralın [önem derecesi ayarına](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) bağlıdır. Yeni .NET çözümleyicileri ile bağlantı noktası yapılan kuralların durumunu görmek için bkz. [Bağlantı noktası ve raporlanmamış kurallar.](../code-quality/fxcop-rule-port-status.md)

> [!NOTE]
> 2019 Visual Studio 16.8 ve .NET 5.0'dan önce, bu çözümleyiciler NuGet `Microsoft.CodeAnalysis.FxCopAnalyzers` [olarak gönderildi.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) 2019 Visual Studio 16.8 ve .NET 5.0'dan başlayarak, bu çözümleyiciler [.NET SDK'sı ile birlikte gelir.](/dotnet/fundamentals/code-analysis/overview) Bunlar, paket NuGet `Microsoft.CodeAnalysis.NetAnalyzers` [kullanılabilir.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Daha fazla bilgi için [bkz. FxCop çözümleyicilerinden .NET çözümleyicilere geçiş.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

## <a name="configuration"></a>Yapılandırma

.NET çözümleyicilerini yapılandırma hakkında daha fazla bilgi edinmek için:

- .NET çözümleyicilerini yapılandırmak için [bkz. .NET çözümleyicilerini yapılandırma.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

- EditorConfig veya bir kural kümesi dosyasıyla önceden tanımlanmış kuralları kullanarak çözümleyicileri yapılandırma hakkında bilgi için [bkz. Kural kategorisini etkinleştirme.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

## <a name="see-also"></a>Ayrıca bkz.

- [FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme](migrate-from-fxcop-analyzers-to-net-analyzers.md)
