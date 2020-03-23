---
title: Diğer Ad Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 031f1a4bab1acee3f3d0999b17c0b607f7808df9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596911"
---
# <a name="alias-command"></a>Diğer Ad Komutu
Tam bir komut, tam komut ve bağımsız değişkenler veya başka bir takma ad için yeni bir takma ad oluşturur.

> [!TIP]
> Bağımsız `>alias` değişkenolmadan yazma, geçerli takma ad listesini ve tanımlarını görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`aliasname`\
İsteğe bağlı. Yeni takma adın adı. Hiçbir `aliasname`değer için sağlanmışsa, geçerli diğer adların ve tanımlarının listesi görüntülenir.

`aliasstring`\
İsteğe bağlı. Tam komut adı veya varolan diğer ad ve diğer ad olarak oluşturmak istediğiniz parametreler. Belirtilen diğer ad görüntüler `aliasstring`için diğer ad adı ve diğer ad dizesi için hiçbir değer sağlanmışsa.

## <a name="switches"></a>Anahtarlar
/silme veya /del veya /d\
İsteğe bağlı. Belirtilen diğer adı siler ve otomatik tamamlamadan kaldırır.

/sıfırlama\
İsteğe bağlı. Önceden tanımlanmış diğer adların listesini özgün ayarlarına sıfırlar. Diğer bir arada, önceden tanımlanmış tüm diğer adları geri yükler ve kullanıcı tanımlı tüm diğer adları kaldırır.

## <a name="remarks"></a>Açıklamalar
Takma adlar komutları temsil ettiğiiçin, komut satırının başında yer almalıdır.

Bu komutu verirken, diğer adlardan sonra değil, komuttan hemen sonra anahtarları eklemeniz gerekir, aksi takdirde anahtarın kendisi diğer ad dizesinin bir parçası olarak eklenecektir.

Anahtar, `/reset` takma adlar geri yüklenmeden önce onay ister. Hiçbir kısa formu `/reset`.

## <a name="examples"></a>Örnekler
Bu örnek, `upper`tam komut Edit.MakeUpperCase için yeni bir takma ad oluşturur.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Bu örnek, `upper`diğer adı siler.

```cmd
>Tools.alias /delete upper
```

Bu örnek, geçerli tüm diğer adların ve tanımların bir listesini görüntüler.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
