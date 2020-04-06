---
title: IDebugComPlusSymbolProvider | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733469"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Yönetilen koda özgü yöntemlerle com+ sembol sağlayıcısını temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir ifade değerlendiricisi (EE) için yararlı olan arabirimler (EE) ile hata ayıklama motoru (DE) tarafından kullanılması amaçlanan arabirimler arasında herhangi bir ayrım olmamasına rağmen, aşağıdaki yöntemler büyük olasılıkla yalnızca DE geliştiricilerin ilgisini çekecektir: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, Replace Symbols, UnloadSymbols ve UpdateSymbols.

## <a name="methods"></a>Yöntemler
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimindeki yöntemlere ek olarak, bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Uygulama etki alanı tanımlayıcısı verilen belirtilen modül için hata ayıklama sembollerinin yüklenip yüklenmeyileceğini belirler.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Belirtilen ilkel türden bir tür oluşturur.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Belirtilen modüldeki belge konumunu hata ayıklama adresleri dizisiyle eşler.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Hata ayıklama adresi verilen belirtilen dizi yle ilgili tür bilgilerini alır.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Modülü ve uygulama etki alanı verilen derlemenin adını alır.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Verilen programlama dilinde uygulanan belirtilen öznitelik ile sınıfları alır.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Belirli bir modülde belirtilen özniteliğe sahip sınıfları alır.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Uygulama giriş noktasını alır.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Verilen satır ofsetini temsil eden bir işlev içindeki adresi alır.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Bir dizi yöntem için yerel değişkenlerin düzenini alır.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Meta veri nesnesi verilen belirtilen belirteçle ilişkili adı döndürür.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Belirtilen modül için verilen üst öznitelik ile hata ayıklama sembolleri alır.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Yönetilmeyen kod tarafından kullanılmak üzere sembol okuyucuyu alır.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Hata ayıklama adresi verilen bir sembol türüne alır.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Belirtilen hata ayıklama adresindeki işlevin silinip silinip silinmeyyeni belirler.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Belirtilen hata ayıklama adresindeki işlevin bayat kabul edilip edilemeyişolduğunu belirler.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Belirtilen hata ayıklama adresindeki kodun gizli olup olmadığını belirler.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Bellekte belirtilen hata ayıklama simgelerini yükler.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Veri akışı verilen hata ayıklama simgelerini yükler.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Geçerli hata ayıklama sembollerini belirtilen veri akışındakilerle değiştirir.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Belirtilen modülün hata ayıklama sembollerini bellekten kaldırır.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Bellekteki hata ayıklama sembollerini belirtilen veri akışıyla güncelleştirir.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Ş.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll
