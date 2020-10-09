---
title: FxCop 'den kaynak analizine (FxCop çözümleyicileri) geçiş
ms.custom: SEO-VS-2020
description: Kodu ilk kez analiz etmeyi veya ikili analizden (FxCop) kaynak analizini (FxCop çözümleyicileri) kullanarak yönetilen kodu analiz etmenin yeni yoluna nasıl geçireceğinizi öğrenin.
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
manager: jillfra
ms.openlocfilehash: cb75b7374e7f88f4643a5ecc4a9c193d8144efc4
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91860484"
---
# <a name="migrate-from-legacy-analysis-fxcop-to-source-analysis-fxcop-analyzers"></a>Eski analizden (FxCop) kaynak analizine (FxCop çözümleyicileri) geçiş

.NET Compiler Platform ("Roslyn") Çözümleyicileri kaynak analizi, yönetilen kod için [eski analizler](../code-quality/code-analysis-for-managed-code-overview.md) yerini alır. .NET Core ve .NET Standard projeleri gibi daha yeni proje şablonları için eski analiz kullanılamaz.

Birçok eski analiz (FxCop) kuralı, bir Roslyn kod Çözümleyicileri kümesi olan FxCop çözümleyicileri için zaten yeniden yazıldı. FxCop çözümleyicileri, proje veya çözüm tarafından başvurulan [bir NuGet paketi olarak yüklersiniz](install-fxcop-analyzers.md#nuget-package) . FxCop çözümleyicileri, derleyici yürütme sırasında kaynak kodu tabanlı analizler çalıştırır. Çözümleyici sonuçları derleyici sonuçlarıyla birlikte raporlanır.

Eski analiz ve kaynak analizi arasındaki farklılıklar hakkında daha fazla bilgi için aşağıdakilere bakın:

- [Kaynak kodu analizi ve eski analiz karşılaştırması](../code-quality/fxcop-analyzers-faq.md#whats-the-difference-between-legacy-fxcop-and-fxcop-analyzers)

- [FxCop çözümleyicileri hakkında SSS](../code-quality/fxcop-analyzers-faq.md)

Kaynak analizine geçiş yapmak için [FxCop çözümleyicileri](../code-quality/install-fxcop-analyzers.md)' ni yükler. Eski analiz kuralı ihlallerine benzer şekilde, kaynak kodu çözümleme ihlalleri Visual Studio 'daki Hata Listesi penceresinde görüntülenir. Ayrıca, kaynak kodu çözümleme ihlalleri, kod Düzenleyicisi 'nde, sorunlu kodun altında *dalgalı çizgiler* olarak da görünür. Dalgalı çizginin rengi kuralın [önem derecesi ayarına](../code-quality/use-roslyn-analyzers.md#configure-severity-levels) bağlıdır. Yeni FxCop çözümleyicilerine yapılan kuralların durumunu görmek için bkz. bağlantı noktası [ve olmayan kurallar](../code-quality/fxcop-rule-port-status.md).

FxCop çözümleyicileri 'nin nasıl yapılandırılacağı hakkında daha fazla bilgi edinmek için:

- FxCop çözümleyicileri yapılandırmak için bkz. [FxCop çözümleyicileri yapılandırma](/dotnet/fundamentals/code-analysis/code-quality-rule-options).

- EditorConfig veya bir kural kümesi dosyası ile önceden tanımlanmış kuralları kullanarak Çözümleyicileri yapılandırma hakkında bilgi edinmek için bkz. [kuralların kategorisini etkinleştirme](/dotnet/fundamentals/code-analysis/code-quality-rule-options).
