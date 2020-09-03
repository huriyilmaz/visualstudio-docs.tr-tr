---
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 29bbb4eed485d3ff354757ab8c83a60b92f566aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85461051"
---
# <a name="symtagenum"></a>SymTagEnum
Simgenin türünü belirtir.

## <a name="syntax"></a>Syntax

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
`SymTagNull` Simgenin tür içermediğini belirtir.

`SymTagExe` Simgenin bir. exe dosyası olduğunu gösterir. `SymTagExe`Sembol deposu başına yalnızca bir sembol vardır. Genel kapsam olarak işlev görür ve bir üst öğeye sahip değildir.

`SymTagCompiland` Sembol deposunun her compiland bileşeni için compiland sembolünü gösterir. Yerel uygulamalar için, `SymTagCompiland` semboller görüntüye bağlı nesne dosyalarına karşılık gelir. Bazı Microsoft ara dil (MSIL) görüntüleri için, sınıf başına bir compiland vardır.

`SymTagCompilandDetails` Simgenin compiland 'ın genişletilmiş özniteliklerini içerdiğini belirtir. Bu özelliklerin alınması için compiland sembolleri yüklenmesi gerekebilir.

`SymTagCompilandEnv` Simgenin compiland için tanımlanan bir ortam dizesi olduğunu gösterir.

`SymTagFunction` Simgenin bir işlev olduğunu belirtir.

`SymTagBlock` Simgenin iç içe geçmiş bir blok olduğunu gösterir.

`SymTagData` Simgenin veri olduğunu gösterir.

`SymTagAnnotation` Simgenin bir kod ek açıklaması için olduğunu gösterir. Bu sembolün alt öğeleri sabit veri dizeleridir ( `SymTagData` , `LocIsConstant` , `DataIsConstant` ). Çoğu istemci bu simgeyi yoksayar.

`SymTagLabel` Simgenin bir etiket olduğunu gösterir.

`SymTagPublicSymbol` Simgenin ortak bir sembol olduğunu gösterir. Yerel uygulamalar için bu simge, görüntü bağlanırken karşılaşılan COFF dış sembolüdür.

`SymTagUDT` Simgenin Kullanıcı tanımlı bir tür (yapı, sınıf veya birleşim) olduğunu gösterir.

`SymTagEnum` Simgenin bir numaralandırma olduğunu gösterir.

`SymTagFunctionType` Simgenin bir işlev imza türü olduğunu gösterir.

`SymTagPointerType` Simgenin bir işaretçi türü olduğunu gösterir.

`SymTagArrayType` Simgenin bir dizi türü olduğunu gösterir.

`SymTagBaseType` Simgenin bir temel tür olduğunu gösterir.

`SymTagTypedef` Simgenin bir, diğer bir `typedef` tür için diğer ad olduğunu gösterir.

`SymTagBaseClass` Simgenin Kullanıcı tanımlı bir türün temel sınıfı olduğunu gösterir.

`SymTagFriend` Simgenin Kullanıcı tanımlı bir türün arkadaş olduğunu gösterir.

`SymTagFunctionArgType` Simgenin bir işlev bağımsız değişkeni olduğunu gösterir.

`SymTagFuncDebugStart` Simgenin, işlevin prolog kodunun bitiş konumu olduğunu gösterir.

`SymTagFuncDebugEnd` Simgenin, işlevin epıg kodunun başlangıç konumu olduğunu gösterir.

`SymTagUsingNamespace` Simgenin, geçerli kapsamda etkin olan bir ad alanı adı olduğunu gösterir.

`SymTagVTableShape` Simgenin bir sanal tablo açıklaması olduğunu gösterir.

`SymTagVTable` Simgenin bir sanal tablo işaretçisi olduğunu gösterir.

`SymTagCustom` Simgenin özel bir sembol olduğunu ve DIA tarafından yorumlanmadığını gösterir.

`SymTagThunk` Simgenin 16 ila 32 bit kod arasında veri paylaşımında kullanılan bir dönüştürücü olduğunu gösterir.

`SymTagCustomType` Simgenin özel bir derleyici simgesi olduğunu gösterir.

`SymTagManagedType` Simgenin meta verilerde olduğunu gösterir.

`SymTagDimension` Simgenin bir FORTRAN çok boyutlu dizisi olduğunu gösterir.

`SymTagCallSite` Simgenin çağrı sitesini temsil ettiğini belirtir.

`SymTagInlineSite` Simgenin satır içi siteyi temsil ettiğini belirtir.

`SymTagBaseInterface` Simgenin bir temel arabirim olduğunu gösterir.

`SymTagVectorType` Simgenin bir vektör türü olduğunu gösterir.

`SymTagMatrixType` Simgenin bir matris türü olduğunu gösterir.

`SymTagHLSLType` Simgenin yüksek düzey gölgelendirici dil türü olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar
Bir hata ayıklama dosyası içindeki tüm semboller, simgenin türünü belirten bir tanımlama etiketine sahiptir.

Bu Numaralandırmadaki değerler [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metoduna yapılan bir çağrı tarafından döndürülür.

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
