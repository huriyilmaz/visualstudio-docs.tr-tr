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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8fdcc816510642c7800b6fbeacfa3fcdeff5e0b3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748793"
---
# <a name="alias-command"></a>Diğer Ad Komutu
Tüm komut, komut ve bağımsız değişkenler ya da başka bir diğer ad için yeni bir diğer ad oluşturur.

> [!TIP]
> Bağımsız değişken olmadan `>alias` yazmak, diğer adların ve bunların tanımlarının geçerli listesini görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Arguments
`aliasname`\
İsteğe bağlı. Yeni diğer ad için ad. @No__t_0 için hiçbir değer sağlanmazsa, geçerli diğer adların ve tanımlarının bir listesi görüntülenir.

`aliasstring`\
İsteğe bağlı. Tüm komut adı veya var olan diğer ad ve diğer ad olarak oluşturmak istediğiniz parametreler. @No__t_0 için bir değer sağlanmadığında, belirtilen diğer ad için diğer ad ve diğer ad dizesi görüntülenir.

## <a name="switches"></a>Anahtarlar
/DELETE veya/del&lt ya da/d\
İsteğe bağlı. Belirtilen diğer adı siler ve otomatik tamamlamayı kaldırır.

/Reset süpürmeden
İsteğe bağlı. Önceden tanımlanmış diğer adların listesini orijinal ayarlarına sıfırlar. Diğer bir deyişle, önceden tanımlanmış tüm diğer adları geri yükler ve Kullanıcı tanımlı tüm diğer adları kaldırır.

## <a name="remarks"></a>Açıklamalar
Diğer adlar komutları temsil ettiğinden, bunlar komut satırının başlangıcında bulunmalıdır.

Bu komutu verirken, diğer adlarla değil, anahtardan hemen sonra gelen anahtarları eklemeniz gerekir, aksi takdirde anahtar, diğer ad dizesinin bir parçası olarak dahil edilir.

@No__t_0 anahtarı, diğer adlar geri yüklenmeden önce onay ister. @No__t_0 kısa bir biçimi yoktur.

## <a name="examples"></a>Örnekler
Bu örnek, `upper` için yeni bir diğer ad oluşturur. Makebüyük komutu.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Bu örnek, `upper` diğer adı siler.

```cmd
>Tools.alias /delete upper
```

Bu örnek, tüm geçerli diğer adlar ve tanımlar listesini görüntüler.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)