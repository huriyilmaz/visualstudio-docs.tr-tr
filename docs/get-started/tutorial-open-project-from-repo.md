---
title: "Öğretici: Visual Studio'da bir repodan proje açma"
description: Git ile git veya Azure DevOps deposunda proje açmayı Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 11/11/2021
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a71c87c29e7ec6a10eeb551bc1989e4621bbe0cb
ms.sourcegitcommit: 00451b7258ab86e259d0fe787669330b61efa8e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2021
ms.locfileid: "132365001"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: Bir repodan proje açma
F Bu öğreticide, Visual Studio bir depoya ilk kez bağlanacak ve ardından bu depodan bir proje açabilirsiniz.

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker range="vs-2022"

## <a name="open-a-project-from-a-github-repo"></a>GitHub bir GitHub açma

Visual Studio, bir projenin bir repodan açılmasını kolaylaştırır. Bunu, Visual Studio veya doğrudan [IDE'nin](visual-studio-ide.md?view=vs-2022&preserve-view=true)içinde Visual Studio.

Aşağıdaki adımları uygulayın:

### <a name="use-the-start-window"></a>Başlangıç penceresini kullanma

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Visual Studio'de Depo Klonla iletişim kutusunun ekran görüntüsü.":::

1. Depo konumunu girin veya yazın ve ardından Kopyala **düğmesini** seçin.

    :::image type="content" source="../ide/media/vs-2022/clone-repository-enter-location.png" alt-text="[Git deposu URL'si girersiniz Visual Studio Depo Klonla iletişim kutusunun ekran görüntüsü.":::

1. Git Kullanıcı Bilgileri iletişim kutusunda kullanıcı oturum açma bilgileri **istenebilirsiniz.** Bilgileri ekleyebilir veya sağladığı varsayılan bilgileri düzenleyebilirsiniz.

    :::image type="content" source="../ide/media/vs-2022/git-user-information-dialog.png" alt-text="2022'de hesap bilgilerinizi girmeniz veya düzenlemeniz gereken Git Kullanıcı Bilgileri Visual Studio ekran görüntüsü.":::

    Bilgileri **genel** .gitconfig dosyanıza eklemek için Kaydet'i seçin. (Veya daha sonra İptal'i seçerek bunu seçebilirsiniz.)

    > [!TIP]
    > Visual Studio'da oturum açma hakkında daha fazla bilgi [**için**](../ide/signing-in-to-visual-studio.md?view=vs-2022&preserve-view=true) Visual Studio bakın. GitHub hesabınızla oturum açma hakkında daha fazla bilgi için GitHub [**hesabıyla**](../ide/work-with-github-accounts.md?view=vs-2022&preserve-view=true) çalışma Visual Studio bakın. Bir güven bildirimi alırsanız ve bu bildirim hakkında daha fazla bilgi almak için Dosya ve klasörler [için güven ayarlarını yapılandırma sayfasına](../ide/reference/trust-settings.md?view=vs-2022&preserve-view=true) bakın.

### <a name="view-files-in-solution-explorer"></a>Dosyaları Çözüm Gezgini

1. Daha Visual Studio, Çözüm Gezgini'de Klasör Görünümü'ne kullanarak **depodan** [**Çözüm Gezgini.**](../ide/use-solution-explorer.md?view=vs-2022&preserve-view=true)

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-folder-view.png" alt-text="Visual Studio 2022'de Çözüm Gezgini Görünümü'nin ekran görüntüsü.":::

    Çözüm Görünümü'ne bir **çözümü .sln** dosyasına çift tıklayarak görüntüebilirsiniz.

    Ya da Görünümleri Değiştir düğmesini **ve** ardından **Program.cs'yi** seçerek bir çözümün kodunu görüntülayabilirsiniz.

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-switch-views.png" alt-text="Git'te 2022'de Çözüm Gezgini Değiştir düğmesi vurgulanmış şekilde, git'te Visual Studio ekran görüntüsü.":::

> [!TIP]
> Varsayılan görünüm Klasör Görünümü olarak ayarlanır. Git menüsünden Çözüm Görünümü olarak **değiştirebilirsiniz.** Kaynak **Ayarlar** Git Genel  >  **Denetimi'Ayarlar** git deposu açılırken çözümü otomatik  >    >  **olarak yükle'yi** seçin.

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Daha önce kopyalanmış bir GitHub açma

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Proje veya çözüm **aç'ı seçin.**

    Visual Studio çözüm veya Dosya Gezgini göz atabilir ve ardından açmak için seçerek bir Dosya Gezgini örneği açılır.

    :::image type="content" source="../ide/media/vs-2022/open-local-project-from-cloned-repo.png" alt-text="Visual Studio 2022'de 'Proje veya çözüm aç' penceresinin ekran görüntüsü.":::

    > [!TIP]
    > Projeyi veya çözümü yakın zamanda açtıysanız Son kullanılanları aç bölümünden **seçerek** hızlı bir şekilde yeniden açın.

    Kodlamaya başlama!

