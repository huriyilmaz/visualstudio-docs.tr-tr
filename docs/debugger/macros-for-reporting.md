---
title: Raporlama için makrolar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.macros
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- macros, CRT reporting macros
- macros, debugging with
- _RPTFn macro
- CRT, reporting macros
- debugging [CRT], reporting macros
- _RPTn macro
ms.assetid: f2085314-a3a8-4caf-a5a4-2af9ad5aad05
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2129db98293cef678527fb331992c6c5960d8f9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72731384"
---
# <a name="macros-for-reporting"></a>Raporlama Makroları
Hata ayıklama için, CRTDBG içinde tanımlanan **_Rptn** ve **_Rptfn** makrolarını kullanabilirsiniz. H, `printf` deyimlerinin kullanımını değiştirmek için. **_Hata ayıklama** tanımlanmadığında yayın derlemenize otomatik olarak kaybolduğu için **#ifdef**s 'de bunları almanız gerekmez.

|Makroya|Açıklama|
|-----------|-----------------|
|**_Rpt0**, **_RPT1**, **_rpt2**, **_rpt3**, **_RPT4**|İleti dizesi ve sıfırdan dört bağımsız değişken verir. _RPT1 ile **_Rpt4**arasında, ileti dizesi bağımsız değişkenler için bir printf stili biçimlendirme dizesi işlevi görür.|
|**_Rptf0**, **_rptf1**, **_RPTF2**, **_rptf4**|**_Rptn**ile aynı, ancak bu makrolar, makronun bulunduğu dosya adı ve satır numarası da çıktı.|

 Aşağıdaki örneği göz önünde bulundurun:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Bu kod `someVar` ve `otherVar` değerlerini **stdout**' a çıkarır. Aynı değerleri raporlamak ve ayrıca dosya adı ve satır numarasını bildirmek için `_RPTF2` için aşağıdaki çağrıyı kullanabilirsiniz:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Belirli bir uygulamanın, C çalışma zamanı kitaplığı ile sağlanan makroların sunmadığından hata ayıklama raporlaması gerektiğini görebilirsiniz. Bu gibi durumlarda, kendi gereksinimlerinize uyacak şekilde tasarlanan bir makro yazabilirsiniz. Başlık dosyalarından birinde, örneğin, **ALERT_IF2**adlı bir makro tanımlamak için aşağıdakine benzer bir kod ekleyebilirsiniz:

```cpp
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

 **ALERT_IF2** öğesine yapılan bir çağrı, **printf** kodunun tüm işlevlerini verebilir:

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Farklı hedeflere daha fazla veya daha az bilgi bildirebilmeniz için özel bir makroyu kolayca değiştirebilirsiniz. Bu yaklaşım özellikle hata ayıklama gereksinimleriniz geliştikçe yararlı olur.

## <a name="see-also"></a>Ayrıca bkz.
- [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)
