---
title: Visual Studio'de bir Visual Studio
titleSuffix: ''
description: Git kullanarak Visual Studio depo oluşturun veya bir depoya Azure DevOps gidin.
ms.date: 10/29/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 3eb85359ca8c00bd129051acc92c62eb4e5f1716
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131130531"
---
# <a name="create-a-repo-in-visual-studio"></a>Visual Studio'de bir Visual Studio

Visual Studio, IDE'den bir repo kopyalamayı kolaylaştırır. Aşağıdaki adımları uygulayın:

## <a name="create-a-github-repo"></a>Bir GitHub oluşturma

1. Yeni Visual Studio'yi açın ve Yeni **proje oluştur'a seçin.**

    > [!TIP]
    > Henüz bir repoya eklemek Visual Studio projeniz yoksa, hızla yeni bir [C#](../get-started/csharp/tutorial-console.md#create-a-project) konsol uygulaması oluşturabilir ve **Bunu MyNewApp olarak adlandırabilirsiniz.** Visual Studio yeni uygulamanıza varsayılan "*Hello, World!*" Kod.

1. Git **menüsünden Git** Deposu **Oluştur'a tıklayın.**

    :::image type="content" source="media/vs-2022/git-menu-create-git-repository.png" alt-text="Git menüsündeki Git Deposu Oluştur seçeneğinin ekran görüntüsü Visual Studio.":::

1. Git **deposu oluştur iletişim kutusunun Yeni** bir uzak **bölüme itme bölümünde** Yeni bir uzak depoya GitHub. 

    :::image type="content" source="media/vs-2022/git-menu-create-github-repo-dialog.png" alt-text="Visual Studio'daki Git menüsündeki Git Deposu Oluştur seçeneğinin ekran GitHub vurgulanmış.":::

1. **Git** **deposu oluştur iletişim GitHub** yeni depo oluştur bölümünde oluşturmak istediğiniz deponun adını girin.

    > [!TIP]
    > Henüz GitHub hesabınızla oturum GitHub bu ekrandan da oturum açın.

1. Oturum açın ve repo bilgilerinizi girdikten  sonra, oluştur ve Itme düğmesini seçerek kendiponuz oluşturun ve uygulamanızı ekleyin.

    :::image type="content" source="media/vs-2022/git-menu-create-git-repo-push-code.png" alt-text="Git Deposu Oluştur penceresini kullanarak GitHub kullanıcıya özel güvenlik bilgileri ekran görüntüsü.":::

## <a name="create-an-azure-devops-repo"></a>Bir Azure DevOps oluşturma

1. Yeni Visual Studio'yi açın ve Yeni **proje oluştur'a seçin.**

    > [!TIP]
    > Henüz bir repoya eklemek Visual Studio projeniz yoksa, hızla yeni bir [C#](../get-started/csharp/tutorial-console.md#create-a-project) konsol uygulaması oluşturabilir ve **Bunu MyNewApp olarak adlandırabilirsiniz.** Visual Studio yeni uygulamanıza varsayılan "*Hello, World!*" Kod.

1. Git **menüsünden Git** Deposu **Oluştur'a tıklayın.**

1. Git **deposu oluştur iletişim kutusunun Yeni** bir uzak **bölüme itme bölümünde** Yeni bir uzak depoya Azure DevOps. 

1. Yeni **bir Azure DevOps deposu oluştur** bölümünde Azure hesabınızla oturum açın ve açılan listeden **Project** proje seçin.

1. Oluştur **ve Itme düğmesini** seçerek bir repo oluşturun ve uygulama ekleyin.

    :::image type="content" source="media/vs-2022/git-menu-publish-azure-devops.png" alt-text="Tek bir eylemle kod yayımlamak için kullanabileceğiniz Git deposu oluştur iletişim kutusunun Create and Push işlevinin ekran görüntüsü.":::

## <a name="next-steps"></a>Sonraki adımlar

Genel bakış için bkz. Git [deneyimi Visual Studio.](git-with-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Bir repodan proje açma](../get-started/tutorial-open-project-from-repo.md)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Birden çok kullanıcı hesabıyla çalışma](../ide/work-with-multiple-user-accounts.md)
- [Visual Studio’da oturum açma](../ide/signing-in-to-visual-studio.md)