### <a name="use-the-ide"></a>IDE kullanma

Deponun klasörleri ve dosyalarıyla  etkileşim kurmak için Visual Studio IDE'de **Git** menüsünü veya Depo Seç denetimi de kullanabilirsiniz.

Aşağıdaki adımları uygulayın:

#### <a name="to-clone-a-repo-and-open-a-project"></a>Bir repo klonlamak ve bir projeyi açmak için

1. IDE'Visual Studio Git **menüsünü** ve ardından Depoyu **Klonla'ya tıklayın.**

    :::image type="content" source="../ide/media/vs-2022/git-menu-clone-repository.png" alt-text="'Depoyu Kopyala'nın seçili olduğu 2022'Visual Studio Git menüsünün ekran görüntüsü.":::

1. İstemleri takip edin ve arayabilirsiniz dosyaları içeren Git deposuna bağlanabilirsiniz.

#### <a name="to-open-local-folders-and-files"></a>Yerel klasörleri ve dosyaları açmak için

1. IDE'Visual Studio Git menüsünü seçin,  Yerel **Depolar'ı ve** ardından Yerel Depoyu **Aç'ı seçin.**

    :::image type="content" source="../ide/media/vs-2022/git-menu-local-repositories.png" alt-text="2022'de Yerel Depo ve Visual Studio Yerel Depoyu Aç'ın görüntü olduğu 'Git menüsünün ekran görüntüsü.":::

    Alternatif olarak, aynı görevi **Çözüm Gezgini.** Bunu yapmak için Depo **Seç** denetimine  tıklayın, Depoları filtrele kutusunun  yanındaki üç nokta simgesini seçin ve ardından Yerel Depoyu **Aç'ı seçin.**

    :::image type="content" source="../ide/media/vs-2022/select-repository-filter-ellipsis.png" alt-text="Üç nokta simgesinin seçili olduğu ve Yerel Depoyu Aç seçeneğinin görüntü olduğu Depo Seç denetimi ekran görüntüsü.":::

1. İstemleri takip edin ve arayabilirsiniz dosyaları olan Git deposuna bağlanabilirsiniz.

## <a name="browse-to-an-azure-devops-repo"></a>Bir Azure DevOps göz atma

Burada, Azure DevOps kullanarak bir Azure DevOps'a göz atma ve kopyalama Visual Studio.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Visual Studio'da Depo Klonla iletişim kutusunun ekran Azure DevOps.":::

1. Bir **depoya gözat bölümünde Depo'ya** **Azure DevOps.**

    :::image type="content" source="../ide/media/vs-2022/browse-repository-azure-devops.png" alt-text="Visual Studio'de 'Depoyu klonla' iletişim kutusunun 'Depoya gözat' bölümünün Azure DevOps görüntüsü.":::

1. İstemleri takip edin ve Azure DevOps dosyalarını içeren bir veri Azure DevOps kopyasını açın ve ardından projenizi açın.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2019"></a>Visual Studio 2019 ile GitHub bir Visual Studio açma

GitHub kullanarak bir GitHub açma Visual Studio hangi sürüme sahip olduğunuz bağlıdır. Özellikle, Visual Studio 2019 sürüm [**16.8**](/visualstudio/releases/2019/release-notes-history) veya sonraki bir sürümü yüklemiş olursanız, size yeni, daha tam olarak [tümleşik git Visual Studio](../ide/git-with-visual-studio.md) kullanılabilir.

Ancak, hangi sürümü yüklemiş olur olur olun, bir projeyi her zaman GitHub bir Visual Studio.

### <a name="visual-studio-2019-version-168-and-later"></a>Visual Studio 2019 sürüm 16.8 ve sonrası

Visual Studio 2019 sürüm [**16.8**](/visualstudio/releases/2019/release-notes-history) veya sonraki sürümlerde Git'i nasıl kullanabileceğiniz burada açık ve açık bir şekilde açıklandı.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Bir GitHub kopyalama ve ardından projeyi açma

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Depo Klonla iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository.png)

