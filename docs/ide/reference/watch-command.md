---
title: İzle Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d7c89761dfc12d342747567389e39daeed4a227
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585658"
---
# <a name="watch-command"></a>İzle Komutu
**İzleme** penceresinin belirli bir örneğini oluşturur ve açar. Bu değerleri yeniden yapmak ve sonuçları kaydetmek için değişkenlerin, ifadelerin ve kayıtların değerlerini hesaplamak için **Bir İzleme** penceresi kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Bağımsız Değişkenler

`index`\
Gereklidir. Saat penceresinin örnek numarası.

## <a name="remarks"></a>Açıklamalar

Bir `index` sonda olmalı. Geçerli değerler 1, 2, 3 veya 4'tür.

## <a name="example"></a>Örnek

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatikler ve Yereller Pencereleri](../../debugger/autos-and-locals-windows.md)
- [Visual Studio'da Watch ve QuickWatch Windows'u kullanarak Değişkenlere Göz Kırtın](../../debugger/watch-and-quickwatch-windows.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
