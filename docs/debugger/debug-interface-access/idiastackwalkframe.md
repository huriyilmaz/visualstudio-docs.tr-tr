---
description: IDiaFrameData::execute) yönteminin çağrıları arasında yığın bağlamını sürdürür.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 785766a8fb0de87b967ecebdae391a5167bca466
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626852"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yönteminin çağrıları arasında yığın bağlamını sürdürür.

## <a name="syntax"></a>Syntax

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDiaStackWalkFrame` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|Bir yazmanın değerini verir.|
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|Yazmanın değerini ayarlar.|
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|Görüntüden bellek okur.|
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|Belirtilen yığın çerçevesinde en yakın işlev dönüş adresini arar.|
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|Belirtilen yığın çerçevesinde belirtilen adreste veya yakınında bir dönüş adresi arar.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, yazmazları okumak ve yazmak, belleğe erişmek ve dönüş adreslerini bulmak için program yürütme sırasında kullanılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 İstemci uygulaması bu arabirimi kullanır ve arabirimin bir örneğini [IDiaFrameData::execute yöntemine](../../debugger/debug-interface-access/idiaframedata-execute.md) iletir. Bu arabirimin aynı örneği, yönteminin her çağrılsı sırasında yazmaların durumunu korumak için tekrar tekrar `execute` kullanılır. yöntemi, `execute` dönüş adresini belirlemek için de bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)
