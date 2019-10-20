---
title: Modülleri Listele komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listmodules
helpviewer_keywords:
- Debug.ListModules command
- ListModules command
- list modules command
ms.assetid: 3cb73774-6ac0-43b2-b781-75ed47175bfd
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4600f27f62d6e840041a65b4128df128e4d36873
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659527"
---
# <a name="list-modules-command"></a>Modülleri Listele Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Geçerli işlem için modülleri listeler.

## <a name="syntax"></a>Sözdizimi

```
Debug.ListModules [/Address:yes|no] [/Name:yes|no] [/Order:yes|no]
[/Path:yes|no] [/Process:yes|no] [/SymbolFile:yes|no]
[/SymbolStatus:yes|no] [/Timestamp:yes|no] [/Version:yes|no]
```

#### <a name="parameters"></a>Parametreler
 /Address: Isteğe bağlı `yes|no`. Modüllerin bellek adreslerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes`.

 /Name: Isteğe bağlı `yes|no`. Modüllerin adlarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes`.

 /Order: Isteğe bağlı `yes|no`. Modüllerin sırasının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

 /Path: `yes|no` Isteğe bağlı. Modüllerin yollarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes`.

 /Process: Isteğe bağlı `yes|no`. Modül işlemlerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

 /SymbolFile: Isteğe bağlı `yes|no`. Modüllerin sembol dosyalarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

 /SymbolStatus: Isteğe bağlı `yes|no`. Modüllerin sembol durumlarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `yes`.

 /Timestamp: Isteğe bağlı `yes|no`. Modüllerin zaman damgalarının gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

 /Version: Isteğe bağlı `yes|no`. Modüllerin sürümlerinin gösterilip gösterilmeyeceğini belirtir. Varsayılan değer `no`.

## <a name="remarks"></a>Açıklamalar

## <a name="example"></a>Örnek
 Bu örnekte, geçerli işlem için modül adları, adresler ve zaman damgaları listelenmektedir.

```
Debug.ListModules /Address:yes /Name:yes /Order:no /Path:no /Process:no /SymbolFile:no /SymbolStatus:no /Timestamp:yes /Version:no
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) [komut penceresi](../../ide/reference/command-window.md) [nasıl yapılır: modüller penceresini kullanma](../../debugger/how-to-use-the-modules-window.md)
