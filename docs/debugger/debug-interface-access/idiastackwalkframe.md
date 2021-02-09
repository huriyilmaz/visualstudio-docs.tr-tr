---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 05db065b047629e1eaac49e5f6aeeb05eed4307e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99863825"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yönteminin etkinleştirmeleri arasında yığın bağlamını korur.

## <a name="syntax"></a>Syntax

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaStackWalkFrame` .

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Bir kaydın değerini alır.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Bir kaydın değerini ayarlar.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Görüntüden belleği okur.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|En yakın işlev dönüş adresi için belirtilen yığın çerçevesini arar.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Belirtilen adreste veya yakınında bir dönüş adresi için belirtilen yığın çerçevesini arar.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, kayıt ve yazma ve dönüş adreslerini okuma ve yazma için program yürütme sırasında kullanılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 İstemci uygulaması bu arabirimi uygular ve arabirim örneğini [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yöntemine geçirir. Bu arabirimin aynı örneği yeniden kullanılır ve her yöntemin çağrılması sırasında yazmaçların durumunu korumak için yeniden kullanılır `execute` . `execute`Bu yöntem, dönüş adresini belirlemekte de bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)