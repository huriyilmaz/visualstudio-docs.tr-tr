---
title: Çalışma zamanı hata raporlama işlevi yazma | Microsoft Docs
description: Visual Studio özel bir çalışma zamanı hata raporlama işlevi yazma örneklerine bakın. _CrtDbgReportW aynı bildirime sahip olmalıdır ve 1 değerini döndürür.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9f4131f5bea3f3c1a2c880c64302fd44ab5a3535
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146855"
---
# <a name="how-to-write-a-run-time-error-reporting-function-c"></a>Nasıl yapılır: Run-Time hata raporlama Işlevi yazma (C++)
Çalışma zamanı hataları için özel bir raporlama işlevi, ile aynı bildirime sahip olmalıdır `_CrtDbgReportW` . Hata ayıklayıcıya 1 değerini döndürmelidir.

Aşağıdaki örnek, bir özel raporlama işlevinin nasıl tanımlanacağını göstermektedir.

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
Aşağıdaki örnekte, daha karmaşık bir özel raporlama işlevi gösterilmektedir. Bu örnekte, Switch ifadesinde parametresi tarafından tanımlandığı şekilde çeşitli hata türleri ele alır `reportType` `_CrtDbgReportW` . Değiştirdiğiniz için `_CrtDbgReportW` kullanamazsınız `_CrtSetReportMode` . İşleviniz çıktıyı işlemelidir. Bu işlevdeki ilk değişken bağımsız değişkeni bir çalışma zamanı hata numarası alır. Daha fazla bilgi için bkz. [_RTC_SetErrorType](/cpp/c-runtime-library/reference/rtc-seterrortype).

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
Yerine `_RTC_SetErrorFuncW` özel işlevinizi yüklemek için kullanın `_CrtDbgReportW` . Daha fazla bilgi için bkz. [_RTC_SetErrorFuncW](/cpp/c-runtime-library/reference/rtc-seterrorfuncw). `_RTC_SetErrorFuncW`Dönüş değeri, bir önceki raporlama işlevidir ve gerekirse bunları kaydedebilir ve geri yükleyebilirsiniz.

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
[Yerel Run-Time denetimleri özelleştirmesi](../debugger/native-run-time-checks-customization.md)
