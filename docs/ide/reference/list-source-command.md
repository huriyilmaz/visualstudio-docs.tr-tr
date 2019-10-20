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
ms.openlocfilehash: 3123479d819662905020c27060e1234bd01c9077
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610510"
---
# <a name="list-source-command"></a>Kaynağı Listele Komutu
Belirtilen kaynak kodu satırlarını görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
/Count: `number`

İsteğe bağlı. Görüntülenecek satır sayısını belirtir.

/Current

İsteğe bağlı. Geçerli satırı gösterir.

/File: `filename`

İsteğe bağlı. Gösterilecek dosyanın yolu. Dosya adı belirtilmemişse, komut geçerli deyimin satırı için kaynak kodunu gösterir.

/Line: `number`

İsteğe bağlı. Belirli bir satır numarasını gösterir.

/ShowLineNumbers: `yes|no`

İsteğe bağlı. Satır numaralarının görüntülenip görüntülenmeyeceğini belirtir.

## <a name="example"></a>Örnek
Bu örnek, satır numaraları görünür olan Form1. vb dosyasının 4. satırından kaynak kodu listeler.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)