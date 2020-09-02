---
title: Raporlama için makrolar | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e4aee33d571f95e24a359fa2bc7e12ae8d64eae0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431634"
---
# <a name="macros-for-reporting"></a>Raporlama Makroları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**_RPTn**ve **_RPTFn** makrolarını, Crtdbg içinde tanımlanan şekilde kullanabilirsiniz. H, `printf` hata ayıklama için deyimlerin kullanımını değiştirmek üzere. **_DEBUG** tanımlanmamışsa, bu makrolar otomatik olarak yayın derlemesinde kaybolur, bu nedenle bunları **#ifdef**s 'ye almanız gerekmez.  
  
|Makroya|Açıklama|  
|-----------|-----------------|  
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|İleti dizesi ve sıfırdan dört bağımsız değişken verir. **_RPT4**üzerinden _RPT1 için, ileti dizesi bağımsız değişkenler için bir printf stili biçimlendirme dizesi işlevi görür.|  
|**_RPTF0**, **_RPTF1**, **, _RPTF2**, **_RPTF4**|**_RPTn** ile aynıdır, ancak bu makrolar, makronun bulunduğu dosya adı ve satır numarasını da çıktı olarak alır.|  
  
 Aşağıdaki örneği inceleyin:  
  
```  
#ifdef _DEBUG  
    if ( someVar > MAX_SOMEVAR )  
        printf( "OVERFLOW! In NameOfThisFunc( ),  
               someVar=%d, otherVar=%d.\n",  
               someVar, otherVar );  
#endif  
```  
  
 Bu kod, `someVar` ve değerlerini `otherVar` **stdout**olarak verir. `_RPTF2`Aynı değerleri ve ek olarak dosya adını ve satır numarasını raporlamak için aşağıdaki çağrısını kullanabilirsiniz:  
  
```  
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );  
```  
  
 Belirli bir uygulamanın, C çalışma zamanı kitaplığı ile sağlanan makroların sağlamadığına ilişkin hata ayıklama için gerekli olduğunu fark ederseniz, özellikle kendi gereksinimlerinize uyacak şekilde tasarlanan bir makro yazabilirsiniz. Başlık dosyalarından birinde, örneğin, **ALERT_IF2**adlı bir makro tanımlamak için aşağıdakine benzer bir kod ekleyebilirsiniz:  
  
```  
#ifndef _DEBUG                  /* For RELEASE builds */  
#define  ALERT_IF2(expr, msg, arg1, arg2)  do {} while (0)  
#else                           /* For DEBUG builds   */  
#define  ALERT_IF2(expr, msg, arg1, arg2) \  
    do { \  
        if ((expr) && \  
            (1 == _CrtDbgReport(_CRT_ERROR, \  
                __FILE__, __LINE__, msg, arg1, arg2))) \  
            _CrtDbgBreak( ); \  
    } while (0)  
#endif  
```  
  
 **ALERT_IF2** bir çağrı, bu konunun başlangıcında **printf** kodunun tüm işlevlerini gerçekleştirebilir:  
  
```  
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),   
someVar=%d, otherVar=%d.\n", someVar, otherVar );  
```  
  
 Özel bir makro farklı hedeflere daha fazla veya daha az bilgi bildirmek üzere kolayca değiştirilebildiğinden (daha uygun olan seçeneklere bağlı olarak), hata ayıklama gereksinimleriniz geliştikçe bu yaklaşım özellikle yararlı olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)
