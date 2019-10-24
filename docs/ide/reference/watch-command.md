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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 411452ba0cf8f8625ee67bca51c2f3735f6dc924
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747689"
---
# <a name="watch-command"></a>İzle Komutu
Bir **Gözcü** penceresinin belirtilen bir örneğini oluşturur ve açar. Değişkenler, ifadeler ve yazmaçların değerlerini hesaplamak, bu değerleri düzenlemek ve sonuçları kaydetmek için bir **Gözcü** penceresi kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.Watch[index]
```

## <a name="arguments"></a>Arguments

`index`\
Gerekli. İzleme penceresinin örnek numarası.

## <a name="remarks"></a>Açıklamalar

@No__t_0 bir tamsayı olmalıdır. Geçerli değerler 1, 2, 3 veya 4 ' dir.

## <a name="example"></a>Örnek

```cmd
>Debug.Watch1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatikler ve Yereller Pencereleri](../../debugger/autos-and-locals-windows.md)
- [Visual Studio 'da gözcü ve hızlı gözcü pencerelerini kullanarak değişkenlerde bir Izleme ayarlayın](../../debugger/watch-and-quickwatch-windows.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)