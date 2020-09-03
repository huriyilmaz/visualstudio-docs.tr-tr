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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585658"
---
# <a name="watch-command"></a>İzle Komutu
Bir **Gözcü** penceresinin belirtilen bir örneğini oluşturur ve açar. Değişkenler, ifadeler ve yazmaçların değerlerini hesaplamak, bu değerleri düzenlemek ve sonuçları kaydetmek için bir **Gözcü** penceresi kullanabilirsiniz.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Bağımsız değişkenler

`index`\
Gereklidir. İzleme penceresinin örnek numarası.

## <a name="remarks"></a>Açıklamalar

`index`Bir tamsayı olmalıdır. Geçerli değerler 1, 2, 3 veya 4 ' dir.

## <a name="example"></a>Örnek

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatikler ve Yereller Pencereleri](../../debugger/autos-and-locals-windows.md)
- [Visual Studio 'da gözcü ve hızlı gözcü pencerelerini kullanarak değişkenlerde bir Izleme ayarlayın](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
