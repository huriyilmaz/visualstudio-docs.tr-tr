---
title: Komutu izle | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18e585064bb50db7a0497c6b96e428a662e953ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72604829"
---
# <a name="watch-command"></a>İzle Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir **Gözcü** penceresinin belirtilen bir örneğini oluşturur ve açar. Değişkenler, ifadeler ve yazmaçların değerlerini hesaplamak, bu değerleri düzenlemek ve sonuçları kaydetmek için bir **Gözcü** penceresi kullanabilirsiniz.

## <a name="syntax"></a>Söz dizimi

```
Debug.Watch[index]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `index` Gerekli. İzleme penceresinin örnek numarası.

## <a name="remarks"></a>Açıklamalar
 `index`Bir tamsayı olmalıdır. Geçerli değerler 1, 2, 3 veya 4 ' dir.

## <a name="example"></a>Örnek

```
>Debug.Watch1
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Oto ve Yereller Windows](../../debugger/autos-and-locals-windows.md) [nasıl yapılır: değişken penceresinde bir değeri düzenleme](https://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5) [nasıl yapılır: hızlı Izleme Iletişim kutusunu kullanma](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
