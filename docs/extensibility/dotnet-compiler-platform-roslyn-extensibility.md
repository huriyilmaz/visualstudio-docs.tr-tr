---
title: .NET Derleyici&quot;Platformu (&quot;Roslyn ) Genişletilebilirlik | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712072"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Derleyici&quot;Platformu (&quot;Roslyn ) genişletilebilirlik
.NET Derleyici Platformu'nun ("Roslyn") temel misyonu, C# ve Visual Basic derleyicilerini açmak ve araçların ve geliştiricilerin programlar hakkında sahip olduğu zengin bilgi derleyicilerini paylaşmalarına olanak sağlamaktır. Kod analiz araçları kod kalitesini artırır ve kod üreteçleri uygulama yapısına yardımcı olabilir. Araçlar daha akıllı hale gelince, yalnızca derleyicilerin sahip olduğu daha fazla derin kod bilgisine erişmeye ihtiyaç duyarlar. Roslyn derleyicileri opak çevirmenler (kaynak kodu ve nesne kodu dışarı) olmak yerine, araçlarınızda ve uygulamalarınızda kodla ilgili görevler için kullanabileceğiniz API'ler sunar.

 En iyi kısmı Roslyn derleyicileri, onların API'ler, örnekler ve izthroughs ve bu API'lerin üstüne inşa gerçek araçlar [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)tüm tamamen açık kaynak olmasıdır. Daha fazla bilgi edinmek ve Roslyn ile başlamak için lütfen OSS sitesine gidin. Son kullanıcı olarak kullanabileceğiniz en son C# ve Visual Basic özelliklerini almak için bağlantılar ve Roslyn API'lerinden yararlanan bir araç oluşturucu olarak başlamak için bağlantılar bulacaksınız.

## <a name="see-also"></a>Ayrıca bkz.
- [Roslyn analizörleri ile başlayın](../extensibility/getting-started-with-roslyn-analyzers.md)
