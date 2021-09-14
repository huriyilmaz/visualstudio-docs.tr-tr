---
title: FxCop 'den kaynak analizine (.NET Çözümleyicileri) geçiş
ms.custom: SEO-VS-2020
description: Kodu ilk kez analiz etmeyi veya ikili analizden (FxCop) kaynak analizini (.NET Çözümleyicileri) kullanarak yönetilen kodu analiz etmenin yeni yoluna nasıl geçirebileceğinizi öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631863"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Eski analizden (FxCop) kaynak analizine (.NET Çözümleyicileri) geçiş

.NET Compiler Platform ("roslyn") çözümleyicileri kaynak analizi, yönetilen kod için [eski analizler](../code-quality/code-analysis-for-managed-code-overview.md) yerini alır. .NET Core ve .NET Standard projeleri gibi daha yeni proje şablonları için eski analiz kullanılamaz.

Eski analiz (FxCop) kurallarının birçoğu, bir dizi Roslyn kod Çözümleyicileri olan .NET Çözümleyicileri için zaten yeniden yazıldı. Roslyn Çözümleyicileri, derleyici yürütmesi sırasında kaynak kodu tabanlı analiz çalıştıranlar. Çözümleyici sonuçları derleyici sonuçlarıyla birlikte raporlanır.

Eski analiz ve kaynak analizi arasındaki farklılıklar hakkında daha fazla bilgi için aşağıdakilere bakın:

- [Kaynak kodu analizi ve eski analiz karşılaştırması](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [.NET Çözümleyicileri hakkında SSS](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Geçiş

Kaynak analizine geçiş yapmak için [.net Çözümleyicileri ' ni etkinleştirin veya](install-net-analyzers.md)bu işlemi yapın. Eski analiz kuralı ihlalleri gibi, kaynak kodu çözümleme ihlalleri Visual Studio Hata Listesi penceresinde görüntülenir. Ayrıca, kaynak kodu çözümleme ihlalleri, kod Düzenleyicisi 'nde, sorunlu kodun altında *dalgalı çizgiler* olarak da görünür. Dalgalı çizginin rengi kuralın [önem derecesi ayarına](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) bağlıdır. Yeni .NET çözümleyicilerine yönelik kuralların durumunu görmek için bkz. bağlantı noktası [ve olmayan kurallar](../code-quality/fxcop-rule-port-status.md).

> [!NOTE]
> 2019 16,8 ve .net 5,0 Visual Studio önce, bu çözümleyiciler `Microsoft.CodeAnalysis.FxCopAnalyzers` [NuGet paketi](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)olarak sevk edildi. Visual Studio 2019 16,8 ve .net 5,0 'den başlayarak, bu çözümleyiciler [.net SDK 'ya dahildir](/dotnet/fundamentals/code-analysis/overview). `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet paket](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers)olarak da kullanılabilir. Daha fazla bilgi için bkz. [FxCop çözümleyicilerine .net çözümleyicilerine geçiş](migrate-from-fxcop-analyzers-to-net-analyzers.md).

## <a name="configuration"></a>Yapılandırma

.NET Çözümleyicileri 'nin nasıl yapılandırılacağı hakkında daha fazla bilgi edinmek için:

- .NET Çözümleyicileri yapılandırmak için bkz. [.net Çözümleyicileri yapılandırma](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- EditorConfig veya bir kural kümesi dosyası ile önceden tanımlanmış kuralları kullanarak Çözümleyicileri yapılandırma hakkında bilgi edinmek için bkz. [kuralların kategorisini etkinleştirme](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

## <a name="see-also"></a>Ayrıca bkz.

- [FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme](migrate-from-fxcop-analyzers-to-net-analyzers.md)
