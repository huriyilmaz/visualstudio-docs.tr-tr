---
title: Visual Studio'de bir Visual Studio
titleSuffix: ''
description: Git veya Visual Studio kullanarak bir depo Azure DevOps.
ms.date: 02/02/2022
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
---
# <a name="clone-a-git-repository-in-visual-studio"></a>Visual Studio'de Git deposunu kopyalama

Visual Studio, depoyu IDE'den kopyalamayı kolaylaştırır. Git sağlayıcısıyla uzaktan çalışabilirsiniz( örneğin, GitHub veya Azure DevOps. 


## <a name="prerequisites"></a>Önkoşullar

Bu makaleyi takip etmek için aşağıdakiler gerekir:
+ [Visual Studio yükleme](../install/install-visual-studio.md)
+ [Bir GitHub hesabı](git-create-github-account.md)

## <a name="clone-a-github-repo-and-sign-in"></a>Bir GitHub kopyalama ve oturum açma

1. Visual Studio'yu açın.

1. **Git menüsünden** Depoyu **Kopyala'ya tıklayın**.

    :::image type="content" source="../ide/media/vs-2022/git-menu-clone-repository.png" alt-text="Visual Studio'daki Git menüsündeki Depoyu Kopyala seçeneğinin ekran Visual Studio.":::

    > [!NOTE]
    > Git menüsüyle daha önce **etkileşim** kurmadıysanız Depoyu **Klonla** yerine **Klonla seçeneğini kullanabilirsiniz**. Öyleyse Kopyala'ya **seçin**.
    >
    > Git **menü çubuğunda** değilse  >  AraçlarSeçeneklerKaynak >  >  **DenetimiBağlı Seçim'e** gidin ve geçerli kaynak denetimi eklentisi açılan **listesinden Git'i** seçin.

1. Depoyu **klonla penceresindeki** **Git deposu URL'si** girin bölümünün altında depo bilgilerinizi **Depo konumu kutusuna** ekleyin.

    Ardından Yol **bölümünde** yerel kaynak dosyalarınızın varsayılan yolunu kabul etme veya farklı bir konuma göz atabilirsiniz.

    Ardından Bir **depoya göz at bölümünde** **Depo'GitHub.**

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog.png" alt-text="Depo Klonla iletişim kutusunun ekran görüntüsü, GitHub vurgulanmış.":::

1. Hesaptan **aç GitHub** penceresinde, hesap GitHub doğrular veya eklersiniz. Bunu yapmak için açılan **menüden** Oturum aç'ı seçin.

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog-github-account.png" alt-text="Oturum aç penceresinin Oturum aç açılan bölümünün ekran GitHub görüntüsü.":::

    İlk kez GitHub Visual Studio oturum Visual Studio bildirimi görüntülenir. İstediğiniz seçenekleri belirleyin ve ardından **Github'ı yetkilendir'i seçin**.

    :::image type="content" source="media/vs-2022/git-menu-github-authorize-visual-studio-sml.png" alt-text="Yetkilendirme iletişim kutusunun ekran görüntüsü." lightbox="media/vs-2022/git-menu-github-authorize-visual-studio-lrg.png":::

    Ardından yetkilendirme onayı penceresi açılır. Parolanızı girin ve parolayı **onayla'ya seçin**.

    :::image type="content" source="media/vs-2022/git-menu-github-authorize-confirm-access-sml.png" alt-text="Erişimi onayla iletişim kutusunun ekran görüntüsü." lightbox="media/vs-2022/git-menu-github-authorize-confirm-access-lrg.png":::

    Hesap hesabınızla GitHub bağlantı Visual Studio başarılı bildirimi görüntülenir.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="GitHub hesabınızla bağlantı verdikten sonra Visual Studio.":::

1. Oturum açtıktan sonra Visual Studio kopyala iletişim kutusuna geri dönersiniz;  burada **GitHub'den** aç penceresi erişiminiz olan tüm depoları listeler. İstediğinizi seçin ve ardından Kopyala'ya **seçin**.

    Depo listesi görünmüyorsa deponun konumunu girin ve Kopyala'ya **tıklayın**.

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog-open-from-github-location-sml.png" alt-text="Bir repo seçerek veya GitHub aç penceresinin ekran görüntüsü." lightbox="media/vs-2022/git-menu-clone-repo-dialog-open-from-github-location-lrg.png":::

1. Daha Visual Studio, depoda bir çözüm listesi sunar. Yüklemek istediğiniz çözümü seçin veya Klasör Görünümü'Çözüm Gezgini  [**.**](../ide/use-solution-explorer.md?view=vs-2022&preserve-view=true)

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-folder-view.png" alt-text="Çözüm Gezgini 2022'de Visual Studio görüntüsü.":::

    > [!TIP]
    > Git menüsünden varsayılan Klasör Görünümü'yü Çözüm Görünümü olarak **değiştirebilirsiniz** . Bunu **Ayarlar** >  **Kaynak DenetimiGit** >  **Genel Ayarlar** >  **Otomatik olarak bir Git deposu a açılışında** çözümü yükle'yi seçin.

### <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu açma

Depoyu klonladikten veya oluşturduktan [sonra Visual Studio Git](git-create-repository.md) deposunu algılar ve Git menüsündeki Yerel Depolar listenize ekler. Buradan Git depolarına hızlıca erişin ve bu depolar arasında geçişe geçin.

## <a name="browse-to-and-then-clone-an-azure-devops-repo"></a>Bir veri Azure DevOps kopyalama

1. Visual Studio'yu açın.

1. **Git menüsünden** Depoyu **Kopyala'ya tıklayın**.

    :::image type="content" source="media/vs-2022/git-menu-clone-repository.png" alt-text="Visual Studio'daki Git menüsündeki Tam Depoyu Klonla seçeneğinin ekran görüntüsü.":::

1. Depo **klonla iletişim kutusunun** Depoya **gözat iletişim kutusunda** Depoya **gözat'ı Azure DevOps**.

    :::image type="content" source="../ide/media/vs-2022/browse-repository-azure-devops.png" alt-text="Visual Studio'daki 'Depoyu klonla' iletişim kutusunun 'Depoya gözat' Azure DevOps ekran görüntüsü.":::

1. Bir **Bağlan iletişim Project** iletişim kutusu görüntülenir. İstemleri takip edin ve Azure hesabınızla oturum açın ve Azure DevOps Server dosyaları barındıran sunuculara gidin.

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek için [, Repo oluşturma sayfasını ziyaret](git-create-repository.md) edin.
