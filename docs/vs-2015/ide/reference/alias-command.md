---
title: Diğer ad komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6da744b0db9e41cd1e5039a1bd0d5c93bc4c734a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651686"
---
# <a name="alias-command"></a>Diğer Ad Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tüm komut, komut ve bağımsız değişkenler ya da başka bir diğer ad için yeni bir diğer ad oluşturur.

> [!TIP]
> Bağımsız değişken olmadan `>alias` yazmak, diğer adların ve bunların tanımlarının geçerli listesini görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]
```

## <a name="arguments"></a>Arguments
 Isteğe bağlı `aliasname`. Yeni diğer ad için ad. @No__t_0 için hiçbir değer sağlanmazsa, geçerli diğer adların ve tanımlarının bir listesi görüntülenir.

 Isteğe bağlı `aliasstring`. Tüm komut adı veya var olan diğer ad ve diğer ad olarak oluşturmak istediğiniz parametreler. @No__t_0 için bir değer sağlanmadığında, belirtilen diğer ad için diğer ad ve diğer ad dizesi görüntülenir.

## <a name="switches"></a>Anahtarlar
 /DELETE veya/del&lt ya da/d Isteğe bağlı. Belirtilen diğer adı siler ve otomatik tamamlamayı kaldırır.

 /Reset süpürmeden isteğe bağlı. Önceden tanımlanmış diğer adların listesini orijinal ayarlarına sıfırlar. Diğer bir deyişle, önceden tanımlanmış tüm diğer adları geri yükler ve Kullanıcı tanımlı tüm diğer adları kaldırır.

## <a name="remarks"></a>Açıklamalar
 Diğer adlar komutları temsil ettiğinden, bunlar komut satırının başlangıcında bulunmalıdır.

 Bu komutu verirken, diğer adlarla değil, anahtardan hemen sonra gelen anahtarları eklemeniz gerekir, aksi takdirde anahtar, diğer ad dizesinin bir parçası olarak dahil edilir.

 @No__t_0 anahtarı, diğer adlar geri yüklenmeden önce onay ister. @No__t_0 kısa bir biçimi yoktur.

## <a name="examples"></a>Örnekler
 Bu örnek, `upper` için yeni bir diğer ad oluşturur. Makebüyük komutu.

```
>Tools.Alias upper Edit.MakeUpperCase
```

 Bu örnek, `upper` diğer adı siler.

```
>Tools.alias /delete upper
```

 Bu örnek, tüm geçerli diğer adlar ve tanımlar listesini görüntüler.

```
>Tools.Alias
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
