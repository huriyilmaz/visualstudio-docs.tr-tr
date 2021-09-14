---
description: Exe, .exe veya .dll dosyasının genel kapsamını temsil ettiğinden, sözcük temelli ya da sınıf üst öğesi olmayan tek simgedir.
title: Exe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dll files
- Exe symbol
- .exe files
- executable files, Exe symbol
ms.assetid: a781d2cf-55fe-4373-9cf1-b732864244e0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 32f559e2365e0c422497573dc19ce2ce094caa9a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630602"
---
# <a name="exe"></a>Exe
Exe, .exe veya .dll dosyasının genel kapsamını temsil ettiğinden, sözcük temelli ya da sınıf üst öğesi olmayan tek simgedir. Dosya başına etiket içeren tek bir sembol vardır `SymTagExe` . [IDiaSession:: get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md) yöntemi simgeyi döndürür.

## <a name="properties"></a>Özellikler
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.

|Özellik|Veri türü|Açıklama|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|`DWORD`|Bu yürütülebilir dosyanın yaşı.|
|[IDiaSymbol::get_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|`GUID`|`GUID` Bu yürütülebilir dosya.|
|[IDiaSymbol::get_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|`BOOL`|`TRUE` Bu yürütülebilirle ilişkilendirilen sembol dosyası C türleri içeriyorsa (yalnızca DIA SDK v 8.0 veya üzeri).|
|[IDiaSymbol::get_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|`BOOL`|`TRUE` özel semboller bu yürütülebilir dosya ile ilişkili sembol dosyasından çıkarıldı (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde).|
|[IDiaSymbol::get_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|`DWORD`|Hedef CPU belirten değer ( [CV_CPU_TYPE_e sabit listesi](../../debugger/debug-interface-access/cv-cpu-type-e.md) değerlerinden biri).|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|.exe dosyanın adı.|
|[IDiaSymbol::get_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|`DWORD`|Yürütülebilir dosyanın imzası.|
|[IDiaSymbol::get_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|`BSTR`|.exe dosyasının. pdb veya. dbg dosyasının tam yolu.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagExe` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|

## <a name="see-also"></a>Ayrıca bkz.
- [IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