1. Depo konumunu girin veya yazın ve ardından Kopyala'ya **basın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki bir sürüme Git deposu URL'si girmenizi istediğiniz Depoyu Klonla iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Git Kullanıcı Bilgileri iletişim kutusunda kullanıcı oturum açma bilgileri **istenebilirsiniz.** Bilgileri ekleyebilir veya sağladığı varsayılan bilgileri düzenleyebilirsiniz.

   ![2019 sürüm 16.8 ve sonraki bir sürüme hesap bilgilerinizi Visual Studio veya düzenley istediğiniz Git Kullanıcı Bilgileri iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/git-user-information-dialog.png)

    Bilgileri **genel** .gitconfig dosyanıza eklemek için Kaydet'i seçin. (Veya daha sonra İptal'i seçerek bunu seçebilirsiniz.)

    > [!TIP]
    > Visual Studio'da oturum açma hakkında daha fazla bilgi [için](../ide/signing-in-to-visual-studio.md?view=vs-2019&preserve-view=true) Visual Studio bakın. Oturum a açma için GitHub hesabı kullanma hakkında daha fazla bilgi için GitHub [hesabıyla](../ide/work-with-github-accounts.md?view=vs-2019&preserve-view=true) çalışma Visual Studio bakın.

    Ardından Visual Studio otomatik olarak yüklenir ve çözüm depodan açılır.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Çözüm Gezgini Git'te açık olan projenin ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer.png )

