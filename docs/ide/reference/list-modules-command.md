---
title: Modülleri Listele Komutu
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
ms.openlocfilehash: 1e083a0e1baeefc6807dccb2199cd0e5a9bd883d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595507"
---
# <a name="list-modules-command"></a>Modülleri Listele Komutu
Geçerli işlemin modüllerini listeler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametreler
/Adres:`yes|no`

İsteğe bağlı. Modüllerin bellek adreslerinin gösterip göstermeyeceğini belirtir. Varsayılan değer. `yes`

/Adı:`yes|no`

İsteğe bağlı. Modüllerin adlarının gösterip göstermeyeceğini belirtir. Varsayılan değer. `yes`

/Sipariş:`yes|no`

İsteğe bağlı. Modüllerin sırasını gösterip göstermeyeceğini belirtir. Varsayılan değer. `no`

/Yol:`yes|no`

İsteğe bağlı. Modüllerin yollarınıgösterip göstermeyeceğini belirtir. Varsayılan değer. `yes`

/İşlem:`yes|no`

İsteğe bağlı. Modüllerin süreçlerinin gösterip göstermeyeceğini belirtir. Varsayılan değer. `no`

/SymbolFile:`yes|no`

İsteğe bağlı. Modüllerin sembol dosyalarını gösterip göstermeyeceğini belirtir. Varsayılan değer. `no`

/SembolDurumu:`yes|no`

İsteğe bağlı. Modüllerin sembol durumlarını gösterip göstermeyeceğini belirtir. Varsayılan değer. `yes`

/Zaman damgası:`yes|no`

İsteğe bağlı. Modüllerin zaman damgalarını gösterip göstermeyeceğini belirtir. Varsayılan değer. `no`

/Sürüm:`yes|no`

İsteğe bağlı. Modüllerin sürümlerini gösterip göstermeyeceğini belirtir. Varsayılan değer. `no`

## <a name="example"></a>Örnek
Bu örnekte, geçerli işlemin modül adları, adresleri ve zaman damgaları listelenir.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Nasıl Yapılır: Modüller Penceresini Kullanma](../../debugger/how-to-use-the-modules-window.md)
