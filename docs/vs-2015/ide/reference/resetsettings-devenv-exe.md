---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 41e402a9268acecb70c83e26bab0e682d4ec59f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665590"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Varsayılan ayarları geri yükler ve IDE 'yi otomatik olarak başlatır [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . İsteğe bağlı olarak ayarları belirtilen bir. vssettings dosyasına sıfırlar.

 Varsayılan ayarlar, ilk başlatıldığında seçili olan profil tarafından belirlenir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="syntax"></a>Söz dizimi

```
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Bağımsız değişkenler
 `SettingsFile` Uygulanacak. vssettings dosyasının tam yolu ve adı [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

 Genel geliştirme ayarları profilini geri yüklemek için kullanın `General` .

## <a name="remarks"></a>Açıklamalar
 Hayır `SettingsFile` belirtilirse, bir sonraki başlatmanızda bir varsayılan ayarlar koleksiyonu seçmeniz istenir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="example"></a>Örnek
 Aşağıdaki komut satırı, dosyasında depolanan ayarları uygular `MySettings.vssettings` .

```
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Devenv komut satırı anahtarlarında](../../ide/reference/devenv-command-line-switches.md) geliştirme ayarlarını özelleştirme
