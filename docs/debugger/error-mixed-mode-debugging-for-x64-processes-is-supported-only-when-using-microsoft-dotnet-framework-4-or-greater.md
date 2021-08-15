---
description: 64 bitlik bir işlemde karışık yerel ve yönetilen kodda hata ayıklamak için .NET Framework sürüm 4 ' e sahip olmanız gerekir.
title: x64 işlemlerine yönelik karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: 30240992d9d4eef838adf33c201c7e270a7eb1c749fab37b2eb7c9d9d73f08de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121263848"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Hata: x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir
64 bitlik bir işlemde karışık yerel ve yönetilen kodda hata ayıklamak için .NET Framework sürüm 4 ' e sahip olmanız gerekir. 4 ' ten önceki .NET Framework sürümleriyle 64 bitlik işlemlerin karışık modda hata ayıklaması desteklenmiyor.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Aşağıdaki adımlardan birini uygulayın:

  - .NET Framework sürüm 4 ' e yükseltin.

  - Hata ayıklama için uygulamanızın 32 bitlik bir sürümünü oluşturun.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan hata ayıklama](../debugger/remote-debugging.md)
