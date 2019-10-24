---
title: Rapor kancası Işlevleri | Microsoft Docs
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
ms.openlocfilehash: a0bb14b47fb17c4d59089aafa123115b85ab9342
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729865"
---
# <a name="report-hook-functions"></a>Kanca İşlevlerini Raporla
[_Crtsetreporthook](/cpp/c-runtime-library/reference/crtsetreporthook)kullanılarak yüklenen bir rapor kancası Işlevi, [_Crtdbgreport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) bir hata ayıklama raporu oluşturduğunda her seferinde çağrılır. Diğer şeyler arasında, raporları belirli ayırma türlerine odaklanmak üzere filtrelemek için kullanabilirsiniz. Bir rapor kancası işlevinin, aşağıdaki gibi bir prototipi olmalıdır:

```cpp
int YourReportHook(int nRptType, char *szMsg, int *retVal);
```

 **_Crtsetreporthook** 'e geçirdiğiniz işaretçi, CRTDBG Içinde tanımlanan **_CRT_REPORT_HOOK**türüdür. Olsun

```cpp
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);
```

 Çalışma zamanı kitaplığı, kanca işlevinizi çağırdığında, *nRptType* bağımsız değişkeni raporun kategorisini Içerir ( **_CRT_WARN**, **_CRT_ERROR**veya **_CRT_ASSERT**), *szMsg* , tam olarak birleştirilmiş bir rapora yönelik bir işaretçi içerir ileti dizesi ve *retval* , rapor oluşturulduktan sonra `_CrtDbgReport` normal yürütmeye devam edip etmediğini belirtir veya hata ayıklayıcıyı başlatın. (Bir *retval* değeri sıfır yürütmeye devam eder, 1 değeri hata ayıklayıcıyı başlatır.)

 Kanca sorudaki iletiyi tamamen işlediğinde daha fazla raporlama gerekmiyorsa, **true**döndürmelidir. **Yanlış**döndürürse `_CrtDbgReport` iletiyi normalde rapor eder.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Kanca İşlevi Yazma](../debugger/debug-hook-function-writing.md)
- [crt_dbg2 örneği](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)