1. Depoda birden çok çözüm varsa bunları Çözüm Gezgini. Görünüm değiştir düğmesini seçerek çözüm  listesini görüntü Çözüm Gezgini.

   ![Çözüm Gezgini 2019 sürüm 16.8 ve sonraki sürümlerde Visual Studio Görünüm değiştir düğmesi vurgulanmış şekilde Git'te açık olan bir projenin ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Çözüm Gezgini, klasör görünümü'ne kök klasörü açma **veya** açılacak bir çözüm dosyası seçme seçeneği sunar.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki bir sürümde Görünümleri Değiştir düğmesini seçtikten sonra, Çözüm Gezgini'da açık olan Git'te .sln dosyasının ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Görünümü değiştirmek için Görünümleri Değiştir **düğmesini yeniden** seçin.

    > [!TIP]
    > Depo klonlamak ve bir projeyi açmak için Visual Studio IDE'de **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Git menüsünün ekran görüntüsü.](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Daha önce kopyalanmış bir GitHub açma

1. 2019 Visual Studio 16.8 veya sonraki bir sürümü açın.

1. Başlangıç penceresinde Proje veya çözüm **aç'ı seçin.**

    Visual Studio çözüm veya Dosya Gezgini göz atabilir ve ardından açmak için seçerek bir Dosya Gezgini örneği açılır.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde 'Proje veya çözüm aç' penceresinin ekran görüntüsü.](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Projeyi veya çözümü yakın zamanda açtıysanız Son kullanılanları aç bölümünden **seçerek** hızlı bir şekilde yeniden açın.

    > [!TIP]
    > Daha önce kopyalanmış bir depodan yerel Visual Studio ve dosyaları açmak için IDE'de **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Yerel Depolar seçeneği genişletilmiş git menüsünün ekran görüntüsü.](../ide/media/vs-2019/git-menu-local-repositories.png)

    Kodlamaya başlama!

### <a name="visual-studio-2019-version-167-and-earlier"></a>Visual Studio 2019 sürüm 16.7 ve önceki sürümler

Visual Studio 2019 sürüm [**16.7**](/visualstudio/releases/2019/release-notes-history) veya önceki bir sürümde Git'i nasıl kullanabileceğiniz burada açıklandı.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Bir GitHub kopyalama ve sonra bir proje açma

1. 2019 Visual Studio 16.7 veya önceki bir sürümü açın.

1. Başlangıç penceresinde Kopyala'ya **tıklayın veya kodu kontrol edin.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Yeni proje oluştur' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından Kopyala'ya **basın.**

   ![2019 sürüm 16.7 ve Visual Studio 'Kodu kopyala veya iade edin' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio, projeyi repodan açar.

1. Kullanılabilir bir çözüm dosyanız varsa, bu dosya "Çözümler ve Klasörler" açılır menüsünde görünür. Seçin ve Visual Studio açılır.

   ![2019 Çözüm Gezgini 16.7 ve Visual Studio açılan listesinin ekran görüntüsü.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Bir çözüm dosyanız (özel olarak, bir .sln dosyası) yoksa açılır menüde "Çözüm Bulunamadı" yazıyor. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

    Kodlamaya başlama!

## <a name="browse-to-an-azure-devops-repo-with-visual-studio-2019"></a>Visual Studio 2019 ile Azure DevOps bir Visual Studio göz atma

Azure DevOps 2019'da Azure DevOps depoya göz atarak Visual Studio gördüğünüz sürüme bağlıdır. Özellikle, [**sürüm 16.8**](/visualstudio/releases/2019/release-notes-history) veya sonraki bir sürümü yüklemişsanız, kullanıcı arabirimini Visual Studio'daki Visual Studio'de yeni, tam olarak tümleştirilmiş [bir Git](../ide/git-with-visual-studio.md) deneyimine uyum sağlayacak şekilde Visual Studio.

Ancak, hangi sürümü yüklemiş olur olun, her zaman bir Azure DevOps ile Visual Studio.

### <a name="visual-studio-2019-version-168-and-later"></a>Visual Studio 2019 sürüm 16.8 ve sonrası

1. 2019 Visual Studio [**16.8 veya sonraki bir sürümü**](/visualstudio/releases/2019/release-notes-history) açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın.**

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde depo kopyalama iletişim kutusunun ekran Azure DevOps.](../ide/media/vs-2019/clone-repository.png)

1. Bir **depoya gözat bölümünde Depo'ya** Azure DevOps.

    ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde 'Bağlan Project' iletişim kutusunun 'Depoya gözat' bölümünün ekran görüntüsü.](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Bağlan iletişim Project** kutusunda, bağlanmak istediğiniz repo'ya tıklayın ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerden oluşturulan 'Bağlan bir Project' iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > Bağlanmak için önceden doldurulmuş bir repos listesi görmüyorsanız,  sunucu URL'si girmek için Azure DevOps Server Ekle'yi seçin. (Alternatif olarak, mevcut bir sunucu ekleme veya bir Azure DevOps Server hesabı oluşturma bağlantılarını içeren bir "Sunucu Azure DevOps" istemini de görebilirsiniz.)

   Ardından Visual Studio ve **Çözüm Gezgini** gösteren bir dosya açılır.

1. Takım Gezgini **eylemlerini** görüntülemek için Azure DevOps seçin.

      ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerden oluşturulan 'Takım Gezgini' iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="visual-studio-2019-version-167-and-earlier"></a>Visual Studio 2019 sürüm 16.7 ve önceki sürümler

1. 2019 Visual Studio [**16.7 veya önceki bir sürümü**](/visualstudio/releases/2019/release-notes-history) açın.

1. Başlangıç penceresinde Kopyala'ya **tıklayın veya kodu kontrol edin.**

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde 'Yeni proje oluştur' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Bir **depoya gözat bölümünde Depo'ya** Azure DevOps.

   ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde liste Azure DevOps 'Depoya göz at' bölümünün yer alan 'Kodu kopyala veya iade edin' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görüyorsanız, hesabınızla oturum açın.

1. Bir **Bağlan iletişim Project** kutusunda, bağlanmak istediğiniz repo'ya tıklayın ve ardından Kopyala'ya **tıklayın.**

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerden oluşturulan 'Bağlan bir Project' iletişim kutusunun ekran görüntüsü.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda ne gördüğünüz, erişiminiz olan Azure DevOps depolara bağlıdır.

   Visual Studio, **Takım Gezgini** tamamlandığında bir bildirim görüntülenir.

     ![Kopyalama tamamlandıktan sonra Takım Gezgini 2019 Visual Studio 16.7 ve önceki sürümlerindeki uygulama penceresinin ekran görüntüsü.](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için Klasör Görünümünü **Göster bağlantısını** seçin.

     ![Kopyalama tamamlandıktan sonra Takım Gezgini 2019 Visual Studio 16.7 ve önceki sürümlerindeki Çözümler bölümünün ekran görüntüsü.](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **,** Çözüm Gezgini.

1. Açılacak **bir çözüm dosyası** (özel olarak bir .sln dosyası) aramak için Çözümler ve Klasörler bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16.7 ve önceki sürümlerde Takım Gezgini 'Çözümler ve Klasörler' bildiriminin ekran görüntüsü.](./media/open-proj-repo-solutions-folders.png)

   Bir çözüm dosyanız yoksa, 'Çözüm Bulunamadı' iletisi görüntülenir. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2017"></a>2017'de GitHub bir Visual Studio açma

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Kaynak Denetiminden **Dosya** >  > **Aç Aç'ı seçin.**

   Takım Gezgini **- Bağlan** bölmesi açılır.

    ![Takım Gezgini IDE içindeki Visual Studio penceresi](./media/open-proj-repo-team-explorer.png)

1. Yerel **Git Depoları bölümünde Kopyala'ya** **tıklayın.**

    ![Yerel Git Depoları bölümünden Kopyala'ya tıklayın](./media/open-proj-repo-local-git-repo-clone.png)

1. * yazarak kopyalanan **Git** depolarının URL'sini girin _ kutusuna depo için URL yazın veya yapıştırın ve _*Enter** tuşuna basın. (Oturum açma istemiyle oturum GitHub, oturum açın.)

   Bu Visual Studio sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. Çözümler listesini görüntülemek için *yukarıdaki Çözümler ve Klasörler'e tıklayın iletisi görüntülenir.* Çözümler **ve Klasörler'i seçin.**

   ![Dosyadan "Çözümler ve Klasörler" Çözüm Gezgini](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, bu dosya "Çözümler ve Klasörler" açılır menüsünde görünür. Seçin ve Visual Studio açılır.

   ![Açılır listeden neleri açmak Çözüm Gezgini seçin.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Bir çözüm dosyanız (özel olarak, bir .sln dosyası) yoksa, açılır menüde "Çözüm Bulunamadı" olur. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirme

Önceki bölümde tamamlamış olduğunu işi kontrol etmek için aşağıdaki animasyonu görüntüebilirsiniz.

   ![Visual Studio 2017'GitHub bir GitHub açma animasyonu.](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-with-visual-studio-2017"></a>2017'de Azure DevOps bir Visual Studio açma

1. Visual Studio 2017'yi açın.

1. Üst menü çubuğundan Kaynak Denetiminden **Dosya** >  > **Aç Aç'ı seçin.**

   Takım Gezgini **- Bağlan** bölmesi açılır.

    ![Takım Gezgini IDE içindeki Visual Studio penceresi.](./media/open-proj-repo-team-explorer.png)

1. Azure DevOps Azure DevOps:

      - Barındırılan **Hizmet Sağlayıcıları bölümünde** **Bağlan... öğesini seçin.**

        ![Visual Studio IDE içindeki Takım Gezgini penceresinin Barındırılan Hizmet Sağlayıcıları bölümü.](./media/open-proj-repo-azure-devops.png)

      - Bağlantıları **Yönet açılan** listesinde Bir **Bağlan... seçeneğini Project.**

        ![Visual Studio IDE içindeki Takım Gezgini penceresinin Bağlantıları Visual Studio.](./media/open-proj-repo-azuredevops-manage-connections.png)

1. Bir **Bağlan iletişim Project** kutusunda, bağlanmak istediğiniz repo'ya tıklayın ve ardından Kopyala'ya **tıklayın.**

      ![Dosyadan Bağlan 'Project' iletişim kutusu Visual Studio.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > Liste kutusunda ne gördüğünüz, erişiminiz olan Azure DevOps depolara bağlıdır.

1. Bu Visual Studio sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. Çözümler listesini görüntülemek için *yukarıdaki Çözümler ve Klasörler'e tıklayın iletisi görüntülenir.* Çözümler **ve Klasörler'i seçin.**

      ![Takım Gezgini'daki "Çözümler ve Klasörler" Visual Studio.](./media/open-proj-repo-solutions-folders.png)

   "Çözümler ve Klasörler" açılır menüsünde bir çözüm dosyası (özel olarak bir .sln dosyası) görüntülenir. Seçin ve Visual Studio açılır.

   Bir çözüm dosyanız yoksa, açılır menüde "Çözüm Bulunamadı" ifadesini görünür. Ancak, klasör menüsünden herhangi bir dosyaya çift tıklar ve dosyayı kod düzenleyicisinde Visual Studio açabilirsiniz.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki dile özgü öğreticilerden herhangi birini öğrenmekten bağımsız olarak:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript,** **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="<=vs-2019"

- [Visual Studio git deneyimi](../ide/git-with-visual-studio.md)
- [Git ve Takım Gezgini yan yana karşılaştırın](../ide/git-team-explorer-feature-comparison.md)
- [Microsoft Learn: Visual Studio Git ve GitHub kullanmaya başlama](/learn/modules/visual-studio-github-push/)
- [Microsoft Learn: Azure DevOps kullanmaya başlama](/learn/modules/get-started-with-devops/)
- [Azure DevOps Services: Azure Repos ve Visual Studio kullanmaya başlayın](/azure/devops/repos/git/gitquickstart/)

::: moniker-end

::: moniker range="vs-2022"

[sürüm denetimi belgelerini Visual Studio](../version-control/index.yml)

::: moniker-end