---
title: Visual Studio bir dal oluşturun
titleSuffix: ''
description: Git veya Azure DevOps kullanarak Visual Studio bir dal oluşturun.
ms.date: 11/10/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 9f6e72e1254f251114b1798d97e2937ddd41aab0
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264005"
---
# <a name="create-a-branch-in-visual-studio"></a>Visual Studio bir dal oluşturun

Visual Studio ' de yeni bir dal oluşturmak kolaydır; Bunu yapmanız, var olan bir dalın temelini oluşturma.

Aşağıdaki adımları uygulayın:

1. Başlamak için önceden [oluşturulmuş](git-create-repository.md) veya [kopyalanmış](git-clone-repository.md) bir deponun açık olduğundan emin olun.

1. **Git** menüsünde **yeni dal**' ı seçin.

    :::image type="content" source="media/vs-2022/git-menu-new-branch.png" alt-text="Git menüsündeki yeni dal seçeneğinin ekran görüntüsü.":::

1. **Yeni dal oluştur** iletişim kutusunda bir dal adı girin.

    :::image type="content" source="media/vs-2022/git-create-new-branch-dialog.png" alt-text="Yeni dal oluştur iletişim kutusunun ekran görüntüsü.":::

1. **Temel alan** bölümünde, yeni dalınızı mevcut bir yerel dalı veya uzak bir dalı dışına dayandırmak isteyip istemediğinizi seçmek için açılan listeyi kullanın.

1. Varsayılan olarak üzerinde olan **kullanıma alma dalı** onay kutusu otomatik olarak yeni oluşturulan dala geçer. Geçerli dalda kalmak istiyorsanız bu seçeneği değiştirin.

Bunu yapabilirsiniz; Yeni bir dal oluşturdunuz.

> [!TIP]
> Bu eylem için eşdeğer komut `git checkout -b <new-branch> <existing-branch>` .

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğa devam etmek için [Işleme oluşturma](git-make-commit.md) sayfasını ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Git deneyimi Visual Studio](git-with-visual-studio.md)
- [Visual Studio & GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)