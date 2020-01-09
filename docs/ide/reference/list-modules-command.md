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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595507"
---
# <a name="list-modules-command"></a>Modülleri Listele Komutu
Geçerli işlem için modülleri listeler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametreler
/Address:`yes|no`

İsteğe bağlı. Modüllerin bellek adreslerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes`.

/Name:`yes|no`

İsteğe bağlı. Modüllerin adlarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes`.

/Order:`yes|no`

İsteğe bağlı. Modüllerin sırasının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

/Path:`yes|no`

İsteğe bağlı. Modüllerin yollarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes`.

/Process:`yes|no`

İsteğe bağlı. Modül işlemlerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

/SymbolFile:`yes|no`

İsteğe bağlı. Modüllerin sembol dosyalarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

/SymbolStatus:`yes|no`

İsteğe bağlı. Modüllerin sembol durumlarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes`.

/Timestamp:`yes|no`

İsteğe bağlı. Modüllerin zaman damgalarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

/Version:`yes|no`

İsteğe bağlı. Modüllerin sürümlerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

## <a name="example"></a>Örnek
Bu örnekte, geçerli işlem için modül adları, adresler ve zaman damgaları listelenmektedir.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Nasıl Yapılır: Modüller Penceresini Kullanma](../../debugger/how-to-use-the-modules-window.md)
