---
title: Visual Studio bir depoyu kopyalama
titleSuffix: ''
description: Git veya Azure DevOps kullanarak Visual Studio bir depoyu kopyalayın.
ms.date: 12/08/2021
ms.topic: how-to
author: TerryGLee
ms.author: tglee
ms.manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.openlocfilehash: 9cf37c2130b8df72a8543a696e45b0f186916e94
ms.sourcegitcommit: ba40c6208b2cb27d047fec4fa2c83c6be4f9ee5a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "134463461"
---
# <a name="clone-a-repo-in-visual-studio"></a>Visual Studio bir depoyu kopyalama

Visual Studio, bir GitHub deposunun veya Azure DevOps deposunun doğrudan ıde 'den klonlamanızı kolaylaştırır. ayrıca, GitHub veya Azure DevOps ' de oturum açabilirsiniz. Aşağıdaki adımları uygulayın:

## <a name="clone-a-github-repo-and-sign-in"></a>GitHub depoyu kopyalayın ve oturum açın

1. Visual Studio'yu açın.

1. **Git** menüsünde **depoyu Kopyala**' yı seçin.

    :::image type="content" source="../ide/media/vs-2022/git-menu-clone-repository.png" alt-text="Visual Studio Git menüsünden depoyu Kopyala seçeneğinin ekran görüntüsü.":::

    > [!NOTE]
    > Daha önce **Git** menüsüyle etkileşim kurmadıysa kopya **deposu** yerine **kopya** ' ı görebilirsiniz. Öyleyse, **Kopyala**' yı seçin.
    >
    > **Git** , menü çubuğunda değilse, **Araçlar**  >  **Seçenekler**  >  **kaynak denetimi**  >  **eklentisi seçimi**' ne gidin ve ardından **geçerli kaynak denetimi eklentisi** açılan listesinden **Git** ' i seçin.

1. **Depoyu Kopyala** penceresinde, **BIR GIT deposu URL 'Si girin** bölümünde **Depo konumu kutusuna depo** bilgilerinizi ekleyin.

    Sonra, **yol** bölümünde, yerel kaynak dosyalarınızın varsayılan yolunu kabul edebilir veya farklı bir konuma gidebilirsiniz.

    Ardından, **bir depoya gözatıp** bölümünde **GitHub**' yi seçin.

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog.png" alt-text="GitHub vurgulanmış bir depoyu kopyala iletişim kutusunun ekran görüntüsü.":::

1. **GitHub aç** penceresinde, GitHub hesabı bilgilerinizi doğrulayabilirsiniz veya ekleyebilirsiniz. Bunu yapmak için, açılan menüden **oturum aç** ' ı seçin.

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog-github-account.png" alt-text="GitHub açma penceresinin oturum açma açılır bölümünün ekran görüntüsü.":::

    Visual Studio ilk kez GitHub oturum açıyorsanız, bir **yetkilendirme Visual Studio** bildirimi görüntülenir. İstediğiniz seçenekleri belirleyin ve ardından **GitHub 'ı Yetkilendir**' i seçin.

    :::image type="content" source="media/vs-2022/git-menu-github-authorize-visual-studio-sml.png" alt-text="Yetkilendirme iletişim kutusunun ekran görüntüsü." lightbox="media/vs-2022/git-menu-github-authorize-visual-studio-lrg.png":::

    Ardından, bir yetkilendirme onay penceresi görürsünüz. Parolanızı girin ve **Parolayı Onayla**' yı seçin.

    :::image type="content" source="media/vs-2022/git-menu-github-authorize-confirm-access-sml.png" alt-text="Erişimi Onayla iletişim kutusunun ekran görüntüsü." lightbox="media/vs-2022/git-menu-github-authorize-confirm-access-lrg.png":::

    GitHub hesabınızı Visual Studio bağlantıladıktan sonra, bir başarı bildirimi görüntülenir.

    :::image type="content" source="../ide/media/github-success-signin.png" alt-text="GitHub hesabınızı Visual Studio bağlantıladıktan sonra aldığınız başarı bildiriminin ekran görüntüsü.":::

