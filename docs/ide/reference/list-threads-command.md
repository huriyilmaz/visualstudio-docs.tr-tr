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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1b36b8f4d9970d94eb83c47b59e85d01f932589
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595494"
---
# <a name="list-threads-command"></a>İş Parçacıklarını Listele Komutu
Geçerli programdaki iş parçacıklarının listesini görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Bağımsız Değişkenler
`index`

İsteğe bağlı. Geçerli iş parçacığı olmak için dizin tarafından bir iş parçacığı seçer.

## <a name="remarks"></a>Açıklamalar
Belirtildiğinde, `index` bağımsız değişken belirtilen iş parçacığı geçerli iş parçacığı olarak işaretler. Geçerli iş parçacığının yanındaki listede yıldız işareti (*) görüntülenir.

## <a name="example"></a>Örnek

```
>Debug.ListThreads
```

## <a name="see-also"></a>Ayrıca bkz.

- [Liste Çağrı Yığını Komutu](../../ide/reference/list-call-stack-command.md)
- [Ayrıştırılmış Kodu Listele Komutu](../../ide/reference/list-disassembly-command.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
