---
title: Çalışma zamanı hata raporlama işlevi | Microsoft Docs
description: Çalışma alanı içinde özel çalışma zamanı hata raporlama işlevi yazma örneklerine Visual Studio. Bu, 1 değeri _CrtDbgReportW ile aynı bildirime sahip olması gerekir.
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- run-time errors, reporting functions
- reporting function
ms.assetid: 989bf312-5038-44f3-805f-39a34d18760e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d62b7502f1742da57dbb2d25eb4912adcb8d19a2
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972563"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>Nasıl kullanılır: Hata Run-Time İşlevi Yazma (C++)
Çalışma zamanı hataları için özel raporlama işlevinin bildirimi ile aynı olması `_CrtDbgReportW` gerekir. Hata ayıklayıcısına 1 değerinin dönmesini sağlar.

Aşağıdaki örnekte, özel raporlama işlevinin nasıl tanımlanmasına yer ve ardından bir örnek ve daha fazla bilgi ve açıklama yer amektedir.

## <a name="example-1"></a>Örnek 1

```cpp
#include <stdio.h>
int errorhandler = 0;
void configureMyErrorFunc(int i)
{
    errorhandler = i;
}

int MyErrorFunc(int errorType, const wchar_t *filename,
                int linenumber, const wchar_t *moduleName,
                const wchar_t *format, ...)
{
    switch (errorhandler)
    {
    case 0:
    case 1:
        wprintf(L"Error type %d at %s line %d in %s",
                errorType, filename, linenumber, moduleName);
        break;
    case 2:
    case 3:
        fprintf(stderr, "Error type");
        break;
    }

    return 1;
}
```

## <a name="example-2"></a>Örnek 2
Aşağıdaki örnekte daha karmaşık bir özel raporlama işlevi yer almaktadır. Bu örnekte switch deyimi, parametresiyle tanımlandığı gibi çeşitli hata türlerini `reportType` ele `_CrtDbgReportW` alır. yerine yenisini `_CrtDbgReportW` değiştirerek `_CrtSetReportMode` kullanabilirsiniz. İşlevin çıkışı işlemesi gerekir. Bu işlevde ilk değişken bağımsız değişkeni bir çalışma zamanı hata numarası alır. Daha fazla bilgi için [bkz. _RTC_SetErrorType.](/cpp/c-runtime-library/reference/rtc-seterrortype)

```cpp
#include <windows.h>
#include <stdarg.h>
#include <rtcapi.h>
#include <malloc.h>
#pragma runtime_checks("", off)
int Catch_RTC_Failure(int errType, const wchar_t *file, int line,
                      const wchar_t *module, const wchar_t *format, ...)
{
    // Prevent re-entrance.
    static long running = 0;
    while (InterlockedExchange(&running, 1))
        Sleep(0);
    // Now, disable all RTC failures.
    int numErrors = _RTC_NumErrors();
    int *errors=(int*)_alloca(numErrors);
    for (int i = 0; i < numErrors; i++)
        errors[i] = _RTC_SetErrorType((_RTC_ErrorNumber)i, _RTC_ERRTYPE_IGNORE);

    // First, get the rtc error number from the var-arg list.
    va_list vl;
    va_start(vl, format);
    _RTC_ErrorNumber rtc_errnum = va_arg(vl, _RTC_ErrorNumber);
    va_end(vl);

    wchar_t buf[512];
    const char *err = _RTC_GetErrDesc(rtc_errnum);
    swprintf_s(buf, 512, L"%S\nLine #%d\nFile:%s\nModule:%s",
        err,
        line,
        file ? file : L"Unknown",
        module ? module : L"Unknown");
    int res = (MessageBox(NULL, buf, L"RTC Failed...", MB_YESNO) == IDYES) ? 1 : 0;
    // Now, restore the RTC errortypes.
    for(int i = 0; i < numErrors; i++)
        _RTC_SetErrorType((_RTC_ErrorNumber)i, errors[i]);
    running = 0;
    return res;
}
#pragma runtime_checks("", restore)
```

## <a name="example-3"></a>Örnek 3
yerine `_RTC_SetErrorFuncW` özel işlevinizi yüklemek için `_CrtDbgReportW` kullanın. Daha fazla bilgi için [bkz. _RTC_SetErrorFuncW.](/cpp/c-runtime-library/reference/rtc-seterrorfuncw) Dönüş `_RTC_SetErrorFuncW` değeri, gerekirse kaydederek geri yükleyerek önceki raporlama işlevidir.

```cpp
#include <rtcapi.h>
int main()
{
    _RTC_error_fnW oldfunction, newfunc;
    oldfunction = _RTC_SetErrorFuncW(&MyErrorFunc);
    // Run some code.
    newfunc = _RTC_SetErrorFuncW(oldfunction);
    // newfunc == &MyErrorFunc;
    // Run some more code.
}
```

## <a name="see-also"></a>Ayrıca bkz.
[Yerel Run-Time Denetimleri Özelleştirme](../debugger/native-run-time-checks-customization.md)
