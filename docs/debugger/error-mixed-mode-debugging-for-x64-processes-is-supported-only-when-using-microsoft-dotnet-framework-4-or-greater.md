---
title: X64 işlemlerine yönelik karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: e8cfc3ac5cb606637fe5c2818750168a239a46fa
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852621"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Hata: x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir
64 bitlik bir işlemde karışık yerel ve yönetilen kodda hata ayıklamak için .NET Framework sürüm 4 ' e sahip olmanız gerekir. 4 ' ten önceki .NET Framework sürümleriyle 64 bitlik işlemlerin karışık modda hata ayıklaması desteklenmiyor.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Aşağıdaki adımlardan birini uygulayın:

  - .NET Framework sürüm 4 ' e yükseltin.

  - Hata ayıklama için uygulamanızın 32 bitlik bir sürümünü oluşturun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)