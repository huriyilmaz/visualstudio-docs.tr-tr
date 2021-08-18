---
title: Ayrıştırılmış Kodu Listele Komutu
description: Liste Ayrıştırma komutu ve hata ayıklama işlemine nasıl başladığı hakkında bilgi edinin ve hataların nasıl işleneceğini belirtmenize izin verir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f41021b3b0d8c4dd0d0d688573bdc2e5c37da8f6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143813"
---
# <a name="list-disassembly-command"></a>Ayrıştırılmış Kodu Listele Komutu
Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
Her anahtar, tamamı ya da kısa bir form kullanılarak çağrılabilir.

/Count: `number` [veya]/c: `number` [veya]/length: `number` [veya]/l: `number`

İsteğe bağlı. Görüntülenecek yönerge sayısı. Varsayılan değer 8 ' dir.

/endadddress: `expression` [veya]/e: `expression`

İsteğe bağlı. Ayrıştırılmış kodun durdurulacağı adres.

/codebytes: `yes`&#124;`no` [veya]/bytes: `yes`&#124;`no` [veya]/b: `yes`&#124;`no`

İsteğe bağlı. Kod baytlarının görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `no` olarak belirlenmiştir.

/Source: `yes`&#124;`no` [veya]/s: `yes`&#124;`no`

İsteğe bağlı. Kaynak kodun görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `no` olarak belirlenmiştir.

/symbolnames: `yes`&#124;`no` [veya]/names: `yes`&#124;`no` [veya]/n: `yes`&#124;`no`

İsteğe bağlı. Sembol adlarının görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `yes` olarak belirlenmiştir.

 [/linenumbers: `yes`&#124;`no` ]

İsteğe bağlı. Kaynak kodla ilişkili satır numaralarının görüntülenmesine izin vermez. /Linenumbers anahtarını kullanmak için/Source anahtarının bir değeri olmalıdır `yes` .

## <a name="example"></a>Örnek

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı yığınını Listele komutu](../../ide/reference/list-call-stack-command.md)
- [Iş parçacıklarını Listele komutu](../../ide/reference/list-threads-command.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)