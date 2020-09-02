---
title: İşlev (hata ayıklama arabirimi erişim SDK 'Sı) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- Function symbol
ms.assetid: 458dc91c-b78b-4427-84f4-615d89e26760
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fb1355dfebaad4230c349c0c7b30ae400ecdaa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65692179"
---
# <a name="function-debug-interface-access-sdk"></a>İşlev (Arabirim Erişimi SDK'sında Hata Ayıklama)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Her işlev bir sembol tarafından tanımlanır `SymTagFunction` .  
  
## <a name="properties"></a>Özellikler  
 Aşağıdaki tabloda, bu sembol türü için geçerli olan özellikler gösterilmektedir.  
  
|Özellik|`Data type`|Açıklama|  
|--------------|-----------------|-----------------|  
|[IDiaSymbol::get_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|`DWORD`|[CV_access_e numaralandırmanın](../../debugger/debug-interface-access/cv-access-e.md)değerlerinden biri, işlev bir üye işlevdir.|  
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Konumun konum parçası; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Konumun bölüm bölümü; Ayrıntılar için bkz. [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md).|  
|[IDiaSymbol::get_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|`IDiaSymbol*`|İşlev bir üye işlevise, sınıfın simgesi.|  
|[IDiaSymbol::get_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|`DWORD`|Sınıf üst simgesinin KIMLIĞI.|  
|[IDiaSymbol::get_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|`BOOL`|`TRUE` işlev bir sabit olarak işaretlenmişse.|  
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` işlev özel bir çağırma kuralı kullanıyorsa (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` işlev bir sanal geri dönüş gerçekleştiriyorsa (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|`BOOL`|`TRUE` işlev ayrılmış bellek işlevini kullanıyorsa (yalnızca uınnder DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|`BOOL`|`TRUE` işlev C++ stili özel durum işleme (yalnızca DIA SDK V 8.0 veya üzeri) içeriyorsa.|  
|[IDiaSymbol::get_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|`BOOL`|`TRUE` işlev zaman uyumsuz özel durum işleme içeriyorsa (yalnızca DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|`BOOL`|`TRUE` işlev satır içi derleme içeriyorsa (yalnızca DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|`BOOL`|`TRUE` işlev bir [longjmp](https://msdn.microsoft.com/library/0e13670a-5130-45c1-ad69-6862505b7a2f) çağrısı içeriyorsa (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` işlev güvenlik denetimleri içeriyorsa (yalnızca DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|`BOOL`|`TRUE` işlev Win32 stili yapılandırılmış özel durum işleme (yalnızca DIA SDK V 8.0 veya üzeri) içeriyorsa.|  
|[IDiaSymbol::get_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|`BOOL`|`TRUE` işlev bir [setjmp](https://msdn.microsoft.com/library/684a8b27-e8eb-455b-b4a8-733ca1cbd7d2) çağrısı içeriyorsa (yalnızca DIA SDK v 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` işlevin kesintiye döndürme işlemi varsa (yalnızca DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|`BOOL`|`TRUE` bir işlev giriş sanal ise.|  
|[IDiaSymbol::get_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|`BOOL`|`TRUE` işlev, [satır içi, __inline \_ _forceinline](../../misc/inline-inline-forceinline.md) özniteliklerinden biri ile işaretlenmişse.|  
|[IDiaSymbol::get_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|`BOOL`|`TRUE` işlev [Naked](https://msdn.microsoft.com/library/69723241-05e1-439b-868e-20a83a16ab6d) özniteliğiyle işaretlenmişse (yalnızca DIA SDK v 8.0 veya üzeri).|  
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` işlev statikse (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|`ULONGLONG`|Konumdan başlayarak işlev kodundaki bayt sayısı.|  
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Kapsayan compiland 'ın simgesi.|  
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|Sözlü üst simgenin KIMLIĞI.|  
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|İşlevler statik veya meta veri konumlarına sahip olabilir; Ayrıntılar için bkz. [sembol konumları](../../debugger/debug-interface-access/symbol-locations.md).|  
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|İşlevin adı.|  
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` işlev bir satır içi işlev değilse (yalnızca n DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` işlev erişilebilir değilse (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` işlev bir değer döndürmezse (yalnızca DIA SDK V 8.0 veya üzeri).|  
|[IDiaSymbol::get_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|`BOOL`|`TRUE` işlev arabellek güvenliği denetimleri ile derlenmişse ancak yığın sıralaması yapılamadığını.|  
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` kodda iyileştirilmiş kod için hata ayıklama bilgileri varsa (yalnızca DIA SDK V 8.0 veya üzeri sürümlerde).|  
|[IDiaSymbol::get_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|`BOOL`|`TRUE` Eğer işlevi saf sanal ise.|  
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Bu işlevin modülünün içindeki göreli konumu.|  
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Simgenin dizin KIMLIĞI.|  
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Döndürür `SymTagFunction` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) değerlerinden biri).|  
|[IDiaSymbol::get_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|`DWORD`|İşlev için meta veri belirteci.|  
|[IDiaSymbol::get_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|`IDiaSymbol*`|İşlev imzasının simgesi.|  
|[IDiaSymbol::get_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|`DWORD`|Tür sembolünün KIMLIĞI.|  
|[IDiaSymbol::get_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|`BOOL`|`TRUE` işlevin hizalanmamış olması durumunda.|  
|[IDiaSymbol::get_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|`BSTR`|İşlev adının süslenmiş biçimi (yalnızca DIA SDK v 8.0 veya üzeri)|  
|[IDiaSymbol::get_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|`BSTR`|İşlev adının bir kısmı veya tamamı (yalnızca DIA SDK v 8.0 veya üzeri).|  
|[IDiaSymbol::get_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|`BOOL`|`TRUE` bir sanal işlev.|  
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Bu işlevin yürütülebilir görüntü içinde konumu.|  
|[IDiaSymbol::get_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|`DWORD`|Sanal bir işlev ise, sanal işlev tablosundaki fark.|  
|[IDiaSymbol::get_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|`BOOL`|`TRUE` işlev geçici olarak işaretlenmişse.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [CV_access_e numaralandırması](../../debugger/debug-interface-access/cv-access-e.md)   
 [Sembol türlerinin sözcük hiyerarşisi hiyerarşisi](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [LocationType numaralandırması](../../debugger/debug-interface-access/locationtype.md)   
 [Simge Konumları](../../debugger/debug-interface-access/symbol-locations.md)
