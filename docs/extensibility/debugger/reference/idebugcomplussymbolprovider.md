---
description: Yönetilen koda özgü yöntemlere sahip bir COM+ sembol sağlayıcısını temsil eder.
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: da8d6c4ebd64c4dd4f3a4610e2f4753b86aa0ef5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122145048"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Yönetilen koda özgü yöntemlere sahip bir COM+ sembol sağlayıcısını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 bir ifade değerlendirici (EE) ve bir hata ayıklama altyapısı (DE) tarafından kullanılması amaçlanan arabirimler arasında ayrım olmamasına karşın, aşağıdaki yöntemler muhtemelen yalnızca geliştiricileri de ilgileniyor: aresymbolsloaded, GetAddressesInModuleFromPosition, getentrypoint, getfunctionlinekayması, getlocalvariablelayout, ısfunctionstale, loadsymbols, loadsymbolsfromstream, selectioncesymbar, unloadsymbols ve updatesymbols.

## <a name="methods"></a>Yöntemler
 Bu arabirim, [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Uygulama etki alanı tanımlayıcısı verilen belirtilen modül için hata ayıklama simgelerinin yüklenip yüklenmediğini belirler.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Belirtilen ilkel türden bir tür oluşturur.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|belirtilen modüldeki bir belge konumunu hata ayıklama adresleri dizisine Haritalar.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Belirtilen dizi hakkında hata ayıklama adresini verilen tür bilgilerini alır.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Modül ve uygulama etki alanı verilen derlemenin adını alır.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Belirtilen özniteliğine sahip sınıfları verilen programlama dilinde uygulanan şekilde alır.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Belirli bir modülde belirtilen özniteliğe sahip sınıfları alır.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Uygulama giriş noktasını alır.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Verilen satır sapmasını temsil eden bir işlev içindeki adresi alır.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Bir dizi yöntem için yerel değişkenlerin yerleşimini alır.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Belirtilen belirteçle ilişkili, meta veri nesnesi verilen adı döndürür.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Belirtilen modül için verilen üst özniteliğe sahip hata ayıklama sembollerini alır.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Yönetilmeyen kod tarafından kullanılacak simge okuyucuyu alır.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Hata ayıklama adresi verilen bir sembol türüne alır.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Belirtilen hata ayıklama adresindeki işlevin silinip silinmediğini belirler.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Belirtilen hata ayıklama adresindeki işlevin eski olarak kabul edileceğini belirler.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Belirtilen hata ayıklayıcı adresindeki kodun gizli olup olmadığını belirler.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Belirtilen hata ayıklama sembollerini belleğe yükler.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Veri akışı verilen hata ayıklama sembollerini yükler.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Geçerli hata ayıklama sembollerini, belirtilen veri akışındaki verilerle değiştirir.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Belirtilen modülün hata ayıklama sembollerini bellekten kaldırır.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Bellekteki hata ayıklama sembollerini, belirtilen veri akışı ile güncelleştirir.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: SH. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll
