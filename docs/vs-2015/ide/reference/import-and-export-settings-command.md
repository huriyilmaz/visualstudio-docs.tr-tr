---
title: Ayarları içeri ve dışarı aktar komutu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e3ee8549fd8cf1a4551818c013551ba24128f95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671047"
---
# <a name="import-and-export-settings-command"></a>Ayarları İçeri ve Dışarı Aktar Komutu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ayarları içeri aktarır, dışarı aktarır veya sıfırlar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .

## <a name="syntax"></a>Syntax

```
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Anahtarlar
 /Export: `filename` isteğe bağlı. Geçerli ayarları belirtilen dosyaya dışa aktarır.

 /import: `filename` isteğe bağlı. Belirtilen dosyadaki ayarları içeri aktarır.

 /Reset süpürmeden isteğe bağlı. Geçerli ayarları sıfırlar.

## <a name="remarks"></a>Açıklamalar
 Bu komutu hiçbir anahtar olmadan çalıştırmak, **Ayarları içeri ve dışarı aktarma** Sihirbazı 'nı açar. Daha fazla bilgi için bkz. [nasıl yapılır: ayarları bilgisayarlar veya Visual Studio sürümleri arasında paylaşma](https://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882).

## <a name="example"></a>Örnek
 Aşağıdaki komut, dosya ayarlarını dosyaya dışa aktarır `MyFile.vssettings` .

```
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio [Visual Studio komutları](../../ide/reference/visual-studio-commands.md) ['Nda geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)
