---
title: Çağrı Yığınını Listele Komutu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f62852550c161566832a7ab78d4058d1d14028f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "72748718"
---
# <a name="list-call-stack-command"></a>Çağrı Yığınını Listele Komutu
Geçerli çağrı yığınını görüntüler.

## <a name="syntax"></a>Sözdizimi

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Bağımsız Değişkenler

`index`\
İsteğe bağlı. Geçerli yığın çerçevesini ayarlar ve çıktı görüntülemez.

## <a name="switches"></a>Anahtarlar
Her anahtar tam formu veya kısa bir form kullanılarak çağrılabilir.

/Sayı:`number` [veya] /C:`number`

İsteğe bağlı. Görüntülenecek maksimum çağrı yığını sayısı. Varsayılan değer sınırsızdır.

/ShowTypes:`yes` `no`&#124;[veya]`yes` /T:&#124;`no`

İsteğe bağlı. Parametre türlerinin görüntülenip görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer. `yes`

/ShowNames:`yes` `no`&#124;[veya]`yes` /N:&#124;`no`

İsteğe bağlı. Parametre adlarının görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer. `yes`

/ShowValues:`yes` `no`&#124;[veya]`yes` /V:&#124;`no`

İsteğe bağlı. Parametre değerlerinin gösterip gösterilemeyeceğini belirtir. Varsayılan değer. `yes`

/ShowModule:`yes` `no`&#124;[veya]`yes` /M:&#124;`no`

İsteğe bağlı. Modül adının görüntülenip görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer. `yes`

/ShowLineOffset:`yes` `no`&#124;[veya]`yes` /#:&#124;`no`

İsteğe bağlı. Hat ofsetinin görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer. `no`

/ShowByteOffset:`yes` `no`&#124;[veya]`yes` /B:&#124;`no`

İsteğe bağlı. Bayt mahsulünün gösterip göstermeyeceğini belirtir. Varsayılan değer. `no`

/ShowLanguage:`yes` `no`&#124;[veya]`yes` /L:&#124;`no`

İsteğe bağlı. Dili gösterip göstermeyeceğini belirtir. Varsayılan değer. `no`

/IncludeCallsAcrossThreads:`yes` `no`&#124;[veya]`yes` /I:&#124;`no`

İsteğe bağlı. Diğer iş parçacıklarına veya diğer iş parçacıklarından gelen çağrıların dahil edilip edilemeyeceğini belirtir. Varsayılan değer. `no`

/ShowExternalCode:`yes`&#124;`no`

İsteğe bağlı. Çağrı yığını için Yalnızca Kodum'un görüntülenip görüntülenip görüntülenmeyeceğini belirtir. Yalnızca Kodum kapalıyken, kullanıcı olmayan tüm kod görüntülenir. Yalnızca Kodum açıktı, kullanıcı olmayan kod `[external]` çağrı yığını çıkışında olduğu gibi görüntülenir.

Iş parçacığı:`n`

İsteğe bağlı. İş parçacığı `n`için çağrı yığınını görüntüler. İş parçacığı belirtilmemişse, geçerli iş parçacığı için çağrı yığını nı görüntüler.

## <a name="remarks"></a>Açıklamalar
Bağımsız değişkenlerde veya anahtarlarda yapılan değişiklikler, bu komutun gelecekteki çağrıları için geçerlidir. Debug.ListCallStackby kendisi sorunu varsa, tüm arama yığını görüntüler. Örneğin, bir dizin belirtirseniz,

```cmd
Debug.ListCallStack 2
```

sonra geçerli yığın çerçevesi bu çerçeveye ayarlanır (bu durumda, ikinci kare).

Ayrıca bu komutu önceden tanımlanmış takma adı olan kb'yi kullanarak da yazabilirsiniz. Örneğin,

```cmd
kb 2
```

geçerli yığın çerçevesini ikinci çerçeveye ayarlamak için.

## <a name="example"></a>Örnek

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ayrıştırılmış Kodu Listele Komutu](../../ide/reference/list-disassembly-command.md)
- [Liste Konuları Komutu](../../ide/reference/list-threads-command.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)