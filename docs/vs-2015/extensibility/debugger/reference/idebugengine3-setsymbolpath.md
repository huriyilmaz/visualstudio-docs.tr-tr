---
title: 'IDebugEngine3:: SetSymbolPath | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d3ea3086931ab655209a5ca26d4d1527462fb205
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476807"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklama sembolleri için aranan yolu veya yolları ayarlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```csharp  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`szSymbolSearchPath`|'ndaki Sembol arama yolunu veya yollarını içeren dize. Ayrıntılar için "açıklamalar" başlığına bakın. Null olamaz.|  
|`szSymbolCachePath`|'ndaki Simgelerin önbelleğe alınbildiği yerel yolu içeren dize. Null olamaz.|  
|`Flags`|'ndaki Kullanılmıyor; her zaman 0 olarak ayarlayın.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Dize `szSymbolSearchPath`, sembolleri aramak için noktalı virgülle ayrılmış bir veya daha fazla yolun listesidir. Bu yollar yerel bir yol, bir UNC stili yol veya URL olabilir. Bu yollar farklı türlerin karışımı de olabilir. Yol UNC ise (örneğin \\, \Symserver\Symbols), hata ayıklama altyapısı yolun bir sembol sunucusuna olup olmadığını belirlemelidir ve bu sunucudan sembolleri yükleyip `szSymbolCachePath`belirtilen yolda önbelleğe almasını bilmelidir.  
  
 Sembol yolu bir veya daha fazla önbellek konumu da içerebilir. Önbellekler öncelik sırasıyla, en yüksek öncelikli önbellek ve * simgelerle ayrılmış şekilde listelenir. Örnek:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) yöntemi, simgelerin gerçek yükünü gerçekleştirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
