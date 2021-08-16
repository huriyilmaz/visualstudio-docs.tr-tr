---
description: Aşağıdaki tabloda sözcük hiyerarşisinde sembol türleri gösterilir.
title: Sembol Türlerinin Sözcük Hiyerarşisi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9d8691f5c1f2b72b6f82336d4b1304fc47c0f4a1fca8c43bd199c75a8b737ae3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379660"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Simge Türlerinin Sözcük Hiyerarşisi
Aşağıdaki tabloda sözcük hiyerarşisinde sembol türleri gösterilir.

## <a name="symbol-types"></a>Sembol Türleri

|Sembol türü|Açıklama|
|-----------------|-----------------|
|[Ek Açıklama](../../debugger/debug-interface-access/annotation.md)|Program kodunda açıklamalı bir konum belirtir.|
|[Block](../../debugger/debug-interface-access/block.md)|İşlevlerde iç içe geçmiş kapsamları belirtir.|
|`Compiland`|.exe `compiland` belirtir.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Ek derleme ayrıntılarının yüklenmesini gerektirten ve bu nedenle almak için çalışma zamanı yüküne neden olan derleme verilerini belirtir.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Derleme derlemesi için önemli olan tüm ek ortam değişkenlerini belirtir.|
|[Özel (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Kullanıcı tanımlı bir simge belirtir.|
|[Veriler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Parametreler, yerel değişkenler, genel değişkenler ve sınıf üyeleri gibi değişkenleri belirtir.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Verilerin genel kapsamını belirtir; , dosyanın tamamını .exe veya .dll olur.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Hata ayıklamanın sona erer olduğu tanımlı bir noktaya sahip olan bir işlevi belirtir.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Hata ayıklamanın başlayacağı tanımlı bir noktaya sahip olan bir işlevi belirtir.|
|[İşlev (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Bir işlevi belirtir.|
|[Etiket (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Program kodunda bir konum belirtir.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Yürütülebilir program çalıştırılabilir bir program çalıştırılabilirken görünen bir dış simge belirtir.|
|[Dönüştürücü](../../debugger/debug-interface-access/thunk.md)|`thunk`Belirtir.|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Bir tanımlayıcı `namespace` belirtir.|

> [!NOTE]
> Sembol türüne bağlı olarak ek sembol özellikleri kullanılabilir. Bu özellikler tek tek sembol konu başlıklarında listelenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Simgeler ve Simge Etiketleri](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
