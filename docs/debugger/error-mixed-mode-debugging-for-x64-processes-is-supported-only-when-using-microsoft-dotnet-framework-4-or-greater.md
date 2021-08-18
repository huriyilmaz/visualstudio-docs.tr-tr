---
description: 64 bit işlemde karışık yerel ve yönetilen kodlarda hata ayıklamak için 4. .NET Framework gerekir.
title: x64 işlemleri için karma mod hata ayıklaması yalnızca Microsoft .NET Framework 4 veya daha büyük bir | Microsoft Docs
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
ms.openlocfilehash: cceddd78e7ba6aa7d0cf59e61ea23230b4f555be
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065676"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Hata: x64 işlemleri için karışık modda hata ayıklama yalnızca Microsoft .NET Framework 4 veya daha yenisi kullanılırken desteklenir
64 bit işlemde karışık yerel ve yönetilen kodlarda hata ayıklamak için 4. .NET Framework gerekir. 64 bit işlemlerde 4'den önceki .NET Framework karışık mod hata ayıklaması desteklenmiyor.

### <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Aşağıdaki adımlardan birini uygulayın:

  - Dosyanızı .NET Framework 4'e yükseltin.

  - Hata ayıklama için uygulamanın 32 bit sürümünü derleme.

## <a name="see-also"></a>Ayrıca bkz.
- [Uzaktan Hata Ayıklama](../debugger/remote-debugging.md)
