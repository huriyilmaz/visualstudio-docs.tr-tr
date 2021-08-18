---
title: -Log (devenv.exe)
description: Sorun giderme için log devenv komut satırı anahtarını kullanarak tüm etkinlikleri günlük dosyasına günlüğe kaydedin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 244ff78a82838bcd2d65766680fe86c059cd43d3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151385"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Tüm etkinliği, sorun giderme amacıyla günlük dosyasına kaydeder. Bu dosya, en az bir kez `devenv /log` çağrıldıktan sonra görüntülenir. Günlük dosyası varsayılan olarak burada bulunur:

**%APPDATA% \\ Microsoft \\ VisualStudio \\** \<Version\> **\\ActivityLog.xml**

burada, \<Version\> Visual Studio sürümüdür. Ancak, farklı bir yol ve dosya adı belirtebilirsiniz.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Bağımsız değişkenler

- *NameOfLogFile*

  Gereklidir. Kaydedilen günlük dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, diğer tüm anahtarlardan sonra komut satırının en sonunda görünmelidir.

Günlük yalnızca anahtarıyla açtığınız Visual Studio tüm örneklerde `/Log` yazılır.

## <a name="example"></a>Örnek

Bu örnek, günlüğe `MyVSLog.xml` kaydetmeyi kullanıcının giriş dizininde dosyaya yönlendiren bir örnektir.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
