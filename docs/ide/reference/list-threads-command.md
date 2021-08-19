---
title: İş Parçacıklarını Listele Komutu
description: İş Parçacıklarını Listele komutunu ve geçerli programda iş parçacıklarının listesini nasıl görüntüle olduğunu öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 2585399f9e63286eb6c846054eb30e80fad8fe20
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151450"
---
# <a name="list-threads-command"></a>İş Parçacıklarını Listele Komutu
Geçerli programda iş parçacıklarının listesini görüntüler.

## <a name="syntax"></a>Söz dizimi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Bağımsız değişkenler
`index`

İsteğe bağlı. Geçerli iş parçacığı olmak için dizinine göre bir iş parçacığı seçer.

## <a name="remarks"></a>Açıklamalar
Belirtilen bağımsız `index` değişken, belirtilen iş parçacığını geçerli iş parçacığı olarak işaretler. Geçerli iş parçacığının yanındaki listede bir yıldız işareti (*) görüntülenir.

## <a name="example"></a>Örnek

```
>Debug.ListThreads
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı Yığınını Listele Komutu](../../ide/reference/list-call-stack-command.md)
- [Disassembly Komutunu Listele](../../ide/reference/list-disassembly-command.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
