---
description: Program hata ayıklama veritabanı (. pdb) dosyasını kullanarak yığını yürüme işlemini kolaylaştırır.
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 06ba4964be340bd5d087a73fb5af9e9d48ded02d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626787"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Program hata ayıklama veritabanı (. pdb) dosyasını kullanarak yığını yürüme işlemini kolaylaştırır.

## <a name="syntax"></a>Syntax

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>VTable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDiaStackWalkHelper` :

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Bir kaydın değerini alır.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Bir kaydın değerini ayarlar.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Bellek içindeki yürütülebilir dosyanın görüntüsünden bir veri bloğunu okur.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|En yakın işlev dönüş adresi için belirtilen yığın çerçevesini arar.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Belirtilen yığın adresinde veya yakınında bir dönüş adresi için belirtilen yığın çerçevesini arar.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Belirtilen sanal adresi içeren yığın çerçevesini alır.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Belirtilen sanal adresi içeren simgeyi alır. **Note:**  Simgenin türü `SymTagFunctionType` ( [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) numaralandırmasından bir değer) olmalıdır.|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Belirtilen sanal adresle ilişkili PDATA veri bloğunu döndürür.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Yürütülebilir dosyanın başlangıç sanal adresini alır ve bir sanal adres, çalıştırılabilirin bellek alanında bir yere verilir.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, program yürütmesi sırasında yığın çerçevelerinin bir listesini oluşturmak üzere yürütülebilir dosya hakkında bilgi almak için, DIA kodu tarafından çağırılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 İstemci uygulaması, program yürütme sırasında yığını yürüme desteğini desteklemek için bu arabirimi uygular. Bu arabirimin bir örneği [ıdiastackdenetçisi:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) veya [ıdiastackdenetçisi:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) yöntemlerine geçirilir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: dia2. h

 Kitaplık: diaguid. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
