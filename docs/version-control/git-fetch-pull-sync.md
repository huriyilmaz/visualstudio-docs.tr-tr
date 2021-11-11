---
title: Visual Studio'de getirme, çekme, Visual Studio
titleSuffix: ''
description: Git veya Azure DevOps kullanarak Visual Studio içinde getirme, çekme, Azure DevOps.
ms.date: 11/10/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 617af7d27fa696d5221093bb3d0cb7c5f619df10
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264207"
---
# <a name="fetch-pull-and-sync-in-visual-studio"></a>Verilerde getirme, çekme ve Visual Studio

Visual Studio indirme (getirme ve çekme) ve karşıya yükleme (anında yükleme) işlemleri aracılığıyla yerel dalını uzak dalınıza eşitlenmiş durumda tutmanıza yardımcı olur.

Git menüsünü kullanarak Visual Studio 2022'de getirme, çekme ve **eşitleme yapabilirsiniz.**

:::image type="content" source="media/vs-2022/git-menu-fetch.png" alt-text="2022'de Getir seçeneğinin vurgulanmış olduğu Git Visual Studio.":::

Önceki ekran görüntüsünde **Getir** seçeneği vurgulanmış. Git menüsü aşağıdaki ek seçenekleri de içerir:

- **Çekme**
- **Itme**
- **Eşitleme (Çekme ve Itme)**

Bu işlemleri gerçekleştirmek için Git Değişiklikleri **penceresindeki** düğme denetimlerini de kullanabilirsiniz.

:::image type="content" source="media/vs-2022/git-changes-window-options.png" alt-text="2022'de Getirme, Çekme, Itme ve Eşitleme düğme denetimlerinin vurgulanmış olduğu Git Değişiklikleri Visual Studio.":::

Soldan sağa doğru düğme denetimleri **Fetch,** **Pull,** **Push** ve **Sync denetimlerini içerir.**

Ek olarak, ek işlemler için **üç nokta** (**...**) düğme denetimi de vardır. Bunu seçerek bir bağlam menüsü açılır. Getirme, çekme, itme ve eşitleme işlemlerinize ince ayar yapmak için bu ayarı kullanabilirsiniz.

:::image type="content" source="media/vs-2022/git-changes-window-ellipsis.png" alt-text="2022'de Git Değişiklikleri penceresinde üç nokta düğme denetimi Visual Studio açılır.":::

## <a name="fetch"></a>Getir

Çekmeden önce getirme ve çekme önemlidir. Yerel değişikliklerinize dahil etmek için herhangi bir uzak işleme olup bu denetimleri getirme. Varsa, yukarı akış birleştirme çakışmalarını önlemek için önce çekin.

Bir dalı getirebilirsiniz. **Git Değişiklikleri** penceresinde, dal açılan listesinde uzak daldan gelen işlanmamış işlemelerin sayısını gösteren bir gösterge vardır. Bu gösterge ayrıca size, işlenmiş olmayan yerel işlemelerin sayısını gösterir.

Gösterge ayrıca sizi Git Deposu penceresinde bu dalın işleme geçmişine götüren bir **bağlantı olarak da** işlev gösterir. Geçmişin en üstünde artık bu gelen ve giden işlemelerin ayrıntıları görüntülenir. Buradan işlemeleri çekme veya itme kararlarını da vesersiniz.

## <a name="pull"></a>Çek

Her zaman itmeden önce çekin. İlk çekme işlemiyle yukarı akış birleştirme [çakışmalarını önleyebilirsiniz.](git-resolve-conflicts.md)

## <a name="push"></a>Gönder

Commit'leri oluşturmanın doğal olarak kodunuzun yerel anlık görüntülerini kaydetmeniz gerekir. **Commit'leri** yedekleme olarak depo GitHub veya kodunuzu başkalarla paylaşabilirsiniz.

Ancak daha önce belirtildiği gibi, her zaman itmeden önce çekin. Güvenli koruma olarak Visual Studio yerel dal uzak dalın arkasında ise işlemeleri itmenize izin vermez. Itmeye denersiniz, bir iletişim kutusu, çekmeden önce çekmeni istenir.

## <a name="sync"></a>Sync

Bu işlemi aynı anda hem çekme hem de itme için kullanın.

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için [Git depolarına göz atın sayfasını ziyaret](git-browse-repository.md) edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Bir repodan proje açma](../get-started/tutorial-open-project-from-repo.md)
- [Visual Studio & GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
