---
title: Ayrıştırılmış Kodu Listele Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaeab2e65088b8f1bfce3a6a12f8cd66c3245b75
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747931"
---
# <a name="list-disassembly-command"></a>Ayrıştırılmış Kodu Listele Komutu
Hata ayıklama işlemini başlatir ve hataların nasıl işleneceğini belirtmenize olanak tanır.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListDisassembly [/count:number] [/endaddress:expression]
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]
[/linenumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
Her anahtar tam formu veya kısa bir form kullanılarak çağrılabilir.

/count: `number` [veya] /c: `number` [veya] `number` /length: [veya] /l:`number`

İsteğe bağlı. Görüntülenecek yönerge sayısı. Varsayılan değer 8'dir.

/endaddress: `expression` [veya] /e:`expression`

İsteğe bağlı. Sökmeyi durduracak adres.

/codebaytlar:`yes` `no`&#124;[veya] /bayt:`yes`&#124;`no` [veya] /b:`yes`&#124;`no`

İsteğe bağlı. Kod baytlarının gösterip görüntülemeyeceğini gösterir. Varsayılan değer. `no`

/kaynak:`yes` `no`&#124;[veya]`yes` /s:&#124;`no`

İsteğe bağlı. Kaynak kodunun görüntülenip görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer. `no`

/sembolnames:`yes` `no`&#124;[veya]`yes` /adlar:&#124;`no` `yes` [veya] /n:&#124;`no`

İsteğe bağlı. Sembol adlarının gösterip görüntülemeyeceğini gösterir. Varsayılan değer. `yes`

 [/satır`yes` numaraları: `no`&#124;]

İsteğe bağlı. Kaynak koduyla ilişkili satır numaralarının görüntülenmesini sağlar. /kaynak anahtarının /linenumbers `yes` anahtarını kullanma değeri olmalıdır.

## <a name="example"></a>Örnek

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Ayrıca bkz.

- [Liste Çağrı Yığını Komutu](../../ide/reference/list-call-stack-command.md)
- [Liste Konuları Komutu](../../ide/reference/list-threads-command.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)