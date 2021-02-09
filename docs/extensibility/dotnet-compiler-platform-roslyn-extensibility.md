---
title: .NET Compiler Platform ( &quot; Roslyn &quot; ) genişletilebilirliği | Microsoft Docs
description: Araçlar ve geliştiricilerin zengin bilgi derleyicileri ' de paylaşmasına izin veren .NET Compiler Platform hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8c0286bb35f8a58a2f5fd6cfa95cff62d523567c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883564"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler Platform ( &quot; Roslyn &quot; ) genişletilebilirliği
.NET Compiler Platform ana görevi ("Roslyn"), C# ve Visual Basic derleyicilerini açıyor ve araçların ve geliştiricilerin zengin bilgi derleyicileri, programlarla paylaşmasına izin verir. Kod analizi araçları kod kalitesini geliştirir ve kod oluşturucuları uygulama oluşturma konusunda yardımcı olur. Araçların daha akıllı bir şekilde yararlanabileceği için, yalnızca derleyicilerin sahip olduğu derin kod bilgisine daha fazla ve daha fazlasına erişmesi gerekir. Sabit bir çevirmenin (ve nesne kodu içindeki kaynak kodu) değil, Roslyn derleyicileri, araçlarınızdaki ve uygulamalarınızda kod ile ilgili görevler için kullanabileceğiniz API 'Ler sunar.

 En iyi bölüm, Roslyn derleyicilerinin, API 'Lerinin, örneklerin ve izlenecek yolların yanı sıra bu API 'lerin üzerine inşa edilen gerçek araçların, [GitHub.com/DotNet/Roslyn](https://github.com/dotnet/Roslyn)adresindeki tamamen açık kaynaktır. Daha fazla bilgi edinmek ve Roslyn 'yi kullanmaya başlamak için lütfen OSS sitesine gidin. Son Kullanıcı olarak kullanabileceğiniz en son C# ve Visual Basic özelliklerinin yanı sıra Roslyn API 'Lerinden yararlanan bir araç Oluşturucusu olarak kullanmaya başlamak için bağlantılar bulacaksınız.

## <a name="see-also"></a>Ayrıca bkz.
- [Roslyn Çözümleyicileri ile çalışmaya başlama](../extensibility/getting-started-with-roslyn-analyzers.md)
