---
title: Roslyn Analizörleri ile Başlarken | Microsoft Dokümanlar
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711267"
---
# <a name="get-started-with-roslyn-analyzers"></a>Roslyn analizörleri ile başlayın

Visual Studio'daki canlı, proje tabanlı kod çözümleyicileri ile API yazarları NuGet paketlerinin bir parçası olarak etki alanına özgü kod çözümlemesi aktarabilirler. Bu çözümleyiciler .NET Derleyici Platformu (kod adı "Roslyn" tarafından desteklendirilmiştir) için, satırı bitirmeden önce bile yazarken kodunuzda uyarılar üretebilirler (sorunları bulmak için kodunuzu oluşturmak için artık beklemeyin). Çözümleyiciler ayrıca, kodunuzu hemen temizlemenize izin vermek için Visual Studio ampul istemi ile otomatik kod düzeltmesini yüzeye çıkarabilirsiniz.

## <a name="get-started"></a>başlarken

[Roslyn analizörleri genel bakış](../code-quality/roslyn-analyzers-overview.md)

[Öğretici: İlk çözümleyicinizi ve kod düzeltmenizi yazın](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Kod düzeltmeleri ekleme Walkthrough: Kullanıcıların çözümleyici sorunları için düzeltmeler sağlayın](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Gerçek dünya Roslyn analizörü](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) de bir [konuşma](https://channel9.msdn.com/events/Build/2015/3-725) olarak izleyebilirsiniz

[GitHub'da üç tür çözümleyiciye göre gruplanmış birkaç örnek](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET derleyici platformu paket sürüm başvurusu](roslyn-version-support.md)
- [GitHub OSS sitesinde daha fazla doküman](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Roslyn analizörleri ile uygulanan FxCop kuralları](../code-quality/fxcop-rule-port-status.md)
