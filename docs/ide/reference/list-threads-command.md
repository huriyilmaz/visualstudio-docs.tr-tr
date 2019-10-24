---
title: İş Parçacıklarını Listele Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c89f4e38d21e7dd66f53b8e768019a3e53c7a39
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747884"
---
# <a name="list-threads-command"></a>İş Parçacıklarını Listele Komutu
Geçerli programdaki iş parçacıklarının listesini görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Arguments
`index`

İsteğe bağlı. Geçerli iş parçacığı olarak dizini tarafından bir iş parçacığı seçer.

## <a name="remarks"></a>Açıklamalar
Belirtildiğinde `index` bağımsız değişkeni, belirtilen iş parçacığını geçerli iş parçacığı olarak işaretler. Geçerli iş parçacığının yanındaki listede bir yıldız işareti (*) görüntülenir.

## <a name="example"></a>Örnek

```
>Debug.ListThreads
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı Yığınını Listele Komutu](../../ide/reference/list-call-stack-command.md)
- [Ayrıştırılmış Kodu Listele Komutu](../../ide/reference/list-disassembly-command.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)