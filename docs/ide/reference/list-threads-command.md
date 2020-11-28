---
title: İş Parçacıklarını Listele Komutu
description: Iş parçacıklarını Listele komutu ve geçerli programdaki iş parçacıklarının bir listesini görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf7b3ed8b28a43c31efe68c6512f08883cb4187a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305263"
---
# <a name="list-threads-command"></a>İş Parçacıklarını Listele Komutu
Geçerli programdaki iş parçacıklarının listesini görüntüler.

## <a name="syntax"></a>Söz dizimi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Bağımsız değişkenler
`index`

İsteğe bağlı. Geçerli iş parçacığı olarak dizini tarafından bir iş parçacığı seçer.

## <a name="remarks"></a>Açıklamalar
Belirtildiğinde `index` bağımsız değişken belirtilen iş parçacığını geçerli iş parçacığı olarak işaretler. Geçerli iş parçacığının yanındaki listede bir yıldız işareti (*) görüntülenir.

## <a name="example"></a>Örnek

```
>Debug.ListThreads
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı yığınını Listele komutu](../../ide/reference/list-call-stack-command.md)
- [Ayrıştırılmış kodu Listele komutu](../../ide/reference/list-disassembly-command.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
