---
title: Visual Studio'de bir Visual Studio
titleSuffix: ''
description: Git kullanarak Visual Studio depo oluşturun veya bir depoya Azure DevOps gidin.
ms.date: 11/10/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 3ef08c327e7fb0945338477f2a971a0decb364eb
ms.sourcegitcommit: dc12d3d0ca2ec3601cb9de7c22e61ecf22c7c514
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "132264164"
---
# <a name="create-a-repo-in-visual-studio"></a>Visual Studio'de bir Visual Studio

Visual Studio, IDE'den bir repo kopyalamayı kolaylaştırır. Aşağıdaki adımları uygulayın:

## <a name="create-a-github-repo"></a>Bir GitHub oluşturma

1. Yeni Visual Studio'yi açın ve Yeni **proje oluştur'a seçin.**

    > [!TIP]
    > Henüz bir repoya eklemek Visual Studio projeniz yoksa, hızla yeni bir [C#](../get-started/csharp/tutorial-console.md#create-a-project) konsol uygulaması oluşturabilir ve **Bunu MyNewApp olarak adlandırabilirsiniz.** Visual Studio yeni uygulamanıza varsayılan "*Hello, World!*" Kod.

1. Git **menüsünden Git** Deposu **Oluştur'a tıklayın.**

    :::image type="content" source="media/vs-2022/git-menu-create-git-repository.png" alt-text="Visual Studio'daki Git menüsünden Git Deposu Oluştur seçeneğinin ekran Visual Studio.":::

1. Git **deposu oluştur iletişim kutusunun Yeni** bir uzak **bölüme itme bölümünde Git'e** GitHub. 

    :::image type="content" source="media/vs-2022/git-menu-create-github-repo-dialog.png" alt-text="Uygulama seçiminin vurgulanmış olduğu git menüsündeki Git Visual Studio Git Deposu GitHub ekran görüntüsü.":::

1. **Git** **deposu oluştur iletişim GitHub** yeni bir depo oluştur bölümünde oluşturmak istediğiniz deponun adını girin.

    > [!TIP]
    > Henüz GitHub oturum GitHub bu ekrandan da oturum açın.

1. Oturum açın ve repo bilgilerinizi girdikten  sonra, oluştur ve Itme düğmesini seçerek kendiponuz oluşturun ve uygulamanızı ekleyin.

    :::image type="content" source="media/vs-2022/git-menu-create-git-repo-push-code.png" alt-text="Git Deposu Oluştur penceresini kullanarak GitHub bilgileri ekran görüntüsü.":::

### <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu açma

Depoyu oluşturduktan veya klonladikten sonra [Visual Studio](git-clone-repository.md)Git deposunu algılar ve Git menüsündeki  Yerel Depolar listenize ekler. Buradan Git depolarına hızlıca erişin ve bu depolar arasında geçişe geçin.

## <a name="create-an-azure-devops-repo"></a>Bir Azure DevOps oluşturma

1. Yeni Visual Studio'yi açın ve Yeni **proje oluştur'a seçin.**

    > [!TIP]
    > Henüz bir repoya eklemek Visual Studio projeniz yoksa, hızla yeni bir [C#](../get-started/csharp/tutorial-console.md#create-a-project) konsol uygulaması oluşturabilir ve **Bunu MyNewApp olarak adlandırabilirsiniz.** Visual Studio yeni uygulamanıza varsayılan "*Hello, World!*" Kod.

1. Git **menüsünden Git** Deposu **Oluştur'a tıklayın.**

1. Git **deposu oluştur iletişim kutusunun Yeni** bir uzak **bölüme itme bölümünde** Yeni bir uzak depoya Azure DevOps. 

1. Yeni **bir depolama Azure DevOps bölümünde** Azure hesabınızla oturum açın ve açılan listeden bir **Project** seçin.

1. Oluştur **ve Itme düğmesini** seçerek bir repo oluşturun ve uygulama ekleyin.

    :::image type="content" source="media/vs-2022/git-menu-publish-azure-devops.png" alt-text="Tek bir eylemle kod yayımlamak için kullanabileceğiniz Git deposu oluştur iletişim kutusunun Create and Push işlevinin ekran görüntüsü.":::

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için Dal [oluşturma sayfasını ziyaret](git-create-branch.md) edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Bir repodan proje açma](../get-started/tutorial-open-project-from-repo.md)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Birden çok kullanıcı hesabıyla çalışma](../ide/work-with-multiple-user-accounts.md)
- [Visual Studio’da oturum açma](../ide/signing-in-to-visual-studio.md)
- [Visual Studio & GitHub: Birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)