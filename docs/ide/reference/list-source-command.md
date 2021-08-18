---
title: Kaynağı Listele Komutu
description: Kaynağı Listele komutunu ve kaynak kodun belirtilen satırlarını nasıl görüntüle olduğunu öğrenin.
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
ms.openlocfilehash: 03f62140322bca8efb3a3f8ba006293ab52ce665
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143761"
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