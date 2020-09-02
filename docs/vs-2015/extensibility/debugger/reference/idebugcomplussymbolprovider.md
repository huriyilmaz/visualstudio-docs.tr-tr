---
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b70701aa9c4b339749554601e2a565c17697c6a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186511"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Yönetilen koda özgü yöntemlere sahip bir COM+ sembol sağlayıcısını temsil eder.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bir ifade değerlendirici (EE) ve bir hata ayıklama altyapısı (DE) tarafından kullanılması amaçlanan arabirimler arasında ayrım olmamasına karşın, aşağıdaki yöntemler muhtemelen yalnızca geliştiricileri DE ilgileniyor: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, Getfunctionlinekayması, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, Selectioncesymbar, UnloadSymbols ve UpdateSymbols.  
  
## <a name="methods"></a>Yöntemler  
 Bu arabirim, [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) arabirimindeki yöntemlere ek olarak aşağıdaki yöntemleri uygular:  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Uygulama etki alanı tanımlayıcısı verilen belirtilen modül için hata ayıklama simgelerinin yüklenip yüklenmediğini belirler.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Belirtilen ilkel türden bir tür oluşturur.|  
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Belirtilen modüldeki bir belge konumunu hata ayıklama adresleri dizisine eşler.|  
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
