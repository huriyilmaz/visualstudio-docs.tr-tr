---
title: Visual Studio'de dal oluşturma
titleSuffix: ''
description: Git veya Visual Studio kullanarak bir dal Azure DevOps.
ms.date: 11/08/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 59d6b39817ed4175b646acf7a83c6decca849163
ms.sourcegitcommit: 67dc39e93c86ba50eb5ca877b0471fb8ab8475ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2021
ms.locfileid: "132002557"
---
# <a name="create-a-branch-in-visual-studio"></a>Visual Studio'de dal oluşturma

Yeni bir dal oluşturmak Visual Studio; Tek gereken bunu mevcut bir dalı temel alan bir daldır.

Aşağıdaki adımları uygulayın:

1. Başlamak için önceden oluşturulmuş veya kopyalanmış bir [repo](git-create-repository.md) [açık olduğundan](git-clone-repository.md) emin olun.

1. Git **menüsünden** Yeni **Dal'ı seçin.**

    :::image type="content" source="media/vs-2022/git-menu-new-branch.png" alt-text="Git menüsündeki Yeni Dal seçeneğinin ekran görüntüsü.":::

1. Yeni **dal oluştur iletişim** kutusuna bir dal adı girin.

    :::image type="content" source="media/vs-2022/git-create-new-branch-dialog.png" alt-text="Yeni Dal Oluştur iletişim kutusunun ekran görüntüsü.":::

1. Temel **alınan bölümünde,** yeni dalını mevcut bir yerel daldan mı yoksa uzak daldan mı temel almak istediğinize karar almak için açılan listeyi kullanın.

1. Varsayılan **olarak açık** olan Teslim alma dalı onay kutusu otomatik olarak yeni oluşturulan dala geçiş eder. Geçerli dalda kalmak için bu seçeneği açık olarak belirleyin.

İşte bu var; yeni bir dal oluşturduğunuza göre.

> [!TIP]
> Bu eylemin eşdeğer komutu şu `git checkout -b <new-branch> <existing-branch>` şekildedir: .

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için Commit [yapma sayfasını ziyaret](git-make-commit.md) edin.

## <a name="see-also"></a>Ayrıca bkz.

[Visual Studio'da Git deneyimi](git-with-visual-studio.md)