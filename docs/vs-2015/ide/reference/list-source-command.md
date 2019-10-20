---
title: Kaynağı Listele komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f13689b6e3ac4db2d58c1def3a5d0dd05c219f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672327"
---
# <a name="list-source-command"></a>Kaynağı Listele Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen kaynak kodu satırlarını görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListSource [/Count:number] [/Current] [/File:filename]
[/Line:number] [/ShowLineNumbers:yes|no]
```

## <a name="switches"></a>Anahtarlar
 /Count: Isteğe bağlı `number`. Görüntülenecek satır sayısını belirtir.

 /Current Isteğe bağlı. Geçerli satırı gösterir.

 /File: Isteğe bağlı `filename`. Gösterilecek dosyanın yolu. Dosya adı belirtilmemişse, komut geçerli deyimin satırı için kaynak kodunu gösterir.

 /Line: Isteğe bağlı `number`. Belirli bir satır numarasını gösterir.

 /ShowLineNumbers: Isteğe bağlı `yes|no`. Satır numaralarının görüntülenip görüntülenmeyeceğini belirtir.

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Bu örnek, satır numaraları görünür olan Form1. vb dosyasının 4. satırından kaynak kodu listeler.

```
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md)
