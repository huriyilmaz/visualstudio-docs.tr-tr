---
description: Program hata ayıklama veritabanı (.pdb) dosyasını kullanarak yığının üzerinde dolmasına yardımcı olur.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128826"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Program hata ayıklama veritabanı (.pdb) dosyasını kullanarak yığının üzerinde dolmasına yardımcı olur.

## <a name="syntax"></a>Syntax

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>VTable Sırasına Göre Yöntemler
 Aşağıdaki tabloda yöntemleri `IDiaStackWalkHelper` gösterilmiştir:

|Yöntem|Açıklama|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Bir yazmanın değerini verir.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Yazmanın değerini ayarlar.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Yürütülebilir dosyanın görüntüsünden bellekte bir veri bloğu okur.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Belirtilen yığın çerçevesinde en yakın işlev dönüş adresini arar.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Belirtilen yığın çerçevesinde belirtilen yığın adresinin üzerinde veya yakınında bir dönüş adresi arar.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Belirtilen sanal adresi içeren yığın çerçevesini alın.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Belirtilen sanal adresi içeren simgeyi alın. **Not:**  Sembol türüne `SymTagFunctionType` [(SymTagEnum Numaralama numaralarından bir değer)](../../debugger/debug-interface-access/symtagenum.md) sahip olması gerekir.|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Belirtilen sanal adresle ilişkili PDATA veri bloğunü döndürür.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Yürütülebilir dosyanın bellek alanı içinde bir yerde bir sanal adres verilen bir yürütülebilir dosyanın başlangıç sanal adresini alın.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, program yürütme sırasında yığın çerçeveleri listesi oluşturmak üzere yürütülebilir dosya hakkında bilgi almak için DIA kodu tarafından çağrılır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 İstemci uygulaması, program yürütme sırasında yığının yürütülmesini desteklemek için bu arabirimi uygulamaya almaktadır. Bu arabirimin bir örneği [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) veya [IDiaStackWalker::getEnumFrames2 yöntemlerine](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Dia2.h

 Kitaplık: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Arabirimler (Arabirim Erişimi SDK'sında Hata Ayıklama)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
