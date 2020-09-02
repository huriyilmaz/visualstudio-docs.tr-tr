---
title: -Log (devenv.exe)
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
ms.openlocfilehash: 008e7ca15595db249c05485f0d9e8f8b1277993e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595468"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Tüm etkinliği, sorun giderme amacıyla günlük dosyasına kaydeder. Bu dosya, `devenv /log` en az bir kez çağrıldıktan sonra görüntülenir. Varsayılan olarak, günlük dosyası şurada bulunur:

**% AppData% \\ Microsoft \\ VisualStudio \\ ** \<Version\> ** \\ActivityLog.xml**

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
