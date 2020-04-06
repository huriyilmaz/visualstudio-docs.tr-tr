---
title: IDebugEngine3::SetSymbolPath | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730668"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Hata ayıklama sembolleri için aranan yolu veya yolları ayarlar.

## <a name="syntax"></a>Sözdizimi

```cpp
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

## <a name="parameters"></a>Parametreler

`szSymbolSearchPath`\
[içinde] Sembol arama yolunu veya yollarını içeren dize. Ayrıntılar için "Açıklamalar" konusuna bakın. Null olamaz.

`szSymbolCachePath`\
[içinde] Sembollerin önbelleğe alınabileceği yerel yolu içeren dize. Null olamaz.

`Flags`\
[içinde] Kullanılmaz; her zaman 0 olarak ayarlanır.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dize, `szSymbolSearchPath` sembolleri aramak için yarım sütunlarla ayrılmış bir veya daha fazla yolun listesidir. Bu yollar yerel bir yol, UNC tarzı bir yol veya URL olabilir. Bu yollar da farklı türde bir karışımı olabilir. Yol UNC ise (örneğin, \\\Symserver\Symbols), hata ayıklama motoru yolun bir sembol sunucusuna olup olmadığını belirlemeli ve bu sunucudan semboller `szSymbolCachePath`yükleyebilmeli ve onları belirtilen yolda önbelleğe almalıdır.

 Sembol yolu bir veya daha fazla önbellek konumu da içerebilir. Önbellekler önce en yüksek öncelikli önbellekle öncelikli sırada listelenir ve * sembollerle ayrılır. Örnek:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) yöntemi sembollerin gerçek yükünü gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
