---
title: Git depo oluşturma
description: Git kullanarak Visual Studio depo oluşturun veya bir depoya Azure DevOps gidin.
ms.date: 02/02/2022
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
---
# <a name="create-a-git-repository-from-visual-studio"></a>Visual Studio'den Git deposu oluşturma

Visual Studio, IDE'den bir repo oluşturmanızı kolaylaştırır. Depodan depo Visual Studio, GitHub için iyileştirilmiştir, ancak tercih edilen Git sağlayıcısıyla uzaktan çalışabilirsiniz.  Aşağıdaki adımları uygulayın:

## <a name="prerequisites"></a>Önkoşullar

Bu makaleyi takip etmek için aşağıdakiler gerekir:
+ [Visual Studio yükleme](../install/install-visual-studio.md)
+ [Bir GitHub hesabı](git-create-github-account.md)

## <a name="create-a-github-repo"></a>Bir GitHub oluşturma

1. Yeni Visual Studio'yi açın ve Yeni **proje oluştur'a seçin**.

    > [!TIP]
    > Henüz bir repoya eklemek Visual Studio projeniz yoksa, hızla yeni bir [C#](../get-started/csharp/tutorial-console.md#create-a-project) konsol uygulaması oluşturabilir ve **MyNewApp olarak anabilirsiniz**. Visual Studio yeni uygulamanıza varsayılan "*Merhaba Dünya!*" Kod.

1. **Git menüsünden Git** Deposu **Oluştur'a tıklayın**.

    :::image type="content" source="media/vs-2022/git-menu-create-git-repository.png" alt-text="Visual Studio'daki Git menüsündeki Git Deposu Oluştur seçeneğinin ekran Visual Studio.":::

1. **Git deposu oluştur iletişim kutusunun** Yeni bir uzak **bölüme itme** bölümünde Git'e **GitHub**.

    :::image type="content" source="media/vs-2022/git-menu-create-github-repo-dialog.png" alt-text="Uygulama seçiminin vurgulanmış olduğu git menüsündeki Git Visual Studio Git Deposu GitHub ekran görüntüsü.":::

1. **Git** **deposu oluştur iletişim GitHub** yeni bir depo oluştur bölümünde, oluşturmak istediğiniz deponun adını girin.

    > [!TIP]
    > Henüz GitHub oturum GitHub bu ekrandan da oturum açın.

1. Oturum açın ve repo bilgilerinizi girdikten sonra, oluştur ve Itme düğmesini seçerek kendiponuz oluşturun ve uygulamanızı ekleyin.

    :::image type="content" source="media/vs-2022/git-menu-create-git-repo-push-code.png" alt-text="Git Deposu Oluştur penceresini kullanarak GitHub kullanıcı bilgileri ekran görüntüsü.":::

### <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu açma

Depoyu oluşturduktan veya klonladikten [sonra Visual Studio Git](git-clone-repository.md) deposunu algılar ve Git menüsündeki Yerel Depolar listenize ekler. Buradan Git depolarına hızlıca erişin ve bu depolar arasında geçişe geçin.

## <a name="create-an-azure-devops-repo"></a>Bir Azure DevOps oluşturma

1. Yeni Visual Studio'yi açın ve Yeni **proje oluştur'a seçin**.

    > [!TIP]
    > Henüz bir repoya eklemek Visual Studio projeniz yoksa, hızla yeni bir [C#](../get-started/csharp/tutorial-console.md#create-a-project) konsol uygulaması oluşturabilir ve **MyNewApp olarak anabilirsiniz**. Visual Studio yeni uygulamanıza varsayılan "*Merhaba Dünya!*" Kod.

1. **Git menüsünden Git** Deposu **Oluştur'a tıklayın**.

1. **Git deposu oluştur iletişim kutusunun** Yeni bir uzak **bölüme itme** bölümünde Git'e **Azure DevOps**.

1. Yeni **bir Azure DevOps deposu oluştur** bölümünde Azure hesabınızla oturum açın ve açılan listeden **Project** proje seçin.

1. Oluştur **ve Itme düğmesini** seçerek bir repo oluşturun ve uygulama ekleyin.

    :::image type="content" source="media/vs-2022/git-menu-publish-azure-devops.png" alt-text="Tek bir eylemle kod yayımlamak için kullanabileceğiniz Git deposu oluştur iletişim kutusunun Create and Push işlevinin ekran görüntüsü.":::

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için Dal [oluşturma sayfasını ziyaret](git-create-branch.md) edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Öğretici: Bir repodan proje açma](../get-started/tutorial-open-project-from-repo.md)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
