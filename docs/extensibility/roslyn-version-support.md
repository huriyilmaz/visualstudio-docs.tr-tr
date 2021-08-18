---
title: Desteklenen Roslyn paket sürümü eşlemeleri
description: Bu makalede, farklı Visual Studio sürümleri için hangi .NET derleyici platformu (Roslyn) paketi sürümlerinin desteklendiği gösterilmektedir.
ms.custom: SEO-VS-2020
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 213dd6f76cab8dfaf87e498ea5e020386e3d3e8af4a68ee50df704fe4ed2b193
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121447798"
---
# <a name="net-compiler-platform-package-version-reference"></a>.NET derleyicisi platform paketi sürüm başvurusu

Aşağıdaki tabloda, Visual Studio farklı sürümleri için hangi [.NET derleyici platformu (Roslyn) paketi](https://www.nuget.org/packages/Microsoft.Net.Compilers/) sürümlerinin desteklendiği gösterilmektedir.

örnek olarak, özel çözümleyicinizi Visual Studio 2017 ' nin tüm sürümlerinde çalışacağından emin olmak için, Microsoft.Net. derleyicilerin sürüm 2,0 ' i hedeflemelidir.

| Roslyn paket sürümü | desteklenen en düşük Visual Studio sürümü |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 sürüm 15,9 |
| 2.9.0 | Visual Studio 2017 sürüm 15,8 |
| 2.8.2 | Visual Studio 2017 sürüm 15.7 Sürüm Notları |
| 2.7.0 | Visual Studio 2017 sürüm 15.6 |
| 2.6.1 | Visual Studio 2017 sürüm 15.5 |
| 2.4.0 | Visual Studio 2017 sürüm 15.4 |
| 2.3.2 | Visual Studio 2017 sürüm 15.3 |
| 2.2.0 | Visual Studio 2017 sürüm 15.2 |
| 2.1.0 | Visual Studio 2017 sürüm 15.1 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 güncelleştirme 3 |
| 1.2.2 | Visual Studio 2015 güncelleştirme 2 |
| 1.1.1 | Visual Studio 2015 güncelleştirme 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> desteklenen en düşük Visual Studio sürümünün Visual Studio 2017 sürümü olduğu roslyn paketleri için, daha sonra gelmiş oldukları için tüm Visual Studio 2019 sürümleri de desteklenir.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Compiler Platform SDK’sı](/dotnet/csharp/roslyn-sdk/)
- [Roslyn Çözümleyicileri ile çalışmaya başlama](getting-started-with-roslyn-analyzers.md)
