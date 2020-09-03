---
title: Bellek komutunu Listele | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2630402e03d1256f63e542818a9066745206d2c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672757"
---
# <a name="list-memory-command"></a>Belleği Listele Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen bellek aralığının içeriğini görüntüler.

## <a name="syntax"></a>Söz dizimi

```
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Bağımsız değişkenler
 `expression` Seçim. Belleği görüntülemeye başlamak için gereken bellek adresi.

## <a name="switches"></a>Anahtarlar
 /ANSI&#124;Unicode Isteğe bağlı. Belleği, ANSI veya Unicode bellek baytlarına karşılık gelen karakterler olarak görüntüler.

 /Count: `number` isteğe bağlı. ' Den başlayarak, kaç baytlık bellek gösterileceğini belirler `expression` .

 /Format: `formattype` isteğe bağlı. **Bellek penceresinde bellek** bilgilerini görüntülemek için biçim türü; OneByte, TwoBytes, on bayt, sekizinci TBytes, float (32-bit) veya Double (64-bit) olabilir. Eğer OneByte kullanılıyorsa `/Unicode` kullanılamaz.

 /Hex&#124;Imzalı&#124;Işaretsiz Isteğe bağlı. Sayıları görüntüleme biçimini belirtir: imzalı, işaretsiz veya onaltılı olarak.

## <a name="remarks"></a>Açıklamalar
 Tüm anahtarlarla birlikte bir **hata ayıklama. ListMemory** komutu yazmak yerine, belirtilen değerlere bazı anahtarlar önceden ayarlanmış şekilde, önceden tanımlanmış diğer adlar kullanılarak komutu çağırabilirsiniz. Örneğin, şunu girmek yerine:

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

 şunu yazabilirsiniz:

```
>df /Count:30 /Unicode
```

 **Debug. ListMemory** komutu için kullanılabilir diğer adların listesi aşağıdadır:

|Diğer ad|Komut ve anahtarlar|
|-----------|--------------------------|
|**TID**|Debug. ListMemory|
|**kapattığımda**|Debug. ListMemory/ANSI|
|**veritabanı**|Debug. ListMemory/Format: OneByte|
|**'ye**|Debug. ListMemory/Format: on bayt/ANSI|
|**gg**|Debug. ListMemory/Format: on bayt|
|**df**|Debug. ListMemory/Format: float|
|**DQ**|Debug. ListMemory/Format: sekizinci TBytes|
|**du**|Debug. ListMemory/UNICODE|

## <a name="example"></a>Örnek

```
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Çağrı yığınını Listele komut](../../ide/reference/list-call-stack-command.md) [listesi iş parçacıkları komutu](../../ide/reference/list-threads-command.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
