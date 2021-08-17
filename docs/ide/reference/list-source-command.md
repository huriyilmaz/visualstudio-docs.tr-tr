---
title: Kaynağı Listele Komutu
description: Kaynağı Listele komutunu ve kaynak kodun belirtilen satırlarını nasıl görüntüley olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 467abd21c80036b1b16edbb1b64ee818ca726e5e3218eb77d002408c49843e1c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121387427"
---
# <a name="list-source-command"></a>Kaynağı Listele Komutu
Kaynak kodun belirtilen satırlarını görüntüler.

## <a name="syntax"></a>Syntax

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
/Count:`number`

İsteğe bağlı. Görüntü eklenecek satır sayısını belirtir.

/Current

İsteğe bağlı. Geçerli satırı gösterir.

/File:`filename`

İsteğe bağlı. Gösterilen dosyanın yolu. Dosya adı belirtilmezse, komut geçerli deyimin satırı için kaynak kodu gösterir.

/Line:`number`

İsteğe bağlı. Belirli bir satır numarasını gösterir.

/ShowLineNumbers:`yes|no`

İsteğe bağlı. Satır numaralarının görüntü olup olmadığını belirtir.

## <a name="example"></a>Örnek
Bu örnekte Form1.vb dosyasının 4. satırına gelen kaynak kodu, satır numaraları görünür olarak listelemektedir.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)