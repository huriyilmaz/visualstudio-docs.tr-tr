---
title: .NET Compiler Platform ( &quot; Roslyn &quot; ) Genişletilebilirlik | Microsoft Docs
description: Araçların ve geliştiricilerin .NET Compiler Platform zengin bilgi derleyicileri ile paylaşmalarına olanak sağlayan uygulama hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b09aa03ae6af6789ddcc87dc60797af5eda3f19bcde6148dd7bfe1b568b7f0f2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121388935"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform ( &quot; Roslyn &quot; ) genişletilebilirliği
.NET Compiler Platform("Roslyn") görevinin temel görevi, C# ve Visual Basic derleyicilerinin açılması ve araçların ve geliştiricilerin programlarla ilgili zengin bilgi derleyicilerinin sahip olduğu bilgileri paylaşmasına olanak vermektir. Kod analizi araçları kod kalitesini iyiler ve kod oluşturucular uygulamanın yapısına yardımcı olur. Araçlar daha akıllı hale geldi mi, yalnızca derleyicilerin sahip olduğu derin kod bilgisine erişmeleri gerekir. Roslyn derleyicileri, opak çevirmenler (içinde kaynak kodu ve nesne kodu dışarı) olmak yerine, araçlarınız ve uygulamalarınız için kodla ilgili görevler için kullanabileceğiniz API'ler sunar.

 En iyi bölüm, Roslyn derleyicilerinin, API'lerinin, örneklerinin ve izlenecek yollarının yanı sıra bu API'ler üzerinde derlenmiş olan gerçek araçların [github.com/dotnet/roslyn.](https://github.com/dotnet/Roslyn) Daha fazla bilgi edinmek ve Roslyn ile çalışmaya başlamayı öğrenmek için lütfen OSS sitesine gidin. Son kullanıcı olarak kullanabileceğiniz en son C# ve Visual Basic özelliklerine ek olarak Roslyn API'lerini kullanan bir araç oluşturucu olarak çalışmaya başlama bağlantılarını da bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [roslyn Kullanmaya başlayın ile birlikte yükleme](../extensibility/getting-started-with-roslyn-analyzers.md)
