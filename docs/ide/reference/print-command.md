---
title: Print
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.print
helpviewer_keywords:
- Debug.Print command
- Print method
- Print command
ms.assetid: 0412d381-590a-483f-bab4-6e1cca095645
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3056570e52893f1c21eaf10c7856b21fbbc02c61
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567846"
---
# <a name="print-command"></a>Yazdır komutu

Bir ifadeyi değerlendirir veya belirtilen metni görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Bağımsız Değişkenler

`text`

Gereklidir. Değerlendirilecek ifade veya görüntülenecek metin.

## <a name="remarks"></a>Açıklamalar

Bu komut için diğer ad olarak soru işaretini (?) kullanabilirsiniz. Yani, örneğin, komut

```cmd
>Debug.Print expA
```

olarak da yazılabilir

```cmd
? expA
```

Bu komutun her iki sürümü de `expA`ifadenin geçerli değerini döndürün.

## <a name="example"></a>Örnek

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Ayrıca bkz.

- [Deyimi Değerlendir Komutu](../../ide/reference/evaluate-statement-command.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
