---
description: İçeri aktarmalar, dışarı aktarmalar veya ayarları Visual Studio sıfırlar. vssettings dosya uzantısı
title: Ayarları İçeri ve Dışarı Aktar komutu
ms.date: 05/28/2021
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3074371bbf76d3f393e89655d85e2ed1a08ec58e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101277"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Import and Export Ayarlar komutu (.vssettings dosyası)

ayarları dosyası olan Visual Studio içeri Visual Studio veya `.vssettings` sıfırlar.

Dosyanın şeması açık. En yaygın olarak şema, her kategorinin bir etiket olduğu ve alt kategori etiketlerini içerenin bir XML yapısını izler. Bu alt kategori etiketleri özellik değeri etiketlerini içerebilir. Paketlerin çoğu ortak yapıyı kullansa da, Visual Studio şemayla dosyaya rastgele XML katkıda bulunabilirsiniz.

## <a name="syntax"></a>Syntax

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Anahtarlar

/export:`filename`

İsteğe bağlı. Geçerli ayarları belirtilen dosyaya dışarı aktarır.

/import:`filename`

İsteğe bağlı. Belirtilen dosyada ayarları içeri aktarır.

/reset

İsteğe bağlı. Geçerli ayarları sıfırlar.

## <a name="remarks"></a>Açıklamalar

Bu komutu hiçbir anahtarla çalıştırarak İçeri **ve Dışarı Aktarma Ayarlar** açılır. Daha fazla bilgi için [bkz. Ayarlarınızı ve Ortam](../synchronized-settings-in-visual-studio.md) [ayarlarınızı eşitleme.](../environment-settings.md)

## <a name="example"></a>Örnek

Aşağıdaki komut, geçerli ayarları dosyasına dışarı `MyFile.vssettings` aktarır:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```



## <a name="see-also"></a>Ayrıca bkz.

- [Ortam ayarları](../../ide/environment-settings.md)
- [Ayarlarınızı eşitleme](../../ide/synchronized-settings-in-visual-studio.md)
- [IDE'Visual Studio kişiselleştirme](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio komutları](../../ide/reference/visual-studio-commands.md)
