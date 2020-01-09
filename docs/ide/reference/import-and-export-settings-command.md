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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568834"
---
# <a name="import-and-export-settings-command"></a>Ayarları İçeri ve Dışarı Aktar komutu

Visual Studio ayarlarını içeri aktarır, dışarı aktarır veya sıfırlar.

## <a name="syntax"></a>Sözdizimi

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Geçişler

/Export:`filename`

İsteğe bağlı. Geçerli ayarları belirtilen dosyaya dışa aktarır.

/import:`filename`

İsteğe bağlı. Belirtilen dosyadaki ayarları içeri aktarır.

/Reset süpürmeden

İsteğe bağlı. Geçerli ayarları sıfırlar.

## <a name="remarks"></a>Açıklamalar

Bu komutu hiçbir anahtar olmadan çalıştırmak, **Ayarları içeri ve dışarı aktarma** Sihirbazı 'nı açar. Daha fazla bilgi için bkz. ayarlarınızı ve [ortam ayarlarınızı](../environment-settings.md) [eşitler](../synchronized-settings-in-visual-studio.md) .

## <a name="example"></a>Örnek

Aşağıdaki komut, geçerli ayarları dosyaya `MyFile.vssettings`dışa aktarır:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../../ide/environment-settings.md)
- [Ayarlarınızı eşitler](../../ide/synchronized-settings-in-visual-studio.md)
- [Visual Studio IDE'yi kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
