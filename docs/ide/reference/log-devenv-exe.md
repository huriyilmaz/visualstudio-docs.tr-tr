---
title: -Log (devenv.exe)
description: Tüm etkinlikleri sorun giderme için günlük dosyasına kaydetmek üzere log Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9dae594df60d75ced4ba6bdda5cb37c8c07a852
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040582"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Tüm etkinliği, sorun giderme amacıyla günlük dosyasına kaydeder. Bu dosya, `devenv /log` en az bir kez çağrıldıktan sonra görüntülenir. Varsayılan olarak, günlük dosyası şurada bulunur:

**% AppData% \\ Microsoft \\ VisualStudio \\** \<Version\> **\\ActivityLog.xml**

\<Version\>Visual Studio sürümüdür. Ancak, farklı bir yol ve dosya adı belirtebilirsiniz.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Bağımsız değişkenler

- *NameOfLogFile*

  Gereklidir. Kaydedilecek günlük dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, diğer tüm anahtarlardan sonra komut satırının en sonunda görünmelidir.

Günlük yalnızca, anahtarla açtığınız tüm Visual Studio örnekleri için yazılır `/Log` .

## <a name="example"></a>Örnek

Bu örnek `MyVSLog.xml` , kullanıcının giriş dizinindeki dosyasına günlüğü yönlendirir.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
