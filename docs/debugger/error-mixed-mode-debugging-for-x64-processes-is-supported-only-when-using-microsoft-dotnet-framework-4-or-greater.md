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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 01f8bf0b018ed5dd91cedcc221a037f3502815e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871500"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Hata: x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir
64 bitlik bir işlemde karışık yerel ve yönetilen kodda hata ayıklamak için .NET Framework sürüm 4 ' e sahip olmanız gerekir. 4 ' ten önceki .NET Framework sürümleriyle 64 bitlik işlemlerin karışık modda hata ayıklaması desteklenmiyor.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Aşağıdaki adımlardan birini uygulayın:

  - .NET Framework sürüm 4 ' e yükseltin.

  - Hata ayıklama için uygulamanızın 32 bitlik bir sürümünü oluşturun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)