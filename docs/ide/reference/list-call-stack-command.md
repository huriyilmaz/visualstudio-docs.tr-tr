---
title: Çağrı Yığınını Listele Komutu
description: Çağrı Yığınını Listele komutunu ve geçerli çağrı yığınını nasıl görüntüle olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 7984cc74cf2116c72b9c9a35aa2cf0f272ec6cd3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628748"
---
# <a name="list-call-stack-command"></a>Çağrı Yığınını Listele Komutu
Geçerli çağrı yığınını görüntüler.

## <a name="syntax"></a>Söz dizimi

```cmd
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Bağımsız değişkenler

`index`\
İsteğe bağlı. Geçerli yığın çerçevesini ayarlar ve hiçbir çıkış görüntülemez.

## <a name="switches"></a>Anahtarlar
Her anahtar, tam formu veya kısa formu kullanılarak çağrılabilir.

/Count: `number` [or] /C:`number`

İsteğe bağlı. Görüntü için en fazla çağrı yığını sayısı. Varsayılan değer sınırsızdır.

/ShowTypes: `yes`&#124;`no` [veya] /T: `yes`&#124;`no`

İsteğe bağlı. Parametre türlerinin görüntü olup olmadığını belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

/ShowNames: `yes`&#124;`no` [veya] /N: `yes`&#124;`no`

İsteğe bağlı. Parametre adlarının görüntü olup olmadığını belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

/ShowValues: `yes`&#124;`no` [veya] /V: `yes`&#124;`no`

İsteğe bağlı. Parametre değerlerinin görüntü olup olmadığını belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

/ShowModule: `yes`&#124;`no` [veya] /M: `yes`&#124;`no`

İsteğe bağlı. Modül adının görüntü olup olmadığını belirtir. Varsayılan değer `yes` olarak belirlenmiştir.

/ShowLineOffset: `yes`&#124;`no` [veya] /#: `yes`&#124;`no`

İsteğe bağlı. Satır uzaklığının görüntü olup olmadığını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/ShowByteOffset: `yes`&#124;`no` [veya] /B: `yes`&#124;`no`

İsteğe bağlı. Byte uzaklığının görüntü olup olmadığını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/ShowLanguage: `yes`&#124;`no` [veya] /L: `yes`&#124;`no`

İsteğe bağlı. Dilin görüntü olup olmadığını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/IncludeCallsAcrossThreads: `yes`&#124;`no` [veya] /I: `yes`&#124;`no`

İsteğe bağlı. Diğer iş parçacıklarına veya diğer iş parçacıklarına yapılan çağrıların dahil olup olmadığını belirtir. Varsayılan değer `no` olarak belirlenmiştir.

/ShowExternalCode: `yes`&#124;`no`

İsteğe bağlı. Çağrı yığını için Yalnızca kendi kodum görüntü olup olmadığını belirtir. Bu Yalnızca kendi kodum kapalı olduğunda, kullanıcı olmayan tüm kod görüntülenir. Bu Yalnızca kendi kodum olduğunda, kullanıcı olmayan kod çağrı yığını `[external]` çıkışında olduğu gibi görüntülenir.

Iş parçacığı:`n`

İsteğe bağlı. İş parçacığı için çağrı yığınını `n` görüntüler. İş parçacığı belirtilmezse, geçerli iş parçacığı için çağrı yığınını görüntüler.

## <a name="remarks"></a>Açıklamalar
Bağımsız değişkenler veya anahtarlarda yapılan değişiklikler, bu komutun gelecekteki çağrılarında geçerlidir. Debug.ListCallStackby'nin kendisini görüntülerse çağrı yığınının tamamı görüntülenir. Bir dizin belirtirsiniz, örneğin,

```cmd
Debug.ListCallStack 2
```

ardından geçerli yığın çerçevesi bu çerçeveye (bu durumda ikinci çerçeve) ayarlanır.

Bu komutu önceden tanımlanmış diğer adı olan kb kullanarak da yazabilirsiniz. Örneğin,

```cmd
kb 2
```

geçerli yığın çerçevesini ikinci kareye ayarlamak için.

## <a name="example"></a>Örnek

```cmd
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Ayrıca bkz.

- [Disassembly Komutunu Listele](../../ide/reference/list-disassembly-command.md)
- [İş Parçacıklarını Listele Komutu](../../ide/reference/list-threads-command.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Bul/Komut Kutusu](../../ide/find-command-box.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)