1. oturum açtıktan sonra, Visual Studio **depoyu kopyala** iletişim kutusuna geri döner; burada **GitHub aç** penceresi, erişiminiz olan tüm depoları listeler. İstediğiniz birini seçin ve ardından **Kopyala**' yı seçin.

    Depo listesi görünmezse, deponuzın konumunu girin ve ardından **Kopyala**' yı seçin.

    :::image type="content" source="media/vs-2022/git-menu-clone-repo-dialog-open-from-github-location-sml.png" alt-text="bir depoyu seçebileceğiniz veya bir tane ekleyebileceğiniz GitHub aç penceresinin ekran görüntüsü." lightbox="media/vs-2022/git-menu-clone-repo-dialog-open-from-github-location-lrg.png":::

1. sonra, Visual Studio depodaki çözüm listesini gösterir. Yüklemek istediğiniz çözümü seçin veya [**Çözüm Gezgini**](../ide/use-solution-explorer.md?view=vs-2022&preserve-view=true) **klasör görünümünü** açın.

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-folder-view.png" alt-text="Visual Studio 2022 ' de Çözüm Gezgini klasör görünümünün ekran görüntüsü.":::

    > [!TIP]
    > Varsayılan klasör görünümünü **Git** menüsünden çözüm görünümü olarak değiştirebilirsiniz. **Ayarlar**  >  **kaynak denetimi**  >  **git genel Ayarlar**  >  **bir git deposu açarken çözümü otomatik olarak yükle** ' yi seçin.

### <a name="open-an-existing-local-repository"></a>Mevcut bir yerel depoyu aç

bir depoyu kopyaladıktan veya [bir tane oluşturduktan](git-create-repository.md)sonra, Visual Studio git deposunu algılar ve git menüsündeki **yerel depolar** listenize ekler. Buradan git depolarınız arasında hızlı bir şekilde erişebilir ve geçiş yapabilirsiniz.

## <a name="browse-to-and-then-clone-an-azure-devops-repo"></a>Azure DevOps depoya gidin ve kopyalayın

1. Visual Studio'yu açın.

1. **Git** menüsünde **depoyu Kopyala**' yı seçin.

    :::image type="content" source="media/vs-2022/git-menu-clone-repository.png" alt-text="Visual Studio Git menüsünde Tam kopya deposu seçeneğinin ekran görüntüsü.":::

1. **Depoyu Kopyala** iletişim kutusunun **bir depoya gözatın** bölümünde **Azure DevOps**' yi seçin.

    :::image type="content" source="../ide/media/vs-2022/browse-repository-azure-devops.png" alt-text="Visual Studio Azure DevOps vurgulanmış olan ' depoyu kopyala ' iletişim kutusunun ' bir depoya gözatatıon ' bölümünün ekran görüntüsü.":::

1. Project iletişim kutusu **Bağlan** görüntülenir. Azure hesabınızda oturum açmak için istemleri izleyin ve ardından aradığınız dosyaları barındıran Azure DevOps Server göz önüne geçin.

## <a name="next-steps"></a>Sonraki adımlar

Yolculuğa devam etmek için [depo oluşturma](git-create-repository.md) sayfasını ziyaret edin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio git deneyimi](../ide/git-with-visual-studio.md)
- [Visual Studio & GitHub: birlikte daha iyi](https://visualstudio.microsoft.com/vs/github/)
- [Öğretici: bir depodan bir proje açın](../get-started/tutorial-open-project-from-repo.md)
- [Visual Studio’da GitHub hesaplarıyla çalışma](../ide/work-with-github-accounts.md)
- [Birden çok kullanıcı hesabıyla çalışma](../ide/work-with-multiple-user-accounts.md)
- [Visual Studio oturum açın](../ide/signing-in-to-visual-studio.md)