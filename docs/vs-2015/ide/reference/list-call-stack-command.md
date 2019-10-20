---
title: Çağrı yığınını Listele komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listcallstack
helpviewer_keywords:
- list call stack command
- Debug.ListCallStack command
ms.assetid: a8b20bf2-81d2-4069-aea8-23e6b15b4347
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9c44ac18468fbd26adab2cf973a21df58ebb28c1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657654"
---
# <a name="list-call-stack-command"></a>Çağrı Yığınını Listele Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Geçerli çağrı yığınını görüntüler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListCallStack [/Count:number] [/ShowTypes:yes|no]
[/ShowNames:yes|no] [/ShowValues:yes|no] [/ShowModule:yes|no]
[/ShowLineOffset:yes|no] [/ShowByteOffset:yes|no]
[/ShowLanguage:yes|no] [/IncludeCallsAcrossThreads:yes|no]
[/ShowExternalCode:yes|no] [Thread:n] [index]
```

## <a name="arguments"></a>Arguments
 Isteğe bağlı `index`. Geçerli yığın çerçevesini ayarlar ve çıkış görüntülemez.

## <a name="switches"></a>Anahtarlar
 Her anahtar, tamamı ya da kısa bir form kullanılarak çağrılabilir.

 /Count: `number` [veya]/C: `number` Isteğe bağlı. Görüntülenecek en fazla çağrı yığını sayısı. Varsayılan değer sınırsızdır.

 /ShowTypes: `yes`&#124; `no` [veya]/t: `yes`&#124; `no` isteğe bağlı. Parametre türlerinin görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `yes`.

 /ShowNames: `yes`&#124; `no` [veya]/n: `yes`&#124; `no` isteğe bağlı. Parametre adlarının görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `yes`.

 /ShowValues: `yes`&#124; `no` [veya]/v: `yes`&#124; `no` isteğe bağlı. Parametre değerlerinin görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `yes`.

 /ShowModule: `yes`&#124; `no` [veya]/m: `yes`&#124; `no` isteğe bağlı. Modül adının görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `yes`.

 /Showlinekayması: `yes`&#124; `no` [veya]/#: `yes`&#124; `no` isteğe bağlı. Çizgi kaydırın görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `no`.

 /Showbytekayması: `yes`&#124; `no` [veya]/b: `yes`&#124; `no` isteğe bağlı. Bayt kaydırının görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `no`.

 /ShowLanguage: `yes`&#124; `no` [veya]/l: `yes`&#124; `no` isteğe bağlı. Dilin görüntülenip görüntülenmeyeceğini belirtir. Varsayılan değer `no`.

 /Includecallsacrossthreads: `yes`&#124; `no` [veya]/i: `yes`&#124; `no` isteğe bağlı. Diğer iş parçacıklarından veya çağrıların eklenip eklenmeyeceğini belirtir. Varsayılan değer `no`.

 /ShowExternalCode: `yes`&#124; `no` isteğe bağlı. Callstack için Yalnızca kendi kodum gösterilip gösterilmeyeceğini belirtir. Yalnızca kendi kodum kapalıyken, tüm Kullanıcı dışı kod görüntülenir. Yalnızca kendi kodum açık olduğunda, Kullanıcı olmayan kod, çağrı yığını çıktısında `[external]` olarak görüntülenir.

 Thread: Isteğe bağlı `n`. İş parçacığı `n` için çağrı yığını 'i görüntüler. Hiçbir iş parçacığı belirtilmemişse, geçerli iş parçacığı için çağrı yığını ' i yürütür.

## <a name="remarks"></a>Açıklamalar
 Bağımsız değişkenlerde veya anahtarlarda yapılan değişiklikler, bu komutun gelecekteki etkinleştirmeleri için geçerlidir. Kendi kendine hata ayıkla. Listcallstackbir sorun varsa, tüm çağrı yığını görüntülenir. Bir dizin belirtirseniz, örneğin

```
Debug.ListCallStack 2
```

 sonra geçerli yığın çerçevesi bu çerçeveye ayarlanır (Bu örnekte ikinci kare).

 Bu komutu, önceden tanımlanmış bir diğer ad olan KB kullanarak da yazabilirsiniz. Örneğin,

```
kb 2
```

 geçerli yığın çerçevesini ikinci çerçeveye ayarlamak için.

## <a name="example"></a>Örnek

```
>Debug.CallStack /Count:4 /ShowTypes:yes
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Ayrıştırılmış kod komut](../../ide/reference/list-disassembly-command.md) [listesi Iş parçacıklarını Listele komutu](../../ide/reference/list-threads-command.md) [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [Bul/komut kutusu](../../ide/find-command-box.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md)
