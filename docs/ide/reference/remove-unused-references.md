---
title: Kullanılmayan başvuruları kaldırma
description: Yeni Kullanılmayan Başvuruları Kaldır komutuyla proje başvurularını temizlemeyi ve NuGet paketleri temizlemeyi öğrenin.
ms.custom: SEO-VS-2021
ms.date: 09/14/2021
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
ms.openlocfilehash: df388659e0776fc15155d338c97334b2c5283468
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428704"
---
# <a name="remove-unused-references"></a>Kullanılmayan Başvuruları Kaldırma

Bu yeniden düzenleme aşağıdakiler için geçerlidir:

- C#
- Visual Basic

**Ne:** SDK stili projeleri için kullanılmayan başvuruları [kaldırmaya olanak sağlar.](/dotnet/core/project-sdk/overview)

**Ne zaman:** Proje başvurularını temizlemek ve kullanımı NuGet paketlerine sahip olmak istediğiniz.

**Neden:** Kullanımın kullanılmaması gereken proje başvurularının kaldırılması, her modülün yüklemesi zaman alalı ve hiçbir zaman kullanılmayacak derleyici yükleme meta verilerine sahip olmaktan kaçınarak uygulamanıza yer tasarrufu ve başlatma süresinin azaltılmasına yardımcı olabilir.

## <a name="how-to"></a>Nasıl yapılır

1. Proje adı veya bağımlılıklar düğümüne sağ tıklayın Çözüm Gezgini.

2. Kullanılmayan **Başvuruları Kaldır'ı seçin.**

    ![Kullanılmayan Başvuruları Kaldır komutu](media/remove-unused-references-command.png)

3. Kullanılmayan **Başvuruları Kaldır iletişim** kutusu, kaynak kodda hiç kullanımın olmadığını gösteren başvurular açılır. Kullanılmayan başvurular, Eylem açılan listesinden seçerek başvuruları koruma seçeneğiyle birlikte kaldırma `Keep` için önceden seçilir.

    ![Kullanılmayan Başvuruları Kaldır iletişim kutusu](media/remove-unused-references-dialog.png)

5. Seçili `Apply` başvuruları kaldırmak için tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)