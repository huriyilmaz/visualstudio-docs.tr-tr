---
title: Belleği Listele Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listmemory
helpviewer_keywords:
- Debug.ListMemory command
- ListMemory command
- list memory command
ms.assetid: a84de361-a6a6-4f6d-96aa-a0d4a424371e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7bb92f3ac3420f146fdcd39b5925f7b3a517959a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748709"
---
# <a name="list-memory-command"></a>Belleği Listele Komutu
Belirtilen bellek aralığının içeriğini görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListMemory [/ANSI|Unicode] [/Count:number] [/Format:formattype]
[/Hex|Signed|Unsigned] [expression]
```

## <a name="arguments"></a>Arguments
`expression`

İsteğe bağlı. Belleği görüntülemeye başlamak için gereken bellek adresi.

## <a name="switches"></a>Anahtarlar
/ANSI&#124;Unicode

İsteğe bağlı. Belleği, ANSI veya Unicode bellek baytlarına karşılık gelen karakterler olarak görüntüler.

/Count: `number`

İsteğe bağlı. @No__t_0 başlayarak, kaç baytlık bellek gösterileceğini belirler.

/Format: `formattype`

İsteğe bağlı. **Bellek penceresinde bellek** bilgilerini görüntülemek için biçim türü; OneByte, TwoBytes, on bayt, sekizinci TBytes, float (32-bit) veya Double (64-bit) olabilir. OneByte kullanılıyorsa `/Unicode` kullanılamaz.

/Hex&#124;imzalı&#124;işaretsiz

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

|Alias|Komut ve anahtarlar|
|-----------| - |
|**TID**|Debug. ListMemory|
|**kapattığımda**|Debug. ListMemory/ANSI|
|**veritabanı**|Debug. ListMemory/Format: OneByte|
|**'ye**|Debug. ListMemory/Format: on bayt/ANSI|
|**gg**|Debug. ListMemory/Format: on bayt|
|**df**|Debug. ListMemory/Format: float|
|**DQ**|Debug. ListMemory/Format: sekizinci TBytes|
|**du**|Debug. ListMemory/UNICODE|

## <a name="example"></a>Örnek

```cmd
>Debug.ListMemory /Format:float /Count:30 /Unicode
```

## <a name="see-also"></a>Ayrıca bkz.

- [Çağrı Yığınını Listele Komutu](../../ide/reference/list-call-stack-command.md)
- [İş Parçacıklarını Listele Komutu](../../ide/reference/list-threads-command.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)