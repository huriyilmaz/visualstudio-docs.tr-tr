---
description: Yönetilen koda özgü yöntemlerle bir COM+ sembol sağlayıcısını temsil eder.
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
ms.openlocfilehash: 524663723537dd84233a9570104a779cbc3411921640768f1bcdc6a9d89e1ee2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121308057"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Yönetilen koda özgü yöntemlerle bir COM+ sembol sağlayıcısını temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir ifade değerlendirici (EE) ve bir hata ayıklama altyapısı (DE) tarafından kullanılmak üzere tasarlanmış arabirimler arasında ayrım yoktur, ancak aşağıdaki yöntemler yalnızca DE geliştiricileriyle ilgili olacaktır: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols ve UpdateSymbols.

## <a name="methods"></a>Yöntemler
 [Bu arabirim, IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) arabiriminde yöntemlere ek olarak aşağıdaki yöntemleri de kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Uygulama etki alanı tanımlayıcısı verilmelidir, belirtilen modül için hata ayıklama sembollerinin yük olup olmadığını belirler.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Belirtilen ilkel türden bir tür oluşturur.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Haritalar modülde bir belge konumunu hata ayıklama adresleri dizisine ekler.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Belirtilen diziyle ilgili tür bilgilerini hata ayıklama adresiyle birlikte verir.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Modülüne ve uygulama etki alanına göre derlemenin adını alın.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Belirtilen programlama dilinde uygulanan belirtilen öznitelikle sınıfları alın.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Belirli bir modülde belirtilen öznitelikle sınıfları alınır.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Uygulama giriş noktasını alın.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Verilen satır uzaklığını temsil eden bir işlev içindeki adresi verir.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Bir yöntem kümesi için yerel değişkenlerin düzenini alın.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Belirtilen belirteçle ilişkili adı meta veri nesnesine göre döndürür.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Belirtilen modül için verilen üst öznitelikle hata ayıklama sembollerini alın.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Unmanaged code tarafından kullanılacak sembol okuyucuyu alın.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Hata ayıklama adresi verilen bir sembol türüne alınır.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Belirtilen hata ayıklama adresine sahip işlevin silinebilir olup olmadığını belirler.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Belirtilen hata ayıklama adresli işlevin eski olarak kabul edilir olup olmadığını belirler.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Belirtilen hata ayıklayıcı adresli kodun gizli olup olmadığını belirler.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Belirtilen hata ayıklama sembollerini belleğe yükler.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Veri akışına göre hata ayıklama sembollerini yükler.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Geçerli hata ayıklama sembollerini belirtilen veri akışındaki sembollerle değiştirir.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Belirtilen modül için hata ayıklama sembollerini bellekten kaldırıyor.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Bellekte hata ayıklama sembollerini belirtilen veri akışıyla güncelleştirme.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Sh.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll
