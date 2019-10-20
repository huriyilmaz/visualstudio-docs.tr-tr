---
title: -ResetSettings (devenv. exe) | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665590"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Varsayılan [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ayarlarını geri yükler ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 'yi otomatik olarak başlatır. İsteğe bağlı olarak ayarları belirtilen bir. vssettings dosyasına sıfırlar.

 Varsayılan ayarlar, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ilk kez başlatıldığında seçilen profil tarafından belirlenir.

## <a name="syntax"></a>Sözdizimi

```
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Arguments
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] uygulanacak. vssettings dosyasının tam yolunu ve adını `SettingsFile`.

 Genel geliştirme ayarları profilini geri yüklemek için `General` kullanın.

## <a name="remarks"></a>Açıklamalar
 @No__t_0 belirtilmemişse, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bir sonraki başlatmanızda varsayılan ayar koleksiyonunu seçmeniz istenir.

## <a name="example"></a>Örnek
 Aşağıdaki komut satırı `MySettings.vssettings` dosya içinde depolanan ayarları uygular.

```
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [Devenv komut satırı anahtarlarında](../../ide/reference/devenv-command-line-switches.md) geliştirme ayarlarını özelleştirme
