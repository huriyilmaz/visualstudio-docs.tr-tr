---
title: Raporlama Raporları makroları | Microsoft Docs
description: CRTDBG'de sağlanan _RPTn ve _RPTFn hata ayıklama makroları hakkında bilgi öğrenin. H ve kendi hata ayıklama makrolarınızı oluşturma hakkında.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c3479483b5baf1bef9d6001ff5a8bffca53a675bd9d50d916d7241c8e67ee96c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453126"
---
# <a name="macros-for-reporting"></a>Raporlama Makroları
Hata ayıklama için, CRTDBG'de **_RPTn** ve **_RPTFn** makrolarını kullanabilirsiniz. deyimlerinin kullanımını değiştirmek için `printf` H. Bunlar tanımlanmamış olduğunda yayın **#ifdef** otomatik olarak kaybolduğu için bunları _DEBUG **gerek** yok.

|Makro|Açıklama|
|-----------|-----------------|
|**_RPT0**, **_RPT1**, **_RPT2,** **_RPT3**, **_RPT4**|Bir ileti dizesi ve sıfırdan dört bağımsız değişkene çıkış verir. bu **_RPT1** için **_RPT4** dize, bağımsız değişkenler için printf stili biçimlendirme dizesi olarak görev alır.|
|**_RPTF0**, **_RPTF1**, **_RPTF2**, **_RPTF3**, **_RPTF4**|ile **_RPTn,** ancak bu makrolar da makronun bulunduğu dosya adını ve satır numarasını çıkış olarak belirtir.|

 Aşağıdaki örneği inceleyin:

```cpp
#ifdef _DEBUG
    if ( someVar > MAX_SOMEVAR )
        printf( "OVERFLOW! In NameOfThisFunc( ),
               someVar=%d, otherVar=%d.\n",
               someVar, otherVar );
#endif
```

 Bu kod, ve değerlerini `someVar` `otherVar` **stdout'a verir.** Bu değerleri ve ek olarak dosya adını ve satır numarasını rapor etmek için aşağıdaki `_RPTF2` çağrısı kullanabilirsiniz:

```cpp
if (someVar > MAX_SOMEVAR) _RPTF2(_CRT_WARN, "In NameOfThisFunc( ), someVar= %d, otherVar= %d\n", someVar, otherVar );
```

Belirli bir uygulamanın C çalışma zamanı kitaplığıyla sağlanan makroların sağlamamasına neden olan hata ayıklama raporlaması gerektiğini bulabilirsiniz. Bu durumlarda, özel olarak kendi gereksinimlerinize uyacak şekilde tasarlanmış bir makro yazabilir. Örneğin, üst bilgi dosyalarınızın birsinde aşağıdakine benzer bir kod ekleyen ve **ALERT_IF2:**

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

 Tek bir **ALERT_IF2** printf kodunun tüm **işlevlerini yapabiliriz:**

```cpp
ALERT_IF2(someVar > MAX_SOMEVAR, "OVERFLOW! In NameOfThisFunc( ),
someVar=%d, otherVar=%d.\n", someVar, otherVar );
```

 Farklı hedeflere daha fazla veya daha az bilgi rapor etmek için özel bir makroyu kolayca değiştirebilirsiniz. Hata ayıklama gereksinimleriniz geliştikçe bu yaklaşım özellikle yararlıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [CRT Hata Ayıklama Teknikleri](../debugger/crt-debugging-techniques.md)
