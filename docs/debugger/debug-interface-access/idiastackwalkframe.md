---
title: IDiaStackWalkFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5b2657127726e387e81a5b28c639abbaa5399019
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741436"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yönteminin etkinleştirmeleri arasında yığın bağlamını korur.

## <a name="syntax"></a>Sözdizimi

```
IDiaStackWalkFrame : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda `IDiaStackWalkFrame` yöntemleri gösterilmektedir.

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
 İstemci uygulaması bu arabirimi uygular ve arabirim örneğini [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) yöntemine geçirir. Bu arabirimin aynı örneği yeniden kullanılır ve `execute` yönteminin her çağrılması sırasında yazmaçların durumunu korumak için yeniden kullanılır. @No__t_0 yöntemi, dönüş adresini belirleyebilmek için de bu arabirimi kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: Msdia80. dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)