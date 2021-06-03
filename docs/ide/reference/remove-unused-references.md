---
title: Kullanılmayan başvuruları kaldır
description: Yeni kullanılmayan başvuruları kaldır komutuyla kullanımı olmayan proje başvurularını ve NuGet paketlerini temizlemeyi öğrenin.
ms.custom: SEO-VS-2021
ms.date: 06/01/2021
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 707769229ad7bc1864a135bade1df918d4b27847
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2021
ms.locfileid: "111352096"
---
# <a name="remove-unused-references"></a>Kullanılmayan başvuruları kaldır

Bu yeniden düzenleme için geçerlidir:

- C#
- Visual Basic

**Ne:** Kullanılmayan başvuruları kaldırmanızı sağlar.

**Ne zaman:** Kullanım içermeyen proje başvurularını ve NuGet paketlerini temizlemek istiyorsunuz. 

**Neden:** Kullanım içermeyen proje başvurularını kaldırmak, her modülün yüklenmesi ve derleyicinin yükleme meta verilerinin hiç kullanılmayacağı zaman alacağından, alan tasarrufu ve uygulamanızın başlama süresini azaltmaya yardımcı olabilir.

## <a name="how-to"></a>Nasıl yapılır

1. Çözüm Gezgini bir proje adına veya bağımlılıklar düğümüne sağ tıklayın.

2. **Kullanılmayan başvuruları kaldır**' ı seçin.

    ![Kullanılmayan başvuruları Kaldır komutu](media/remove-unused-references-command.png)

3. **Kullanılmayan başvuruları kaldır** iletişim kutusu, kaynak kodunda kullanımı olmayan başvuruları görüntüleyen açılır. Kullanılmayan başvurular `Keep` , eylem açılan listesinden seçerek başvuruları koruma seçeneği ile kaldırma için önceden seçilir.

    ![Kullanılmayan başvuruları Kaldır iletişim kutusu](media/remove-unused-references-dialog.png)

5. `Apply`Seçili başvuruları kaldırmak için tıklayın. 

## <a name="see-also"></a>Ayrıca bkz.

- [Yeniden Düzenle](../refactoring-in-visual-studio.md)