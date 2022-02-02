---
title: "Öğretici: Visual Studio'de bir repodan proje açma"
description: Git'te veya Azure DevOps kullanarak Azure DevOps depoda proje açmayı Visual Studio.
ms.custom: vs-acquisition, get-started
ms.date: 01/31/2022
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
ms.openlocfilehash: eac23743e69f9f5fc0df3ba4e46437f2536abe7f
ms.sourcegitcommit: 3766c051f9a8b35106b16f751db7fecde0b92254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "137951669"
---
# <a name="tutorial-open-a-project-from-a-repo"></a>Öğretici: Bir repodan proje açma

Bu öğreticide, Visual Studio bir depoya ilk kez bağlanmak, bunu klonlamak ve ardından bundan bir proje açmak için Visual Studio kullanılır.

Daha önce yüklememiş Visual Studio indirmeler [Visual Studio](https://visualstudio.microsoft.com/downloads) sayfasına gidip ücretsiz yükleyin.

::: moniker range="vs-2022"

## <a name="open-a-project-from-a-github-repo"></a>GitHub GitHub açma

Visual Studio, bir projenin bir repodan açılmasını kolaylaştırır. Bunu, Visual Studio veya doğrudan [IDE'nin içinde Visual Studio.](visual-studio-ide.md?view=vs-2022&preserve-view=true)

Aşağıdaki adımları uygulayın:

### <a name="use-the-start-window"></a>Başlangıç penceresini kullanma

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın**.

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Visual Studio'de Depo Klonla iletişim kutusunun ekran görüntüsü.":::

1. Depo konumunu girin veya yazın ve ardından Kopyala **düğmesini** seçin.

    :::image type="content" source="../ide/media/vs-2022/clone-repository-enter-location.png" alt-text="Git deposu URL'sini girebilirsiniz Visual Studio Depo Klonla iletişim kutusunun ekran görüntüsü.":::

1. Git Kullanıcı Bilgileri iletişim kutusunda kullanıcı oturum açma bilgileri **istenebilirsiniz** . Bilgileri ekleyebilir veya sağladığı varsayılan bilgileri düzenleyebilirsiniz.

    :::image type="content" source="../ide/media/vs-2022/git-user-information-dialog.png" alt-text="2022'de hesap bilgilerinizi girmeniz veya düzenlemeniz gereken Git Kullanıcı Bilgileri Visual Studio ekran görüntüsü.":::

    Bilgileri **genel** .gitconfig dosyanıza eklemek için Kaydet'i seçin. (Veya bilgileri daha **sonra** eklemek için İptal'i de seçebilirsiniz.)

    > [!TIP]
    > Visual Studio'da oturum açma hakkında daha fazla bilgi için [**Visual Studio bakın.**](../ide/signing-in-to-visual-studio.md?view=vs-2022&preserve-view=true) GitHub hesabınızla oturum açma hakkında daha fazla bilgi için GitHub [**hesabıyla çalışma Visual Studio**](../ide/work-with-github-accounts.md?view=vs-2022&preserve-view=true) bakın. Bir güven bildirimi alırsanız ve bu bildirim hakkında daha fazla bilgi almak için Dosya ve klasörler [için güven ayarlarını yapılandırma sayfasına](../ide/reference/trust-settings.md?view=vs-2022&preserve-view=true) bakın.

### <a name="view-files-in-solution-explorer"></a>Dosyaları Çözüm Gezgini

1. Ardından Visual Studio' klasöründeki Klasör Görünümünü kullanarak **depodan Çözüm Gezgini**[**.**](../ide/use-solution-explorer.md?view=vs-2022&preserve-view=true)

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-folder-view.png" alt-text="Visual Studio 2022'de Çözüm Gezgini Görünümü'nin ekran görüntüsü.":::

    Çözüm Görünümü'ne bir **çözümü .** sln dosyasına çift tıklayarak görüntüebilirsiniz.

    Ya da Görünümleri Değiştir düğmesini **ve** ardından **Program.cs'yi** seçerek bir çözümün kodunu görüntülayabilirsiniz.

    :::image type="content" source="../ide/media/vs-2022/git-solution-explorer-switch-views.png" alt-text="Çözüm Gezgini 2022'de Görünüm Değiştir düğmesi vurgulanmış şekilde Git'te Visual Studio ekran görüntüsü.":::

> [!TIP]
> Varsayılan görünüm Klasör Görünümü olarak ayarlanır. Git menüsünden Çözüm Görünümü olarak **değiştirebilirsiniz** . Bunu **Ayarlar** >  Git **deposu a0 Ayarlar** >  **Otomatik** olarak çözümü yüklemek için Ayarlar **Source ControlGit** >  Global'i seçin.

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Daha önce kopyalanmış bir GitHub açma

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Proje veya çözüm **aç'ı seçin**.

    Visual Studio çözüm veya Dosya Gezgini göz atarak açmak için seçerek bir Dosya Gezgini örneği açılır.

    :::image type="content" source="../ide/media/vs-2022/open-local-project-from-cloned-repo.png" alt-text="Visual Studio 2022'de 'Proje veya çözüm aç' penceresinin ekran görüntüsü.":::

    > [!TIP]
    > Projeyi veya çözümü yakın zamanda açtıysanız Son kullanılanları aç bölümünden **seçerek hızlı** bir şekilde yeniden açın.

    Kodlamaya başlama!

### <a name="use-the-ide"></a>IDE kullanma

Deponun klasörleri ve dosyalarıyla etkileşim kurmak için  Visual Studio IDE'de **Git** menüsünü veya Depo Seç denetimi de kullanabilirsiniz.

Aşağıdaki adımları uygulayın:

#### <a name="to-clone-a-repo-and-open-a-project"></a>Bir repo klonlamak ve bir projeyi açmak için

1. IDE'Visual Studio **Git** menüsünü ve ardından Depoyu **Klonla'ya tıklayın**.

    :::image type="content" source="../ide/media/vs-2022/git-menu-clone-repository.png" alt-text="Visual Studio 2022'de Depoyu Kopyala'nın seçili olduğu Git menüsünün ekran görüntüsü.":::

1. İstemleri takip edin ve arayabilirsiniz dosyaları içeren Git deposuna bağlanabilirsiniz.

#### <a name="to-open-local-folders-and-files"></a>Yerel klasörleri ve dosyaları açmak için

1. IDE'Visual Studio Git menüsünü seçin **, Yerel** **Depolar'ı ve** ardından Yerel Depoyu **Aç'ı seçin**.

    :::image type="content" source="../ide/media/vs-2022/git-menu-local-repositories.png" alt-text="Visual Studio 2022'de Yerel Depo ve Yerel Depoyu Aç'ın görüntü olduğu Git menüsünün ekran görüntüsü.":::

    Alternatif olarak, aynı görevi diğer görevlerden **Çözüm Gezgini**. Bunu yapmak için Depo **Seç** denetimi seçin, Depoları filtrele kutusunun  yanındaki üç nokta simgesini seçin ve ardından Yerel Depoyu  **Aç'ı seçin**.

    :::image type="content" source="../ide/media/vs-2022/select-repository-filter-ellipsis.png" alt-text="Üç nokta simgesinin seçili olduğu ve Yerel Depoyu Aç seçeneğinin gösterdiği Depo Seç denetimi ekran görüntüsü.":::

1. İstemleri takip edin ve arayabilirsiniz dosyaları olan Git deposuna bağlanabilirsiniz.

## <a name="browse-to-an-azure-devops-repo"></a>Bir Azure DevOps göz atma

Bir Azure DevOps kullanarak bir Azure DevOps'a göz atma ve kopyalama Visual Studio.

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın**.

    :::image type="content" source="../ide/media/vs-2022/clone-repository.png" alt-text="Visual Studio'de Depo Klonla iletişim kutusunun ekran Azure DevOps.":::

1. Depoya **gözat bölümünde Depo'ya** **Azure DevOps**.

    :::image type="content" source="../ide/media/vs-2022/browse-repository-azure-devops.png" alt-text="Visual Studio'daki 'Depoyu klonla' iletişim kutusunun 'Depoya gözat' Visual Studio Azure DevOps görüntüsü.":::

1. İstemleri takip edin Azure DevOps dosyalarını içeren bir veri Azure DevOps bir kopyasını açın ve ardından projenizi açın.

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2019"></a>Visual Studio 2019 ile GitHub bir Visual Studio açma

Visual Studio kullanarak bir GitHub bir Visual Studio açma, sahip olduğunuz sürüme bağlıdır. Özellikle, Visual Studio 2019 sürüm [**16.8**](/visualstudio/releases/2019/release-notes-history) veya sonraki bir sürümü yüklemiş olursanız, Visual Studio'de yeni ve daha tam olarak [tümleştirilmiş git](../version-control/git-with-visual-studio.md) Visual Studio kullanılabilir.

Ancak, hangi sürümü yüklemiş olur olur olun, bir projeyi her zaman GitHub bir Visual Studio.

### <a name="visual-studio-2019-version-168-and-later"></a>Visual Studio 2019 sürüm 16.8 ve sonrası

Visual Studio 2019 sürüm [**16.8 veya sonraki sürümlerde Git'i nasıl kullanabileceğiniz burada**](/visualstudio/releases/2019/release-notes-history) açık ve açık bir şekilde açıklandı.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>Bir GitHub kopyalama ve sonra bir proje açma

1. 2019 Visual Studio açın.

1. Başlangıç penceresinde Depoyu **klonla'ya tıklayın**.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Depo Klonla iletişim kutusunun ekran görüntüsü](../ide/media/vs-2019/clone-repository.png)

1. Depo konumunu girin veya yazın ve Ardından Kopyala'ya **basın**.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki bir sürüme Git deposu URL'si girmenizi istediğiniz Depoyu Klonla iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/clone-repository-enter-location.png)

1. Git Kullanıcı Bilgileri iletişim kutusunda kullanıcı oturum açma bilgileri **istenebilirsiniz** . Bilgileri ekleyebilir veya sağladığı varsayılan bilgileri düzenleyebilirsiniz.

   ![2019 sürüm 16.8 ve sonraki bir sürüme hesap bilgilerinizi Visual Studio veya düzenley istediğiniz Git Kullanıcı Bilgileri iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/git-user-information-dialog.png)

    Bilgileri **genel** .gitconfig dosyanıza eklemek için Kaydet'i seçin. (Veya bilgileri daha **sonra** kaydetmek için İptal'i de seçebilirsiniz.)

    > [!TIP]
    > Visual Studio'da oturum açma hakkında daha fazla bilgi için [Visual Studio bakın.](../ide/signing-in-to-visual-studio.md?view=vs-2019&preserve-view=true) Oturum açma için GitHub hesabınızla çalışma hakkında daha fazla bilgi için GitHub [hesabıyla çalışma Visual Studio](../ide/work-with-github-accounts.md?view=vs-2019&preserve-view=true) bakın.

    Ardından Visual Studio otomatik olarak yüklenir ve çözüm depodan açılır.

   ![Çözüm Gezgini 2019 sürüm 16.8 ve Visual Studio Git'te açık olan projenin ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer.png )

1. Depoda birden çok çözüm varsa Çözüm Gezgini görüntüler. Çözümlerin liste görünümü için Görünüm Değiştir **düğmesini seçin** ve Çözüm Gezgini.

   ![Çözüm Gezgini 2019 sürüm 16.8 ve sonraki sürümlerde Görünümleri Değiştir düğmesi Visual Studio Git'te açık olan bir projenin ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer-switch-views.png)

   Çözüm Gezgini, klasör görünümü'ne kök klasörü açma **veya** açılacak bir çözüm dosyası seçme seçeneği sunar.

   ![Visual Studio Çözüm Gezgini 2019 sürüm 16.8 ve sonraki bir sürümde Görünümleri Değiştir düğmesini seçtikten sonra Git'te açık olan .sln dosyasının ekran görüntüsü.](../ide/media/vs-2019/git-solution-explorer-view-solution.png)

    Görünümü değiştirmek için Görünümleri Değiştir **düğmesini yeniden** seçin.

    > [!TIP]
    > Depo klonlamak **ve bir** projeyi açmak için Visual Studio IDE'de Git menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Git menüsünün ekran görüntüsü.](../ide/media/vs-2019/git-menu-clone-create-git-repository.png)

#### <a name="open-a-project-locally-from-a-previously-cloned-github-repo"></a>Daha önce kopyalanmış bir GitHub açma

1. 2019 Visual Studio 16.8 veya sonraki bir sürümü açın.

1. Başlangıç penceresinde Proje veya çözüm **aç'ı seçin**.

    Visual Studio çözüm veya Dosya Gezgini göz atarak açmak için seçerek bir Dosya Gezgini örneği açılır.

   ![Visual Studio 2019 sürüm 16.8 ve sonraki bir sürümde 'Proje veya çözüm aç' penceresinin ekran görüntüsü.](../ide/media/vs-2019/open-local-project-from-cloned-repo.png)

    Projeyi veya çözümü yakın zamanda açtıysanız Son kullanılanları aç bölümünden **seçerek hızlı** bir şekilde yeniden açın.

    > [!TIP]
    > Daha önce kopyalanmış bir depodan yerel Visual Studio ve dosyaları açmak için IDE'de **Git** menüsünü de kullanabilirsiniz.
    >
    > ![Visual Studio 2019 sürüm 16.8 ve sonraki sürümlerde Yerel Depolar seçeneği genişletilmiş Git menüsünün ekran görüntüsü.](../ide/media/vs-2019/git-menu-local-repositories.png)

    Kodlamaya başlama!

### <a name="visual-studio-2019-version-167-and-earlier"></a>Visual Studio 2019 sürüm 16.7 ve önceki sürümler

işte Visual Studio 2019 [**sürüm 16,7**](/visualstudio/releases/2019/release-notes-history) veya önceki sürümlerde Git 'i kullanma.

#### <a name="clone-a-github-repo-and-then-open-a-project"></a>GitHub depoyu kopyalayın ve ardından bir proje açın

1. Visual Studio 2019 sürüm 16,7 veya öncesini açın.

1. Başlat penceresinde, **Kopyala veya kullanıma alma kodu**' nu seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' yeni proje oluştur ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. Depo konumunu girin veya yazın ve ardından **Kopyala**' yı seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' kopya veya kullanıma alma kodu ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Visual Studio projeden projeyi açar.

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. bunu seçin ve çözümünüzü Visual Studio açar.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Çözüm Gezgini açılan listesinin ekran görüntüsü.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsü "hiçbir çözüm bulunamadı" ifadesini ifade etmez. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

    Kodlamaya başlayın!

## <a name="browse-to-an-azure-devops-repo-with-visual-studio-2019"></a>Visual Studio 2019 ile Azure DevOps depoya gidin

Visual Studio 2019 kullanarak bir Azure DevOps deposuna gözatıp klonladığınızda gördüğünüz özellikler, sahip olduğunuz sürüme bağlıdır. özellikle, sürüm [**16,8**](/visualstudio/releases/2019/release-notes-history) veya sonraki bir sürümü yüklediyseniz, kullanıcı arabirimini Visual Studio Visual Studio yeni, daha fazla tümleşik [Git deneyimine](../version-control/git-with-visual-studio.md) uyum sağlayacak şekilde değiştirdik.

ancak hangi sürümü yüklediğinizden bağımsız olarak, Visual Studio Azure DevOps depoya her zaman gidebilirsiniz ve kopyalayabilirsiniz.

### <a name="visual-studio-2019-version-168-and-later"></a>Visual Studio 2019 sürüm 16,8 ve üzeri

1. Visual Studio 2019 [**sürüm 16,8**](/visualstudio/releases/2019/release-notes-history) veya üstünü açın.

1. Başlangıç penceresinde **depoyu Kopyala**' yı seçin.

   ![Azure DevOps için Visual Studio 2019 sürüm 16,8 ve üzeri bir depoyu kopyala iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/clone-repository.png)

1. **Bir depoya gözatıp** bölümünde **Azure DevOps**' yi seçin.

    ![Visual Studio 2019 sürüm 16,8 ve sonrasında ' Bağlan Project ' iletişim kutusunun ' bir depoya gözatatıon ' bölümünün ekran görüntüsü.](../ide/media/vs-2019/browse-repository-azure-devops.png)

1. Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,8 ve sonrasında oluşturulan ' Bağlan Project ' iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/connect-project-azure-devops.png)

      > [!TIP]
      > bağlanılacak olan depoların önceden doldurulmuş bir listesini görmüyorsanız sunucu URL 'si girmek için **Azure DevOps Server ekle** ' yi seçin. (alternatif olarak, var olan bir Azure DevOps Server ekleme veya Azure DevOps hesabı oluşturma bağlantıları içeren "sunucu bulunamadı" istemi görebilirsiniz.)

   sonra, Visual Studio klasörleri ve dosyaları gösteren **Çözüm Gezgini** açar.

1. Azure DevOps eylemlerini görüntülemek için **Takım Gezgini** sekmesini seçin.

      ![Visual Studio 2019 sürüm 16,8 ve sonrasında oluşturulan ' Takım Gezgini ' iletişim kutusunun ekran görüntüsü.](../ide/media/vs-2019/team-explorer-azure-devops.png)

#### <a name="visual-studio-2019-version-167-and-earlier"></a>Visual Studio 2019 sürüm 16,7 ve öncesi

1. Visual Studio 2019 [**sürüm 16,7**](/visualstudio/releases/2019/release-notes-history) veya öncesini açın.

1. Başlat penceresinde, **Kopyala veya kullanıma alma kodu**' nu seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde ' yeni proje oluştur ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-dark.png)

1. **Bir depoya gözatıp** bölümünde **Azure DevOps**' yi seçin.

   ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Azure DevOps listeleyen ' bir depoya göz at ' bölümü ile ' kopyalama veya kullanıma alma kodu ' penceresinin ekran görüntüsü.](../get-started/media/vs-2019/clone-checkout-code-git-repo-dark.png)

   Oturum açma penceresi görürseniz hesabınızda oturum açın.

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio 2019 sürüm 16,7 ve öncesinden oluşturulan ' Bağlan Project ' iletişim kutusunun ekran görüntüsü.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > liste kutusunda gördükleriniz, erişiminizin olduğu Azure DevOps depolarına bağlıdır.

   Visual Studio **Takım Gezgini** açılır ve kopya tamamlandığında bir bildirim belirir.

     ![kopyalama tamamlandıktan sonra, Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin ekran görüntüsü.](./media/vs-2019/clone-complete-azure-devops.png)

