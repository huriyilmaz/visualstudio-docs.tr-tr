---
title: Başlat Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 946c4e39b48d15352ef5fa8ae240fb3fe9da5b9b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645232"
---
# <a name="start-command"></a>Başlat Komutu
Başlangıç projesinde hata ayıklamaya başlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Arguments
`address`

İsteğe bağlı. Kaynak kodundaki bir kesme noktasına benzer şekilde programın yürütmeyi askıya aldığı adres. Bu bağımsız değişken yalnızca hata ayıklama modunda geçerlidir.

## <a name="remarks"></a>Açıklamalar
Çalıştırıldığında **Başlat** komutu, belirtilen adrese bir RunToCursor işlemi gerçekleştirir.

## <a name="example"></a>Örnek
Bu örnek, hata ayıklayıcıyı başlatır ve oluşan tüm özel durumları yoksayar.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)