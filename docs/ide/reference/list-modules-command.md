---
title: Modülleri Listele Komutu
description: Modülleri Listele komutunu ve geçerli işlem için modülleri nasıl listeley olduğunu öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 90a76b448fa4670e87baee821102734391f120415a29ec66f1d021aeb70f0f78
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429192"
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

İsteğe bağlı. Modüllerin bellek adreslerinin göster olup olmadığını belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

/Name:`yes|no`

İsteğe bağlı. Modüllerin adlarının göster olup olmadığını belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

/Order:`yes|no`

İsteğe bağlı. Modüllerin sırası gösterip göstermey kararlarını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/Path:`yes|no`

İsteğe bağlı. Modüllerin yollarının göster olup olmadığını belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

/Process:`yes|no`

İsteğe bağlı. Modüllerin işlemlerinin göster olup olmadığını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/SymbolFile:`yes|no`

İsteğe bağlı. Modüllerin sembol dosyalarının göster olup olmadığını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/SymbolStatus:`yes|no`

İsteğe bağlı. Modüllerin sembol durumlarının göster olup olmadığını belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

/Timestamp:`yes|no`

İsteğe bağlı. Modüllerin zaman damgasının gösterilip gösteril olmadığını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/Version:`yes|no`

İsteğe bağlı. Modüllerin sürümlerinin göster olup olmadığını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

## <a name="example"></a>Örnek
Bu örnekte geçerli işlem için modül adları, adresler ve zaman damgası listelendi.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Nasıl Yapılır: Modüller Penceresini Kullanma](../../debugger/how-to-use-the-modules-window.md)