1. Klasörlerinizi ve dosyalarınızı görüntülemek için **klasör görünümünü göster** bağlantısını seçin.

     ![kopyalama tamamlandıktan sonra, Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini penceresinin çözümler bölümünün ekran görüntüsü.](./media/vs-2019/show-folder-view-azure-devops.png)

     Visual Studio **Çözüm Gezgini** açılır.

1. Açmak için bir çözüm dosyası (özellikle bir. sln dosyası) aramak üzere **çözümler ve klasörler** bağlantısını seçin.

      ![Visual Studio 2019 sürüm 16,7 ve önceki sürümlerde Takım Gezgini ' çözümler ve klasörler ' bildiriminin ekran görüntüsü.](./media/open-proj-repo-solutions-folders.png)

   Deponuzda bir çözüm dosyanız yoksa, ' hiçbir çözüm bulunamadı ' iletisi görüntülenir. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="open-a-project-from-a-github-repo-with-visual-studio-2017"></a>Visual Studio 2017 ile GitHub deposundan proje açma

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda, **kaynak denetiminden** **Dosya** > > **Aç Aç '** ı seçin.

   **Takım Gezgini Bağlan** bölmesi açılır.

    ![Visual Studio ıde içindeki Takım Gezgini penceresi](./media/open-proj-repo-team-explorer.png)

