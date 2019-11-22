---
title: Roslyn çözümleyicilerine Başlarken | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2d45491fe031c01a31812f5ed4944f76d059cd60
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300010"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Roslyn Çözümleyicileriyle Çalışmaya Başlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da canlı, proje tabanlı kod Çözümleyicileri sayesinde, API yazarları, NuGet paketlerinin bir parçası olarak etki alanına özgü kod analizini sevk edebilir.  Bu çözümleyiciler .NET Compiler Platform (kod-adı "Roslyn") tarafından korunduğundan, satırı bitirmeden (sorunları çözmek için kodunuzu derlemek için daha fazla beklememeniz gerekmez) kodunuzda uyarı üretebilirler.  Çözümleyiciler, kodunuzu hemen temizleyebilmeniz için Visual Studio ampul istemi aracılığıyla otomatik bir kod düzeltmesini de yüzeyler.

## <a name="getting-started"></a>Başlarken
[Roslyn canlı kod Çözümleyicileri tanıtım ve Izlenecek yol](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Kod düzeltmeleri ekleme Izlenecek yol: çözümleyici sorunları için kullanıcılara düzeltmeler sağlama](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Gerçek dünya Çözümleyicisi konuşmasıyla tanışın ve gözden geçirme](https://channel9.msdn.com/events/Build/2015/3-725)

[Gerçek dünya Roslyn Çözümleyicisi](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) ve ayrıca [konuşabilirsiniz](https://channel9.msdn.com/events/Build/2015/3-725)

[GitHub 'daki birkaç örnek, üç tür çözümleyiciler halinde gruplandırılır](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Birkaç çözümleyiciler için giriş ve tur konuşur](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Diğer Kaynaklar
[GitHub OSS sitesinde daha fazla belge](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[GitHub 'da Roslyn Çözümleyicileri ile uygulanan FxCop kuralları](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
