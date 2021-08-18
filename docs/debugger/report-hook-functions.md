---
title: Rapor Kancası İşlevleri | Microsoft Docs
description: Rapor kancası işlevlerini Visual Studio. _CrtSetReportHook kullanılarak yüklenmiş olan bir rapor kancası işlevi, _CrtDbgReport bir hata ayıklama raporu oluşturması için çağrılır.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6274c9131ecfd8d49bf0a741a1ced69590b96c9d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161134"
---
# <a name="report-hook-functions"></a>Kanca İşlevlerini Raporla
_CrtSetReportHook kullanılarak yüklenmiş olan [bir rapor](/cpp/c-runtime-library/reference/crtsetreporthook)kancası işlevi, her _CrtDbgReport [hata](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) ayıklama raporu oluşturması için çağrılır. Raporları belirli ayırma türlerine odaklanmak üzere filtrelemek için bunu başka şeyler de kullanabilirsiniz. Rapor kancası işlevinin aşağıdakine benzer bir prototipi olması gerekir:

```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);
```

 CRTDBG'de **_CrtSetReportHook** **işaretçisi _CRT_REPORT_HOOK** türüne sahip. H:

```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);
```

 Çalışma zamanı kitaplığı kanca işlevinizi *çağırsa, nRptType* bağımsız değişkeni raporun kategorisini (**_CRT_WARN**, **_CRT_ERROR** veya **_CRT_ASSERT),** *szMsg* tam olarak birleştirilmiş bir rapor ileti dizesinin işaretçisini içerir ve *retVal* rapor oluşturma veya hata ayıklayıcıyı başlatmadan sonra normal yürütmeye devam edip edeceğini `_CrtDbgReport` belirtir. (Sıfır *retVal değeri* yürütmeye devam eder, 1 değeri hata ayıklayıcıyı başlatır.)

 Kanca, söz konusu iletiyi tamamen ele aldıysa, başka raporlama gerektirsinsin mi, TRUE dönüş **getirsin.** FALSE **döndürürse,** `_CrtDbgReport` iletiyi normal şekilde raporlar.

## <a name="see-also"></a>Ayrıca bkz.
- [Kanca İşlevi YazmaDa Hata Ayıklama](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 Örneği](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
