---
description: Derlenmiş bir programla ilgili hata ayıklama bilgileri, program veritabanı (. pdb) dosyasında hata ayıklama arabirimi erişimi (DIA) SDK API 'Leri kullanılarak erişilebilen semboller olarak depolanır.
title: Semboller ve sembol etiketleri | Microsoft Docs
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
ms.workload:
- multiple
ms.openlocfilehash: 98631149e5a53c13bfc9b12b0d6de165c345e29a
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155287"
---
# <a name="symbols-and-symbol-tags"></a>Simgeler ve Simge Etiketleri
Derlenmiş bir programla ilgili hata ayıklama bilgileri, program veritabanı (. pdb) dosyasında hata ayıklama arabirimi erişimi (DIA) SDK API 'Leri kullanılarak erişilebilen semboller olarak depolanır. Tüm semboller bir [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) ve [ıdiasymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) özelliğine sahiptir. `symTag`Özelliği, [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) numaralandırması tarafından tanımlanan sembolün türünü gösterir. `symIndexId`Özelliği, `DWORD` bir simgenin her örneği için benzersiz tanımlayıcıyı içeren bir değerdir.

 Semboller ayrıca, simgenin yanı sıra diğer simgelere yönelik başvurular ve genellikle bir [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) ya da [ıdiasymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)gibi ek bilgileri belirten özelliklere sahiptir. Başvuru içeren bir özelliği sorguladığınızda, başvuru bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi olarak döndürülür. Bu tür özellikler her zaman aynı ada sahip başka bir özellikle eşleştirilir, ancak "ID" ile (örneğin, [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) ve [ıdiasymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)). [Sembol konumlarındaki](../../debugger/debug-interface-access/symbol-locations.md)tablolar, [simge türlerinin sözcük hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)ve [sembol türlerinin sınıf hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) , her farklı sembol türünün özelliklerini özetler. Bu özelliklerde ilgili bilgiler veya diğer simgelere başvurular olabilir. Özellikler, `*Id` ilişkili özelliklerinin yalnızca sayısal sıra tanımlayıcıları olduğundan, bunlar daha fazla tartışmalardan çıkarılır. Bunlara yalnızca parametre açıklaması için gerektiğinde başvurulur.

 Özelliğe erişmeye çalışırken, hiçbir hata oluşmazsa ve symbol özelliğine bir değer atanmışsa, özelliğin "Get" yöntemi döndürür `S_OK` . Dönüş değeri, `S_FALSE` özelliğin geçerli simge için geçerli olmadığını gösterir.

## <a name="in-this-section"></a>Bu Bölümde

[Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)

Bir sembolün sahip olduğu farklı konum türlerini açıklar.

[Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Dosyalar, modüller ve işlevler gibi sözcük hiyerarşileri biçimli sembol türlerini açıklar.

[Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Sınıflar, diziler ve işlev dönüş türleri gibi farklı dil öğelerine karşılık gelen sembol türlerini açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