1. **Yerel Git depoları** bölümünde, **Kopyala**' yı seçin.

    ![Yerel Git depoları bölümünden kopyayı seçin](./media/open-proj-repo-local-git-repo-clone.png)

1. ***Kopyalanacak bir git deposunun URL 'Sini girin** _, deponuzu URL 'sini yazın veya yapıştırın ve ardından _ * ENTER * * tuşuna basın. (GitHub oturum açmak için bir istem alabilirsiniz.)

   deponuzu Visual Studio klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. "**Çözümlerin bir listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini** belirten bir ileti görüntülenir. _ * Çözümler ve klasörler * * öğesini seçin.

   ![Çözüm Gezgini "çözümler ve klasörler" i seçin](./media/open-proj-repo-github-solutions-folders.png)

1. Kullanılabilir bir çözüm dosyanız varsa, "çözümler ve klasörler" açılır menüsünde görünür. bunu seçin ve çözümünüzü açar Visual Studio.

   ![Çözüm Gezgini açılır listesinden ne açmak istediğinizi seçin.](./media/open-proj-repo-github-solutions-folders-picker.png)

   Deponuzda bir çözüm dosyanız (özellikle bir. sln dosyası) yoksa, giriş menüsü "hiçbir çözüm bulunamadı" ifadesini görürsünüz. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

