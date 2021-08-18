---
title: Kullanılmayan başvuruları kaldırma
description: Yeni Kullanılmayan Başvuruları Kaldır komutuyla proje başvurularını temizlemeyi ve kullanımı NuGet paketleri kullanmayı öğrenin.
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 19fe9badea98eafa040557d6d373ad72df588229
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122143605"
---
# <a name="remove-unused-references"></a>Kullanılmayan Başvuruları Kaldırma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#
- Visual Basic

**Ne:** Kullanılmayan başvuruları kaldırmanız için izin verir.

**Ne zaman:** Proje başvurularını temizlemek ve kullanımı NuGet paketleri temizlemek istediğiniz. 

**Neden:** Kullanımız proje başvurularının kaldırılması, her modülün yüklemesi zaman alalı ve hiçbir zaman kullanılmayacak derleyici yükleme meta verilerine sahip olmaktan kaçınarak uygulamanıza yer tasarrufu ve başlatma süresinin azaltılmasına yardımcı olabilir.

## <a name="how-to"></a>Nasıl yapılır

1. Proje adı veya bağımlılıklar düğümüne sağ tıklayın Çözüm Gezgini.

2. Kullanılmayan **Başvuruları Kaldır'ı seçin.**

    ![Kullanılmayan Başvuruları Kaldır komutu](media/remove-unused-references-command.png)

3. Kullanılmayan **Başvuruları Kaldır iletişim kutusu,** kaynak kodda hiç kullanımın olmadığını gösteren başvurular görüntülenir. Kullanılmayan başvurular, Eylem açılan listesinden seçerek başvuruları koruma seçeneğiyle birlikte kaldırma `Keep` için önceden seçilir.

    ![Kullanılmayan Başvuruları Kaldır iletişim kutusu](media/remove-unused-references-dialog.png)

5. Seçili `Apply` başvuruları kaldırmak için tıklayın. 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)