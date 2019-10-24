---
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738512"
---
# <a name="symtagenum"></a>SymTagEnum
Simgenin türünü belirtir.

## <a name="syntax"></a>Sözdizimi

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>Öğeler
`SymTagNull`, simgenin tür Içermediğini belirtir.

`SymTagExe`, simgenin bir. exe dosyası olduğunu gösterir. Sembol deposu başına yalnızca bir `SymTagExe` sembol vardır. Genel kapsam olarak işlev görür ve bir üst öğeye sahip değildir.

`SymTagCompiland`, sembol deposunun her compiland bileşeni için compiland sembolünü gösterir. Yerel uygulamalar için `SymTagCompiland` sembolleri görüntüye bağlı nesne dosyalarına karşılık gelir. Bazı Microsoft ara dil (MSIL) görüntüleri için, sınıf başına bir compiland vardır.

`SymTagCompilandDetails`, simgenin compiland 'ın genişletilmiş özniteliklerini içerdiğini gösterir. Bu özelliklerin alınması için compiland sembolleri yüklenmesi gerekebilir.

`SymTagCompilandEnv`, simgenin compiland için tanımlanan bir ortam dizesi olduğunu gösterir.

`SymTagFunction`, simgenin bir işlev olduğunu belirtir.

`SymTagBlock`, simgenin iç içe geçmiş bir blok olduğunu gösterir.

`SymTagData`, simgenin veri olduğunu gösterir.

`SymTagAnnotation`, simgenin bir kod ek açıklaması için olduğunu gösterir. Bu sembolün alt öğeleri sabit veri dizeleridir (`SymTagData`, `LocIsConstant`, `DataIsConstant`). Çoğu istemci bu simgeyi yoksayar.

`SymTagLabel`, simgenin bir etiket olduğunu gösterir.

`SymTagPublicSymbol`, simgenin ortak bir sembol olduğunu gösterir. Yerel uygulamalar için bu simge, görüntü bağlanırken karşılaşılan COFF dış sembolüdür.

`SymTagUDT`, simgenin Kullanıcı tanımlı bir tür (yapı, sınıf veya birleşim) olduğunu gösterir.

`SymTagEnum`, simgenin bir numaralandırma olduğunu gösterir.

`SymTagFunctionType`, simgenin bir işlev imza türü olduğunu gösterir.

`SymTagPointerType`, simgenin bir işaretçi türü olduğunu gösterir.

`SymTagArrayType`, simgenin bir dizi türü olduğunu gösterir.

`SymTagBaseType`, simgenin bir temel tür olduğunu gösterir.

`SymTagTypedef`, simgenin bir `typedef`, diğer bir tür için diğer ad olduğunu gösterir.

`SymTagBaseClass`, simgenin Kullanıcı tanımlı bir türün temel sınıfı olduğunu gösterir.

`SymTagFriend`, simgenin Kullanıcı tanımlı bir türün arkadaş olduğunu gösterir.

`SymTagFunctionArgType`, simgenin bir işlev bağımsız değişkeni olduğunu gösterir.

`SymTagFuncDebugStart`, simgenin işlevin prolog kodunun bitiş konumu olduğunu gösterir.

`SymTagFuncDebugEnd`, simgenin, işlevin epıg kodunun başlangıç konumu olduğunu gösterir.

`SymTagUsingNamespace`, simgenin geçerli kapsamda etkin olan bir ad alanı adı olduğunu gösterir.

`SymTagVTableShape`, simgenin bir sanal tablo açıklaması olduğunu gösterir.

`SymTagVTable`, simgenin bir sanal tablo işaretçisi olduğunu gösterir.

`SymTagCustom`, simgenin özel bir sembol olduğunu ve DIA tarafından yorumlanmadığını gösterir.

`SymTagThunk`, simgenin 16 ve 32 bit kod arasında veri paylaşımında kullanılan bir dönüştürücü olduğunu gösterir.

`SymTagCustomType`, simgenin özel bir derleyici simgesi olduğunu gösterir.

`SymTagManagedType`, simgenin meta verilerde olduğunu gösterir.

`SymTagDimension`, simgenin bir FORTRAN çok boyutlu dizisi olduğunu gösterir.

`SymTagCallSite`, simgenin çağrı sitesini temsil ettiğini gösterir.

`SymTagInlineSite`, simgenin satır içi siteyi temsil ettiğini gösterir.

`SymTagBaseInterface`, simgenin bir temel arabirim olduğunu gösterir.

`SymTagVectorType`, simgenin bir vektör türü olduğunu gösterir.

`SymTagMatrixType`, simgenin bir matris türü olduğunu gösterir.

`SymTagHLSLType`, simgenin yüksek düzey gölgelendirici dil türü olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
Bir hata ayıklama dosyası içindeki tüm semboller, simgenin türünü belirten bir tanımlama etiketine sahiptir.

Bu Numaralandırmadaki değerler [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) yöntemi çağrısıyla döndürülür.

Bu Numaralandırmadaki değerler, aramanın kapsamını belirli bir sembol türüyle sınırlamak için aşağıdaki yöntemlere geçirilir:

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Gereksinimler
Üst bilgi: cvconst. h

## <a name="see-also"></a>Ayrıca bkz.
- [Enumerations and Structures](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Simge Türlerinin Sözcük Hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
