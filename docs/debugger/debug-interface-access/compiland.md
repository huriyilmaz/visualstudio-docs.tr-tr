---
title: Compiland | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- compiland symbol
- compilands, compiland symbol
ms.assetid: c798eb2b-664a-41ec-ae90-5e9d292507ca
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccb4ca05374c86912cd48956262645b80fb14e40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745446"
---
# <a name="compiland"></a>Compiland
. Exe dosyasına bağlı her bir compiland için bir `SymTagCompiland` sembolü vardır. Compiland bilgileri, ek sembol yükleme gerektirebilecek bir `SymTagCompilandDetails` etiketiyle birlikte, Ek compiland sembolleri yüklemeden alınabilecek `SymTagCompiland` etiketiyle semboller arasında bölünür.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|derlemede Düzenle ve devam et etkinleştirildiyse `TRUE`.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|. Exe dosyasının simgesi.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|
|[IDiaSymbol::get_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|`BSTR`|Nesnenin yüklendiği kitaplığın veya nesne dosyasının adı.|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Compiland 'ın nesne dosyasının dosya adı.|
|[IDiaSymbol::get_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|`BSTR`|Kaynak dosyanın adı.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|@No__t_0 döndürür ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|

## <a name="see-also"></a>Ayrıca bkz.
- [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)
- [CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)