### <a name="review-your-work"></a>Çalışmanızı gözden geçirin

Önceki bölümde tamamladığınız işi denetlemek için aşağıdaki animasyonu görüntüleyin.

   ![GitHub deposunda proje açma animasyonu Visual Studio 2017 ' i kullanarak.](./media/open-project-from-github.gif)

## <a name="open-a-project-from-an-azure-devops-repo-with-visual-studio-2017"></a>Visual Studio 2017 ile Azure DevOps deposundan proje açma

1. Visual Studio 2017'yi açın.

1. Üstteki menü çubuğunda, **kaynak denetiminden** **Dosya** > > **Aç Aç '** ı seçin.

   **Takım Gezgini Bağlan** bölmesi açılır.

    ![Visual Studio ıde içindeki Takım Gezgini penceresi.](./media/open-proj-repo-team-explorer.png)

1. işte Azure DevOps depoya bağlanmanın iki yolu vardır:

      - **barındırılan hizmet sağlayıcıları** bölümünde **Bağlan..**. seçeneğini belirleyin.

        ![Visual Studio ıde içindeki Takım Gezgini penceresinin barındırılan hizmet sağlayıcıları bölümü.](./media/open-proj-repo-azure-devops.png)

      - **bağlantıları yönet** açılan listesinde **bir Project Bağlan seçin...**

        ![Visual Studio ıde içindeki Takım Gezgini penceresinin bağlantıları yönet bölümü.](./media/open-proj-repo-azuredevops-manage-connections.png)

1. **Bağlan bir Project** iletişim kutusunda, bağlanmak istediğiniz depoyu seçin ve ardından **kopyala**' yı seçin.

      ![Visual Studio tarafından oluşturulan ' Bağlan Project ' iletişim kutusu.](./media/open-proj-azure-devops-connect-cloud-clone.png)

    > [!NOTE]
    > liste kutusunda gördükleriniz, erişiminizin olduğu Azure DevOps depolarına bağlıdır.

1. deponuzu Visual Studio klonladıktan sonra, Takım Gezgini kapanır ve Çözüm Gezgini açılır. *Çözümlerin listesini görüntülemek için yukarıdaki çözüm ve klasörler ' e tıkladiğini* belirten bir ileti görüntülenir. **Çözümler ve klasörler ' i** seçin.

      ![Visual Studio ' deki Takım Gezgini çözüm ve klasörler "bildirimi.](./media/open-proj-repo-solutions-folders.png)

   "Çözümler ve klasörler" açılan menüsünde bir çözüm dosyası (özellikle bir. sln dosyası) görüntülenir. bunu seçin ve çözümünüzü açar Visual Studio.

   Deponuzda bir çözüm dosyanız yoksa, açılan menü "hiçbir çözüm bulunamadı" ifadesini görürsünüz. ancak, klasör menüsünden herhangi bir dosyaya çift tıklayarak Visual Studio kod düzenleyicisinde açabilirsiniz.

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki dile özgü öğreticilerden herhangi birine daha fazla bilgi alabilirsiniz:

- [Visual Studio öğreticileri | **C#**](./csharp/index.yml)
- [Visual Studio öğreticileri | **Visual Basic**](./visual-basic/index.yml)
- [Visual Studio öğreticileri | **C++**](/cpp/get-started/tutorial-console-cpp)
- [Visual Studio öğreticileri | **Python**](../python/index.yml)
- [Visual Studio öğreticileri | **JavaScript**, **TypeScript** ve **Node.js**](../javascript/index.yml)

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="<=vs-2019"

- [Visual Studio git deneyimi](../version-control/git-with-visual-studio.md)
- [Git ve Takım Gezgini yan yana karşılaştırın](../version-control/git-team-explorer-feature-comparison.md)
- [Microsoft Learn: Visual Studio Git ve GitHub kullanmaya başlama](/learn/modules/visual-studio-github-push/)
- [Microsoft Learn: Azure DevOps kullanmaya başlama](/learn/modules/get-started-with-devops/)
- [Azure DevOps Services: Azure Repos ve Visual Studio kullanmaya başlayın](/azure/devops/repos/git/gitquickstart/)

::: moniker-end

::: moniker range="vs-2022"

[sürüm denetimi belgelerini Visual Studio](../version-control/index.yml)

::: moniker-end