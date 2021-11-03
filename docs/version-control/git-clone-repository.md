---
title: Visual Studio'de bir Visual Studio
titleSuffix: ''
description: Git veya Visual Studio kullanarak bir depo Azure DevOps.
ms.date: 10/29/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 6f8b7bef8b9c8c94d505e3d3b2dfbcbf45a0ac80
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131130535"
---
# <a name="clone-a-repo-in-visual-studio"></a>Visual Studio'de bir Visual Studio

Visual Studio, bir GitHub veya Azure DevOps IDE'den kopyalamayı kolaylaştırır. Ayrıca, bunu yaparken GitHub veya Azure DevOps oturum açma. Aşağıdaki adımları uygulayın:

## <a name="clone-a-github-repo-and-sign-in"></a>Bir GitHub kopyalama ve oturum açma

1. Visual Studio'yu açın.

1. Git **menüsünden** Depoyu **Klonla'ya tıklayın.**

    :::image type="content" source="../ide/media/vs-2022/git-menu-clone-repository.png" alt-text="Visual Studio'daki Git menüsündeki Depoyu Kopyala seçeneğinin ekran Visual Studio.":::

    > [!NOTE]
    > Git menüsüyle daha önce  etkileşim kurmadıysanız, Depoyu **Klonla** yerine **Klonla seçeneğini kullanabilirsiniz.** Öyleyse **Kopyala'ya seçin.**

1. Depoyu **klonla penceresindeki** **Git deposu URL'si** girin bölümünün altında depo bilgilerinizi Depo konumu **kutusuna** ekleyin.

    Ardından, **Yol bölümünde** yerel kaynak dosyalarınızın varsayılan yolunu kabul etme veya farklı bir konuma göz atabilirsiniz.

    Ardından, Bir **depoya göz atma bölümünde** GitHub. 

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog.png" alt-text="Depo Klonla iletişim kutusunun ekran görüntüsü, GitHub vurgulanmış.":::

1. Oturum **açma GitHub** penceresinde, hesap GitHub doğrular veya eklersiniz. Bunu yapmak için açılan **menüden** Oturum aç'ı seçin.

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog-github-account.png" alt-text="Oturum aç penceresinin Oturum aç açılan bölümünün ekran GitHub görüntüsü.":::

    İlk kez GitHub Visual Studio oturum Visual Studio **bildirimi** görüntülenir. İstediğiniz seçenekleri belirleyin ve ardından **Github'ı yetkilendir'i seçin.**

    :::image type="content" source="media/vs-2022/git-menu-github-authorize-visual-studio-sml.png" alt-text="Yetkilendirme iletişim kutusunun ekran görüntüsü." lightbox="media/vs-2022/git-menu-github-authorize-visual-studio-lrg.png":::

    Ardından yetkilendirme onayı penceresi açılır. Parolanızı girin ve ardından Parolayı **onayla'ya basın.**

    :::image type="content" source="media/vs-2022/git-menu-github-authorize-confirm-access-sml.png" alt-text="Erişimi onayla iletişim kutusunun ekran görüntüsü." lightbox="media/vs-2022/git-menu-github-authorize-confirm-access-lrg.png":::

    GitHub Visual Studio başarı bildirimi görüntülenir.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="GitHub hesabınızla bağlantı verdikten sonra Visual Studio.":::

1. Oturum açtıktan sonra Visual Studio Bir  depoyu klonla iletişim kutusuna geri dönersiniz; burada **GitHub'den** aç penceresi erişiminiz olan tüm depoları listeler. İstediğinizi seçin ve ardından **Kopyala'ya seçin.**

    Depo listesi görünmüyorsa deponun konumunu girin ve Kopyala'ya **tıklayın.**

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog-open-from-github-location-sml.png" alt-text="Bir repo seçerek veya GitHub aç penceresinin ekran görüntüsü." lightbox="media/vs-2022/git-menu-clone-repo-dialog-open-from-github-location-lrg.png":::

1. Daha Visual Studio, depoda bir çözüm listesi sunar. Yüklemek istediğiniz çözümü seçin veya klasör görünümünde [](../ide/use-solution-explorer.md?view=vs-2022&preserve-view=true) **Klasör Görünümü'Çözüm Gezgini.**

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-folder-view.png" alt-text="Visual Studio 2022'de Çözüm Gezgini Görünümü'nin ekran görüntüsü.":::

    > [!TIP]
    > Git menüsünden varsayılan Klasör Görünümü'yü Çözüm Görünümü olarak **değiştirebilirsiniz.** Kaynak **Ayarlar** Git Genel  >    >  **Denetimi'Ayarlar** Git deposu açılırken  >  **çözümü otomatik olarak yükle'yi** seçin.

Tebrikler! GitHub'da başarıyla oturum GitHub kullanarak Visual Studio.

## <a name="browse-to-and-then-clone-an-azure-devops-repo"></a>Bir veri Azure DevOps kopyalama

1. Visual Studio'yu açın.

1. Git **menüsünden** Depoyu **Klonla'ya tıklayın.**

    :::image type="content" source="media/vs-2022/git-menu-clone-repository.png" alt-text="Visual Studio'daki Git menüsündeki Tam Depoyu Klonla seçeneğinin ekran Visual Studio.":::

1. Depoyu **klonla iletişim** kutusunun **Depoya gözat iletişim kutusunda** Depoya gözat'ı **Azure DevOps.**

    :::image type="content" source="../ide/media/vs-2022/browse-repository-azure-devops.png" alt-text="Visual Studio'daki 'Depoyu klonla' iletişim kutusunun 'Depoya gözat' Azure DevOps ekran görüntüsü.":::

1. Bir **Bağlan iletişim Project** iletişim kutusu görüntülenir. İstemleri takip edin ve Azure hesabınızla oturum açın ve Azure DevOps Server dosyaları barındıran sunuculara gidin.

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğunuza devam etmek [için, Repo oluşturma sayfasını ziyaret](git-create-repository.md) edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Git deneyimi](../ide/git-with-visual-studio.md)
- [Öğretici: Bir repodan proje açma](../get-started/tutorial-open-project-from-repo.md)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Birden çok kullanıcı hesabıyla çalışma](../ide/work-with-multiple-user-accounts.md)
- [Visual Studio’da oturum açma](../ide/signing-in-to-visual-studio.md)