---
title: Modülleri Listele Komutu
description: Modülleri Listele komutu ve geçerli işlem için modülleri nasıl listeleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa0c3f6445a22ee80457e8a7f9f24fb7008f77ed
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305307"
---
# <a name="list-modules-command"></a>Modülleri Listele Komutu
Geçerli işlem için modülleri listeler.

## <a name="syntax"></a>Söz dizimi

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametreler
Adrestir`yes|no`

İsteğe bağlı. Modüllerin bellek adreslerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

Ada`yes|no`

İsteğe bağlı. Modüllerin adlarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

Siparişi`yes|no`

İsteğe bağlı. Modüllerin sırasının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no` olarak belirlenmiştir.

Yolun`yes|no`

İsteğe bağlı. Modüllerin yollarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

İşle`yes|no`

İsteğe bağlı. Modül işlemlerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/SymbolFile:`yes|no`

İsteğe bağlı. Modüllerin sembol dosyalarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/SymbolStatus:`yes|no`

İsteğe bağlı. Modüllerin sembol durumlarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

İlişkin`yes|no`

İsteğe bağlı. Modüllerin zaman damgalarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no` olarak belirlenmiştir.

Sürümünüze`yes|no`

İsteğe bağlı. Modüllerin sürümlerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no` olarak belirlenmiştir.

## <a name="example"></a>Örnek
Bu örnekte, geçerli işlem için modül adları, adresler ve zaman damgaları listelenmektedir.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Nasıl Yapılır: Modüller Penceresini Kullanma](../../debugger/how-to-use-the-modules-window.md)
