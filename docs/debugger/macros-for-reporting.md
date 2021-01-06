---
title: Raporlama için makrolar | Microsoft Docs
description: CRTDBG içinde _RPTn hata ayıklama makroları ve _RPTFn hakkında bilgi edinin. H ve kendi hata ayıklama makrolarınızı oluşturma hakkında.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1920b4eddcbffa5cd51d548ade9af3a3a2f208d0
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903798"
---
# <a name="macros-for-reporting"></a>Raporlama Makroları
Hata ayıklama için, CRTDBG içinde tanımlanan **_RPTn** ve **_RPTFn** makrolarını kullanabilirsiniz. H, deyimlerin kullanımını değiştirmek için `printf` . **_DEBUG** tanımlanmadığında yayın derlemeniz otomatik olarak kaybolduğu için **#ifdef** s 'de bunları almanız gerekmez.

|Makroya|Açıklama|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2**, **_RPT3**, **_RPT4**|İleti dizesi ve sıfırdan dört bağımsız değişken verir. **_RPT4** üzerinden **_RPT1** için, ileti dizesi bağımsız değişkenler için bir printf stili biçimlendirme dizesi işlevi görür.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3**, **_RPTF4**|**_RPTn** ile aynıdır, ancak bu makrolar, makronun bulunduğu dosya adı ve satır numarasını da çıktı olarak alır.|

 Aşağıdaki örneği inceleyin:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Bu kod, `someVar` ve değerlerini `otherVar` **stdout** olarak verir. `_RPTF2`Aynı değerleri ve ek olarak dosya adını ve satır numarasını raporlamak için aşağıdaki çağrısını kullanabilirsiniz:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Belirli bir uygulamanın, C çalışma zamanı kitaplığı ile sağlanan makroların sunmadığından hata ayıklama raporlaması gerektiğini görebilirsiniz. Bu gibi durumlarda, kendi gereksinimlerinize uyacak şekilde tasarlanan bir makro yazabilirsiniz. Başlık dosyalarından birinde, örneğin, **ALERT_IF2** adlı bir makro tanımlamak için aşağıdakine benzer bir kod ekleyebilirsiniz:

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

 **ALERT_IF2** bir çağrı, **printf** kodunun tüm işlevlerini yapabilirim:

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Farklı hedeflere daha fazla veya daha az bilgi bildirebilmeniz için özel bir makroyu kolayca değiştirebilirsiniz. Bu yaklaşım özellikle hata ayıklama gereksinimleriniz geliştikçe yararlı olur.

## <a name="see-also"></a>Ayrıca bkz.
- [CRT hata ayıklama teknikleri](../debugger/crt-debugging-techniques.md)
