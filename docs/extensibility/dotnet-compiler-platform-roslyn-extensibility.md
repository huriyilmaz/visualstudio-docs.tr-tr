---
title: .NET Compiler Platform ( &quot; roslyn &quot; ) genişletilebilirliği | Microsoft Docs
description: araçlar ve geliştiricilerin zengin bilgi derleyicileri ' de paylaşmasına izin veren .NET Compiler Platform hakkında bilgi edinin.
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
ms.openlocfilehash: d04383359133e64ec97fecc1ca0eb8082fcd42c2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152490"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform ( &quot; roslyn &quot; ) genişletilebilirliği
.NET Compiler Platform ana görevi ("roslyn"), C# ve Visual Basic derleyicilerini açıyor ve araçların ve geliştiricilerin zengin bilgi derleyicileri, programlarla paylaşmasına izin verir. Kod analizi araçları kod kalitesini geliştirir ve kod oluşturucuları uygulama oluşturma konusunda yardımcı olur. Araçların daha akıllı bir şekilde yararlanabileceği için, yalnızca derleyicilerin sahip olduğu derin kod bilgisine daha fazla ve daha fazlasına erişmesi gerekir. Sabit bir çevirmenin (ve nesne kodu içindeki kaynak kodu) değil, Roslyn derleyicileri, araçlarınızdaki ve uygulamalarınızda kod ile ilgili görevler için kullanabileceğiniz API 'Ler sunar.

 En iyi bölüm, Roslyn derleyicilerinin, API 'Lerinin, örneklerin ve izlenecek yolların yanı sıra bu API 'lerin üzerine inşa edilen gerçek araçların, [GitHub.com/DotNet/Roslyn](https://github.com/dotnet/Roslyn)adresindeki tamamen açık kaynaktır. Daha fazla bilgi edinmek ve Roslyn 'yi kullanmaya başlamak için lütfen OSS sitesine gidin. son kullanıcı olarak kullanabileceğiniz en son C# ve Visual Basic özelliklerinin yanı sıra roslyn apı 'lerinden yararlanan bir araç oluşturucusu olarak kullanmaya başlamak için bağlantılar bulacaksınız.

## <a name="see-also"></a>Ayrıca bkz.
- [Roslyn Çözümleyicileri ile çalışmaya başlama](../extensibility/getting-started-with-roslyn-analyzers.md)
