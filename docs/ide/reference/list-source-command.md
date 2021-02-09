---
title: Kaynağı Listele Komutu
description: Liste kaynağı komutu ve belirtilen kaynak kodu satırlarını görüntüleme hakkında bilgi edinin.
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
ms.workload:
- multiple
ms.openlocfilehash: 4efd5ab0ddd94b17fa6a683366707d635f844bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919435"
---
# <a name="list-source-command"></a>Kaynağı Listele Komutu
Belirtilen kaynak kodu satırlarını görüntüler.

## <a name="syntax"></a>Syntax

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
Biriktirme`number`

İsteğe bağlı. Görüntülenecek satır sayısını belirtir.

/Current

İsteğe bağlı. Geçerli satırı gösterir.

Dosyasýný`filename`

İsteğe bağlı. Gösterilecek dosyanın yolu. Dosya adı belirtilmemişse, komut geçerli deyimin satırı için kaynak kodunu gösterir.

Satırı`number`

İsteğe bağlı. Belirli bir satır numarasını gösterir.

ShowLineNumbers`yes|no`

İsteğe bağlı. Satır numaralarının görüntülenip görüntülenmeyeceğini belirtir.

## <a name="example"></a>Örnek
Bu örnek, satır numaraları görünür olan Form1. vb dosyasının 4. satırından kaynak kodu listeler.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)