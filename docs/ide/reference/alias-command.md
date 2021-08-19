---
title: Diğer Ad Komutu
description: Tüm komut, komut ve bağımsız değişkenler ya da başka bir diğer ad için yeni bir diğer ad oluşturmak üzere Alias komutunu nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: f5c1b3f07a563484b70e36ed4257ee4dac005faf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101641"
---
# <a name="alias-command"></a>Diğer Ad Komutu
Tüm komut, komut ve bağımsız değişkenler ya da başka bir diğer ad için yeni bir diğer ad oluşturur.

> [!TIP]
> `>alias`Bağımsız değişken olmadan yazmak, diğer adların ve tanımlarının geçerli listesini görüntüler.

## <a name="syntax"></a>Söz dizimi

```cmd
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Bağımsız değişkenler
`aliasname`\
İsteğe bağlı. Yeni diğer ad için ad. İçin hiçbir değer sağlanmazsa `aliasname` , geçerli diğer adların ve tanımlarının bir listesi görüntülenir.

`aliasstring`\
İsteğe bağlı. Tüm komut adı veya var olan diğer ad ve diğer ad olarak oluşturmak istediğiniz parametreler. İçin değer sağlanmazsa `aliasstring` , belirtilen diğer ad için diğer ad ve diğer ad dizesi görüntülenir.

## <a name="switches"></a>Anahtarlar
/DELETE veya/del&lt ya da/d\
İsteğe bağlı. Belirtilen diğer adı siler ve otomatik tamamlamayı kaldırır.

/Reset süpürmeden
İsteğe bağlı. Önceden tanımlanmış diğer adların listesini orijinal ayarlarına sıfırlar. Diğer bir deyişle, önceden tanımlanmış tüm diğer adları geri yükler ve Kullanıcı tanımlı tüm diğer adları kaldırır.

## <a name="remarks"></a>Açıklamalar
Diğer adlar komutları temsil ettiğinden, bunlar komut satırının başlangıcında bulunmalıdır.

Bu komutu verirken, diğer adlarla değil, anahtardan hemen sonra gelen anahtarları eklemeniz gerekir, aksi takdirde anahtar, diğer ad dizesinin bir parçası olarak dahil edilir.

Bu `/reset` anahtar, diğer adlar geri yüklenmeden önce onay ister. İçin kısa bir biçim yoktur `/reset` .

## <a name="examples"></a>Örnekler
Bu örnek, `upper` tüm komut Edit. Makebüyük komutu için yeni bir diğer ad oluşturur.

```cmd
>Tools.Alias upper Edit.MakeUpperCase
```

Bu örnek, diğer adı siler, `upper` .

```cmd
>Tools.alias /delete upper
```

Bu örnek, tüm geçerli diğer adlar ve tanımlar listesini görüntüler.

```cmd
>Tools.Alias
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
