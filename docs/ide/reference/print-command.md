---
title: Hata Ayıkla. Yazdır
description: Print komutu ve bir ifadeyi değerlendirme veya belirtilen metni görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 02cc2625c4c9bc04ccbfb5f6a5ab6854453be99b43edd341bb6f2a5750cd0249
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121271816"
---
# <a name="print-command"></a>Yazdır komutu

Bir ifadeyi değerlendirir veya belirtilen metni görüntüler.

## <a name="syntax"></a>Söz dizimi

```cmd
>Debug.Print text
```

## <a name="arguments"></a>Bağımsız değişkenler

`text`

Gereklidir. Değerlendirilecek ifade veya görüntülenecek metin.

## <a name="remarks"></a>Açıklamalar

Bu komut için bir diğer ad olarak soru işareti (?) kullanabilirsiniz. Bu nedenle, örneğin, komut

```cmd
>Debug.Print expA
```

Ayrıca, şöyle yazılabilir

```cmd
? expA
```

Bu komutun her iki sürümü de ifadenin geçerli değerini döndürür `expA` .

## <a name="example"></a>Örnek

```cmd
>Debug.Print DateTime.Now.Day
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ifadeyi değerlendir komutu](../../ide/reference/evaluate-statement-command.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
