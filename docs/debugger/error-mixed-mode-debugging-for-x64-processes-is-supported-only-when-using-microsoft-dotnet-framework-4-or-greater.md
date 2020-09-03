---
title: Hata-x64 işlemlerine yönelik karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir | Microsoft Docs
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
ms.openlocfilehash: 9f30fe9b729df84506f6717e5fd895297390dea6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460643"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Hata: x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir
64 bitlik bir işlemde karışık yerel ve yönetilen kodda hata ayıklamak için .NET Framework sürüm 4 ' e sahip olmanız gerekir. 4 ' ten önceki .NET Framework sürümleriyle 64 bitlik işlemlerin karışık modda hata ayıklaması desteklenmiyor.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Aşağıdaki adımlardan birini uygulayın:

  - .NET Framework sürüm 4 ' e yükseltin.

  - Hata ayıklama için uygulamanızın 32 bitlik bir sürümünü oluşturun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)