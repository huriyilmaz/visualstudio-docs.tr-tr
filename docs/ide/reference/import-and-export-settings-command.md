---
title: Ayarları İçeri ve Dışarı Aktar komutu
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 409c0f40adfd374065dedb842965d2d1237bc9a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568834"
---
# <a name="import-and-export-settings-command"></a>Ayarları İçeri ve Dışarı Aktar komutu

Visual Studio ayarlarını içe aktarma, dışa aktarma veya sıfırlama.

## <a name="syntax"></a>Sözdizimi

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Anahtarlar

/ihracat:`filename`

İsteğe bağlı. Geçerli ayarları belirtilen dosyaya aktarın.

/import:`filename`

İsteğe bağlı. Belirtilen dosyadaki ayarları aktarın.

/sıfırlama

İsteğe bağlı. Geçerli ayarları sıfırlar.

## <a name="remarks"></a>Açıklamalar

Bu komutu anahtarsız **çalıştırmak, İçe Ve Dışa Aktar Ayarları** sihirbazını açar. Daha fazla bilgi için ayarlarınızı ve [Çevre ayarlarınızı](../environment-settings.md) [eşitle'ye](../synchronized-settings-in-visual-studio.md) bakın.

## <a name="example"></a>Örnek

Aşağıdaki komut geçerli ayarları dosyaya `MyFile.vssettings`aktarın:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../../ide/environment-settings.md)
- [Ayarlarınızı senkronize edin](../../ide/synchronized-settings-in-visual-studio.md)
- [Visual Studio IDE'yi kişiselleştirin](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
