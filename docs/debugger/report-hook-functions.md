---
title: Rapor kancası Işlevleri | Microsoft Docs
description: Visual Studio 'da rapor kanca işlevlerini gözden geçirin. _CrtSetReportHook kullanılarak yüklenen bir rapor kancası işlevi, _CrtDbgReport bir hata ayıklama raporu oluşturduğunda her seferinde çağırılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- hooks, report
- _CrtDbgReport function
- debugger, report hook functions
- memory allocation, debug heap
- debugging [C++], hook functions
- _CrtSetReportHook function
- report hook functions
ms.assetid: 1854bca7-d7eb-4502-89bf-b1ee64cb50ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8dea558d2f125c1e64f46bb4fbf738434eda2394
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205625"
---
# <a name="report-hook-functions"></a>Kanca İşlevlerini Raporla
[_CrtSetReportHook](/cpp/c-runtime-library/reference/crtsetreporthook)kullanılarak yüklenen bir rapor kancası işlevi, [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) bir hata ayıklama raporu oluşturduğunda her seferinde çağırılır. Diğer şeyler arasında, raporları belirli ayırma türlerine odaklanmak üzere filtrelemek için kullanabilirsiniz. Bir rapor kancası işlevinin, aşağıdaki gibi bir prototipi olmalıdır:

```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);
```

 **_CrtSetReportHook** için geçirdiğiniz işaretçi, CRTDBG içinde tanımlanan **_CRT_REPORT_HOOK** türündedir. Olsun

```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);
```

 Çalışma zamanı kitaplığı, kanca işlevinizi çağırdığında, *nRptType* bağımsız değişkeni raporun kategorisini içerir (**_CRT_WARN**, **_CRT_ERROR** veya **_CRT_ASSERT**), *szMsg* , tam olarak birleştirilmiş bir rapor iletisi dizesine yönelik bir işaretçi içerir ve *retval* , `_CrtDbgReport` raporu oluşturduktan veya hata ayıklayıcısını başlattıktan sonra normal yürütmeye devam edilip edilmeyeceğini belirtir. (Bir *retval* değeri sıfır yürütmeye devam eder, 1 değeri hata ayıklayıcıyı başlatır.)

 Kanca sorudaki iletiyi tamamen işlediğinde daha fazla raporlama gerekmiyorsa, **true** döndürmelidir. **False** döndürürse, `_CrtDbgReport` iletiyi normal olarak rapor eder.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 örneği](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
