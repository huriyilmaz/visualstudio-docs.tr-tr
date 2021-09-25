---
title: FxCop'tan kaynak analizine (.NET çözümleyicileri) geçiş
ms.custom: SEO-VS-2020
description: Kodu ilk kez analiz etmeyi veya ikili analizden (FxCop) kaynak analizini (.NET çözümleyicileri) kullanarak yönetilen kodu analiz etmenin yeni yolunu nasıl geçirilmelerini öğrenin.
ms.date: 09/17/2021
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
ms.openlocfilehash: c1cdffdd0970818f19a07c188cee7a75711e73e3
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128427401"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-net-analyzers"></a>Eski analizden (FxCop) kaynak analizine (.NET çözümleyicileri) geçiş

.NET Compiler Platform ("Roslyn") çözümleyicileri tarafından yapılan kaynak analizi, yönetilen kod [için eski](../code-quality/code-analysis-for-managed-code-overview.md) analizin yerini alır. .NET Core ve .NET Standard gibi daha yeni proje şablonları için eski analiz kullanılamaz.

Bir dizi Roslyn kod çözümleyicisi olan .NET çözümleyicileri için eski analiz (FxCop) kurallarının çoğu zaten yeniden yazılmıştır. Roslyn çözümleyicileri, derleyici yürütme sırasında kaynak kodu tabanlı analizler çalıştırabilir. Çözümleyici sonuçları, derleyici sonuçlarıyla birlikte rapor edilir.

Eski analiz ile kaynak analizi arasındaki farklar hakkında daha fazla bilgi için aşağıdakilere bakın:

- [Kaynak kodu analiziyle eski analiz karşılaştırması](../code-quality/net-analyzers-faq.yml#what-s-the-difference-between-legacy-fxcop-and--net-analyzers-)

- [.NET çözümleyicileri hakkında SSS](../code-quality/net-analyzers-faq.yml)

## <a name="migration"></a>Geçiş

Kaynak analizine geçiş yapmak için:

1. [.NET çözümleyicilerini etkinleştirin veya yükleyin.](install-net-analyzers.md) Eski analiz kuralı ihlalleri gibi kaynak kodu analizi ihlalleri de veri kaynağındaki Hata Listesi penceresinde Visual Studio. Ayrıca kaynak kod analizi ihlalleri, kod düzenleyicisinde rahatsız olan kodun altında *geçişler* olarak da ortaya çıktı. Geçişin rengi, kuralın [önem derecesi ayarına](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) bağlıdır. Yeni .NET çözümleyicileri ile bağlantı noktası yapılan kuralların durumunu görmek için bkz. [Bağlantı noktası ve raporlanmamış kurallar.](../code-quality/fxcop-rule-port-status.md)

   > [!NOTE]
   > 2019 Visual Studio 16.8 ve .NET 5.0'dan önce, bu çözümleyiciler NuGet `Microsoft.CodeAnalysis.FxCopAnalyzers` [olarak gönderildi.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) 2019 Visual Studio 16.8 ve .NET 5.0'dan başlayarak, bu çözümleyiciler [.NET SDK'sı ile birlikte gelir.](/dotnet/fundamentals/code-analysis/overview) Bunlar aynı zamanda bir paket `Microsoft.CodeAnalysis.NetAnalyzers` [NuGet kullanılabilir.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) Daha fazla bilgi için [bkz. FxCop çözümleyicilerinden .NET çözümleyicilere geçiş.](migrate-from-fxcop-analyzers-to-net-analyzers.md)

1. CA0507'yi çözmek için proje için eski kod analizinin devre dışı bırakıldı olduğundan emin olun. Proje dosyasında özelliğini `RunCodeAnalysis` false olarak ayarlayın:

   `<RunCodeAnalysis>false</RunCodeAnalysis>`

   Veya **Project'Code Analysis'ı**  >   açın ve Derlemede çalıştır ayarını devre dışı olduğu **gibi.**

## <a name="configuration"></a>Yapılandırma

.NET çözümleyicilerini yapılandırma hakkında daha fazla bilgi edinmek için:

- .NET çözümleyicilerini yapılandırmak için [bkz. .NET çözümleyicilerini yapılandırma.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

- EditorConfig veya bir kural kümesi dosyasıyla önceden tanımlanmış kuralları kullanarak çözümleyicileri yapılandırma hakkında bilgi için [bkz. Kural kategorisini etkinleştirme.](/dotnet/fundamentals/code-analysis/code-quality-rule-options)

## <a name="see-also"></a>Ayrıca bkz.

- [FxCop çözümleyicilerinden .NET çözümleyicilerine geçirme](migrate-from-fxcop-analyzers-to-net-analyzers.md)
