---
title: Rapor kancası Işlevleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.hooks
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0a492a1db8b65cad74d02cec0f43bf0c81461730
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687506"
---
# <a name="report-hook-functions"></a>Kanca İşlevlerini Raporla
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[_CrtSetReportHook](https://msdn.microsoft.com/library/1ae7c64f-8c84-4797-9574-b59f00f7a509)kullanılarak yüklenen bir rapor kancası işlevi, [_CrtDbgReport](https://msdn.microsoft.com/library/6e581fb6-f7fb-4716-9432-f0145d639ecc) bir hata ayıklama raporu oluşturduğunda her seferinde çağırılır. Diğer şeyler arasında, raporları belirli ayırma türlerine odaklanmak üzere filtrelemek için kullanabilirsiniz. Bir rapor kancası işlevinin, aşağıdaki gibi bir prototipi olmalıdır:  
  
```  
int YourReportHook(int nRptType, char *szMsg, int *retVal);  
```  
  
 **_CrtSetReportHook** için geçirdiğiniz işaretçi, CRTDBG içinde tanımlanan **_CRT_REPORT_HOOK**türündedir. Olsun  
  
```  
typedef int (__cdecl *_CRT_REPORT_HOOK)(int, char *, int *);  
```  
  
 Çalışma zamanı kitaplığı, kanca işlevinizi çağırdığında, *nRptType* bağımsız değişkeni raporun kategorisini içerir (**_CRT_WARN**, **_CRT_ERROR**veya **_CRT_ASSERT**), *szMsg* , tam olarak birleştirilmiş bir rapor iletisi dizesine yönelik bir işaretçi içerir ve *retval* , `_CrtDbgReport` raporu oluşturduktan veya hata ayıklayıcısını başlattıktan sonra normal yürütmeye devam edilip edilmeyeceğini belirtir. (Bir *retval* değeri sıfır yürütmeye devam eder, 1 değeri hata ayıklayıcıyı başlatır.)  
  
 Kanca sorudaki iletiyi tamamen işlediğinde daha fazla raporlama gerekmiyorsa, **true**döndürmelidir. **False**döndürürse, `_CrtDbgReport` iletiyi normal olarak rapor eder.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklama kanca Işlevi yazma](../debugger/debug-hook-function-writing.md)   
 [crt_dbg2 örneği](https://msdn.microsoft.com/21e1346a-6a17-4f57-b275-c76813089167)
