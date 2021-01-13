---
title: C Run-Time kitaplığı olmadan Run-Time denetimleri kullanma | Microsoft Docs
description: /NODEFAULTLIB' i kullanarak programınızı C çalışma zamanı kitaplığı olmadan bağlayabilirsiniz. Bunu yaparsanız ve çalışma zamanı denetimlerini kullanmak istiyorsanız RunTmChk. lib ile bağlantı oluşturmanız gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bfa83533b1ae929bf443dd6c3eb7f7dc3e7db165
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150866"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>C Çalışma Zamanı Kitaplığını Kullanmadan Çalışma Zamanı Denetimlerini Kullanma
Programınızı, **/nodefaultlib** kullanarak C çalışma zamanı kitaplığı olmadan bağlantılandırdıysanız ve çalışma zamanı denetimlerini kullanmak Istiyorsanız RunTmChk. lib ile bağlantı oluşturmanız gerekir.

`_RTC_Initialize` programınızı çalışma zamanı denetimleri için başlatır. C çalışma zamanı kitaplığıyla bağlantı yapmazsanız, aşağıdaki gibi, çağrılmadan önce programınızın çalışma zamanı hata denetimleri ile derlenip derlenmediğini denetlemeniz gerekir `_RTC_Initialize` :

```cpp
#ifdef __MSVC_RUNTIME_CHECKS
    _RTC_Initialize();
#endif
```

C çalışma zamanı kitaplığıyla bağlantı yapmazsanız, adlı bir işlev da tanımlamanız gerekir `_CRT_RTC_INITW` . `_CRT_RTC_INITW` Kullanıcı tanımlı işlevinizi varsayılan hata raporlama işlevi olarak aşağıdaki gibi kurar:

```cpp
// C version:
_RTC_error_fnW __cdecl _CRT_RTC_INITW(
        void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler.
    return &MyErrorFunc;
}

// C++ version:
extern "C" _RTC_error_fnW __cdecl _CRT_RTC_INITW(
       void *res0, void **res1, int res2, int res3, int res4)
{
    // set the error handler:
    return &MyErrorFunc;
}
```

Varsayılan hata raporlama işlevini yükledikten sonra, ile ek hata raporlama işlevlerini yükleyebilirsiniz `_RTC_SetErrorFuncW` . Daha fazla bilgi için bkz. [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw).

## <a name="see-also"></a>Ayrıca bkz.
[Nasıl yapılır: yerel Run-Time denetimleri kullanma](../debugger/how-to-use-native-run-time-checks.md)
