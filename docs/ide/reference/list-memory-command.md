---
title: Belleği Listele Komutu
description: Belleği Listele komutu ve belirtilen bellek aralığının içeriğini görüntüleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4fb0d62f6f4ade51fe0224917a1e3ec3a199de14
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852056"
---
# <a name="list-memory-command"></a>Belleği Listele Komutu
Belirtilen bellek aralığının içeriğini görüntüler.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Bağımsız değişkenler
`expression`

İsteğe bağlı. Belleği görüntülemeye başlamak için gereken bellek adresi.

## <a name="switches"></a>Anahtarlar
/ANSI&#124;Unicode

İsteğe bağlı. Belleği, ANSI veya Unicode bellek baytlarına karşılık gelen karakterler olarak görüntüler.

Biriktirme`number`

İsteğe bağlı. ' Den başlayarak, kaç baytlık bellek gösterileceğini belirler `expression` .

Formatını`formattype`

İsteğe bağlı. **Bellek penceresinde bellek** bilgilerini görüntülemek için biçim türü; OneByte, TwoBytes, on bayt, sekizinci TBytes, float (32-bit) veya Double (64-bit) olabilir. Eğer OneByte kullanılıyorsa `/Unicode` kullanılamaz.

/Hex&#124;Imzalı&#124;Işaretsiz

İsteğe bağlı. Sayıları görüntüleme biçimini belirtir: imzalı, işaretsiz veya onaltılı olarak.

## <a name="remarks"></a>Açıklamalar
Tüm anahtarlarla birlikte bir **hata ayıklama. ListMemory** komutu yazmak yerine, belirtilen değerlere bazı anahtarlar önceden ayarlanmış şekilde, önceden tanımlanmış diğer adlar kullanılarak komutu çağırabilirsiniz. Örneğin, şunu girmek yerine:

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

şunu yazabilirsiniz:

```cmd
>df /Count:30 /Unicode
```

**Debug. ListMemory** komutu için kullanılabilir diğer adların listesi aşağıdadır:

|Diğer ad|Komut ve anahtarlar|
|-----------| - |
|**d**|Debug. ListMemory|
|**kapattığımda**|Debug. ListMemory/ANSI|
|**veritabanı**|Debug. ListMemory/Format: OneByte|
|**'ye**|Debug. ListMemory/Format: on bayt/ANSI|
|**dd**|Debug. ListMemory/Format: on bayt|
|**df**|Debug. ListMemory/Format: float|
|**DQ**|Debug. ListMemory/Format: sekizinci TBytes|
|**du**|Debug. ListMemory/UNICODE|

## <a name="example"></a>Örnek

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı yığınını Listele komutu](../../ide/reference/list-call-stack-command.md)
- [Iş parçacıklarını Listele komutu](../../ide/reference/list-threads-command.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
- [Komut penceresi](../../ide/reference/command-window.md)
- [Bul/komut kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
