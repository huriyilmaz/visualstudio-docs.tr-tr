---
title: Semboller ve sembol etiketleri | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d2281a82926dabfde88b8d4bb9096f0e9624211
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738527"
---
# <a name="symbols-and-symbol-tags"></a>Simgeler ve Simge Etiketleri
Derlenmiş bir programla ilgili hata ayıklama bilgileri, program veritabanı (. pdb) dosyasında hata ayıklama arabirimi erişimi (DIA) SDK API 'Leri kullanılarak erişilebilen semboller olarak depolanır. Tüm semboller bir [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) ve bir [IDiaSymbol:: get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) özelliğine sahiptir. @No__t_0 özelliği, [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) numaralandırması tarafından tanımlanan simgenin türünü gösterir. @No__t_0 özelliği, bir simgenin her örneği için benzersiz tanımlayıcıyı içeren bir `DWORD` değeridir.

 Semboller ayrıca, simgenin yanı sıra diğer simgelere yönelik başvurular ve genellikle bir [IDiaSymbol:: get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) ya da [IDiaSymbol:: get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)ile ilgili ek bilgi belirten özelliklere sahiptir. Başvuru içeren bir özelliği sorguladığınızda, başvuru bir [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) nesnesi olarak döndürülür. Bu tür özellikler her zaman aynı ada sahip başka bir özellikle eşleştirilir, ancak "ID" ile (örneğin, [IDiaSymbol:: get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) ve [IDiaSymbol:: get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)). [Sembol konumlarındaki](../../debugger/debug-interface-access/symbol-locations.md)tablolar, [simge türlerinin sözcük hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)ve [sembol türlerinin sınıf hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) , her farklı sembol türünün özelliklerini özetler. Bu özelliklerde ilgili bilgiler veya diğer simgelere başvurular olabilir. @No__t_0 özellikleri, ilişkili özelliklerinin yalnızca sayısal sıra tanımlayıcıları olduğundan, bunlar daha fazla tartışmalardan çıkarılır. Bunlara yalnızca parametre açıklaması için gerektiğinde başvurulur.

 Özelliğe erişmeye çalışırken, hiçbir hata oluşmazsa ve symbol özelliğine bir değer atanmışsa, özelliğin "Get" metodu `S_OK` döndürür. @No__t_0 dönüş değeri, özelliğin geçerli simge için geçerli olmadığını gösterir.

## <a name="in-this-section"></a>Bu Bölümde

[Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)

Bir sembolün sahip olduğu farklı konum türlerini açıklar.

[Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)

Dosyalar, modüller ve işlevler gibi sözcük hiyerarşileri biçimli sembol türlerini açıklar.

[Simge Türlerinin Sınıf Hiyerarşisi](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)

Sınıflar, diziler ve işlev dönüş türleri gibi farklı dil öğelerine karşılık gelen sembol türlerini açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Arabirim Erişimi SDK'sında Hata Ayıklama](../../debugger/debug-interface-access/debug-interface-access-sdk.md)