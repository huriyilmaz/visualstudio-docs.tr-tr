---
title: Kaynağı Listele Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c211773f20ab4643b62c8c71fc6ae6581a91987
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72747899"
---
# <a name="list-source-command"></a>Kaynağı Listele Komutu
Kaynak kodunun belirtilen satırlarını görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
/Sayım:`number`

İsteğe bağlı. Görüntülenecek satır sayısını belirtir.

/Akım

İsteğe bağlı. Geçerli satırı gösterir.

/Dosya:`filename`

İsteğe bağlı. Dosyanın gösteriş yolu. Dosya adı belirtilmemişse, komut geçerli deyimsatırının kaynak kodunu gösterir.

/Satır:`number`

İsteğe bağlı. Belirli bir satır numarasını gösterir.

/ShowLineNumbers:`yes|no`

İsteğe bağlı. Satır numaralarının görüntülenip görüntülenip görüntülenmeyeceğini belirtir.

## <a name="example"></a>Örnek
Bu örnek, form1.vb dosyasının 4 satırındaki kaynak kodunu listeler ve satır numaraları görünür.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Ayrıca bkz.

- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)