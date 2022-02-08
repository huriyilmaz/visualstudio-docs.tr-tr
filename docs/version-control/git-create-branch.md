---
title: Dal oluşturma
description: Git ile kaynak denetimi için bir Visual Studio oluşturun.
ms.date: 11/10/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
---
# <a name="create-a-git-branch-in-visual-studio"></a>Visual Studio'de Git dalı oluşturma

Visual Studio'da yeni bir dal oluşturmak kolaydır; tek gereken bunu mevcut bir dalı temel almaktır.

Aşağıdaki adımları uygulayın:

1. Başlamak için önceden oluşturulmuş veya kopyalanmış bir [repo](git-create-repository.md) [açık olduğundan](git-clone-repository.md) emin olun.

1. **Git menüsünden** Yeni **Dal'ı seçin**.

    :::image type="content" source="media/vs-2022/git-menu-new-branch.png" alt-text="Git menüsündeki Yeni Dal seçeneğinin ekran görüntüsü.":::

1. Yeni **dal oluştur iletişim** kutusuna bir dal adı girin.

    :::image type="content" source="media/vs-2022/git-create-new-branch-dialog.png" alt-text="Yeni Dal Oluştur iletişim kutusunun ekran görüntüsü.":::

1. Temel **alınan bölümünde** , yeni dalını mevcut bir yerel daldan mı yoksa uzak bir daldan mı temel almak istediğinize karar almak için açılan listeyi kullanın.

1. Varsayılan **olarak açık** olan Teslim alma dalı onay kutusu otomatik olarak yeni oluşturulan dala geçiş eder. Geçerli dalda kalmak için bu seçeneği açık olarak belirleyin.

İşte bu var; yeni bir dal oluşturduğunuza göre.

> [!TIP]
> Bu eylemin eşdeğer komutu şu şekildedir `git checkout -b <new-branch> <existing-branch>`: .

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için Commit [yapma sayfasını ziyaret](git-make-commit.md) edin.
