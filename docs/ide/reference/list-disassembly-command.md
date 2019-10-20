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
ms.openlocfilehash: e2e9177ee7048f626c61fee087468f991e4ed548
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610728"
---
# <a name="list-disassembly-command"></a>Ayrıştırılmış Kodu Listele Komutu
Hata ayıklama işlemini başlatır ve hataların nasıl işleneceğini belirtmenizi sağlar.

## <a name="syntax"></a>Sözdizimi

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

/codebytes: `yes`&#124; `no` [veya]/bytes: `yes`&#124; `no` [veya]/b: `yes`&#124; `no`

İsteğe bağlı. Kod baytlarının görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `no`.

/Source: `yes`&#124; `no` [veya]/s: `yes`&#124; `no`

İsteğe bağlı. Kaynak kodun görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `no`.

/symbolnames: `yes`&#124; `no` [veya]/names: `yes`&#124; `no` [veya]/n: `yes`&#124; `no`

İsteğe bağlı. Sembol adlarının görüntülenip görüntülenmeyeceğini gösterir. Varsayılan değer `yes`.

 [/linenumbers: `yes`&#124; `no`]

İsteğe bağlı. Kaynak kodla ilişkili satır numaralarının görüntülenmesine izin vermez. /Linenumbers anahtarını kullanmak için/Source anahtarı `yes` bir değere sahip olmalıdır.

## <a name="example"></a>Örnek

```cmd
>Debug.ListDisassembly
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Çağrı Yığınını Listele Komutu](../../ide/reference/list-call-stack-command.md)
- [İş Parçacıklarını Listele Komutu](../../ide/reference/list-threads-command.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)