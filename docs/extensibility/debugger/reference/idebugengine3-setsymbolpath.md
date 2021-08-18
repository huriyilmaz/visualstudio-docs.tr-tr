---
description: Hata ayıklama sembolleri için aranan yolu veya yolları ayarlar.
title: IDebugEngine3::SetSymbolPath | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73e7d4cb8ed36546e60326bc0935817d9b647adb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122118989"
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
[in] Sembol arama yolunu veya yollarını içeren dize. Ayrıntılar için bkz. "Açıklamalar". Null olamaz.

`szSymbolCachePath`\
[in] Sembollerin önbelleğe alınarak alına yerel yolu içeren dize. Null olamaz.

`Flags`\
[in] Kullanılmadı; her zaman 0 olarak ayarlayın.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, S_OK; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Dize, simgeleri aramak için noktalı virgülle ayrılmış `szSymbolSearchPath` bir veya daha fazla yolun listesidir. Bu yollar yerel yol, UNC stilinde bir yol veya URL olabilir. Bu yollar farklı türlerin bir karışımı da olabilir. Yol UNC ise (örneğin, \Symserver\Symbols), hata ayıklama altyapısı yolun bir sembol sunucusuna olup olmadığını belirlemeli ve bu sunucudan sembolleri yükerek tarafından belirtilen yolda önbelleğe \\ `szSymbolCachePath` almalı.

 Sembol yolu bir veya daha fazla önbellek konumu da içerebilir. Önbellekler öncelik sırasına göre listelenir ve en yüksek öncelikli önbellek önceliğe sahip olur ve * simgeleriyle ayrılır. Örnek:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) yöntemi sembollerin gerçek yükünü gerçekleştirir.

## <a name="see-also"></a>Ayrıca bkz.
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
