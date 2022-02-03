---
title: Git getirme, çekme, gönderim, & eşitleme
description: Git veya Azure DevOps kullanarak Visual Studio getirme, çekme, gönderme ve eşitleme.
ms.date: 11/10/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 9608696c752619e0305a262eb94ec3d82ef16fb6
ms.sourcegitcommit: 204973a0fde6c1dbe1e8fd6e1d2483bc1b7873ae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "138000449"
---
# <a name="use-git-fetch-pull-push-and-sync-for-version-control-in-visual-studio"></a>Visual Studio sürüm denetimi için git getirme, çekme, gönderme ve eşitleme kullanın

Visual Studio, yerel dalınızı karşıdan yükleme (getirme ve çekme) ve karşıya yükleme (gönderme) işlemleri aracılığıyla uzak dalınızla eşitlenmiş halde tutmanıza yardımcı olur.

**Git** menüsünü kullanarak Visual Studio 2022 ' de getirme, çekme ve eşitleme yapabilirsiniz.

:::image type="content" source="media/vs-2022/git-menu-fetch.png" alt-text="Visual Studio 2022 ' de vurgulanan getirme seçeneği ile Git menüsü.":::

Önceki ekran görüntüsünde, **getirme** seçeneği vurgulanır. Git menüsü Ayrıca aşağıdaki ek seçenekleri de içerir:

- **Çek**
- **Hareketle**
- **Eşitle (çekme ve gönderme)**

Ayrıca, bu işlemleri gerçekleştirmek için **Git değişiklikleri** penceresinde düğme denetimlerini de kullanabilirsiniz.

:::image type="content" source="media/vs-2022/git-changes-window-options.png" alt-text="Git; Visual Studio 2022 ' de vurgulanan getirme, çekme, gönderme ve eşitleme düğmesi denetimleriyle Git değişiklikleri penceresi.":::

Soldan sağa, düğme denetimleri **getirme**, **çekme**, **gönderme** ve **eşitleme**' yi içerir.

Ayrıca, ek işlemler için **üç nokta** (**...**) düğme denetimi de vardır. Seçtiğinizde, bir bağlam menüsü görüntülenir. Bunu, getirme, çekme, gönderme ve eşitleme işlemlerinizi hassas bir şekilde ayarlamak için kullanabilirsiniz.

:::image type="content" source="media/vs-2022/git-changes-window-ellipsis.png" alt-text="Visual Studio 2022 ' deki Git değişiklikleri penceresinde üç nokta düğmesi denetimini seçtikten sonra görüntülenen bağlam menüsü.":::

## <a name="fetch"></a>Çağrıldıktan

Göndermeden önce getirmek ve çekmek önemlidir. Yerel değişikliklerinizle birleştirme yapmanız gereken uzak işlemeler olup olmadığını denetler. Herhangi bir varsa, yukarı akış birleştirme çakışmalarını engellemek için önce çekin.

Bir dalı getirirken, **Git değişiklikleri** penceresinde, uzak daldaki çekolmayan işlemeler sayısını görüntüleyen dal açılan penceresinin altında bir gösterge bulunur. Bu gösterge Ayrıca, gönderilen yerel işlemelerin sayısını gösterir.

Gösterge Ayrıca **Git deposu** penceresinde bu dalın tamamlama geçmişine gidebileceğiniz bir bağlantı olarak çalışır. Geçmiş en üst kısmında, bu gelen ve giden işlemelerin ayrıntıları görüntülenir. Buradan, yürütmeleri çekme veya gönderim de yapabilirsiniz.

## <a name="pull"></a>Çek

Göndermeden önce her zaman çekin. İlk kez çektiğinizde, yukarı akış [birleştirme çakışmalarını](git-resolve-conflicts.md)önleyebilirsiniz.

## <a name="push"></a>Gönder

İşlemeler oluştururken, kodunuzun yerel anlık görüntülerini doğal olarak kaydettiniz. yürütmeleri, yedeklemeleri olarak depolayabileceğiniz veya kodlarınızı başkalarıyla paylaşabileceğiniz GitHub göndermek için **push** kullanın.

Ancak, daha önce belirtildiği gibi, göndermeden önce her zaman çekin. güvenli bir koruyucu olarak, yerel dalınızın uzak dalın arkasında olması durumunda Visual Studio yürütmelere gönderim yapmanıza izin vermez. Gönderim yapmayı denerseniz, bir iletişim kutusu göndermeden önce çekme yapmanızı ister.

## <a name="sync"></a>Sync

Aynı anda hem çekme hem de gönderim için bu işlemi kullanın.

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğa devam etmek için [Git depoları inceleyin sayfasına gidin](git-browse-repository.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: bir depodan bir proje açın](../get-started/tutorial-open-project-from-repo.md)
- [Visual Studio & GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
