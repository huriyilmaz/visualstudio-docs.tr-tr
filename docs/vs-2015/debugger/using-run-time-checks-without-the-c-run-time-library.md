---
title: C çalışma zamanı kitaplığı olmadan çalışma zamanı denetimlerini kullanma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- run-time errors, error checks
- CRT, run-time checks
- debugger, native run-time checks
- run-time errors, run-time checks
- run-time checks, /RTC option
- debugging [Visual Studio], run-time routines
ms.assetid: 30ed90f3-9323-4784-80a4-937449eb54f6
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1eefddd21817360736b9f20f74ca3dc8a83683fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684029"
---
# <a name="using-run-time-checks-without-the-c-run-time-library"></a>C Çalışma Zamanı Kitaplığını Kullanmadan Çalışma Zamanı Denetimlerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Programınızı, **/nodefaultlib**kullanarak C çalışma zamanı kitaplığı olmadan bağlantılandırdıysanız ve çalışma zamanı denetimlerini kullanmak Istiyorsanız RunTmChk. lib ile bağlantı oluşturmanız gerekir.  
  
 `_RTC_Initialize` programınızı çalışma zamanı denetimleri için başlatır. C çalışma zamanı kitaplığıyla bağlantı yapmazsanız, aşağıdaki gibi, çağrılmadan önce programınızın çalışma zamanı hata denetimleri ile derlenip derlenmediğini denetlemeniz gerekir `_RTC_Initialize` :  
  
```  
#ifdef __MSVC_RUNTIME_CHECKS  
    _RTC_Initialize();  
#endif  
```  
  
 C çalışma zamanı kitaplığıyla bağlantı yapmazsanız, adlı bir işlev da tanımlamanız gerekir `_CRT_RTC_INITW` . `_CRT_RTC_INITW` Kullanıcı tanımlı işlevinizi varsayılan hata raporlama işlevi olarak aşağıdaki gibi kurar:  
  
```  
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
  
 Varsayılan hata raporlama işlevini yükledikten sonra, ile ek hata raporlama işlevlerini yükleyebilirsiniz `_RTC_SetErrorFuncW` . Daha fazla bilgi için bkz. [_RTC_SetErrorFuncW](https://msdn.microsoft.com/library/b3e0d71f-1bd3-4c37-9ede-2f638eb3c81a).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: yerel çalışma zamanı denetimlerini kullanma](../debugger/how-to-use-native-run-time-checks.md)
