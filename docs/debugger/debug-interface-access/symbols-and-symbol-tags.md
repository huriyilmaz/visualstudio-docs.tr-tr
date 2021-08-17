---
description: Derlenmiş bir programla ilgili hata ayıklama bilgileri program veritabanı (.pdb) dosyasında Hata Ayıklama Arabirimi Erişimi (DIA) SDK API'leri kullanılarak erişilebilen semboller olarak depolanır.
title: Semboller ve Sembol Etiketleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 5f3b6e176a2a3fec7bb3e6a98e80cf23e4de353c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065871"
---
# <a name="symbols-and-symbol-tags"></a>Simgeler ve Simge Etiketleri
Derlenmiş bir programla ilgili hata ayıklama bilgileri program veritabanı (.pdb) dosyasında Hata Ayıklama Arabirimi Erişimi (DIA) SDK API'leri kullanılarak erişilebilen semboller olarak depolanır. Tüm sembollerin [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) ve [IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) özelliği vardır. `symTag`özelliği, SymTagEnum Numaralama [numaralarıyla tanımlandığı şekilde sembolünü](../../debugger/debug-interface-access/symtagenum.md) gösterir. özelliği, `symIndexId` bir `DWORD` sembolün her örneği için benzersiz tanımlayıcıyı içeren bir değerdir.

 Semboller ayrıca simge hakkında ek bilgi ve diğer sembollere başvurular belirten özelliklere sahiptir. Bu özellikler genellikle [IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) veya [IDiaSymbol::get_classParent.](../../debugger/debug-interface-access/idiasymbol-get-classparent.md) Başvuru içeren bir özelliği sorgularken, başvuru bir [IDiaSymbol nesnesi olarak](../../debugger/debug-interface-access/idiasymbol.md) döndürülür. Bu tür özellikler her zaman aynı adla başka bir özellikle eşleştirildi ancak son ek olarak "Id" ekini alır, örneğin, [IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) ve [IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). Sembol Konumları, [Sembol](../../debugger/debug-interface-access/symbol-locations.md)Türlerinin [Sözcük](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)Hiyerarşisi ve Sembol Türlerinin Sınıf Hiyerarşisi tablolarında, [](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) farklı sembol türlerinin her biri için özellikler ana hatlarıyla gösterilir. Bu özelliklerle ilgili bilgiler veya diğer sembollere başvurular olabilir. Özellikler, ilgili özelliklerinin sayısal ve sayısal tanımlayıcıları olduğundan, bunlar diğer `*Id` tartışmalardan atlanır. Bunlar yalnızca parametrenin netleştirmesi için gereken yere başvurur.

 Özelliğine erişmeye çalışırken hata oluşmazsa ve sembol özelliğine bir değer atanmışsa, özelliğin "get" yöntemi `S_OK` döndürür. dönüş `S_FALSE` değeri, özelliğin geçerli sembol için geçerli olmadığını gösterir.

## <a name="in-this-section"></a>Bu Bölümde

[Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)

Bir sembolün sahip olduğu farklı konum türlerini açıklar.

[Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Dosyalar, modüller ve işlevler gibi sözcük hiyerarşileri oluşturmak için sembol türlerini açıklar.

[Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Sınıflar, diziler ve işlev dönüş türleri gibi farklı dil öğelerine karşılık gelen sembol türlerini açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
